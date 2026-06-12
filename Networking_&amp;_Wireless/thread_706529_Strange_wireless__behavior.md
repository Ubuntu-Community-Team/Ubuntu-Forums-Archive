---
title: "Strange wireless  behavior"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by PlancksCnst on 2008-02-24
I have two systems which connect to a router wirelessly.  Each one works if it is the only one connected, however if I try and connect both simultaneously, neither works, and the router doesn't work over wireless any more (the wired connections still work fine) until I reboot the router.  Any ideas?
Following are some details:

Actiontec MI424WR Router
Netgear WG111 802.11G USB stick
Linksys WET11 802.11B wired<->wireless Bridge

The network uses static IPs on a 192.168.1.x 225.225.225.0 subnet.
The machines have different IP addresses.
Bridge has a clone-mac-address function; it doesn't fix the problem.
Router has a "Wireless Mode" option, set to "Mixed accepts 802.11b and 802.11g connections"
Using WEP 128 bit

---

### Post by nixscripter on 2008-02-24
Which machines have the static IPs, the wired ones? How do the wireless machines get an IP?

If some are static and some are dynamic, make sure that the router isn't trying to give them the same IP (i.e. the dynamic range doesn't overlap the static IPs).

---

### Post by PlancksCnst on 2008-02-25
All have static IPs.  The wireless computers get their IPs the same way as wired computers; the TCP/IP suite works above the data-link and physical layers (which is where wi-fi sits).

---

### Post by nixscripter on 2008-02-25
Re-reading your post, you mentioned router and a bridge. What exactly is connected to what, and which are you connecting the computers to?

---

### Post by PlancksCnst on 2008-02-26
I have an ethernet + 802.11bg router between my broadband connection and my network.  I have a laptop with a 802.11g usb stick (netgear wg111); it is usually running Windows.  I have a desktop system on the ethernet-to-802.11b bridge (Linksys wet11); it is usually running Ubuntu.

---

### Post by nixscripter on 2008-02-26
Okay, so that means it is the router is the one doing the IP management of the network.

I don't know if it will help, but try allowing the router to set up dynamic IP addresses using DHCP for the network. I found what appears to be a bug in the firmware where static IPs are reassigned in certain circumstances. That would confuse the heck out of everyone, and make traffic stop.

I don't know if it quite applies to your situation, but give it a try. That article is here:

[http://www.dslreports.com/forum/r19848466-Actiontec-Firmware-40161560107-Bug-Static-IPs](http://www.dslreports.com/forum/r19848466-Actiontec-Firmware-40161560107-Bug-Static-IPs)

---

### Post by PlancksCnst on 2008-02-27
I finally did iit.

I turned on DHCP in the router, and changed my systems to use DHCP and it worked.  Pretty strange stuff.  It also fixed another problem that I didn't realize was happening - the DNS service wasn't working; now it's flawless.

---

### Post by PlancksCnst on 2008-02-28
Well... it worked for several hours; it was working when I went to bed last night but this morning, it went back to the same behavior.

---

### Post by nixscripter on 2008-02-28
> **PlancksCnst said:**
> Well... it worked for several hours; it was working when I went to bed last night but this morning, it went back to the same behavior.

At least progress was made, and in my mind, one thing is clear: it's the router's fault.

Since I know about networks, but I'm not much on hardware, I'm not sure what to suggest next, except more research. :-|

---

