---
title: "Can't Instal from burned ISO."
date: 2010-03-07
forum: New to Ubuntu
---

### Post by ho0ola on 2010-03-07
Hey fellers,
            My PC in windows runs like crap.. I cant get any games to even load b/c my Onboard GPU doesnt support DX 9.0 (which i cant figure out how to load an earlier driver version) I am extremely frusterated right now with windows, my computer is basically worthless. so i want to try Linux but...

      I just burned the newest .ISO version of Ubuntu to a disk (checked disk and all files are correct) I insert disk and restart Windows XP.  The CD boots the main ubuntu menu, but when i chose "install" i cant seem to get it working. A receive the error :             

I/O error 
                                                        error reading boot CD

I went through forums, tried checking/unchecking the common command prompts by pressing f6, nothing would work. I am the most begginner/noob possible, so any helpful simple tips would be supremely wonderful. Nothing i am reading makes any sense :biggrin:

Thanks guys!

Windows XP 
Onboard nVidia Geforce 4 MX
2gb 2700rpm DDR Ram
120gb Hdd
 ....yada yada....

---

### Post by r-senior on 2010-03-07
Long shot, but you could try the "Try Ubuntu with no changes to your system" option, or whatever it's really called, and run the installer from the desktop icon?

I installed Xubuntu on a machine that wouldn't install from the front menu, but worked OK from the desktop icon.

---

### Post by Phrea on 2010-03-07
Did you check the MD5 sum?

---

### Post by MichealH on 2010-03-07
CD Menu > Check Disk for Defects?

---

### Post by candtalan on 2010-03-07
Welcome!

Which version is it that you have downloaded?

Sounds a bit like a bad burn (guess).

Burning the iso file to blank CD needs to be byte perfect (unlike say audio CDs which will still seem to work ok if they have many errors), and this is more likely to be successful when the burn speed is reduced. 

I use at least only half maximum speed burn, for my system this is about 25x. I would burn slower if I got any CD problems.

After the burn, use the CD and boot from it, and choose 'check this CD for defects' in the target drive. This will check a lot of things, the download quality, the burn, the CD drive itself.

Then boot from the CD again and run as a live CD - choose - run ubuntu without changing anything on your existing system

hope that helps?

---

### Post by ho0ola on 2010-03-08
Hey guys thanks,
       I have this exact version: Ubuntu 9.10-destop i386.iso 


I am burning the disk at 4x the slowest possible. last time when  i tried cheking the disk for errors i got the error message : 
I/O error
error reading boot CD

Hopefully 4x will work.. ill post results in a bit :) thanks ya'll

I dont know how to check the MD5 sum.. Im a newb

---

### Post by Tikkyca on 2010-03-08
Just get the free live CD from [http://shipit.ubuntu.com/](http://shipit.ubuntu.com/) :)

---

### Post by ho0ola on 2010-03-08
Yeah, I tried it again and still getting same error. Connot read Boot CD. Should i try re-downloading Ubuntu? I wouldnt be surprised if my computer just doesnt like it b/c of a hardware conflict, I dont know what happened when i reformatted, but my PC doesnt like anything anymore... Im basically just installing Ubuntu as a last resort OS, because my windows XP disks were corrupt i think. meow my PC is wackkedddd..

---

### Post by ho0ola on 2010-03-08
Okay thanks Tikkyca!

---

### Post by Paddy Landau on 2010-03-08
> **ho0ola said:**
> Should i try re-downloading Ubuntu?
Did you check the MD5 sum of your Ubuntu iso *before* you burned it to CD?

[LIST]
[*][MD5 sums for 9.10]("https://help.ubuntu.com/community/UbuntuHashes#9.10")
[*][How to check MD5 on Windows]("https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows")
[/LIST]
> **ho0ola said:**
> meow my PC is wackkedddd..
If you have an older PC, you may find that [Xubuntu]("http://www.xubuntu.org/") will work better than Ubuntu. Xubuntu is an official Ubuntu distro tweaked to fit smaller and older PCs.

---

### Post by Arijit_Kundu on 2010-03-08
Also, if the md5sum matches and if the problem is with your cd burner, you can try to install it from usb using [unetbootin]("http://unetbootin.sourceforge.net/").

---

### Post by Miljet on 2010-03-08
I'm betting on a defective CD drive. It is much more common than most people realize. Easiest way to check is try the CD in a friend's computer.

---

