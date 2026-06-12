---
title: "Wierd DVD tray problem?!"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by Ben Page on 2009-01-17
Yes, I mean physical DVD tray (door) problem. Its nothing serious, but it is a problem since its bugging me.
I don't use DVDs much in Ubuntu, at least not physical DVDs, so I never gave this issue much attention, but now I got some movies and music from my friend on dozen DVDs. The problem is that when I press eject button on my DVD drive it opens, but closes instantly (after completely opening)and then I have to open it again (and it stays opened). This happens every time when I open it after inserting a DVD. ?!?
DVD drive is Optiarc AD-5200A ATA (no sata).
Note that this device works perfectly normally in Windows**, or while in MB bios etc. - this issue is Ubuntu exclusive issue.
Any thoughts, solutions??

---

### Post by RichTJ99 on 2009-01-17
Do you have anything mounted on the CD?  Try booting Ubuntu with nothing in the drive & see if its still doing that.

---

### Post by ithanium on 2009-01-17
maybe this will help you:
[http://www.itcamefromtheinternet.com/tech/archives/107-Ubuntu-8.10-CDDVD-tray-open-close-issue.html](http://www.itcamefromtheinternet.com/tech/archives/107-Ubuntu-8.10-CDDVD-tray-open-close-issue.html)

---

### Post by Ben Page on 2009-01-17
It doesent matter if something is mounted, it always does that when I try to eject for the first time, afterwards the tray works ok, but when I enter new" DVD and try to eject, it open-closes again - for every DVD ?>?
You think it could be something wrong with mounting the DVD? I think it mounts automatically when I insert any removable disk-drive even USB...

---

### Post by fenian on 2009-01-17
Update your udev to 124-9 ,link to a [.deb is here]("http://archive.ubuntu.cz/ubuntu/pool/main/u/udev/udev_124-9_i386.deb").

---

### Post by Ben Page on 2009-01-17
To itanium, I did everything that link sayed, but after update, problem presisted (i could not find that udev package).
To fenian, this solved the issue (and lasted half an hour shorter than update). Thnx!

---

### Post by Ben Page on 2009-02-09
Hey guys! I'm back with the same problem, but this time on 64-bit OS - Ubuntu 8.10. Could someone please point me to the 64-bit version of "udev_124-9"?

---

### Post by Ben Page on 2009-02-10
bump!:-\"

---

### Post by Ben Page on 2009-02-11
Final bump...Would really want to solve this issue...If there is a fix for 32bit there must be a 64bit version, too, just help me find it!

---

### Post by mc4man on 2009-02-11
[http://packages.ubuntu.com/intrepid-updates/udev](http://packages.ubuntu.com/intrepid-updates/udev)

---

### Post by resander on 2009-02-11
I had this unwanted tray closing problem too in November last year. Don't know if it will help, but here is the thread: 'Drive will not let me remove CD'

    [http://ubuntuforums.org/showthread.php?t=986927](http://ubuntuforums.org/showthread.php?t=986927)

Have never referred to threads before. If this is not the right way, just look for my username resander using the forum extended search facility instead.

---

### Post by Ben Page on 2009-02-11
> **mc4man said:**
> [http://packages.ubuntu.com/intrepid-updates/udev](http://packages.ubuntu.com/intrepid-updates/udev)

Thanx! This one will do...

---

