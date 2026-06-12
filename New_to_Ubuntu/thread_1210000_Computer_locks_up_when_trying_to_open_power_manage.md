---
title: "Computer locks up when trying to open power management"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by servicetech on 2009-07-10
When I try to change the power settings the computer locks up. I have to do a hard power down to get the system to restart.

Power management works fine if Nvidia hardware drivers are disabled

---

### Post by mzcariaga on 2009-07-11
Hi service tech,

have you found a work around of the issue? I also experienced the same problem. Please adivse.

---

### Post by servicetech on 2009-07-11
No solution. For now I'm running the power as constant on since ubuntu won't sleep properly with the Nvdia drivers installed. Screen set at 15 minutes.

I can uninstall the Nvdia drivers if I need to change the settings, then reinstall once the settings are changed. Still, I feel this is a pretty major bug for ubuntu, it's my last major hurdle. I'm running an Asus M3N78-VM board with a 8200 chipset.

---

### Post by mzcariaga on 2009-07-11
I've posted a question on launchpad :[Question #76727]: nvidia drivers cause power management to crash in zotac ion -A

I'm using the zotac ion-a board. right now it works perfectly in win xp due to a well-supported driver for chipset, video, and audio.  I think we're not get any answer until the next release.

do you know / have a "better" procedure description to install nvidia's linux proprietary driver (from the official site)?  I think if this has been installed it would be the answer...

---

### Post by servicetech on 2009-07-11
I looked into the 185 drivers but installing them is a rather complex procedure. Hopefully they will be in the 9.10 distro.

Still it's better than the ATI drivers (another board) which brought ubuntu to it's knees. I had to do an entire reinstall after that.

---

### Post by mzcariaga on 2009-07-11
great to know.  it's already halfway to 9.10, but it would really be nice if they will post a fix to this issue

---

### Post by servicetech on 2009-07-12
FWIW I tried the 9.10 Alpha2 off the Live CD, it's not far enough along to be usable just yet.

---

### Post by mzcariaga on 2009-07-20
I installed the nvidia 185.18 driver using the howto in the ubuntu forum. It solved the hang ups

---

### Post by servicetech on 2009-10-14
ANy word on which driver 9.10 will come with?

---

### Post by mzcariaga on 2009-10-14
it comes with 185.18.36 drver, good thing is it can detect it automatically as restricted driver.  I have not tried it personally,  i dont have an extra hardware for beta testing.  Also I have been testing the9.10 daily build unfortunately some builds last week was not working but the initial beta works.  I'm not planning to upgrade to 9.10 immediately

---

