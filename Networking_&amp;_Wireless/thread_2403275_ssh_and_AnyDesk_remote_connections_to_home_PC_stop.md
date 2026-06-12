---
title: "ssh and AnyDesk remote connections to home PC stopped working"
date: 2018-10-09
forum: Networking &amp; Wireless
---

### Post by rahidz on 2018-10-09
Home setup: Dual Boot Windows 10 and Ubuntu/xfce, with Ubuntu being the default boot option after 60 seconds. TP-Link Router & Arris SB6141 Modem, Comcast Internet connection.

---

I'm on vacation far from home for a week, before I went I decided to set up ssh and AnyDesk on my desktop so I could do some remote coding (what's a good vacation without work? :P). After a bit of trial and error, got them running just fine on both my iPhone (Shelly) and my Windows 10 laptop (PuTTY), and the AnyDesk client on both.

Well it's two days into my vacation and after a few successful sessions, all the connections have decided to drop entirely. PuTTY gives a "connection timed out" error, Shelly gives a "Network is unreachable" error when I use the port I set it up on (any other ports it just stalls out on), and AnyDesk tells me "The desk is not available".

My modem is still running (xFinity app shows it working and I can ping my IP address), and I don't *think *my IP changed since Shelly gives different responses with the right and wrong port numbers. I asked my neighbor and she said the computer is still on, though she couldn't tell what it was doing, and I very highly doubt a power outage occurred (never had any issues with the PC randomly rebooting/shutting down either...though I can't rule it out obviously.)

So the questions...

1) What are the most likely causes?
2) Is there any way I can at least check if the PC is running? 
3) Do I have any method of re-connecting?
4) Can I minimize the chances of this happening next vacation?

---

Thank you all very much in advance :)

---

### Post by TheFu on 2018-10-09
Comcast has mini-outages all the time. Let me check my logs ... 
```
$ internet-up-summary.sh 
  Using /var/log/internet-up.log ... 
 Period 20181007-062611  - 20181009-140211
  Total Time: 3338 (min) 55.63 (hrs)
  Percent Up Time: 99.76 % 
  Percent Down Time: 0.24 % 
  Total Down Time: 8 min or 0.13 hrs
 Currently: UP
```
Last week was worse:
```
$ internet-up-summary.sh /var/log/internet-up.log.1.gz 
  Using /var/log/internet-up.log.1.gz ... 
  Using /tmp/internet-up.log.1
 ... 
 Period 20181001-062612  - 20181007-062411
  Total Time: 8638 (min) 143.97 (hrs)
  Percent Up Time: 99.26 % 
  Percent Down Time: 0.74 % 
  Total Down Time: 64 min or 1.07 hrs
 Currently: UP

```
Do you have a UPS sufficient to keep all equipment necessary working through small, 30min, outages?
Sometimes when a router looses power, the settings get jumbled.  
Sometimes with a Unix-based computer looses power, the disks need repair. Could be at an fsck prompt with a (Y/n):

I'd been running servers at home for over a decade when I left the country in the mid-2000s. 2 weeks into my trip, I lost contact.  My residential Comcast connection was down long enough that they moved the subnet we were on. I'd never needed to use ddclient (a dynamic DNS updater) before.  Got home and sure enough, my computer had lost power, but it booted back up and all services were running fine ... just with a different public IP.

A few years later and I'm overseas again.  On the way, I'd ssh into home from the different hotels and airports along the way to check email (mutt) and everything was fine.  Got to the first stop, had access for 3 days, no issue. Flew to the next stop inside a country with some internet censorship and I cannot connect to my systems.  This was completely unexpected because my domain has technical information about Linux, not political things about other countries (besides my own).  A friend in that country said that home internet was filtered there, but that cell data wasn't.  Tried it using a  local cellular $10 SIM and got to my blog, no problem.  

And there are also places in the world that just don't have internet. I've been travelling more and more to those places "at the edge of the Earth."

If you don't have some alternate means to connect to the systems, there isn't much that can be done remotely.  Main thing is to review the logs when you get home and hope someone didn't take over the system(s) while you were away. Allowing a remote access tool running without protection is a dangerous thing.  

Also, the computer could be stuck at a grub prompt, if you allow automatic updates.

---

### Post by rahidz on 2018-10-09
Thanks for the reply!

> **TheFu said:**
> Comcast has mini-outages all the time. Let me check my logs ...

It's been a few hours at least, and I'd imagine at least AnyDesk would re-connect after a mini outage (also figured out I lost connection to Dropbox on that PC), so I don't think that's what it was.

> Do you have a UPS sufficient to keep all equipment necessary working through small, 30min, outages?
Sometimes when a router looses power, the settings get jumbled.  
Sometimes with a Unix-based computer looses power, the disks need repair. Could be at an fsck prompt with a (Y/n): 

After the last major outage fried my PSU and monitor, yeah, the PC is plugged into a 800VA UPS, should last at least 30 min. I do need to look into some kind of logging options for that, but that's another day's project...:)

> If you don't have some alternate means to connect to the systems, there isn't much that can be done remotely.

Yeah that's what I figured to be honest, guess I'm forced to actually not do work on my vacation, how terrible!

> Main thing is to review the logs when you get home and hope someone didn't take over the system(s) while you were away. Allowing a remote access tool running without protection is a dangerous thing.  

I really hope not! I did use a non-standard port number and secured ssh with a key, and AnyDesk has a long password, so hopefully those two were enough to keep nefarious types at bay.

> Also, the computer could be stuck at a grub prompt, if you allow automatic updates.

Good point, I don't remember if I disabled automatic installs on that...

Thanks very much for the advice, will definitely update this post once I get back home.

---

### Post by TheFu on 2018-10-09
Or it could be something completely different.  I'm just guessing.

800VA might make it 15 min, maybe, if the monitor isn't also connected. And don't forget all the networking equipment, it needs to be on the UPS too.

After a power outage, a printer here will power on even if it was powered off before. Something to consider if the UPS powers that too.

There are telephone devices that can control power resets.  Don't know if that is something you'd want to try or not.  Make a voice call, have it reset all your equipment.

I don't know anything about AnyDesk, but if it is a 3rd party service, I wouldn't trust it.  Other reputable remote access, hosted, solutions have had security issues.  I use x2go for remote GUIs, if necessary, but really ssh is the main method.  On my laptop, I'll setup an ssh tunnel as a SOCKS proxy if I won't want a full VPN. DNS queries leak, however.

To access Windows when I'm away, I x2go into a Linux system, then rdp on the LAN to the Windows VM.  Almost all my systems are virtual machines, including my main desktop.

I run my own openvpn server at home, but also have a paid VPN provider.  2 different purposes.  Using openvpn from android is much easier than using ssh tunnels.  But from my Linux laptop, I tend NOT to openvpn to connect back home.

ssh on a non-standard port, keys only, 3 failures should block the attacking IP automatically. Bad parts of the world are blocked completely.  There are about 10,000 subnets blocked in my router. Passwords for any remote access are a total failure, IMHO.  Doesn't matter how long, though 100% random and 50+ characters _might_ be ok.  Use a password manager, if you don't already.  2FA is good to have for everything.

I'm not much of a Windows person.  I won't use Windows on the internet. Just don't trust it.

---

### Post by rahidz on 2018-10-21
Sorry about the late update!

Got home, PC was running, no outage, nothing. Hadn't even rebooted or lost Internet. Moved the mouse and it worked for a few seconds, then froze up entirely. Looking at the error logs, seems that you were right and AnyDesk was the culprit, as soon as I had closed out of it on my vacation, it must have bugged out and caused a kernel panic of some sort. Will look for alternatives like x2go, and in the meantime stick with ssh.

---

