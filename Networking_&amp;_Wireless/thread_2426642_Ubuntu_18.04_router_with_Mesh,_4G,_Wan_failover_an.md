---
title: "Ubuntu 18.04 router with Mesh, 4G, Wan failover and Open VPN"
date: 2019-09-11
forum: Networking &amp; Wireless
---

### Post by boykeswhite on 2019-09-11
[COLOR=#242729][FONT=Arial]I'm looking for advice on a rather complex Ubuntu 18.04 setup.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Primarily the router will just talk with other "nodes" on a local network using mesh and backhaul 'internet' data through 4G. If mesh is unavailable it should use 4G to talk to another node's 4G for all traffic. This means all routers need to 'listen' on 4G in case another node is sending this way. Additionally, if a node does not have 4G but does have mesh is should use the mesh to connect to another node and use that particular nodes 4G connection. I have attached a few diagrams which hopefully make this more clear. In order to connect the 4G connections together we intend to use OpenVPN (server is already setup and configured).[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The single-board computer and transceiver hardware is:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Gateworks GW6200 with a 2.4Ghz transceiver (wanted as a local mesh radio) and Sierra Wireless 4G modem (for a WAN connection).

All nodes connected: Mesh is primary and web traffic and failover traffic routes through 4G

[Image for all connected noted. The primary connection is mesh with 4G failover]("https://i.stack.imgur.com/gzd63.png")

[A single mesh link is broken so AV1 will be used to route traffic between AV2 and AV 3. 4G is still used as some data is sent to the internet and only local data is sent over the mesh]("https://i.stack.imgur.com/dyAUo.png")

[Here mesh only exists between two nodes to AV3 gets all data sent and received via Wifi until it is back within mesh range.]("https://i.stack.imgur.com/wBoHb.png")

[Here AV1 has lost 4G signal so it uses it's nearest mesh node to sent any internet connections and local traffic over the 4G tunnel]("https://i.stack.imgur.com/CuOeD.png")[/FONT][/COLOR]

---

