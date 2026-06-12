---
title: "Wireless Connection &amp; Browsing Issues"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by kev3124 on 2008-05-28
I'm running hardy 8.04 and have all updates installed.

I use wireless internet and my laptop is only 20' away from the router.

Here are the problems:

- 1. When opening a website in a new tab or queuing up a few sites in tabs, the new tabs will not load the sites. I recieve a "cannot locate server..." type of message. To make it work when this happens I click on the wireless network icon in the task bar, then click on the name of the network that I am already connected to. This seems to 'refresh' the connection. 

- 2. When going from one site to another (ex: browsing ubuntu.com, type youtube.com into the address bar, then hit enter) the new site will not load unless I 'refresh' the connection like I described above. This does not occur every time, but quite often.

- 3. Scrolling though websites is very choppy. Small finger movements on the touch pad result in pages scrolling much further than they should. (its not a hardware settings issue, this only happens with firefox).


If anyone could help me with one, or all of these issues I would really appreciate it. I will check this post often to provide more information if asked. 

Thanks in advance!



Here is the full error message >>>

[PHP]Address Not Found          

Firefox can't find the server at [www.ubuntuforums.org](www.ubuntuforums.org).         

The browser could not find the host server for the provided address.

    * Did you make a mistake when typing the domain? (e.g. "ww.mozilla.org" instead of "www.mozilla.org")
    * Are you certain this domain address exists?  Its registration may have expired.
    * Are you unable to browse other sites?  Check your network connection and DNS server settings.
    * Is your computer or network protected by a firewall or proxy?  Incorrect settings can interfere with Web browsing.[/PHP]

Here is what came up when I ran "lshw -C network"
[PHP]
kevin@kevin-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:ce:08:18
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.2.4 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:a5:bf:f4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes[/PHP]

---

### Post by superprash2003 on 2008-05-29
when you are not able to access the pages in firefox , try pinging any site.. and post output here.( go to the terminal and type ping google.com and post output)

---

### Post by kev3124 on 2008-05-29
While having the connection error message, I ran the ping code. 

[PHP]kevin@kevin-laptop:~$ ping www.google.com
ping: unknown host www.google.com[/PHP]

When the connection was working I ran it again and got:
[PHP]
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=1 ttl=246 time=56.2 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=2 ttl=246 time=38.3 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=3 ttl=246 time=43.9 ms
[/PHP]
It continued to display similar messages.

---

### Post by kev3124 on 2008-05-30
Bump.

I could really use some advice. The problem hasn't gotten any better. Any Ideas?

---

