---
title: "DD-WRT Install from Ubuntu 16.04"
date: 2017-07-26
forum: Networking &amp; Wireless
---

### Post by chris2422 on 2017-07-26
I am trying to install DD-WRT to my Linksys EA6350 router. Unfortunately it is not supported, but I did find a 'Kong build' online. ([http://www.desipro.de/ddwrt/](http://www.desipro.de/ddwrt/)) 

However, it is my understanding that you flash a 'lite' version of DD-WRT before flashing the full version. desipro.de does not have that 'lite' file. I found on the DD-WRT forums someone was using tftp, but so far that has not been working for me.

DD-WRT post about tftp:

"this router has two firmware images. i flashed both images: 

CFE> flash -noheader : nflash0.trx 
CFE> flash -noheader : nflash0.trx2 

from your computer: 
tftp -i 192.168.1.1 put dd-wrt.v24-K3_AC_ARM_STD-27950m.bin 
.....wait for ok, then repeat for 2nd image 
tftp -i 192.168.1.1 put dd-wrt.v24-K3_AC_ARM_STD-27950m.bin 

rebooted, and dd-wrt came up. "

Every time I try using tftp it says "No such file or directory exists." despite the fact I know it is in /home/bin/dd-wrt.v24-K3_AC_ARM_STD.bin

Currently trying:
tftp
connect 192.168.1.1
put /home/bin/dd-wrt.v24-K3_AC_ARM_STD.bin

Any help would be appreciated!

---

### Post by DuckHook on 2017-07-26
Welcome to the forums, chris2422

You would do far better posting on the DD-WRT forum about this matter. I use DD-WRT, but the members of this forum are unlikely to be DD-WRT experts like they are over there: [http://www.dd-wrt.com/phpBB2/](http://www.dd-wrt.com/phpBB2/)

The various ways to install DD-WRT are very involved and vary from router to router. They are also quite arcane, especially for ordinary users. I have not followed your link, nor am I familiar with your router, nor do I feel competent advising you further. However, by way of warning: it is easy to brick your router with the wrong steps, at which point, you would have a very expensive door stop. I strongly recommend you to seek the help of DD-WRT experts at the above forum before proceeding further. It is unwise to simply follow instructions found online when attempting what you are doing.

Also, TFTP client is not part of a default Ubuntu install. You must first install the client by doing:```
sudo apt install tftp
```
As already stated, the rest is at your own risk.

---

### Post by chris2422 on 2017-07-27
> **DuckHook said:**
> Welcome to the forums, chris2422

You would do far better posting on the DD-WRT forum about this matter. I use DD-WRT, but the members of this forum are unlikely to be DD-WRT experts like they are over there: [http://www.dd-wrt.com/phpBB2/](http://www.dd-wrt.com/phpBB2/)

The various ways to install DD-WRT are very involved and vary from router to router. They are also quite arcane, especially for ordinary users. I have not followed your link, nor am I familiar with your router, nor do I feel competent advising you further. However, by way of warning: it is easy to brick your router with the wrong steps, at which point, you would have a very expensive door stop. I strongly recommend you to seek the help of DD-WRT experts at the above forum before proceeding further. It is unwise to simply follow instructions found online when attempting what you are doing.

Also, TFTP client is not part of a default Ubuntu install. You must first install the client by doing:```
sudo apt install tftp
```
As already stated, the rest is at your own risk.

I also have a thread going on the DD-WRT forums, but they are much more inactive than the Ubuntu forums. I was hoping between the two I would find somebody. 

I agree it is very involved. Unfortunately I have no idea where to find information on this subject other than online.

---

### Post by cheese66 on 2017-08-02
That about installing the mini version first, this was I believe because the ROM size of some router devices were too small. (this was with the popular Linksys WRT54GL)
Please note that they recommend to not use old hardware like the WRT54GL. (or others of that age).

As of installing DD-WRT firmware, factory Linksys or openWRT; there are sequences in which order you have to install different firmware brands. You will have to check for this on their forums. This *might* only be the case with upgrading from the web browser.

As for DD-WRT firmware and not having a release yet,
You might want to check LEDE/LuCi. Which might be further with a release of the your router than DD-WRT.(but check)
As for how installing this(and more), there are detailed enough pages on the wiki their I believe.

The old LEDE (openWRT) project is not worked on anymore, LEDE is the new openWRT, which was popular too under Linux users.
You will only have to install a package to make LEDE to look like openWRT did. (! and if you have DD-WRT installed already; go to latest Linksys factory firmware before you upgrade to LEDE).

And an advise: always verify their wiki(or forum) before you do something. A broken router is easily created.

---

