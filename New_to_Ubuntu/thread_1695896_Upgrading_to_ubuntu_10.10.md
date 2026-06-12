---
title: "Upgrading to ubuntu 10.10"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by sp.1990 on 2011-02-26
Hello .. I am newbie to this forum as well as Ubuntu . I want to know is it possible to Upgrade the Ubuntu version from 9.04(April 2009) release to latest Ubuntu without loss of my previous data.

If so kindly let me know or any previous post there regarding this , let me know . 

I have installed Ubuntu 9.04 as wubi and if i need to upgrade , will the size of disk be a problem?

Thanks

---

### Post by runeh76 on 2011-02-26
Yes its possibly from updates menu. But i highly recommend, that u backup important stuff..never knows what happens, u know.

---

### Post by idi0tf0wl on 2011-02-26
> **runeh76 said:**
> yes its possibly from updates menu. But i highly recommend, that u backup important stuff..never knows what happens, u know.

+1

---

### Post by kroq-gar78 on 2011-02-26
You won't lose your data unless something goes HORRIBLY wrong (VERY unlikely), but even then you can recover the data with a LiveCD/LiveUSB.

You need an upgrade as 9.04 is not supported anymore (ended ~October 2010)
 How much disk space do you have left?

---

### Post by sp.1990 on 2011-02-26
I checked the filesystem. Its showing 549.4 MB left.

---

### Post by kroq-gar78 on 2011-02-26
Not COMPLETELY sure about this, but I think you'll have to upgrade to 9.10 first (i THINK). 9.10's support is ending in April, so You'll probaly want to upgrade to 10.04. It wil require more disk space, but you'll have a stable release.

To free up some space, run this command (if you haven't done so lately):
```
sudo apt-get clean
```
and then check how much space is left.

---

### Post by pressko on 2011-02-26
bad ... i recommend to move your data stuff ( pictures, music , movies ) to other partiotions and upgr it :)

---

### Post by sp.1990 on 2011-02-26
Ok thanks ...I will do as u told

---

### Post by sp.1990 on 2011-02-26
I dont have any Picture/Music in Ubuntu as i have it in my Windows and i would mount it when ever needed . I will check the clean command and get back.

---

### Post by kroq-gar78 on 2011-02-26
do you have any documents (e.g. spreadsheets, essays, presentations, etc.) on there? you should move that, too, If you haven't already

EDIT: i confirmed using [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes) that you will have to do

Ubuntu 9.04 --> Ubuntu 9.10 --> Ubuntu 10.04 --> 10.10

that will be THREE upgrades and a LOT of space I think.

---

### Post by alzie on 2011-02-26
Since this is a Wubi install disc space likely won't be an issue.

Seriously, you need to backup everything that is important and put it somewhere safe (thumb drive etc) in case something goes wrong.  

I have not upgraded a Wubi install for some time (10.04 LTS and holding) but it may take some time.  I'm not certain if you will be able to leap to the current distro or if you will have to upgrade in steps and if so, how many.

Open synaptic package manager and go into the repositories (under settings)and click on the tab for updates.  At the bottom you will see a section for release upgrades, change the option to "normal releases" and it should give you the option the next time update manager runs.

The last time I tried to update a Wubi install it went badly, but that was some time ago.  Hopefully it has been improved.

Hope this helps you.

---

### Post by sp.1990 on 2011-02-26
And my ubuntu upgradation says my distribution is not supported anymore. Have attached the screenshot for clear picture. Each time the upgrade window opens , this error pops up

---

### Post by runeh76 on 2011-02-26
Believe me.
Backup important stuff (bookmarks etc.)
Download livecd 10.10 and make clean install!

---

### Post by sp.1990 on 2011-02-26
Ya .. I too felt the same. I think i should first upgrade to 9.10 and then to 10 as the update center tells to upgrade to 9.10 alone.
Making a clean install will be better i feel so .
Thanks guys for replying to my queries. I feel amazed as how quickly and actively you people respond as this is my first post. :)

---

### Post by kroq-gar78 on 2011-02-26
Make sure you install wubi if you still want it, because, from what i've heard, uninstalling a REAL install is a REAL pain

---

### Post by sp.1990 on 2011-02-26
Ya.I installed this version in wubi . So i will first remove it from Windows (Add/Remove Program) and then install new version as wubi again after taking backup.

---

### Post by jeremyjjbrown on 2011-02-26
> **runeh76 said:**
> Believe me.
Backup important stuff (bookmarks etc.)
Download livecd 10.10 and make clean install!

YES!

Back up everything you even might care about! When you are done, lock your backup away. Storage is cheap, cheap, cheap

Do a clean install to 10.04. Since you do not upgrade often use the LTS (10.04) version. It will be supported better for longer.

dist-upgrade is he road to headaches.

---

### Post by kroq-gar78 on 2011-02-26
> **jeremyjjbrown said:**
> YES!

Back up everything you even might care about! When you are done, lock your backup away. Storage is cheap, cheap, cheap

Do a clean install to 10.04. Since you do not upgrade often use the LTS (10.04) version. It will be supported better for longer.

dist-upgrade is he road to headaches.
+1 to 10.04, but the OP says that they want to go to 10.10

sp.1990,
I highly suggest you just install 10.04 instaed of 10.10. It will be supported for ~2 yrs now and will be much more stable because it will be supported longer then 10.10 (~1yr support left)

---

