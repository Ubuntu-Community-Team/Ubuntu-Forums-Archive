---
title: "USB Network Interface issue"
date: 2016-09-15
forum: Networking &amp; Wireless
---

### Post by trispembo on 2016-09-15
I've posted something over at the Apple Hardware forum, but I've had not response. And to be frank, I'm not sure it's actually Apple specific, so I'm posting this here too in the hope someone may be able to help me.

[COLOR=#000000]I've been troubleshooting an Apple USB Network Adaptor. I can't tell whether it's something I'm doing wrong, or a driver that's playing up/failing. However, I suspect it may be an ASIX driver issue (corrupted?).[/COLOR]

[COLOR=#000000]On my MacMini 2,1 I have dual boot OS X and Ubuntu 14.04 and am trying to set it up as a linux gateway/router/firewall. So I have two NICs installed (one onboard, one USB). When I boot into OSX both NICs are working fine. [/COLOR]

[COLOR=#000000]When I boot into 14.04 the onboard ethernet adapter is working fine. However, I can't seem to get the USB adaptor to work properly. [/COLOR]

[COLOR=#000000]It appears in [/COLOR][COLOR=#ff0000]ifconfig[/COLOR][COLOR=#000000], is correctly set up in [/COLOR][COLOR=#ff0000]/etc/network/interfaces[/COLOR][COLOR=#000000][COLOR=#000000],[/COLOR][/COLOR][COLOR=#000000] appears in [/COLOR][COLOR=#FF0000]/etc/udev/rules.d/70[/COLOR][COLOR=#FF0000]-persistent-net.rules [/COLOR][COLOR=#000000][COLOR=#000000]and it[/COLOR][/COLOR][COLOR=#000000][COLOR=#000000] can be successfully pinged from the host machine, [/COLOR][/COLOR][COLOR=#000000][COLOR=#000000]but it just won't pass [/COLOR][/COLOR][COLOR=#000000]traffic. I've flushed iptables and tried as static and dhcp. I've rebooted multiple times. It just won't work.  

I created a lshw.txt file and offered this info about the network interface driver:

[/COLOR][COLOR=#ff0000]driver=asix
firmware=ASIX AX88772 USB 2.0[/COLOR][COLOR=#000000]
[/COLOR]
[COLOR=#000000]Do I need to reinstall a driver? Is it ever possible to reinstall a kernel driver like ASIX? Is there something more I should be doing?[/COLOR]

[COLOR=#000000]Any help would be appreciated.[/COLOR]

---

### Post by howefield on 2016-09-15
Duplicate thread closed.

---

