---
title: "how to speed up my 105-seconds doot?"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by suggestions on 2010-01-18
does anybody know if there is a way to accelerate the boot?


Hardware: eeepc 701 4g (with asus xandros on internal sdd drive)
ubuntu 9.10 booted from SD card 8gb

BOOT TIME: 105 SECONDS

(by the way, xandros boots in 22 seconds)

here you are the times in seconds:

0-35: I continue to see the grub 1.97 beta 4 text menu
36-39: black screen
40-58: ubuntu logo (monochrome, white)
59-71: black screen
72-82: ubuntu screen (brown, with sliding cursor)
83: login (I enter my password)
84-104: ubuntu is loading (same brown screen)
105: I hear the login music, and ubuntu desktop appears within few seconds

I post in attachment a bootchart image, hoping it will help, because I'm unable to understand it.. 

thank you in advance for any help..

---

### Post by 73ckn797 on 2010-01-18
My desktop unit has the same issue. I feel it may be that I have 2 hard drives but have not pursued a solution. My laptop fires up in less than 30 seconds. Both run 9.10.

---

### Post by J V on 2010-01-18
I don't understand the brown screens with the sliding images, but I can speed you up a little bit, install startupmanager and you can lower the wait time for grub (or remove the wait time completley)

---

### Post by MarkC502 on 2010-01-18
Two things you can use to troubleshoot this

Install bootchart and then it can run at bootime and it make a nice color graph that show how long each part of your system bootup is taking. By doing so you should be able to see what is the thing that is taking so long and then work on how to correct that. You may very well find it is something stalling or erroring during boot that is taking so long etc and then you will at least know what to troubleshoot.

Command to install it

sudo apt-get -y install bootchart


Also you can install "bum" which is a bootup manager that lets you turn off services and software you don't need ( I.E. bluetooth or printing if you don't use them on a certain machine ) which can give you faster bootup speed with less software to load.

Command to install bum

sudo apt-get -y install bum


Good Luck

---

### Post by chaanakya_chiraag on 2010-01-18
Is grub installed on a different hard drive than Ubuntu?  That may lead to long wait times.

---

### Post by baizon on 2010-01-18
I recommend that 2 threads:
[HowTo: Speed up ubuntu boot process - the way you can feel it. - updated]("http://ubuntuforums.org/showthread.php?t=89491")
[BUM v.2.x]("http://ubuntuforums.org/showthread.php?t=82783")

---

### Post by 73ckn797 on 2010-01-18
> **MarkC502 said:**
> Also you can install "bum" which is a bootup manager that lets you turn off services and software you don't need ( I.E. bluetooth or printing if you don't use them on a certain machine ) which can give you faster bootup speed with less software to load.


There is also System/Preferences/Startup Applications that will allow the same procedure and is comes with 9.10.

---

### Post by suggestions on 2010-01-20
> **73ckn797 said:**
> There is also System/Preferences/Startup Applications that will allow the same procedure and is comes with 9.10.

done (I have removed all the possible startup apps), but the boot time is actually almost the same.. 

to be more precise, the last 4 boots are now all at 107 seconds (no longer 105).. the boot time seems increasing..

if the boot time will reach 120 seconds, I will remove ubuntu, because in my modest opinion this can only mean that the software is slowly destroying my hardware (SD card in this case) through read/write operations..

---

### Post by clhsharky on 2010-01-20
HI


    SD (Secure Digital) memory card are designed for storage,and are slow. USB is also slower than drives on ATA or SATA. Run a operating systems on a fast drive if you want speed. Ubuntu is fast on properly configured hardware.


Sharky

---

### Post by theozzlives on 2010-01-20
> **clhsharky said:**
> HI


    SD (Secure Digital) memory card are designed for storage,and are slow. USB is also slower than drives on ATA or SATA. Run a operating systems on a fast drive if you want speed. Ubuntu is fast on properly configured hardware.


Sharky

Was just gonna say that, why are we booting from SD??? It's not destroying your hardware.

---

### Post by suggestions on 2010-01-20
> **clhsharky said:**
> HI
    SD (Secure Digital) memory card are designed for storage,and are slow. USB is also slower than drives on ATA or SATA. Run a operating systems on a fast drive if you want speed. Ubuntu is fast on properly configured hardware.
Sharky


of course I definitely accept a slow device.. what is unacceptable and alarming is that the boot is becoming slower and slower.. I strongly suspect that the software is damaging my hardware.. there is no proof that this is true, but there is also no proof that this is false. The only certainty is that the problem is real, and in my opinion it is very serious.

boot times:

105 seconds, then 107 seconds yesterday, and then, few minutes ago, 111 seconds..

a boot above 120 seconds means that for safety reasons I will remove ubuntu from my SD card..

---

