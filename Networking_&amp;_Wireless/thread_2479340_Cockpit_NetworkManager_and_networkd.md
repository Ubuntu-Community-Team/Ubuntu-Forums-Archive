---
title: "Cockpit NetworkManager and networkd"
date: 2022-09-21
forum: Networking &amp; Wireless
---

### Post by plazman30 on 2022-09-21
I installed cockpit on my home 22.04 ubuntu server. This started as 16.04 and I upgraded it to 18.04, 20.04 and 22.04.

Under 22.04, I installed cockpit.

Cockpit is giving me errors on updates. When I go to the update screen, it tells me I am not online.

Doing some Googling today, I found that cockpit seems to require NetworkManager.

My Netplan yaml looks like this:

```

network:
  version: 2
  renderer: networkd
  ethernets:
    eth0:
      dhcp4: no
      addresses: [172.25.100.5/24]
      gateway4: 172.25.100.1
      nameservers: 
        search: [xxx.net]
        addresses: [172.25.100.2]

```

According my DuckDuckGo searches, I need to switch the renderer to NetworkManager in order to get Cockpit to work.

How do I switch to NetworkManager, but continue to use a static IP address.  Can I just change the renderer and reboot?

Or is there some way to get cockpit to work with networkd insead of NetworkManager?

---

### Post by TheFu on 2022-09-26
I cannot believe that cockpit needs network-manager. That makes zero sense, as network-manager isn't even installed on servers and that is were cockpit would typically be installed.  Do you have a reference link?

BTW, is eth0 really correct?  All my NICs got new, funky names, when systemd took over.  Names like ens3 or enp3s0 are what I'm seeing.

---

