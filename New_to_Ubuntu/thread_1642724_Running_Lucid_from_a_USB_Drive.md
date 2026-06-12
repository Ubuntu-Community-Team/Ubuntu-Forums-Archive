---
title: "Running Lucid from a USB Drive"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by tonycm1 on 2010-12-10
I use a work laptop running XP and periodically run the Ubuntu Live CD to get around most of the restrictions imposed on my work image.

I know that you can create a Live USB drive (using unetbootin) and have done this a few times, but I wanted to know if there's a way to INSTALL Lucid on a 16GB USB drive so that I can boot from it and whatever changes I make stick... instead of the "live" version.

I've tried searching about but can't seem to find a suitable guide... maybe one of you guys can point me in the right direction :)

Thanks!

---

### Post by Rex Bouwense on 2010-12-10
You can do that.  Look here:  [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
The part which might be of interest is under alternative methods.  Hope that helps.

---

### Post by beew on 2010-12-10
Yes indeed. You just install Lucid in the usb like you would in the internal hard drive.

so boot from a live usb (sdb probably), and then plug in the usb you want to install into (probably sdc) Now in step 4 of the installation, choose "install manually" and make sure you install in the correct drive or it will wipe out all your data. in my example it would be sdc. You can then partition the usb drive. Since it is only 16 G I don't think you would need a home partition. So you need maybe 15G formatted in ext3 or ext4 for your / partition (mount point set as /) and another 1G as swap (will come back to this later)

Now just proceed and in the last (or second last?) step, when you are asked to choose where to install the bootloader, make sure you choose "advanced" and install the bootloader in the usb drive (sdc in my example)** Make sure you do this right or your PC may not be bootable afterwards, **some people recommend removing your internal hdd first but if you are careful you shouldn't need to.

Now just sit back or surf the web and if you use a live usb to install it may take about 15 minutes.

Now installing in a usb drive has one disadvantage, aside from the storage limitation it is slow, much slower than a live usb because a live usb runs in ram while a full installation does not. So I prefer to create portable systems by installing into an external hdd instead of a flash drive. 

You can speed it up a little by forcing it to use more ram if the computer you plug it in can afford that.  To do that boot into the usb installation, open a terminal and type 
```
sudo gedit /etc/sysctl.conf 
``` and add the line
> vm.swappiness=10
Swappiness is a parameter that determines how readily the system would use swap (therefore using less ram) Its value is between 0 and 100. The lower the value means the system would use more ram before dropping down to swap. The default is 60.

Now this will only take effect when you reboot. If you don't want to reboot in the mean time, you should run```
 sudo sysctl vm.swappiness=10
``` This would take effect immediately but the value will change back to 60 on reboot if you do not add the line in sysctl.conf. You can use this to experiment with different swappiness value before you change it permanently by editing sysctl.conf

---

### Post by beew on 2010-12-10
Oh btw, a live usb can keep changes if it is created with persistence. It is just that Unetbootin doesn't support persistence. In Windows you can use this tool to create a Ubuntu live usb with persistence.
[http://old.linuxliveusb.com/](http://old.linuxliveusb.com/) But using this method you can't have more than 4 G of persistence because the drive is formatted in FAT which only can handle up to 4 G. Also a live usb with persistence doesn't support system level update (so say you can't install propietary graphic driver) But the method I described above installs a full Ubuntu system in your pendrive, as I said the only limitations are storage size and speed.

---

