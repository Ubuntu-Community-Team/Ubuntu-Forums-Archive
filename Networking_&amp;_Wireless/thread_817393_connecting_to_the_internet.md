---
title: "connecting to the internet"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by chaoschops on 2008-06-03
The broadband modem in our apartment is connected to a Windows XP pc.  Can I access the internet through this router? I'm running Heron and have installed my wireless card, but can't seem to connect.

---

### Post by vexingmodstwo on 2008-06-03
> **chaoschops said:**
> The broadband modem in our apartment is connected to a Windows XP pc.  Can I access the internet through this router? I'm running Heron and have installed my wireless card, but can't seem to connect.

You'll need to know what kind of card it is.

---

### Post by superprash2003 on 2008-06-03
in your terminal type iwconfig and post output here

---

### Post by chaoschops on 2008-06-03
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

It is a Motorola wpci810g card.  I used ndiswrapper to install the sys and inf for it. I'm new to Ubuntu and used "Ubuntu Linux for Dummies" and "the official ubuntu book". They both seem to hit big points, but not all the details.  Any other books one might suggest for a noob?  Thx

---

### Post by superprash2003 on 2008-06-04
Do you see any restricted drivers under System->administration->Restricted drivers (or hardware drivers)

---

### Post by chaoschops on 2008-06-04
> **superprash2003 said:**
> Do you see any restricted drivers under System->administration->Restricted drivers (or hardware drivers)

The only thing listed in hardware drivers is my monitor. Then it says that no proprietary software is being used.

---

### Post by chaoschops on 2008-06-19
Man, all I'm hearing is crickets.  Awful quiet around here.  Anyone?

---

### Post by molotov00 on 2008-06-19
It's a vague question.

What do you mean you 'can't connect'? Also, you talk about whether you can connect through a router but you said your setup has a modem and a computer -- no mention of a router. People who post good questions tend to get good answers.

---

### Post by chaoschops on 2008-06-20
ok, I gotcha.  I am running a Motorola wireless card on my pc.  My roommate is running windows xp on his pc, which controls the linksys router, which is connected to the cable modem. 

I am trying to get my pc to recognize and connect to said router.

---

