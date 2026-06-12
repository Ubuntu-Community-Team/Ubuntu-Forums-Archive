---
title: "Machine unreachable on local network after three days"
date: 2016-10-25
forum: Networking &amp; Wireless
---

### Post by digitalrep on 2016-10-25
I've had this issue for a long time now. My Ubuntu machine runs an apache2 web server. I have a Windows PC and an Android tablet on the same network from which I can sftp and ssh into the Ubuntu PC. I can also browse from these to the machine's IP in the browser to see my website. Until... Three days later... Suddenly it's unreachable (on local network; still ok using outside IP address). Always have to power cycle the modem. Don't know why... Lack the knowledge to even know how to begin to figure out why. Don't know if I need a new modem, new wifi adapter for the Ubuntu PC, or what... Anyone able to help?

---

### Post by TheFu on 2016-10-25
wifi? Don't use wifi for a server. That's the first thing to fix. Servers should always be wired ethernet.  wifi issues are just too hard to figure out for 50 different reasons. Go wired.

If you do want help, we need more data.  Post the config files that are relevant and explain how the network is setup - static/dhcp? reservations? types of cables type of switch, router, modem, ... ISP ... and perhaps the URL so we can check other things out too?

Welcome to the forums.

---

### Post by digitalrep on 2016-10-29
What config files are relevant?

It's statically assigned IPs, the modem/router is a Netgear DG843GU. My ISP? Do you really need to know that?

---

### Post by TheFu on 2016-10-29
> **digitalrep said:**
> What config files are relevant?

It's statically assigned IPs, the modem/router is a Netgear DG843GU. My ISP? Do you really need to know that?

I don' t know what I need to know. Based on the issue description the root problem could be **anything**.  So I ask for lots of info. If you don't want to provide that, fine.

All I know is that you have something that hasn't worked for a time. The way to solve problems is to eliminate all the points of failure.  That means looking for 
* physical issues - don't use wifi, swap cables, swap ports used.  Wifi is problematic when troubleshooting stuff like this. Remove it from the possible list.
* logical issues - look at relevant config files.  You made static IPs somehow.  THOSE files.  Any network related files that  have been changed would be helpful. I don't know what was changed.
* driver issues - if it used to work, this might not be an issue. Can't tell. Don't have any information.
* An exact example of the connection that is failing would be helpful too. With ssh, please add -vvvv to the command
* Log files - most things are logged on Unix systems. Most problems are logged a bunch.  Take a look at those.

ISP?  Mine is comcast - is it a secret?  Sometimes an ISP changes things and breaks things.  Hard to search for those without knowing the name.

The router could be an issue too.  I've had wifi issues in commercial locations with netgear.  The wired part of the router - it wasn't a cheap one - worked great, but wifi would drop all the time.  Ended up disabling wifi and connecting a Ubiquiti AP about 6 months ago. Has been working perfectly ever since. Netgear is a reputable brand, but I've had issues with a few different netgear devices over the years.  For me, it isn't worth the hassle anymore, so I don't buy netgear.  We don't know if that is or is not the issue here.  Go wired. See if that fixes it.  That is the first step.

Basically, we will use google to look for possible issues until something jumps out. I'll RTFM a bunch too, trying to help. We ask for actual files, because it is very common for people to misinterpret things in their descriptions.  I've done it from time to time too. Posting the config files removes that layer of interpretation.

That's why I ask questions.  Don't always have time to spell out why, sorry for that.  Now I need to get back to patching 30-ish systems this morning.

---

### Post by digitalrep on 2016-10-29
Okay well I'll move it downstairs and plug it in using an ethernet cable and see what happens after 3 days. Hopefully you're right and that's all she wrote. Fingers crossed

---

### Post by TheFu on 2016-10-29
Or spend $10 and get a long CAT5e cable.  They are handy for all sorts of things.

---

