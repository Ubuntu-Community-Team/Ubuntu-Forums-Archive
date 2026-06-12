---
title: "Unable to find the wubi-installed Ubuntu!"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by senartcon on 2010-07-08
Hi,
I downloaded Ubuntu 10.04 64 bit, and used wubi to install ubuntu in windows xp. After getting installed, apparently, when i opt for 'reboot  now', nothing happens; even if i reboot the computer myself, there is no option like Ubuntu to be selected; it just directly boots into windows. I even ran CHKDSK, but did not help. :-(
Pls help. Thank you.

---

### Post by gandaran on 2010-07-08
> **senartcon said:**
> Hi,
I downloaded Ubuntu 10.04 64 bit, and used wubi to install ubuntu in windows xp. After getting installed, apparently, when i opt for 'reboot  now', nothing happens; even if i reboot the computer myself, there is no option like Ubuntu to be selected; it just directly boots into windows. I even ran CHKDSK, but did not help. :-(
Pls help. Thank you.
we need more details
how did you do the install?
did you burn the Ubuntu iso to a cd as an image or data file ? 
or did you mount the iso file in windows and ran the wubi installer?
did you run the wubi installer from the cd?
or did you first downloaded and installed wubi in windows then tried to run the cd?
I'm inclined to believe Ubuntu isn't installed but check the windows add/remove programs if there is a Ubuntu install.

---

### Post by senartcon on 2010-07-09
I first downloaded both Ubuntu 10.04 and wubi and then mounted the Ubuntu iso file in windows and ran wubi installer. My control panel says that Ubuntu is installed. Even whenever i retry to install freshly it would always ask to uninstall the already installed Ubuntu, which means the installation was apparently complete everytime! But there is no option of Ubuntu to choose when i restart the computer. I dont know the prob!

---

### Post by dzon65 on 2010-07-09
It's been a while since I first tried wubi but why did you download ubuntu.Just run wubi,it'll install ubuntu for you.
Plenty of this on youtube.I just picked one:[http://www.youtube.com/watch?v=UyWVfzm79hU&feature=related](http://www.youtube.com/watch?v=UyWVfzm79hU&feature=related)

---

### Post by Paqman on 2010-07-09
Can you post up the contents of the file C:\boot.ini from Windows?

---

### Post by dzon65 on 2010-07-09
Like I said,it's been a while but he doesn't have to download ubuntu does he?To wubi,ubuntu is already there.

---

### Post by Paqman on 2010-07-09
> **dzon65 said:**
> Like I said,it's been a while but he doesn't have to download ubuntu does he?To wubi,ubuntu is already there.

You can do it either way. If you point Wubi at a disk image, it'll use that one, otherwise it downloads a fresh one and uses that.

---

### Post by dzon65 on 2010-07-09
Oh,thanks for refreshing my mind.Well,if I were him,I'd just  give the "traditional" wubi install a try.
Kind regards,J.

---

### Post by senartcon on 2010-07-09
> **dzon65 said:**
> It's been a while since I first tried wubi but why did you download ubuntu.Just run wubi,it'll install ubuntu for you.
Plenty of this on youtube.I just picked one:[http://www.youtube.com/watch?v=UyWVfzm79hU&feature=related](http://www.youtube.com/watch?v=UyWVfzm79hU&feature=related)

I have tried this earlier and even this time i did it once. As usual it gave me error messages; but after clicking 'cancel' for many times in the dialog box of the error msg, wubi installer resumes and starts downloading the ubuntu iso file, but never completes it even after several minutes (hrs)

---

### Post by senartcon on 2010-07-09
> **Paqman said:**
> Can you post up the contents of the file C:\boot.ini from Windows?

This is for downloading Ubuntu first, then Wubi and letting the Wubi to install:

[boot loader]
;timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect /usepmtimer
;C:\wubildr.mbr = "Ubuntu"
C:\wubildr.mbr = "Ubuntu"

This is for just downloading and running Wubi:

[boot loader]
;timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect /usepmtimer
;C:\wubildr.mbr = "Ubuntu"

---

### Post by senartcon on 2010-07-12
bump

---

### Post by 3rdalbum on 2010-07-12
Wubi doesn't always work. Sorry to admit it, but it's not really a good option for installing Ubuntu. It's a bit of a kludge involving an entire Ubuntu installation sitting inside a file on an NTFS filesystem, and the Windows bootloader booting the Ubuntu bootloader, etc.

I'd definitely recommend removing the Wubi install from the Windows Add/Remove Programs, defragmenting your hard disk, and then booting up an Ubuntu CD and doing a real dual-boot install. There are fewer limitations and a close-to-100% success rate.

---

### Post by senartcon on 2010-07-12
@[3rdalbum]("http://ubuntuforums.org/member.php?u=61044")

thanks for your suggestion
i would consider yours..

---

