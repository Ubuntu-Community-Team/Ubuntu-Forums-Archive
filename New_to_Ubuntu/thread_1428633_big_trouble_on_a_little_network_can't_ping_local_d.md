---
title: "big trouble on a little network can't ping local desktop"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by bradmayne04 on 2010-03-13
I am tryin to get samba working.  I can see the icon on dolphin and the name shows up when I try to set up the printer however i get a "timed out" request on dolphin and an error message on the printer setup page.  I will include screenshots of each.  I can't even ping my mom's desktop (which is running vista).  Can someone tell me if I'm doing something wrong?  Shouldn't I be able to ping her?  I looked in the router for her ip address and it's there however I can't ping her.  I don't know why.  When I do this from the windows 7 OS on the other partition everything is ok.  I followed the how-to for the samb.conf file set-up script.  I gotta be doing something wrong here.

---

### Post by bradmayne04 on 2010-03-14
i got it working this afternoon.  You have to download the winbind!!!
sudo apt-get install winbind

---

