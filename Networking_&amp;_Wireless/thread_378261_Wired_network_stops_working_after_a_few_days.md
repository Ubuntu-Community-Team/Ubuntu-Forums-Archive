---
title: "Wired network stops working after a few days"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by hayawardh on 2007-03-07
I am having a strange problem. 

I am running Ubuntu 6.06 LTS (64 bit) on a Gateway laptop (MX3417, AMD64). 

As soon as I install Ubuntu, wired Internet works fine. A few days (4-5) after installing, when I boot up my laptop, it will just stop working. This has happened 4 times to me so far. The problem is cured by reinstalling, but then again comes up. I am able to access the Internet through the wired network on Windows on the same laptop. 

I had copied all network configuration files and command outputs (that I knew) in the working copy (ifconfig, dmesg, /etc/network/interfaces, lspci, route -n, arp), and compared them to after the net stops working. 

The only difference I am able to find is in dmesg: 

Working copy: 

$ dmesg | grep eth0
forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.48.
eth0: forcedeth.c: subsystem: 0107b:0317 bound to 0000:00:14.0
eth0: no link during initialization
ADDRCONF(NETDEV_UP): eth0: link is not ready
eth0: link up
ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
eth0: no IPv6 routers present

Currently: 

$ dmesg | grep eth0
dmesg | grep eth0
eth0: forcedeth.c: subsystem: 0107b:0317 bound to 0000:00:14.0
eth0: no link during initialization
eth0: link up

Both times, I plugged in the ethernet cable after Ubuntu boots.

Note the ADDRCONF thing difference .. what is this? Could there be any other problem?

Output of lspci: 
0000:00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)

ping says destination host unreachable even for my gateway, ping worked fine just after installation. 

Hayawardh

(Wireless works just fine, anytime. )

---

### Post by Mr. C. on 2007-03-07
A number of people seem to be having issues with various nVidia ethernet controllers.

You do not need to reinstall.

You can bring the interface (network card) down and then back up again.

For example

ifconfig eth0 down
ifconfig eth0 up

---

### Post by hayawardh on 2007-03-07
Mr. C, 

Thanks for the reply. 

I tried ifconfig eth0 down and up, but there is no change. In fact, I've tried all sorts of things before, including making eth0 the default, disabling wlan0 etc. 
As you say, the problem seems to be with the nVidia driver. 

One thing I am able to surely tell is that when I plug in the ethernet cable, dmesg says 
eth0: link up, 
and when I take the cable out, it says
eth0: link down. 

But previously the plugging in of the cable used to give the additional sentence
ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

Should I post in the nVidia driver forums or something Mr. C? Please guide me. Thanks.
Hayawardh

---

### Post by hayawardh on 2007-03-07
Apparently I was wrong about my supposition. 

I did rmmod forcedeth and insmod /../forcedeth.ko
and the ADDRCONF( .. ) lines came in dmesg. 

So there seems to be some other problem :( 

Any ideas?
Hayawardh

---

### Post by conjur3r on 2007-03-07
Are you using Gnome Network Manager applet?  If so, that program only lets you have one network device connected at a time.  Eg, if I'm using my wireless and then plug in my wired ethernet cable, it automatically disables wireless and goes to wired.

You could try comparing your DNS details.  These settings are found in /etc/resolv.conf.  This sounds plausible as you haven't mentioned anything about the network card losing an IP address when it stops working.

If you obtain dynamic IP addresses, you could try manually requesting it again with:
# sudo dhclient eth0
substituting eth0 with the network device.

This command, if successful, will give you the information you need to work on the network.  This usually includes DNS server details too.

---

### Post by hayawardh on 2007-03-07
> Are you using Gnome Network Manager applet? If so, that program only lets you have one network device connected at a time. 

I don't use nm-applet. I use the network-admin provided by Ubuntu. Network Manager is not installed on my system, I just checked. 

> You could try comparing your DNS details.

I am not even able to ping my gateway from Ubuntu (but am able to in Windows), so DNS couldn't be the problem. 

> If you obtain dynamic IP addresses

I am using a static IP address. 

Thanks. 
Hayawardh

---

### Post by Mr. C. on 2007-03-07
> **hayawardh said:**
> I am having a strange problem. 
$ dmesg | grep eth0
forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.48.
eth0: forcedeth.c: subsystem: 0107b:0317 bound to 0000:00:14.0
eth0: no link during initialization
ADDRCONF(NETDEV_UP): eth0: link is not ready
eth0: link up
ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
eth0: no IPv6 routers present

This indicates the device was not ready to begin its initialization procedure when the system was booting, but came up shortly after that.
The NETDEV_CHANGE indicates the define changed state from down to up.

> **hayawardh said:**
> 
Both times, I plugged in the ethernet cable after Ubuntu boots.

Note the ADDRCONF thing difference .. what is this? Could there be any other problem?


The device cannot configure itself with its "link partner" if a cable is not plugged in.  Part of the initialization of the network driver is to determine speed and dupex settings.  How do you think it knows what speed to operate at  (10 or 100mbps)?

Plugging in the cable, allows the device to complete its initialization with its link partner; it establishes Link.  The device informs the driver that a cable has been plugged in, so that the driver can complete its job, and send you those nice (confusing) messages.

As I mentioned, it appears there are some issues with the packaged nvidia driver for some user configurations. I haven't spent time looking too deeply, but others have reported updating the driver solves their issues.  The driver version shown in your output shows it is indeed.

---

### Post by hayawardh on 2007-03-07
Thanks a lot Mr. C. 
That clears a lot of confusion. 

Can you tell me where I could find the latest forcedeth driver? Should I look into the latest kernel versions? 

Updating this driver will require a kernel recompile right? 

Thanks. 
Hayawardh

---

### Post by Mr. C. on 2007-03-07
The latest version of the driver is on nvidia's site:

[http://www.nvidia.com/object/linux_nforce_1.21.html](http://www.nvidia.com/object/linux_nforce_1.21.html)

I believe the 1.21 package is the latest.  This contains the .60 version of the driver.

You will either need to recompile the kernel with the new driver in place, or you may be able to find some references here from others who have done that.  I didn't look that deeply into who had what.

Some dais that the 2.6.20 version of the kernel worked just fine.  The 2.6.20 version has version .59 of the driver; .60 adds recoverable error support (i did not look in detail at the changes).

The current Ubuntu kernel I believe uses .54 of the driver.  The change logs are:

 *      0.55: 22 Mar 2006: Add flow control (pause frame).
 *      0.56: 22 Mar 2006: Additional ethtool and moduleparam support.
 *      0.57: 14 May 2006: Moved mac address writes to nv_probe and nv_remove.
 *      0.58: 20 May 2006: Optimized rx and tx data paths.
 *      0.59: 31 May 2006: Added support for sideband management unit.
 *      0.60: 31 May 2006: Added support for recoverable error.

Without looking at the code, I cannot say how any of these will impact a given situation.

Best of luck!
MrC

---

### Post by hayawardh on 2007-03-08
I compiled kernel 2.6.20, which has forcedeth version 0.59, and eth0 has started working again!
However, I have to check for 4-5 days to see if it stops working, will post the results here. 
Thanks a LOT Mr. C

However, my wireless card is not detected anymore. What driver should I download or what config option of the kernel should I check? 

Hayawardh

---

### Post by Mr. C. on 2007-03-08
That's great news!

I haven't a clue why the wireless card is no longer functional.  I didn't notice any mention of brand / type in the previous posts.

Perhaps create a new post with the appropriate title, so that others can help as well (they might not pickup the wireless aspect here due to the current subject).

MrC

---

### Post by hayawardh on 2007-03-17
The driver is working perfectly now! Thanks everyone. 

I upgraded to 2.6.20 which has version 0.59 of forcedeth.c, as suggested, and all works excellent now. 

Hayawardh

---

### Post by Mr. C. on 2007-03-17
Nice work!

---

