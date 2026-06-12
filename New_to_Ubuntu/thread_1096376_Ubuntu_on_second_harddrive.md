---
title: "Ubuntu on second harddrive"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by Green_Grenade on 2009-03-14
OK! Heres the picture! I have 2 harddrives! I want one to be Windows.. and the other to be Ubuntu.. I have windows as my master right now.. and the second hD as the slave. It is formated. 
What are the actions I need to take to make that formatted drive.. a Ubuntu drive?!?!?!

---

### Post by theozzlives on 2009-03-14
go through the install process, but install to sdb  instead of sda.

---

### Post by Green_Grenade on 2009-03-14
That would be with a Disc and not a download then?!?!

---

### Post by jacksaff on 2009-03-14
Your ubuntu download should be as an .iso file. Burn this to a disc as an .iso file (ie. don't just copy it to the disc, you have to tell the burning program that it's already got a disc image). Then boot up from it by hitting F12 (usually, your machine might be different) when the computer is first turned on, and selecting the cd drive as first boot device.

You could also use your iso file to make a bootable usb device if you have a 1gig or more usb key. Google 'unetbootin' for how.

---

### Post by Green_Grenade on 2009-03-14
What if; everytime I try and download the Ubunut Iso it quits half way thro?!?! I even tried to torrent it.. and ya.. it just wont let me download it..

---

### Post by mkvnmtr on 2009-03-14
There is no reason your torrent download should quit part way through. Just stay with it until it finishes. The thing that makes a torrent better than a straight download is you can stop and come back tomorrow without hurting the download. On a regular download if it stops you lose it.

---

### Post by Green_Grenade on 2009-03-14
OK! Thx.. im tryin to convert my windows loving father to Ubuntu and a dual boot is the only way hes goin to bite! SO! 

OK.. next question... when I do get it loadd onto that second hD, i'll have to pik what hD I want to boot from... Correct?!

---

### Post by RetchingRabbit on 2009-03-14
> **Green_Grenade said:**
> OK! Thx.. im tryin to convert my windows loving father to Ubuntu and a dual boot is the only way hes goin to bite! SO! 

OK.. next question... when I do get it loadd onto that second hD, i'll have to pik what hD I want to boot from... Correct?!

Not exactly. During the installation process you will be able to chose to install GRUB to the MBR. This is generally  the best option. 
When you finin=sh the installation and reboot, GRUB will present you with the option to boot into Ubuntu or Windows. 
That simple.

---

### Post by Green_Grenade on 2009-03-15
Cool! Ok.. Imna have to watch for that.. Thx guys.

Id put it as solved, but.. it is and isnt.. (plus I dnt know how)

---

### Post by Linux000 on 2009-03-15
Do you have the boot disk ready?

---

### Post by munishvit on 2009-03-15
Sorry to mix-up my problem with this thread, but I too have problem with dual-boot and I want to install Windows XP on non-first primary partition. Please Check
[http://ubuntuforums.org/showthread.php?t=1095893](http://ubuntuforums.org/showthread.php?t=1095893)
aaanny help would be great. Thanks :D

---

### Post by Green_Grenade on 2009-03-15
I just wrote the boot disc..

---

### Post by Linux000 on 2009-03-15
***********BACK UP XP BEFORE TRYING THIS, IF IT IS MESSED UP AT ALL YOUR WINDOWS PARTITION COUlD BE GONE FOREVER*************************************


Good,
Start up your computer, with the boot disk in the drive,
Boot from it,
Go through the process, but when it asks about partitions, after Time zone selection I belive,
Select sdb, not sda these are your hdd's sda is the "first" or master disk and sdb is the "second" or slave disk,
with sdb seleceted, cilck guided use entire disk and install

> **theozzlives said:**
> go through the install process, but install to sdb  instead of sda.

Hope it helps

---

### Post by Green_Grenade on 2009-03-15
OK.. imna try it .. im kinda scared.. cuz its not MY computer.. but.. I will try it with all your Info.. and ya.. Im Scared.. Will keep you posted..

Thx..

---

### Post by Nightstrike2009 on 2009-03-15
I can dual-boot too, i can confirm that sdb will be your second hard drive, select use entire disk and make sure you dont select the drive with windows on. after installation your PC should reboot and you should see a black & white menu (Grub) which lets you select either Ubuntu or Windows on booting up. Good Luck ;)

---

### Post by Green_Grenade on 2009-03-16
PROBLEM!!!!! 

I got it to boot on the second harddrive.. (A lil differntly then we talkd) and now.. its stuck at um.. the part where you pik what kinda keyboard your useing.. 
I put in Canada...and ya.. its kinda just sitting there.. thinkin... then not.. I hear the disc run a lil but nothing is really happening.. 

Is this Normal?! Is it kinda sorta supposed to work like this?!?

---

### Post by Green_Grenade on 2009-03-16
NEVER MIND!

No problems! 
I think that it was just searching thro all the harddrives or something cuz after I wrote all that it started to work.. LOL! 
My Bad.

---

### Post by Green_Grenade on 2009-03-17
Well Gentlemen... I have trashed my Fathers computer.

Yep. I managed to crash his cpu fan and the cooling fan. So.. he has no computer and no Ubuntu.. 

All your tips were Awesome.. they totaly helpd me out.. 

Thx..

(if you could tell me how to post this as "Solved" that would be Cool)

---

### Post by Linux000 on 2009-03-17
Sorry about the computer
From what I know, solved and thanks have been disabled

---

