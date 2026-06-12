---
title: "Problems with notebook and 10.04"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by FrankenCub on 2010-12-27
We have an Emprex notebook that came with Ubuntu 8.04, went through the update manager to upgrade to 10.04. All was going fine until we lost wireless connection and now it won't boot at all. It shows Ubuntu 10.04 but only gets so far then shows several errors. I tried booting in recovery and a couple things it shows...

error getting socket: invalid argument
segmentation fault
gave up waiting for root device. Common problems:
  -boot args (cat /proc/cmdline)

missing modules (cat /proc/modules; ls /dev)
Alert! /dev/disk/by-uuid/a5f1131b-1de5-481a-a582-ee4e00080c98 does not exist. Dropping to a shell !

Any advise as how to proceed ? I'm a noobie with Ubuntu but doing well on my desktop with 10.10 and lovin it.

---

### Post by earthpigg on 2010-12-27
grab a 10.04 livecd, boot from it, grab your vital data if it isn't already backed up, and do a clean install.

in the future, in-place updates probably shouldn't be done over wifi or on battery power :D

---

### Post by garvinrick4 on 2010-12-27
#The only thing you can do is chroot into install and run dpkg and if things were far enough
along and just need to set up and dependencies fixed this will work. You can give it a try.
#From live Cd with internet connection:
#I will use sda1 for code you have to change it to your own partition number.
                      ```
sudo mount /dev/sda1 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
``````
dpkg --configure -a
``````
apt-get update && apt-get upgrade
``````
dpkg --configure -a
``````
exit
```                      ```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
``````
sudo reboot
```

---

### Post by FrankenCub on 2010-12-27
garvinrick4....that doesn't get me anywhere, seems to be a lot of "not found". Thanks anyhow ;)
 

earthpigg......Yeah, I shoulda known better on the WIFI but now there's no question :oops:

Seems I'll be doing a clean install, do you think 10.10 for Notebook would be a better choice ? Or is this cheap little junkbook not up to the task lol ?

---

### Post by garvinrick4 on 2010-12-27
Sorry only works if upgrades were already downloaded and needs configured. 
Just according to what stage the update && upgrade was in. So is about a 50/50 chance
of working. Good luck to you and a happy New Year.

---

### Post by Bucky Ball on 2010-12-27
Go 10.04 as it is LTS (long term support) release and has 3 years support rather than two. Having said that, up to you. Either is suitable for your machine. That is what Ubuntu is all about. For a more lightweight install you might try Xubuntu 10.04 LTS. You can install a full Ubuntu - ubuntu-desktop includes all apps - or just install Gnome and the any packages from within later and develop all kinds of hybrids!  Have fun ...

---

### Post by FrankenCub on 2010-12-28
Thank you all for your help so far, it's much appreciated. I decided to go with 10.10 Netbook edition mainly cause I run 10.10 on my desktop. I downloaded the ISO and installed to a USB and the notebook still will not boot from it. Took a screenshot of what's on the USB. Does it look like anything is missing ?

[[IMG]http://i306.photobucket.com/albums/nn244/FrankenCub/Nature%20pics/th_Screenshot-UbuntuUSB.png[/IMG]](http://s306.photobucket.com/albums/nn244/FrankenCub/Nature%20pics/?action=view&current=Screenshot-UbuntuUSB.png)

I did go to the BIOS and made sure it was to boot from USB.
I've also tried Unetbootin to load the ISO to the USB and before it opens it says ....7z not found.

---

### Post by Bucky Ball on 2010-12-28
On the desktop computer, have you tried making the USB via System->Administration->Startup Disk Creator?

Is this a notebook or a netbook??? We're talking single core (generally) 32bit processor and 10" or less screen (generally) for a netbook. If it has a larger screen and beefier processor, Netbook edition is not probably a good choice.

---

### Post by FrankenCub on 2010-12-28
Hi there Bucky...Yepper, startup disk creator was the first one I tried.
It's a little 10" screen Notebook. For a "junkbook" it actually worked surprisingly well. Our 12yr old loves it. I am gonna try to boot my desktop from this USB to see where I get.

---

### Post by FrankenCub on 2010-12-28
When I used Unetbootin, this is what shows on the USB....

[[IMG]http://i306.photobucket.com/albums/nn244/FrankenCub/Nature%20pics/th_Screenshot-UbuntuUnetbootin.png[/IMG]](http://s306.photobucket.com/albums/nn244/FrankenCub/Nature%20pics/?action=view&current=Screenshot-UbuntuUnetbootin.png)

---

### Post by FrankenCub on 2010-12-28
Ok well, I got some progress. It looks to be booting from the USB now and runs through the 10.10 loading screen. Then goes to a screen with a rectangle and a human figure at the bottom but then the screen goes weird like the old TVs did when they needed to be adjusted.

---

### Post by FrankenCub on 2010-12-28
How about a video of what it's doing :???:

[[IMG]http://i306.photobucket.com/albums/nn244/FrankenCub/Nature%20pics/th_MOV02543.jpg[/IMG]](http://s306.photobucket.com/albums/nn244/FrankenCub/Nature%20pics/?action=view&current=MOV02543.mp4)

---

### Post by FrankenCub on 2010-12-29
WTH....photobucket removed the video :mad: I will try to add it again as I can't see no reason it violated their TOS, I've read them again.
Anyone have any ideas as to why I'm having the screen problem when loading ?

I added the video again with a password, boot_issue


[http://s306.photobucket.com/albums/nn244/FrankenCub/Nature%20pics/?action=view&current=MOV02543-1.mp4](http://s306.photobucket.com/albums/nn244/FrankenCub/Nature%20pics/?action=view&current=MOV02543-1.mp4)

---

### Post by FrankenCub on 2010-12-29
I found the problem with Unetbootin, the 7zip that is needed for Linux is not pointed out well and in their help forum someone asked about it not finding 7z which went unanswered. I found the correct version. For those who need it in the future is here....

 [http://www.linuxappfinder.com/package/p7zip-full](http://www.linuxappfinder.com/package/p7zip-full)

I am finally having success with Unetbootin but it looks like this notebook is not compatible with Ubuntu 10.10 or 10.04 so I'm now downloading 9.04 to give that a try. Apparently the graphics set-up is giving problems. If worse comes, I will load it back to the original 8.04 or whatever it was.

---

### Post by Bucky Ball on 2010-12-29
Pity. 9.04 is out of support this coming April.

You can edit the grub line at boot by hitting 'e' at the menu list. You might try adding this to the end of the kernel line, after 'quiet splash'

```
acpi=off
```

---

### Post by FrankenCub on 2010-12-30
Yeah that kinda sucks but I guess it's the best he's gonna get with this notebook. It booted and is setting up now, close call too, it almost had several 357 caliber holes in it lol.

At least he'll have his computer back now.

Thanks for all the help guys ):P

---

