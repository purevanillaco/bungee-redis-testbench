# bungee-redis-testbench
easily test a multi-bungee enviroment (using redis) with this docker compose

# ⚠️
> all joining players will feature all the permissions on both the proxy and the servers, as this is designed to be a test bench for server admins. this is not intended for production.

# how to run
## prerequisites
1. install docker
2. make sure you completed the docker post-installation steps in order to prevent permission issues

## executing
1. ``docker compose up``
2. join the server with ``localhost:25565`` (proxy-1) or ``localhost:25566`` (proxy-2)
3. [!] all joining players will have all bungee and paper permissions
4. do ``CTRL+C`` to stop all severs when you are done testing
5. ``docker compose down`` will delete all data

# structure
this is a two-backend (paper), two-proxy (bungee) setup. the following folders will be created when you execute ``docker compose up``:
## backends (paper servers):
- backend/a
- backend/b
## proxies (bungee servers):
- proxy/1
- proxy/2
## .defaults (common files)
additionally, all contents on .defaults will be copied to:
- .defaults/backend > [all backends] backend/a && backend/b
- .defaults/proxy > [all proxies] proxy/1 && proxy/2
- .defaults/common > [all proxies] (proxy/1 && proxy/2) && [all backends] backend/a && backend/b

you can use this folder if your proxies and/or backends should share some common plugins
## bundled plugins
when running ``docker compose up``, the following plugins will be installed and configured:
- BungeePerms: so all players are op-by-default (proxy+backend)
- RedisBungee: obviously... (proxy)
