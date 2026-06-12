---
title: "No Card/Unclaimed Intel 2200BG in Dell Inspiron 9300 Using Gutsy"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by jevs on 2007-11-11
Ok I give up, I've looked at every post that google turns out (first 5 pages any way) and I can't get my IPW 2200BG to work. It works on Windows XP. It seems that ubuntu is turning it off, because if I boot on XP I have to turn it on with Fn+F2, but it doesn't work in linux. I just upgraded to Gutsy from Feisty, It worked great before.

When I lon on a message prompts saying I don't have a network card and wireless manager has a sign that reads "No Card". System --> Administrator --> Network only lists my modem and wired connection. 

iwcongi

lo        no wireless extensions.

eth0      no wireless extensions.

lshw -C network

*-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=24 mingnt=3


Can anyone help me please?

---

### Post by Bushido89 on 2007-11-11
I'm a complete noob...and could be very wrong...but could it be the drivers aren't installed? I used Ndiswrapper...seemed to install them...

Apologies if I'm wrong.

---

### Post by jevs on 2007-11-11
Thanks, I'll give it a try. The thing is IPW 2200BG is supposed to work out of the box, and it worked before with Feisty. Since then the only thing I've changed is the automatic upgrade to Gutsy.

---

### Post by Bushido89 on 2007-11-11
Ah, mine wasn't :(. Still doesn't really work (though I can't be sure if that's a fault on my part, or the joke of a company that's supposed to provide us WIFI)

Gl getting it fixed, some completely hax pro might log on & save us soon? :p

---

