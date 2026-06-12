---
title: "Activating wlan0 and making it default"
date: 2005-04-23
forum: Networking &amp; Wireless
---

### Post by Diddy1 on 2005-04-23
I've setup my wireless router completely i can even ping. But the internet won't work. Any ideas on making linux connect to the internet through it?

Thank You

---

### Post by bnutting on 2005-04-23
Well a little more information would be helpful. Like:
1. What does it show if you go to: Applications->System Tools->Terminal and type in ifconfig ?
2. I run wireless on my laptop and I do not get a wlan0 only eth0 and eth1. What kind of hardware are you running?
3. Is this on a laptop?

---

### Post by Diddy1 on 2005-04-24
[QUOTE=bnutting]Well a little more information would be helpful. Like:
1. What does it show if you go to: Applications->System Tools->Terminal and type in ifconfig ?
2. I run wireless on my laptop and I do not get a wlan0 only eth0 and eth1. What kind of hardware are you running?
3. Is this on a laptop?[/QUOTE]

I use a compaq presario (desktop). And a netgear ma101 and the network comes up as wlan0. Also everything is set. The essid the mode Ad-Hoc everything except the ap wich i can't figure out. But it seems to be working when i ping other pcs connect to my network. But the internet won't work.

---

### Post by superwesman on 2005-04-24
I think that the first question (aka - the one you ignored) 

> 1. What does it show if you go to: Applications->System Tools->Terminal and type in ifconfig ? 

is important

if, in fact, 

> everything is set.  

it would work, no?  perhaps one of the settings is wrong? please run the command ifconfig in a terminal and show us its output - also, the contents of the file /etc/networking/interfaces might help - are you DHCPing or using a static address?

we can help you

---

### Post by Diddy1 on 2005-04-25
ifconfig and ifconfig wlan0 all show the right info . also i am using dhcp.Evrything seems to be set accoring to my normal config under xp. I dunno what's wrong.

---

