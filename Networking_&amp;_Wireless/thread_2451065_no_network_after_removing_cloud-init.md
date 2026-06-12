---
title: "no network after removing cloud-init"
date: 2020-09-26
forum: Networking &amp; Wireless
---

### Post by lister171254 on 2020-09-26
I have two servers (A & C) 
Server A is on 18 LTS and Sever B 20LTS.

After upgrading B to 20LTS, I experienced intermittent network issues and after digging around I found that it uses cloud-init, while server A doesn't.

I uninstalled cloud-init, removed all remaining cloud-init files   and configure Server B to use netplan and 'my' yaml.

The yaml files for both servers are identical (apart from the obvious)

```
network:
  version: 2
  renderer: networkd
  ethernets:
    ens18:
      dhcp4: no
      addresses: [x.x.x.229/24]
      gateway4: x.x.x.1
      nameservers:
              addresses: [x.x.x.x]

```

I cannot get the network on server B to connect. There are no errors in the logs. The only difference I found is when I display the status of networkd

Server A (works)
```
systemd-networkd.service - Network Service
   Loaded: loaded (/lib/systemd/system/systemd-networkd.service; enabled-runtime; vendor preset: enabled)
   Active: active (running) since Thu 2020-09-24 01:39:48 CEST; 2 days ago
     Docs: man:systemd-networkd.service(8)
 Main PID: 721 (systemd-network)
   Status: "Processing requests..."
    Tasks: 1 (limit: 4915)
   CGroup: /system.slice/systemd-networkd.service
           &#9492;&#9472;721 /lib/systemd/systemd-networkd

Sep 24 01:39:48 mail1 systemd[1]: Starting Network Service...
Sep 24 01:39:48 mail1 systemd-networkd[721]: Enumeration completed
Sep 24 01:39:48 mail1 systemd[1]: Started Network Service.
Sep 24 01:39:48 mail1 systemd-networkd[721]: ens18: IPv6 successfully enabled
Sep 24 01:39:48 mail1 systemd-networkd[721]: lo: Link is not managed by us
Sep 24 01:39:48 mail1 systemd-networkd[721]: ens18: Link UP
Sep 24 01:39:48 mail1 systemd-networkd[721]: ens18: Gained carrier
Sep 24 01:39:49 mail1 systemd-networkd[721]: ens18: Gained IPv6LL
Sep 24 01:39:49 mail1 systemd-networkd[721]: ens18: Configured

```

Server B (fails; see attached)

The difference in the status is that Server B does not gain carrier; not sure why

---

