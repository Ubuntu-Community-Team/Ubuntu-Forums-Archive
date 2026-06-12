---
title: "Cant access router config page"
date: 2014-08-09
forum: Networking &amp; Wireless
---

### Post by whatthefunk on 2014-08-09
I got new internet yesterday and although the internet is working, I cant get into the router config page.  When I first got it, I was able to access it via 192.168.1.1 but then after I attempted (and failed) to get my wireless router working, the config page stopped loading in my browser.  I no longer have the wireless router hooked up so the connection goes direct from my router to my pc.  I am unable to ping my router and the gateway address does not show up anywhere.  I've tried factory resets and countless power cycles and computer restarts and nothing is working.  How can I regain access to my router?

route output:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         *               0.0.0.0         U     0      0        0 ppp0
118.23.62.123   *               255.255.255.255 UH    0      0        0 ppp0

```

ifconfig output:
```

eth0      Link encap:Ethernet  HWaddr bc:5f:f4:1c:46:d2  
          inet6 addr: 2001:a452:ea:a100:f4d5:3a77:8b42:6ce0/64 Scope:Global
          inet6 addr: fe80::be5f:f4ff:fe1c:46d2/64 Scope:Link
          inet6 addr: 2001:a452:ea:a100:be5f:f4ff:fe1c:46d2/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3308 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2145691 (2.1 MB)  TX bytes:509900 (509.9 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:343 errors:0 dropped:0 overruns:0 frame:0
          TX packets:343 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27264 (27.2 KB)  TX bytes:27264 (27.2 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:153.199.75.210  P-t-P:118.23.62.123  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1454  Metric:1
          RX packets:3217 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2066400 (2.0 MB)  TX bytes:416623 (416.6 KB)

```

---

### Post by whatthefunk on 2014-08-09
Did some more testing.  I plugged my laptop into the router and had no problem accessing the router page so this is clearly a problem with my main computer.  Is there a way to reset all the network settings so I can start from scratch?

---

### Post by mn_voyageur on 2014-08-10
Your ifconfig is not dislaying: wlan0  

I hate to be simplistic, but have you checked your wireless setting?  (Is it enabled?)  (Someone with more beans may have a better idea.)

MarkN

---

### Post by JKyleOKC on 2014-08-10
How do you have your router connected to the PC? Your ifconfig result doesn't look like any I've seen before; it includes a "ppp0" interface with an IP address that's not on the same subnet as your router's 192.168.1.1. To the best of my knowledge, the "ppp" prefix is used only for dial-up modems.

If your router is connected through the usual RJ-45 cable, I would expect the "eth0" interface to be the one used. You may need to work with the Network Manager a bit to get things straightened out. Unfortunately I can't help much there since I'm using Xubuntu which has different configuration files.

EDIT: It's possible that simply shutting down the machine, then starting it up again, might clear things up. Also I forgot to mention that lack of any routing to the "192.168.1.0" subnet is why you cannot access the router. Once the "eth0" interface gets cleared up everything should work properly again. The "wlan0" interface mentioned above would be for wireless connection, and as I understand your original post, you've abandoned use of wireless for now...

---

### Post by whatthefunk on 2014-08-10
> **JKyleOKC said:**
> How do you have your router connected to the PC? Your ifconfig result doesn't look like any I've seen before; it includes a "ppp0" interface with an IP address that's not on the same subnet as your router's 192.168.1.1. To the best of my knowledge, the "ppp" prefix is used only for dial-up modems.

If your router is connected through the usual RJ-45 cable, I would expect the "eth0" interface to be the one used. You may need to work with the Network Manager a bit to get things straightened out. Unfortunately I can't help much there since I'm using Xubuntu which has different configuration files.

Yes, this is the problem.  The only way Ive found to connect is with the terminal program pppoeconf.  If I dont use that program, when I plug the network cable into the computer, it says eth0 is connected, but then offers no way for me to enter log-in details.  Network manager doesnt even see the connection and when I try to enter it in manually, offers no way to attempt to connect.  However, if I dont use pppoeconf, my ifconfig output looks normal.

> EDIT: It's possible that simply shutting down the machine, then starting it up again, might clear things up. Also I forgot to mention that lack of any routing to the "192.168.1.0" subnet is why you cannot access the router. Once the "eth0" interface gets cleared up everything should work properly again. The "wlan0" interface mentioned above would be for wireless connection, and as I understand your original post, you've abandoned use of wireless for now...

How do I clear up the eth0 interface?  And yes, Im not concerned with the wireless at the moment.  My hope is that once I get this problem solved, the wireless router issue will solve itself.:rolleyes:

---

### Post by steeldriver on 2014-08-10
What do you mean exactly by "got new internet yesterday"? did that include new hardware from the ISP? it looks like you are connecting directly via a *modem*, rather than a *router*

---

### Post by whatthefunk on 2014-08-10
> **steeldriver said:**
> What do you mean exactly by "got new internet yesterday"? did that include new hardware from the ISP? it looks like you are connecting directly via a *modem*, rather than a *router*

I got new internet.  The ISP gave me a router.

---

### Post by JKyleOKC on 2014-08-10
I'm beginning to suspect that what we have here (to misquote the movie) may be a failure to communicate.

Is it possible that the "router" provided by your new ISP is actually just a modem? And the ISP folk are wrongly calling it a router?

Your report that the laptop can access the router configuration page perfectly indicates otherwise; a plain modem would not usually have such a page. However the IP shown by your listing for ppp0 is definitely NOT a LAN address; it appears to be a WAN address that normally would not be provided by a router! And personally, I've never before encountered a situation in which pppoe configuration was necessary to get out through a true router.

You might try booting the desktop with a live CD/DVD or USB stick, as you do when making the initial installation. This would bring it up with a completely virgin set of network interfaces and should then show connection via eth0 when you do a "sudo ifconfig -a" command in a terminal window. If it does, and eth0 has an IP (inet) address starting with "192.169.1" rather than the inet6 address of your earlier listing, then you should be able to reach the configuration page from the live session at least.

That won't be a cure, but it may well help us figure out just how to clean up the appropriate network configuration files in your actual installation! It's possible, for instance, that something in the router configuration itself might be causing the problem -- and in that case the eth0 IP address might well stay with the inet6 condition rather than correcting itself.

---

### Post by whatthefunk on 2014-08-12
Booted from live disk and was initially able to reach my router, but couldnt connect.  I tried every possible setting configuration in network manager but nothing worked.  I ended up connecting with pppoeconf again and once I did that, my access to the router was gone and ifconfig output was identical to what I have on the normal instalation.  It appears that the problem is with pppoe connections...

---

### Post by steeldriver on 2014-08-12
The point is if you are connected via PPP then you are connecting to a **modem **not a router, and your computer will appear to be on the ISP's network public segment rather than a private LAN - we'd need to have more details about your network hardware to help you resolve this I think

---

### Post by JKyleOKC on 2014-08-12
> **steeldriver said:**
> The point is if you are connected via PPP then you are connecting to a **modem **not a router, and your computer will appear to be on the ISP's network public segment rather than a private LAN - we'd need to have more details about your network hardware to help you resolve this I thinkThis is **probably** the case, but at least one major ISP uses a pppoe variation to control access to its network. For the years that I was on AT&T's "ADSL" service, it used a pppoe-style log-in, even on what they called "static" addresses (which were not truly static, just dynamically assigned addresses that were not allowed to change).

However the inet address of "153.199.75.210" shown for ppp0 is definitely not assigned by a local router, and the lack of any IPv4 address on eth0 is definitely suspicious.

It might help if whatthefunk tells us which ISP he's using, and the make/model of the router involved (all of them, if there's more than one). This is turning into quite a mystery...

FWIW, **whois** shows the "153.199.0.0/17" network to be assigned to "Open Computer Network" by "NTT COMMUNICATIONS CORPORATION" in Japan. Perhaps this is a proxy situation? I know they exist but have absolutely no more knowledge about such an area.

---

### Post by whatthefunk on 2014-08-12
I live in Japan and my carrier is OCN, Open Computer Network. The router is a PR-500MI.  Looks like this:
[IMG]https://web116.jp/shop/hikari_r/pr_500mi/img/pr_500mi_back.jpg[/IMG]
[IMG]https://web116.jp/shop/hikari_r/pr_500mi/img/pr_500mi.jpg[/IMG]

---

### Post by JKyleOKC on 2014-08-12
> **whatthefunk said:**
> I got new internet yesterday and although the internet is working, I cant get into the router config page.  When I first got it, I was able to access it via 192.168.1.1 but then **after I attempted (and failed) to get my wireless router working, the config page stopped loading in my browser**.  I no longer have the wireless router hooked up so the connection goes direct from my router to my pc.  I am unable to ping my router and the gateway address does not show up anywhere.  I've tried factory resets and countless power cycles and computer restarts and nothing is working.  How can I regain access to my router?I just re-read this and in view of your most recent reports, I had a sudden thought. Did your attempt to get the wireless router working perhaps include making any change to the settings at the 192.168.1.1 configuration page, or any sub-page reached from a menu there?

I've seen several how-to postings on the web that involve setting the initial unit to "pass-through" mode or what is sometimes referred to as "DMZ." This setting disables the acrual routing portion of the unit and turns it into just a modem, so that it passes packets unchanged on to another unit located between it and the computer. It's possible (but this is only a wild guess on my part) that such a setting could be linked to a specific MAC address so that it applied only to packets to/from one specific unit behind it -- which would let your laptop work properly but apply the change only to your desktop.

This makes steeldriver's request for more data, and mine for the make/model of everything involved, a bit more essential, I think. If this wild guess is anywhere near correct, I'm confident we will eventually be able to tell you how to undo it and get everything back to normal once again, though...

---

### Post by JKyleOKC on 2014-08-12
Okay, that's a rather new model from Netgear and the web page shows that it is, itself, a wireless router. I just searched the Netgear support site looking for a manual that covers it but found nothing there. More and more I suspect that it's a misconfiguration of the unit that puts it into pass-through mode for your desktop, but I have no idea how to fix that. Steeldriver???

---

### Post by steeldriver on 2014-08-12
... maybe a hard reset of the modem/router box (@whatthefunk can you see a reset button on the unit?) and then start over... ?

---

### Post by whatthefunk on 2014-08-15
Got it!  I cleared my iptables (*sudo iptables -F*) and set managed to "true" in /etc/NetworkManager/NetworkManager.conf.  After restarting the service network-manager (*sudo service network-manager restart*), I did a hard reset of both the router and the wireless router.  I then did a full power cycle and instead of entering my ISP login details in through Ubuntu, I put them in directly into the router via the browser.  I then did another full power cycle and when I turned the computer back on, everything was working fine.  
Thanks for assistance!

---

### Post by JKyleOKC on 2014-08-15
Great!

Please mark the thread as solved. The link in my signature line tells how to do this.

---

