---
title: "Unable to detect Killer Wireless network adapter (16.04)"
date: 2017-12-27
forum: Networking &amp; Wireless
---

### Post by Max-Tyson on 2017-12-27
Hi all,

I've got a fresh new installation of Ubuntu 16.04 on an Asus Zenbook that previously had windows 10. I installed Ubuntu 16.04 over Windows 10 and everything was going great. I was able to reboot, sleep, shutdown without any problems and I would automatically reconnect to my wifi. However this morning I am unable to connect to wifi. I think the problem is that Ubuntu can't detect my wireless adapter now. 

I've input the following code:

```
sudo lshw -c network
```

and the output I get is:

```
*-network                      description: Ethernet interface
       physical id: 1
       logical name: enp0s20f0u2
       serial: 06:be:42:9a:55:2e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.29 link=yes multicast=yes

```

I've tried updating firmware with no success. I have a Killer Wireless 1535 network adapter that worked fine yesterday. For some reason today when I booted up my Bluetooth and wifi adapter just aren't being detected even though it worked perfectly yesterday.

I would greatly appreciate any and all help.

EDIT:

I am a stupid, I was able to fix my problem with the sudo apt-get update and sudo apt dist-upgrade codes.

EDIT 2:

I am not entirely stupid. After using the sudo apt-get update and sudo apt dist-upgrade commands in the console my problem was fixed, however this morning the problem came back and my wireless adapter was not detected. But the weird thing is that after another reboot this morning the problem went away. It seems really random when ubuntu can't detect my network adapter. 

If anyone has any solutions I would greatly appreciate the help, it's no longer a major issue but is annoying to have to boot my laptop multiple times before it can connect to my wifi.

---

