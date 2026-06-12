---
title: "No internet after changing router"
date: 2016-08-12
forum: Networking &amp; Wireless
---

### Post by mike.00 on 2016-08-12
Hello 
I had to buy a new router for my home network and now I can't access internet on a computer with Ubuntu (15.10).
Everything works fine on other computers with Windows operating system (both LAN and WiFi). 
Firefox gives "Server not found" error on every webpage I try to open and Chrome says "server DNS address could not be found". 
I use DHCP and looks like ethernet configuration is obtained properly.
Here is the output of
```
ifconfig -a 
```

```

enp0s25   link encap:Ethernet HWaddr 00:21:9b:64:9c:3e
              inet addr:192.168.1.3 Bcast:192.168.1.255 Mask 255.255.255.0
              inet6 addr: fe80::221:9bff:fe64:9c3e/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST MTU:1500 Metric: 1
              RX packets:3503 errors:0 dropped:0 overruns:0 frame:0 
              TX packets:4905 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000
              RX bytes:429894 (429.8 KB) RX bytes:419507 (419.5 KB)
              Interrupt:21 Memory:fe9e0000-fea00000



lo           link encap:Local loopback
              inet addr:127.0.0.1 Mask 255.0.0.0
              inet6 addr: ::1/128 Scope:Host
              UP LOOPBACK RUNNING MTU:65536 Metric: 1
              RX packets:3202 errors:0 dropped:0 overruns:0 frame:0 
              TX packets:3202 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000
              RX bytes:215083 (215.0 KB) RX bytes:215083 (215.0 KB)

```

Default route is 192.168.1.1
Primary DNS 10.101.208.1

Everything seems to be OK. There is a webpage based configuration system for that router and my PC is identified properly (name, IP, MAC). I tired to manually delete old connection and add a new one in Ubuntu but nothing changes - configuration from DHCP is obtained bu internet still doesn't work, also tried to disable standard Ubuntu Firewall.
I don't know why I can't access internet on that Ubuntu PC. Few days ago while I still had that old router everything was working fine.
Is it Ubuntu or my new router?
Any ideas?
Best regards,
Mike

---

### Post by kurt18947 on 2016-08-12
I doubt this will cure your underlying problem but it's something to keep in your bag of tricks. I've had problems with wifi when creating a connection that goes crossways. I'd tried to delete the flawed connection but bits seemed to stick around and cause problems with subsequent attempts. I discovered a handy little applet which is not easily found in *buntu 16.04. To launch it I use <alt>F2 to open the 'run' box then type this:

```
nm-connection-editor
```

You can then delete failed connection attempts cleanly.

---

### Post by wildmanne39 on 2016-08-12
Hello, every time you change routers you need to remove all connections from network manager and reboot the computer then let network manger find your network. Also I am sure you know 15.10 is outdated there will be no more updates for it and that will put your system at risk.

---

### Post by steeldriver on 2016-08-12
I'm not a networking expert by any means, but it seems odd to me that the primary DNS would be on a different *private *LAN network (10.a.b.c) than the host's address (192.168.x.y). 

Do your other (working - Windows) computers have the same configuration? You can check with Windows command ipconfig

---

### Post by mike.00 on 2016-08-13
Thanks for answering so quickly. 
Unfortunately deleting all connections via Network Manager and setting up new connection didn't change anything. Network configuration was OK but no internet access. I was able to ping other computers in my home network and even "external" IP addresses. However I could not ping web addresses using domain names. For example I could *ping 91.189.89.115* but *ping [www.ubuntu.com](www.ubuntu.com)* would result in *"unresolved hostname"* error.
My limited knowledge suggested that it might by DNS-related issue. After googling a little I found out about **resolv.conf** file and found this solution

[URL="http://askubuntu.com/questions/690511/how-to-change-dns-in-ubuntu-15-10"]http://askubuntu.com/questions/690511/how-to-change-dns-in-ubuntu-15-10

[/URL]After trying to "disable" *dnsmasq* my **resolv.conf** file looks like this:

[LEFT][COLOR=#111111][FONT=Ubuntu] ```
[SIZE=2][COLOR=#111111][FONT=Ubuntu][COLOR=#111111][FONT=Ubuntu]nameserver 10.101.208.1[/FONT][/COLOR][/FONT][/COLOR]
[/SIZE][LEFT][SIZE=2][COLOR=#111111][FONT=Ubuntu]nameserver 85.198.198.199
[/FONT][/COLOR][/SIZE][COLOR=#111111][FONT=Ubuntu][LEFT][SIZE=2][COLOR=#111111][FONT=Ubuntu]nameserver 8.8.8.8[/FONT][/COLOR][/SIZE] 
[/LEFT]
[/FONT][/COLOR]
[/LEFT]

```[LEFT][COLOR=#111111][FONT=Ubuntu][LEFT][COLOR=#111111][FONT=Ubuntu]
Now I can access internet, webpages open as they should in both Firefox and Chrome. 
What could be the cause of this issues with DNS?
Changing resolv.conf mechanism in the way I did...is it an acceptable solution to my problem? [/FONT][/COLOR]
[/LEFT]
[/FONT][/COLOR][/LEFT]
[/FONT][/COLOR][/LEFT]
> **Wild Man said:**
> Also I am sure you know 15.10 is outdated there will be no more updates for it and that will put your system at risk.

I will update to 16.04 promptly.
Do you think that after updating I might again experience problems with internet connection? Or maybe updating to 16.04 will fix everything as it should be?

---

### Post by kurt18947 on 2016-08-13
I too think it's a DNS issue, due to entering I.P. addresses working. My primary router is an Actiontec designed to work with Verizon FiOS. I suspect it may have some features not found on retail routers but one of the features is the ability to choose DNS servers. Verizon has their own DNS servers but I've found others that seem faster. You could poke around the router's UI and see if/what it has for DNS server. I googled public DNS and found [this]("http://public-dns.info/"). You do have your PC's network connection set to its default DHCP, yes?

---

### Post by wildmanne39 on 2016-08-13
> **mike.00 said:**
> Thanks for answering so quickly. 
Unfortunately deleting all connections via Network Manager and setting up new connection didn't change anything. Network configuration was OK but no internet access. I was able to ping other computers in my home network and even "external" IP addresses. However I could not ping web addresses using domain names. For example I could *ping 91.189.89.115* but *ping [www.ubuntu.com](www.ubuntu.com)* would result in *"unresolved hostname"* error.
My limited knowledge suggested that it might by DNS-related issue. After googling a little I found out about **resolv.conf** file and found this solution

[URL="http://askubuntu.com/questions/690511/how-to-change-dns-in-ubuntu-15-10"]http://askubuntu.com/questions/690511/how-to-change-dns-in-ubuntu-15-10

[/URL]After trying to "disable" *dnsmasq* my **resolv.conf** file looks like this:

[LEFT][COLOR=#111111][FONT=Ubuntu] ```
[SIZE=2][COLOR=#111111][FONT=Ubuntu][COLOR=#111111][FONT=Ubuntu]nameserver 10.101.208.1[/FONT][/COLOR][/FONT][/COLOR]
[/SIZE][LEFT][SIZE=2][COLOR=#111111][FONT=Ubuntu]nameserver 85.198.198.199
[/FONT][/COLOR][/SIZE][COLOR=#111111][FONT=Ubuntu][LEFT][SIZE=2][COLOR=#111111][FONT=Ubuntu]nameserver 8.8.8.8[/FONT][/COLOR][/SIZE] 
[/LEFT]
[/FONT][/COLOR]
[/LEFT]

```[LEFT][COLOR=#111111][FONT=Ubuntu][LEFT][COLOR=#111111][FONT=Ubuntu]
Now I can access internet, webpages open as they should in both Firefox and Chrome. 
What could be the cause of this issues with DNS?
Changing resolv.conf mechanism in the way I did...is it an acceptable solution to my problem? [/FONT][/COLOR]
[/LEFT]
[/FONT][/COLOR][/LEFT]
[/FONT][/COLOR][/LEFT]


I will update to 16.04 promptly.
Do you think that after updating I might again experience problems with internet connection? Or maybe updating to 16.04 will fix everything as it should be?It is very possible you will have wireless issues that will have to be solved, especially if you upgrade and do not do a fresh install.

---

