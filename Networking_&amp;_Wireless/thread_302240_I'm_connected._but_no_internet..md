---
title: "I'm connected. but no internet."
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by polaris_tyrant on 2006-11-18
I've made myself DSL connection through my DSL Combo Router from Elcon which is connected to my integrated ethernet network card.I used pppoeconf, when I type "sudo pon dsl-provider" it sais that plugin pppoe.so is loaded. I go to firefox but it wont connect, neither does any other web based aplication work.

---

### Post by wieman01 on 2006-11-18
What's the output of:
> route

---

### Post by dataw0lf on 2006-11-18
Or, even better, ip route show.

---

### Post by Amitava on 2006-11-19
First try to enter a ip address instead name in your browser ,e.g,
[http://82.211.81.186/](http://82.211.81.186/) 
if its open ubuntuforums.org then y need to add DNS nameserver entries in /etc/resolv.conf file. get those info from your provider.
you can also try the ping command, check firewall settings ..etc..keep trying.

---

### Post by stream303 on 2006-11-21
Unfortunately, rewriting /etc/resolv.conf is very temporary as it gets overwritten by dhclient eventually.

I'd first try placing your isp's dns addresses in your router's setup page.

If that doesn't work, or you don't have access to the router, you can force the issue by editing the PREPEND line of /etc/dhcp3/dhclient.conf with your ips's nameservers.

The following thread (although I don't need to use OpenDNS option - just my normal isp nameservers) might help:

[http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf](http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf)

---

