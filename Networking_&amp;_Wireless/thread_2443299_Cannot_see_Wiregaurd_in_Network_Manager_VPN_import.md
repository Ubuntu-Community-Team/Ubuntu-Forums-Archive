---
title: "Cannot see Wiregaurd in Network Manager VPN import menu"
date: 2020-05-13
forum: Networking &amp; Wireless
---

### Post by jvacek on 2020-05-13
I recently upgraded from 19.10 to 20.04 and I'd like to use my Wireguard config file from my server.

I have the below packages installed, however I am unable to see the Wireguard option under Network Manager.

Is there something I'm missing? Do I need to install something extra? All I can find online is that "it is now native in Network Manager" and a 3rd party config, but I'm a bit confused. I assumed the WG NM integration would have been set up from the get go on 20.04...

[IMG]https://i.imgur.com/wdHTFay.png[/IMG]

```

&#9584;&#9472;$ apt policy network-manager      
network-manager:
  Installed: 1.22.10-1ubuntu1
  Candidate: 1.22.10-1ubuntu1
  Version table:
 *** 1.22.10-1ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu focal/main amd64 Packages
        100 /var/lib/dpkg/status


```

```
&#9584;&#9472;$ apt policy wireguard                                                 100 &#8629;
wireguard:
  Installed: 1.0.20200319-1ubuntu1
  Candidate: 1.0.20200319-1ubuntu1
  Version table:
 *** 1.0.20200319-1ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu focal/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu focal/universe i386 Packages
        100 /var/lib/dpkg/status

```

---

### Post by Tr1p on 2020-05-26
check /etc/wireguard/wg0-client.conf
on the server you want to look at /etc/wireguard/wg0.conf

wg-quit up/down wg0/wg0-client

---

