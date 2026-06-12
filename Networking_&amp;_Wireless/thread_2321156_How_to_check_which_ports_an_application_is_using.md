---
title: "How to check which ports an application is using?"
date: 2016-04-20
forum: Networking &amp; Wireless
---

### Post by lakeshore2985 on 2016-04-20
So I've finally set up my P2P solution with Ubuntu Server, which means I have not a GUI.

I managed to set up deluged & deluge-webui successfully on this server and I believe my ISP is throttling some of the P2P ports.

How do I use the terminal command "*netstat*" to check which ports are currently listening (both TCP/UDP)? Or if there are any other better commands to do such, I greatly appreciate it.

Thanks!

---

### Post by TheFu on 2016-04-20
lsof

---

### Post by lakeshore2985 on 2016-04-20
Could you provide some helpful parameters for "*lsof*" or "*netstat*", maybe?

Your suggestion lists way too much info I am not able to digest. Perhaps a little more guidance would help.

---

### Post by TheFu on 2016-04-21
I just use grep.  For anything more, I always have to check the manpage. Sorry.

---

### Post by SeijiSensei on 2016-04-21
If your being throttled upstream, looking at your computer won't tell you anything.

You could try running nmap from a computer at another location and pointing it at your IP address.

---

### Post by TheFu on 2016-04-21
> **SeijiSensei said:**
> If your being throttled upstream, looking at your computer won't tell you anything.

You could try running nmap from a computer at another location and pointing it at your IP address.

Plus I've read in many places that some home routers had "issues" with the thousands of ports used by p2p software. The default configs didn't (and still may not) be tuned for that use-case.  Usually need to allocate more state table space so all the connections can be properly tracked. Clearly, this would be in the advanced settings, if available.
[https://www.dd-wrt.com/wiki/index.php/Router_Slowdown](https://www.dd-wrt.com/wiki/index.php/Router_Slowdown) describes the issue and possible solutions.

[https://www.debian-administration.org/article/184/How_to_find_out_which_process_is_listening_upon_a_port](https://www.debian-administration.org/article/184/How_to_find_out_which_process_is_listening_upon_a_port) - for lsof stuff.

---

### Post by Nahuel_ on 2016-04-21
With netstat, isn't it:

[FONT=courier new]netstat -tulpn
[/FONT]
Or with lsof:

[FONT=courier new]lsof -i[/FONT]

You can also provide a specific port (ie 80)

[FONT=courier new]lsof -i :80[/FONT]

---

### Post by SeijiSensei on 2016-04-21
> **TheFu said:**
> Plus I've read in many places that some home routers had "issues" with the thousands of ports used by p2p software.
That seems more true of older routers I've used.  Recent models have more memory and thus larger table spaces.  I also lean toward routers that support DD-WRT which presumably has the same iptables masquerading code as the Linux kernel.

It's pretty easy to tell if table overflows are the problem.  Open a browser and go to the home page.  If the DNS fails, you need to power-cycle the router.

---

### Post by TheFu on 2016-04-21
> **SeijiSensei said:**
> That seems more true of older routers I've used.  Recent models have more memory and thus larger table spaces.  I also lean toward routers that support DD-WRT which presumably has the same iptables masquerading code as the Linux kernel.

Yep. But we never know what folks have.  The GigE and WiFi AC routers shouldn't have this limit ... but I've seen some funny settings in Netgear stuff.

Been running an Alix box with pfSense for a few years - swapping in a PCEngines APU w/4G and Intel PRO/1000 NICs soon - just arrived from Switzerland today - less than 72hrs to Atlanta!  US$145 - amazing for a GigE router, 6W, running pfSense/OpenSense .... or any x86 Linux router/server distro (though I won't use Linux on an edge router).  [http://www.pcengines.ch/apu2c4.htm](http://www.pcengines.ch/apu2c4.htm) - feel bad for the folks in the EU - they won't sell to individuals there.  Got a few folks together here and we all bought a couple each to share the shipping/customs fees. ;)  

Did run dd-wrt and openwrt and tomato for a few years, before needing more.  For home use, it was the easy and good choice for most normal IT people.  When ddwrt didn't properly support a new router I'd picked up with fantastic specs, I couldn't wait any longer and was tired of non-x86 equipment needing special binaries. Alix.

The new box should easily handle all the bandwidth and VPN traffic here for a decade while 10G gets cheaper.
Alas, this isn't the "why you should use BSD for edge routers" subforum. ;)

Wonder how lakeshore2985 is making out?  There is lots to know, more than I'll ever grasp. Figure I'm around 10% now and dropping. ;)

---

### Post by lakeshore2985 on 2016-04-21
Alright guys thanks but the problem is not my router. Local ISP here driving clients nuts after they see over 5TB/month worth of upstream lol.

So let's go back to the original proposition shall we... my question is really simple, I can't determine what ports are being used by Deluge software since I set "outgoing ports" to random ports. Is it possible to know? I noticed when I restart the service (or restart deluged), upstream speed is sometimes better and my only guess is ISP throttling some ports since Deluge will randomize the outgoing ports at each restart.

---

### Post by TheFu on 2016-04-21
$ sudo lsof -i |grep firefox

From the lsof manpage:
```
       -i [i]   selects the listing of files any  of  whose  Internet  address
                matches  the  address specified in i.  If no address is speci&#8208;
                fied, this option selects the listing of all Internet and x.25
                (HP-UX) network files.

```
The 'firefox' just shows an example. Replace that with whatever program name is actually run, which usually is NOT the name in the menu.  Still don't see what good this will do, but I haven't done any research on proving that an ISP is throttling/blocking, since where I live it isn't illegal, just slightly embarrassing for them.

---

