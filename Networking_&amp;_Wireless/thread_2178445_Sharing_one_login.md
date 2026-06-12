---
title: "Sharing one login?"
date: 2013-10-03
forum: Networking &amp; Wireless
---

### Post by Andrew_Lucas on 2013-10-03
Hi all,

The situation is as follows. I'm living in University accommodation, and the University outsources its network provider to a company called Keycom. I have a Keycom account, but only one login, which doesn't allow multiple logins. I have four devices, (laptop, desktop, tablet, phone) which I'd like to connect - at the moment, it's a pain having to logout (in the case of my desktop, unplug the ethernet cable - the other devices are wireless). There's a spare router at my mother's...would it be possible simply to bung in the router (adding the login details, obviously)?

If possible, the ideal arrangement would be as shown in [here]("https://app.box.com/s/0bd03gprt4y0d8yn2zta") (awful, mouse drawn) picture. (Ethernet from wall to router, ethernet from router to desktop, everything else wireless).

I know about solutions like "[Virtual router]("https://virtualrouter.codeplex.com/")" on Windows, or using my phone as a router (it's running Cyanogenmod 10.1, and I've seen the feature but not actually tried this...USB tethering works for definite though, since my laptop's wireless drivers are crap and unreliable, I use my phone). The trouble with this is that I'd have to get a wireless card for my desktop - something which I'd rather not do, given the option.

Any other solutions welcome!

PS, for the record: I don't think it's possible to activate USB tethering AND the "wifi hotspot" feature on the phone.

---

### Post by TheFu on 2013-10-03
What is possible will completely depend on the authentication model and routing methods used by Keycom.  

So, how do they authenticate and how do they setup routing on a working system?  If you know that, then someone might be able to help who doesn't know anything at all about your situation.  Otherwise, as around the dorm - especially CS and EE and CompE people.

I'd 
* connect with a Linux machine.
* login
* post the output of these items/commands here:
** ifconfig
** route 
** any proxy settings
** any VPN settings
** any DNS settings 
A linux machine can easily be a router.

---

### Post by houstonbofh on 2013-10-03
If they do any kind of DPI and look for NAT tags, you are dead in the water.  You would need a router able to VPN tunnel all of your traffic to a remote endpoint to avoid this.  You might be better off just getting a good data plan.

---

### Post by TheFu on 2013-10-03
> **houstonbofh said:**
> If they do any kind of DPI and look for NAT tags, you are dead in the water.  You would need a router able to VPN tunnel all of your traffic to a remote endpoint to avoid this.  You might be better off just getting a good data plan.

A transparent proxy might work, but probably only for popular protocols - SMTP, HTTP, HTTPS.
If you have time and want to cause problems, demand access to bittorrent and start mirroring all the different Linux distros.  I would expect all of your traffic to be monitored and there probably isn't any way around it.  The logins are their way of saying "we are watching YOU."  It is a way to provide personal accountability, even when that can be done without logins.

---

