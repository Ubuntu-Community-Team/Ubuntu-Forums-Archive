---
title: "Samba commands trouble"
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by salvor_hardin on 2007-11-26
Ok, Samba is working, network is working I see Windows shares but unable to access Linux from Windows. I have real trouble configuring Samba server. I used "http://www.melbpc.org.au/pcupdate/2403/2403article7.htm", but not working, half of the commands there not working, Commands like "smb start" or "/etc/rc.d/init.d/smb start" only give me "file not found". I checked and no "rc.d" dir! Where are these Samba files? I just can't find them. In my Samba dir there are only "gdbcommands" and "smb.conf". I'm using Ubuntu 6.5.1 LTS.

please help

---

### Post by dmizer on 2007-11-26
ubuntu 6.5.1?  i wasn't aware there was such a beast.

follow the guide linked in my sig for how to configure your samba server.

---

### Post by salvor_hardin on 2007-11-26
My mistake, 6.06.1! :)

---

### Post by salvor_hardin on 2007-11-26
Interesting, now when I started samba install, for the second time, it downloaded something from internet and started deamons. Before, when i did samba install, it installed something but said nothing about deamons starting, and when I tried samba stop or start nothing happend. Intresting part is that it worked before, I was in a win network:confused::confused::confused::confused::confused: but before i had no internet connection, is it complicated to do it without internet connection?

---

### Post by dmizer on 2007-11-26
you probably never had samba installed in the first place.

just complete the howto and you should have a working samba share.

---

### Post by jonandrews on 2007-11-26
If you are more familiar with XP than Ubuntu, you might like to look at my step by step networking guide at
[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

---

### Post by salvor_hardin on 2007-11-27
No, it was working before! How would I be able to access Win Xp and share internet connection. And now I have problems making it work so that both machines have static IP address. I need to share internet connection with both machines on static and there are lots of problems with network, in one case I can't see win shares from Ubuntu or other way around. I went through your configuring guide but still lots of problems. In general it works but...

---

### Post by salvor_hardin on 2007-11-27
Is there any way to share internet connection with both pc on static?

---

### Post by salvor_hardin on 2007-11-27
> n one case I can't see win shares from Ubuntu or other way around.

Actually I can access Win shares over smb://x.x.x.x, so I think it is stupid Windows networking stupidity. Only problem is post up :)

---

### Post by salvor_hardin on 2007-11-27
Never mind - got it !!:):):):):)

---

