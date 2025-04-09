# Ansible Collection - lb2255.jumpstarter

Jumpstarter Lab setup (RH Summit 2025)

### Some notes

#### On Developer Hub

We observerd some issues with the developer hub, on first boot where the database migration fails. See this [issue](https://github.com/backstage/backstage/issues/24284). To resolve the issue, we had to manually remove the offending record from the database:

On the Postgresql pod, run the following command:

```shell
psql

# select the database
\c postgresbackstage_plugin_catalog

# delete the offending record
DELETE FROM knex_migrations_lock WHERE is_locked <> 0;
COMMIT;

\q
```


