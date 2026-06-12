---
title: "Tried to get rid of GRUB, now GRUB 17"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by krz.ostr on 2009-10-01
Hi ho,

short:
- have debian & vista
- want ubuntu (&vista)
- while starting having this ****ing grub
- the kubuntu cd doesnt work with grub ... grrr
- tried to get rid of this shitty grub
- formated the ext3 of debian
- grub error 17... EVEN if vista is untouched like a virgin...

i have an untouched vista. what a m*r*n did make this grub? why i cant boot now?

:'( :'( :'( halp

1st time i tried to install ubuntu the install stopped at some point. 
dont know why. installed debian. didnt like it.
so after a time i tried another kubuntu. this time with wubi. 
wubi menu "reboot now". it didnt make anything.
ok... boot? it dont boot. okay. maybe its all about grub.

and than the grub torture started.

---

### Post by SlugSlug on 2009-10-01
If your kubuntu cd is not booting then that is due to your boot order - not grub.

try follow this guide to reinstall your grub..
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by krz.ostr on 2009-10-01
my boot options: 

-cd
-hdd

debian and a old ubuntu cd booted... thx 4 link. i check it out :)

btw... if i dont want to fix grub... just to ... KILL this... will it work either with the link? ^^'



refered to the link: which LiveCD?

---

### Post by krz.ostr on 2009-10-01
baaah,

it dont work...

grub > ...

and than the root (hd0,0) command does nothing... so the following commands dont work... even find /boot/grub/stage1 dont work.

i just want to kill this f*cking grub ****... :'(

---

### Post by ukripper on 2009-10-01
Boot into live cd and use below command and post the output here:

```
sudo cat /boot/grub/menu.lst
```

---

### Post by krz.ostr on 2009-10-01
Dont know what you mean with LiveCD. If you mean Windows... 

I have a "rescue" disk from Toshiba. There is only one option: format kill bam bum all new.

The old XP CD reacts crazy. Pressed R to get this command line (it was even an option). Than i have some seconds to press enter do choose a keyboard layout. take the german one... than i have one option: press enter to restart... what the ****?


And the most interensting thing ever: WHY windows cd boots? WHY debian cd boots? BUT NOT the ubuntu one i downloaded. (i tried the kubuntu 32, kubuntu 64 and ubuntu 32).

---

### Post by Vaphell on 2009-10-01
because apparently your ubuntu cd is broken/unreadable or whatever - if you have proper boot order (cd->hdd) then grub is launched AFTER cd drive not recognizing bootable CD

by liveCD he meant any CD that allows you to use the system without actual installation to the hard drive, for example Ubuntu (working one)

---

### Post by Sef on 2009-10-01
> BUT NOT the ubuntu one i downloaded. (i tried the kubuntu 32, kubuntu 64 and ubuntu 32).

1) Did you md5sum the download?

2) Did you burn them to a cd at 4x or slower?

> Dont know what you mean with LiveCD. If you mean Windows... 


No, not the Windows CD, which is not a Live CD.  A Live CD has an operating system on it, so it can boot up from the Live CD and not touch the hard drive.

---

### Post by SlugSlug on 2009-10-01
To wipe grub you must boot from windows CD drop to recover mode and then type
fixmbr

job done.

---

### Post by krz.ostr on 2009-10-01
I went on the ubuntu.com site. And took the actual version with download from Freie Universität Berlin.
Did I md5sum? What is md5sum? Some hash code to check if I downloaded it correctly? 
No, I did nothing with the download, except extract and than ... oh ****... shouldnt I extract the files and just burn it because its already an iso?
Is is possible to burn slower than 4x? Dont know, didnt check it up. But it should be atleast 4x.
I downloaded 3 different versions, all didnt boot before grub.

I have no "LiveCD". The old Ubuntu CD boot. I press installation, than he starts loading some files, than he has some IO not read problems, than he "ok"s something... and at the end i have $ubuntu$ubuntu$ or something like that.
The other Linux CD I have is a Debian DVD. It boots and it works, but I couldnt see some options except installation.

---

### Post by LewRockwell on 2009-10-01
[http://www.iknowkungfoo.com/blog/index.cfm/2008/6/16/Stupid-solution-for-Grub-error-17](http://www.iknowkungfoo.com/blog/index.cfm/2008/6/16/Stupid-solution-for-Grub-error-17)

.

---

### Post by krz.ostr on 2009-10-01
no no, 
ther is no external hard drive or usb stick...

i hope that the new burned ubuntu (without extracting the iso *shame on me*) will make wonders pissble. :)

EDIT: by the way again: this normal installation ubuntu cd is a liveCD? or do i have to search for one? is there a liveCD on ubuntu.org?

---

### Post by LewRockwell on 2009-10-01
> **krz.ostr said:**
> no no, 
ther is no external hard drive or usb stick...

i hope that the new burned ubuntu (without extracting the iso *shame on me*) will make wonders pissble. :)

EDIT: by the way again: this normal installation ubuntu cd is a liveCD? or do i have to search for one? is there a liveCD on ubuntu.org?

many of the offerings are indeed LiveCDs

the alternate install CD is NOT

.

---

### Post by krz.ostr on 2009-10-01
OK, the ubuntu CDs now work :) 

Dont extract every file that has the winRar logo :) 
(especially if you are downloading a cd image)

I just install ubuntu over the former debian partition and hope it will work. 
And if not I use Knoppix and enter the fixmbr command.

thx 4 help :)

---

### Post by krz.ostr on 2009-10-01
topic closed

all works

thx :)

---

