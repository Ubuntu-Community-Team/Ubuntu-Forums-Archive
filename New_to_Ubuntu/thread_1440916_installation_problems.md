---
title: "installation problems"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by perplexsively miffed on 2010-03-28
Hi, I have been attempting to install Ubuntu 9.10 Karmic Koala to a newly cleaned(formatted) drive for the past several hours with little or no success.I have tried all manner of installation that I can find.When attempting to boot up from a dvd or cd image it seems to start off fine with an initialization of all my computers hardware and then stops with the following prompt...[DR-DOS] A:\> .
When I tried to install the os via the wubi exe inside of windows it went as far as installation of the virtual stuff and then never finished.Upon rebooting ubuntu shows up underneath windows,but when selected it stops partway through loading to inform me that I need to perform chkdsk/r in windows
and then reboot in ubuntu.However when running chkdsk it stalls at the 4/5 point.
Can anyone help?Please,I am poised with an estwing in hand ready to smash my computer!:confused:

---

### Post by NightwishFan on 2010-03-28
If you are installing Ubuntu using a live or alternate CD you should not be getting anything similar to a DOS prompt. At the worst you would see:
```
ubuntu@ubuntu:$
```

Running checkdisk is a Windows error, not a Wubi one. Perhaps your disk is compromised? Uninstall WUBI from Windows Add/Remove, and then run check disk and windows defrag on all of your drives. Then reinstall Wubi.

Read this Faq about burning a disk, however you can simply use WUBI from a standalone .exe.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

---

### Post by 3rdalbum on 2010-03-28
> **perplexsively miffed said:**
> Hi, I have been attempting to install Ubuntu 9.10 Karmic Koala to a newly cleaned(formatted) drive for the past several hours with little or no success.I have tried all manner of installation that I can find.When attempting to boot up from a dvd or cd image it seems to start off fine with an initialization of all my computers hardware and then stops with the following prompt...[DR-DOS] A:\> .

Use the "Burn Image to Disc" or "Burn ISO image" function of your burning software, NOT the "Make bootable disc" function.

NOT the "Make bootable disc" function.

If you're using Windows 7, I think you can right-click on ISO images and burn them to disc that way.

> When I tried to install the os via the wubi exe inside of windows it went as far as installation of the virtual stuff and then never finished.Upon rebooting ubuntu shows up underneath windows,but when selected it stops partway through loading to inform me that I need to perform chkdsk/r in windows
and then reboot in ubuntu.However when running chkdsk it stalls at the 4/5 point.

Congratulations, you've just found one of the limitations of Wubi. If there's something wrong with your Windows filesystem, then Ubuntu can't mount it to get at its disk image, and you can't boot up Ubuntu. Burn your CD again using the correct feature of your burning software, and boot from it, and you'll be able to install Ubuntu the correct way onto its own partition. When Ubuntu is installed onto its own partition, it doesn't depend on Windows to be working.

---

### Post by perplexsively miffed on 2010-03-28
Thank you for the advice,I am using nero express 6 to make the discs,which option do I select ,? I have tried burn image to disc with dvds and cds with the same results,I also tried the bootable disc format, the results were the same.

---

### Post by perplexsively miffed on 2010-03-28
Ok, I finally got some discs that work.I have tried three versions of the 9.1.0
platform,they all begin to install then change to a blank screen(black)and flashing cursor
after the  flashing logo bit.Do I need to just let it sit for a couple days to finish or what?
 I guess it's back to phucking xp,I despise it, but at least it can be installed.
Enjoy your unbuttu!

---

### Post by NightwishFan on 2010-03-28
Bye.

---

