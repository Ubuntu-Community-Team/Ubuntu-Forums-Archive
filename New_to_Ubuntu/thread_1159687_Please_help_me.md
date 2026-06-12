---
title: "Please help me"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by Spinitch on 2009-05-14
[IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG] **after installing Jaunty ERROR city** 
im not so new to ubuntu but still a newbie and could really use the help,after i installed the new Jaunty 9.04 i rebooted after an update and now all iget when i boot right after the boot/grub/menu.lst are error messages repeating about 200 tries saying my root/dev failed or no such file or directory and leaves me in busy box after it gives up waiting for root device...ive tried every sudo trick i know (which isnt very much) and all the forum help i could find and im going to pull my brain out through my nose in a min as nothing has worked for me even trying from the live cd, if anyone is having this problem or a solution i would be forever in your dept im a photographer and all my work is on there and my newbie mistake was forgetting to back up my files :sad:( yes i know i know bad SPIN i will try to list the errors ive been getting hopefully will make it easier to help with my issue thank you everyone 


ata3.00: status: DRDY ERR
ata3.00 error: UNC
end_request:I/O error,dev,sdb,sector131
EXT3-fs:cant read group descriptor 7

mount:mounting /dev/disk/by-uuid/9f5cd2cd-413a-4ab0-95a-6408a0c80820 on /root failed:invalid argument

mount:mounting/dev on /root/dev failed: no such file or directory

mount:mounting/sys on /root/sys failed: no such file or directory

mount:mounting/proc on /root/proc failed: no such file or directory

Target filesystem doesnt have /sbin/init. no init found.try bypassing init=_bootarg.
 
also leaves me with 
 
sdb:detected capacity change from 0 to 500107862016

---

### Post by AndThenWhat on 2009-05-14
Have you tried using the Safe Mode or other kernel versions from the Grub menu?

---

### Post by Spinitch on 2009-05-15
i cant even get the log in screen is thereanother way to get insafe mode? ive tried redoing the aticonfig and anything ive read in the threads and when i tried to go back to my previous verison kernel in the grub menui get the black screen on log in i hear the login sound but just black

---

### Post by bacardiandwatermelon on 2009-05-15
This sounds horrible :-( I take it you couldn't access the drive via the live cd?

---

### Post by Spinitch on 2009-05-15
i put in the cd and try to but theres no option to repair just to install and i try to install and it goes right back into the error messages and repeats over and over went to 2300 attempts last night im losing it and worst comes to worst ill find a program to extraqct my files and blow up my computer lol or format which ever happens first

---

### Post by bennachie on 2009-05-15
If you could RUN from a liveCD (that is, don't use the Install option) you should see your HD as an accessible device. That would allow you to copy the important files to a USB stick or sticks. Unfortunately, it sounds as if your file structure may somehow have been damaged. Have you considered using SystemRescueCD ([http://www.sysresccd.org/](http://www.sysresccd.org/)) or some similar package to interrogate your HD?

---

### Post by Didius Falco on 2009-05-15
When you put the CD in, and the initial screen comes up, press F6 - it gives some different boot options. Try those out one at a time and see if any of them will let it boot successfully.

If one of them works, you can add it as an option at the end of the kernel line in your menu.lst file, which is found at /boot/grub/menu.lst on your Ubuntu partition.

To edit that file, you'll need root privileges,so open a Terminal from **Applications/Accessories/Terminal** and type ```
gksudo gedit
``` and navigate to the file.

To add the option that works (I'm hoping one does, so I thought I'd save you some time and tell you all this now - if none of them work, I'm not sure what to do) just look for the line in your menu.lst file that starts with "kernel". Here is a sample from mine:

 ```
 ## ## End Default Options ##

title        Ubuntu karmic (development branch), kernel 2.6.30-5-generic
uuid        e47525af-4710-4faa-bc80-fbad1ec6d109
kernel        /boot/vmlinuz-2.6.30-5-generic root=UUID=e47525af-4710-4faa-bc80-fbad1ec6d109 ro quiet splash 
initrd        /boot/initrd.img-2.6.30-5-generic
quiet
```

See at the end of the kernel line where it says "quiet"and "splash" - those are kernel options. You'd simply add the same option (I'd recommend writing them down as you try them out) to the end of the kernel line. Again, an example using mine:

```
## ## End Default Options ##

title        Ubuntu karmic (development branch), kernel 2.6.30-5-generic
uuid        e47525af-4710-4faa-bc80-fbad1ec6d109
kernel        /boot/vmlinuz-2.6.30-5-generic root=UUID=e47525af-4710-4faa-bc80-fbad1ec6d109 ro quiet splash newoption
initrd        /boot/initrd.img-2.6.30-5-generic
quiet
```

I hope this helps....

Regards,

Didius

---

### Post by arapa on 2009-05-15
Have you run a filesystem check on the drive from a live CD ([COLOR="Red"]the drive must NOT being mounted![/COLOR])?

```
sudo e2fsck -f -c -v /dev/[device you want to check]
```

replace "[device you want to check]" with your drive info.

---

### Post by Spinitch on 2009-05-15
thanks i will try that! i wasnt sure if i should mess with the f6 or f4  on install :) but i will try and im hoping this will work i had tried adding the splash to the end of the Kernel command line and it looked like it did something diff but still went into the forever never ending error messages lol i appreciate all the help THANK YOU i also read it could be the UUID that needed to be changed in the lkernel line to/dev/mapper/vg1-root--lv and that didnt work either but i will let you know how it fairs when i try your solutiom both bennachi and Didius Falco thank you both again for helping out this newb

---

### Post by Didius Falco on 2009-05-15
I *hope* it works, but I can't make any guarantees...

Good Luck!!

Regards,

Didius

---

### Post by Spinitch on 2009-05-15
well im going to try all of these lol it cant be worse than it already is if i lose all my art anyone who has any the price will go up from my head exploding which you all can buy and take advantage of now while im still alive lmao

---

### Post by Don1500 on 2009-05-15
If you can't get the Live CD to boot then you might have a bad CD. In that mode it doesn't even need a hard drive to load.

---

### Post by Spinitch on 2009-05-15
i was just checking that i think the fact i used the 32 version rather than 64 ....im such a newb

---

### Post by Spinitch on 2009-05-16
well so far the only thing i can get running is the systemrescuecd i burned last night now im going to sound sooo newb but....i dont know what to do now that im in it :S lmao this thing is all new to me and how to use it ......so any ideas would be GREAT lol

---

