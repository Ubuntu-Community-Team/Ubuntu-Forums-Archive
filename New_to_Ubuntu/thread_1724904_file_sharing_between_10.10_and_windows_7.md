---
title: "file sharing between 10.10 and windows 7"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by tysonh80 on 2011-04-08
I'm transferring my world of warcraft file from my windows 7 laptop to my ubuntu 10.10 desktop.  I was able to share my wine c drive folder and transfer in from the laptop.  However the transfer speed is a joke.  I'm getting 50 kbs.  At this rate it would only take 30 hours to complete.  Did I miss a step in setting this transfer up?

---

### Post by rosencrantz on 2011-04-09
If I understand you right, you want to access a Windows shared folder from Linux?
That's what you have samba for, no need for wine.
If I'm not mistaken, you can access the share with
smb://<desktop IP>/<name of shared folder> in the address bar of your file browser.
samba-client should be installed by default, if not, apt-get it.
Cheers,
rosencrantz

---

### Post by pi3.1415926535... on 2011-04-09
Is an external USB drive an option?

---

### Post by tysonh80 on 2011-04-09
> **pi3.1415926535... said:**
> Is an external USB drive an option?
When I go to  places>network  in the window its says windows network.  I click on that then it says workgroup like it should.  then I try to click on that and it says failure to mount can not open share file list.  Do I need to change my desktop to the "workgroup" in order to trade files back and forth.  If so how do I do that?

---

