---
title: "stuck on first  attempt dual boot install (XP and 9.04 )"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by obrienaj on 2009-10-17
Well, my casual idea to try and establish a dual boot sytem turned out BAD!  First attempt seemed to go ok but I got a grub 21 error upon PC reboot. , Seem I had left an external drive plugged in and the install went to it.  I tried to find a way to fix the grub error , without success.   I am not able to boot windows at all despite several tries to find a way at the BIOS level.
 
 
Anyway, once I unplugged the external HD , I tried a dual boot install again.  The ISO disc of 9.04 moves along OK to the partition section and then I am lost.  the dual boot "how too" pages I found on the internet appear to be different from the info I am presented.  I don't want to accidentally zap my Windows OS !  What do I do ?  I am at step 4 of 7.  The screen says...
 
/dev/sda1 ntfs      
 
I think I am then supposed to "edit patition"  Correct ?  If I am , what do I do? I am presented with options to  USE AS, Mount position, and Format the partition.  That's where it begins to get scary. Help would be appreciated.  I would like to get access to Windows back (Windows files are still there , I can see when I use the ubuntu ISO to navigate the hard drive folders.
 
Thanks.

---

### Post by Elfy on 2009-10-17
Can you do a screenshot of the window you are looking at - sounds to me like it is not giving you the option to resize the ntfs partition.

Apps > Accessories > Take Screenshot

Then post new reply and if you page down a bit you will see the Manage attachments - there you can add the screenshot.

---

### Post by obrienaj on 2009-10-17
I'll see if I can do that and somehow store the screen shot.  I am on a different PC at the moment, 
 
You are correct, I just saw a youtube video of the dual boot install, at step 4 the video shows a scfreen that  has a line about having the two side by side and the ability to drag the the size of the partition.  I do not get that.    I get the whle bar as 9.04 and dragging it to size the partition has no effect.

---

### Post by Elfy on 2009-10-17
If that's the case we can use the partition editor to do the first bit and then start the install - not too much different.

First I would ask if you checked the md5sum of the download to make sure it was ok and ran the cd integrity chjeck when the livecd boots.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck)

---

### Post by obrienaj on 2009-10-17
Running the check now.  By the  way, if I plug my external HD in and run the disc, I do get the side by side option but it says only Ubuntu is on there.  If I choose a manual option it displays Windows as being their 100% of the space  but the manual option does not provide a way to resize for adding Ubuntu.
 
Off now to run the check

---

### Post by obrienaj on 2009-10-17
the disc checked out fine

---

### Post by mick55 on 2009-10-17
hi obrienaj

Unplug your USB drive to be safe

First defrag your xp partition

Boot the live Cd and run partition editor

Shrink your windows partition to your desired size

Reboot into windows xp to make sure all is well, reboot again if it asks.

Boot the live Cd again

Select to install Ubuntu in the unpartitioned space

Follow the directions from there onwards

Make sure you write down the username and password you choose

In about 20 minutes you will be running Ubuntu

cheers
mick

---

### Post by obrienaj on 2009-10-17
Thanks.  How do I defrag if I am not able to run Windows ?

---

### Post by newtocade on 2009-10-17
try a third party boot disc partioner like ghost...create the partition then install (prepare everything before unbuntu)...or try the disc mamgement in windows to partition.

---

### Post by obrienaj on 2009-10-17
> **newtocade said:**
> try a third party boot disc partioner like ghost...create the partition then install (prepare everything before unbuntu)...or try the disc mamgement in windows to partition.
 
I am not able to boot Windows so cannot run software to create a partition. The only thing I have that works is the Unbuntu CD. When I try to boot Windows I get the Grub error 21.  Getting Windows back is my main concern at the moment.

---

### Post by mick55 on 2009-10-17
hi again

i hope you have a windows xp cd.

If you do boot up the cd, follow the instructions to repair an installation, select recovery cosole, and run this command
at the prompt
```
fixmbr
```then this command
```
fixboot
```reboot into windows and then follow my above install guide

---

### Post by obrienaj on 2009-10-17
> **mick55 said:**
> hi again
 
i hope you have a windows xp cd.
 
If you do boot up the cd, follow the instructions to repair an installation, select recovery cosole, and run this command
at the prompt
```
fixmbr
```then this command
```
fixboot
```reboot into windows and then follow my above install guide
 
The recovery console is on the HD which I am unable to access at the moment, it is usually available in Windows Safe Mode.

---

### Post by newtocade on 2009-10-17
run windows boot disk...repair...or third party like ghost then chose the partition that windows is on and make it active...thats how i saved my system from a crash... i had a restore partition and used norton ghost to actvate the partition and repaired my windows vista.

---

### Post by mick55 on 2009-10-17
i will repeat my self

boot up the windows xp cd.

it will give you a choice of installing windows or repairing a windows 
installation.

Chose repair a windows install.It will come to a screen 
where one of the choices is recovery console.

do you have a windows xp cd?

i can't help you unless you provide details, and follow the instructions.

---

### Post by newtocade on 2009-10-17
u need an xp boot cd...change bios setting to primary boot device CD or DVD drive and boot with xp CD then repair...also norton ghost is a boot cd with disc management

---

### Post by obrienaj on 2009-10-17
> **newtocade said:**
> run windows boot disk...repair...or third party like ghost then chose the partition that windows is on and make it active...thats how i saved my system from a crash... i had a restore partition and used norton ghost to actvate the partition and repaired my windows vista.
 
 
How would Norton ghost run if you can;t boot Windows ?

---

### Post by mick55 on 2009-10-17
once more........


do you have a windows xp cd?

---

### Post by newtocade on 2009-10-17
its a boot cd...definition...put in your xp cd and restart...hope your bios is set to boot from cd...if not as soon as the bios info is up on the screen hit del button to get into bios and change primary boot device to your cd drive restart then follow instructions on your boot cd...have you ever installed an operating system?...if you cant boot from a cd then something is terribly wrong with your computer

---

### Post by mapes12 on 2009-10-17
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by obrienaj on 2009-10-17
> **newtocade said:**
> its a boot cd...definition...put in your xp cd and restart...hope your bios is set to boot from cd...if not as soon as the bios info is up on the screen hit del button to get into bios and change primary boot device to your cd drive restart then follow instructions on your boot cd...have you ever installed an operating system?...if you cant boot from a cd then something is terribly wrong with your computer
 
 
I can boot the ubuntu CD but the one XP CD I have will not boot, I get the Grub Error 21 when I try to restart the PC and boot from the CD drive.  So, would it not be better to try and get ubuntu to partition correctly and then have access to the HD with Windows on it ?

---

### Post by mick55 on 2009-10-17
hey newtocade 

he can definitely boot to cd , he borked his system
doing it.

I can't get the guy to answer a straight forward question though,
as to whether or not he has a windows xp install cd.

Right now his install is easy enough to fix, but if he goofs 
around with it too much it may not be.

cheers
mick

---

### Post by obrienaj on 2009-10-17
I managed to get a C prompt in DOS, so am trying a few of the suggestions now, thanks

---

### Post by newtocade on 2009-10-17
im sure all is lost for him...he can probly say good buy to all his files...it happens to the best of us...lord knows i learned the hard way way back when...like douglas adams says "don't panic"
this is fun

---

### Post by mick55 on 2009-10-17
hey obrienaj

don't make things worse.

do this and all will be well.
Download this rescue cd, it will restore your xp 

[html]http://www.paragon-software.com/home/rk-express/[/html]It's frre, it's small, and it works.

select the option to fix your boot record

good luck
mick

---

### Post by obrienaj on 2009-10-17
> **mick55 said:**
> hey newtocade 
 
he can definitely boot to cd , he borked his system
doing it.
 
I can't get the guy to answer a straight forward question though,
as to whether or not he has a windows xp install cd.
 
Right now his install is easy enough to fix, but if he goofs 
around with it too much it may not be.
 
cheers
mick
 
Hey Mick, one of us has been up too late...  I answered u twice.

---

### Post by obrienaj on 2009-10-17
> **mick55 said:**
> hey obrienaj
 
don't make things worse.
 
do this and all will be well.
Download this rescue cd, it will restore your xp 
 
[html]http://www.paragon-software.com/home/rk-express/[/html]It's frre, it's small, and it works.
 
select the option to fix your boot record
 
good luck
mick
 
 
Thanks!

---

### Post by obrienaj on 2009-10-17
> **mick55 said:**
> hi again
 
i hope you have a windows xp cd.
 
If you do boot up the cd, follow the instructions to repair an installation, select recovery cosole, and run this command
at the prompt
```
fixmbr
```then this command
```
fixboot
```reboot into windows and then follow my above install guide
 
 
Bill Gates is happy again, Windows is back on my PC.  I'm still gonna try get a dual boot to work!
 
Thanks.

---

### Post by mick55 on 2009-10-17
hi obrienaj

Our messages crossed, i was complaining you hadn't answered while you were answering.

Look go slow on this part you don't want to lose your windows
stuff.That rescue CD works like a champ.

Remember it is very easy to recover files as long as you don't
install over them.

good luck
mick

---

### Post by obrienaj on 2009-10-17
Well Windows is working fine but the new dual boot install attempt  of 9.04 ran in to the same problem.....  no  install side-by-side option and no resize of option for the partitions.  Looks like I am going to have to do it manually.  Any dummies guide for the manual option ?
 
Andy.

---

### Post by mick55 on 2009-10-17
hi Andy 

There is a very good guide for doing what you want.

See post #7 in this thread, it is the original step by step guide i posted for you.

When you boot the live CD let it boot up the whole way
to it's desktop.

Run partition editor from the live CD's desktop.
If it won't let you resize the partition unmount it.

And defrag windows before you resize.

Incidentally what method worked to restore your windows boot record?

---

