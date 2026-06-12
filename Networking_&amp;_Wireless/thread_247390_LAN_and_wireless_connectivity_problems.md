---
title: "LAN and wireless connectivity problems"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by MachineBucket on 2006-08-30
When using a wired ethernet connection after about 10-15min my connection is dropped. I'm not sure why because the system monitor shows small activity and also shows I'm still connected I just can't download anything or surf the internet. This has happened on 2 connections now so I don't think it's a modem problem. Also, I have a Broadcom air force one card that I got working previously, but will no longer connect. I can see networks, I just can't connect to them. I have been using gnome network manager but it no longer recognizes that I have a wireless card installed. It is still shown in the built in network software. I tried reinstalling gnome network manager but that did not help. Also note all these connections work fine in Windows.

Thanks for any help! :)

---

### Post by friedokra on 2006-08-30
I am going through a similar problem with my Broadcom Airforce. My wireless internet worked fine for a while (after a lot of pain to get it to) and then it just stopped working after I used an internet connection with a wire. Now my eth1 card seems to have disappeared. good luck.

---

### Post by KaeseEs on 2006-08-31
I'm having similar issues on a ThinkPad T60, with random dropping, and the connection still displaying as good and minimal traffic showing up, but no data throughput.  Not sure what's going on here.

---

### Post by Randy Winchester on 2006-09-13
This is pretty strange.  I had wireless working on my Dell Latitude C840 laptop w/ internal OEM Orinoco 802.11b up until a week ago.  I just installed Dapper 6.06 on this machine about two weeks ago.  The wireless card worked fine on both the live CD and when I first installed Dapper.  I also have Dapper installed on a Dell OptiPlex GX400, and it had no problem setting up and using the internal Belken 802.11g card.  Both systems initially worked great on first boot and got wireless connections without having to do anything special at all.

Last Sunday, the wireless on both systems just stopped working.  The signal meter shows no signal.  The wireless cards still show up in the Network Manager, but never seem to actually activate.  After clicking on Activate, the little progress bar bounces back and forth longer than expected when things are working, then eventually times out.

I've been getting all regular updates on both machines.  I don't think that this is a kernel related problem.  I'm running 2.6.15-26-386 on both machines, and the networking worked following the kernel upgrade to this version.  I can't recall any suspicious updates just prior to the wireless failure, either.

The eth0 wired NICs on both machines work fine.  Any ideas what this is all about?

---

### Post by Nano on 2006-09-15
I'm experiencing the same thing

---

