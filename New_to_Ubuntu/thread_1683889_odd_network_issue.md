---
title: "odd network issue"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by degarb on 2011-02-08
I have a notebook with ubu 9.1, laptop with xp home, one desktop with dual boot ubu 10.1 and xp home and one desktop ubu 10.1.  Obviously, I need networking working.

All linux distros share with each other and samba fine, and laptop xp. But the desktop xp wont play with ubuntu 10.1 samba, just the ubu 9.1 samba.  I need xp to run on desktop for missing linux aps that don't run in vbox or linux. But the 10.1 desktop cannot mount the xp shares (9.1 can) and the desktop xp cannot mount the ubu 10.1 shares.   Basically the xp desktop isn't compatible with the ubu 10.1 samba, while the xp laptop is, while the ubu 9.1 if compatible with the xp desktop who hates 10.1 ubuntu. 

Is the problem in the xp setup or the Ubu 10.1 setup?  And what?.

---

### Post by ikt on 2011-02-08
It's about how Samba's setup, it hasn't been done properly on some of the ubuntu box's, I can't say how exactly to fix it because it's different each time, but yeah windows machines are always fun :/

---

### Post by degarb on 2011-02-08
I found you need guests account enabled on xp machine to get samba to work with it.  I also found if I typed nautilus smb://ipaddress the shares would pop up.  I discovered the reason is 15 kps max throughput on two machines that are hard wired.   I get 768 on isp, so problem isn't in line. 

Help, if anyone with tips.  Too slow for even audio over LAN, definitely video.

























fssfff

---

