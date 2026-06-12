---
title: "My computer will not upload 10.10!"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by stavrogin1 on 2010-11-19
Hi there.  So I have Ubuntu 10.04 on my computer, and am pretty sure my computer has not updated my system, as the "About Ubuntu" tab still tells me I have 10.04.

So I tried to download 10.10, and my computer will not, will not do so.  I tried burning a CD, and it will not do that.  I tried placing the information on a USB drive, and it will not do that. 

I originally installed Ubuntu on my system about a year ago using the CD drive, so I am very confused about what it going on.  I feel like something has gone very wrong with my system, but have no idea what to do about it.

Can anybody help?

---

### Post by sikander3786 on 2010-11-19
If you've a working install of 10.04. you can do an upgrade to 10.10.

```
sudo apt-get update && sudo apt-get upgrade
```

```
update-manager -d
```

Before upgrade, it is advised oftenly to remove you graphics drivers and then re-install them after upgrade. There have been some issues.

Regarding issues with 10.10 disc, did you check the downloaded image's MD5SUM?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

For burning CD-ROM properly,

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

For USB,

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Make sure you are selecting the proper boot device from Bios menu.

And you didn't list any errors that are appearing with 10.10 disc? What happens when you boot?

---

### Post by Rubi1200 on 2010-11-19
Very Important:

1. Backup all critical data first

2. Read these links:
[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes)

[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857) (the first post makes for essential reading)

Other than that, the advice offered by sikander3786 is on the mark.

---

