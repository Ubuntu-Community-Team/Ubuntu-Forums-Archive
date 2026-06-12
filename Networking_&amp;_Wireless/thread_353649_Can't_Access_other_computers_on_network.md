---
title: "Can't Access other computers on network"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by jflash on 2007-02-04
Ever since I got a new computer and installed Ubuntu on it, my computer has been unable to see the other two (Windows) computers via the network, and vice versa. I have double checked everything I know of to check in my smb.conf file, but I'm attaching it in any case. If there is any other information I need, let me know. If it makes any difference, there are three computers on my network (2 Windows XP and 1 Ubuntu). We use a Linksys WRT54G router and we are configured using static IP addresses on the network. Thanks!

---

### Post by chriscando on 2007-02-05
Could it be the other computers? Maybe they have some firewall software running on them, this will prevent your Ubuntu machine from "seeing" them.

Try pinging the other computers from your Ubuntu machine (ping ip-address-of-other-machine). If you cannot ping them then you know its the other computer.

---

### Post by dmizer on 2007-02-05
don't try to use the default smb.conf file for file sharing.

for allowing your xp computers to view your ubuntu computer, use the first link in my sig.  to configure ubuntu to connect to your windows computers, use the second link in my sig.

---

### Post by jflash on 2007-02-05
> **chriscando said:**
> Could it be the other computers? Maybe they have some firewall software running on them, this will prevent your Ubuntu machine from "seeing" them.

Try pinging the other computers from your Ubuntu machine (ping ip-address-of-other-machine). If you cannot ping them then you know its the other computer.

Tried it, and got 'Destination host unreachable'. Assuming that means that it's the other computers.

> **dmizer said:**
> don't try to use the default smb.conf file for file sharing.

for allowing your xp computers to view your ubuntu computer, use the first link in my sig.  to configure ubuntu to connect to your windows computers, use the second link in my sig.

I'll try that this afternoon.

---

### Post by Metallinut on 2007-02-05
I've noticed a similar problem recently on my Ubuntu laptop.  I had everything working just fine and dandy.  Then after installing some updates (a daily occurrence it seems) I can no longer access any machines on my local network.  I have a Windows box and another Ubuntu desktop.  If I ping either of them (or the Linksys router for that matter) I get "Destination Host Unreachable". 

But here's the thing.  I can do anything I damn well please on the internet with this laptop.  Anything external on my network works fine with Ubuntu, but nothing internal.  Bizarre.

I thought maybe my wireless router was having problems, but if I boot into the laptop under Windows, presto! I get access to all internal network machines....

Ubuntu is great, but so far, with the only changes to this laptop being system updates, I've had my XGL broken, and now internal networking.  What the frig?!?

---

### Post by dmizer on 2007-02-05
if you don't leave your extra repo's for beryl on all the time, you won't get constant updates.  beryl/xgl are still experimental software and there are many changes coming down the pipe for it.  while using experimental software, you should expect it to sometimes break things.  if you want things to be stable and reliable, load dapper and don't turn on any of the extra repos.  and most certainly ... don't use repos that are not *.ubuntu.com.  otherwise, you should expect to end up in a repair situation from time to time.

things to check:
1) have you installed an iptables front end in ubuntu (ie firestarter)?  this is probably your problem.
2) on ubuntu, do you have your router (ie: 192.168.*.*) listed as your primary dns server?  if so, you'll need to change that.
3) have you recently configured opendns?  this can cause problems at the local network level.
4) if not, then you may have a firewall issue at your windows box or at your router.

if none of the above seem to correct your problem, start your own thread because your trouble is not the same as the op.

---

