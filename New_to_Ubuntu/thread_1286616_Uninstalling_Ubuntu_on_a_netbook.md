---
title: "Uninstalling Ubuntu on a netbook"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by itsvan on 2009-10-09
Hello im trying to remove the Ubuntu Netbook remix partition of my ASUS 900, considering it doesnt run very well,it lags to much,,how can i delete the partition and return the space back to wndows,,,being a netbook i cant use any windows repair cds so what do i do? or fix ubuntu to make it run fine

---

### Post by Dangger on 2009-10-09
> **itsvan said:**
> Hello im trying to remove the Ubuntu Netbook remix partition of my ASUS 900, considering it doesnt run very well,it lags to much,,how can i delete the partition and return the space back to wndows,,,being a netbook i cant use any windows repair cds so what do i do? or fix ubuntu to make it run fine

First you have to restore the master boot record to eliminate grub and return to a "normal" netbook state. Later on, defrag your windows partition. 

Once you do this, simply run gparted from the livecd and eliminate the space that Ubuntu has and allocate it to your windows partition.

EDIT: you might want to backup everything before using gparted. It's safe but it's not perfect.

---

### Post by itsvan on 2009-10-09
IS there a way you can explain it in a bit more detail because im rather new at this stuff...also I heard that with the WINDOWS repair cd you can restore the partition, is there any way maybe i can get that into a jumpdrive and boot it off like that?

---

### Post by Kegusa on 2009-10-09
> IS there a way you can explain it in a bit more detail because im rather new at this stuff...also I heard that with the WINDOWS repair cd you can restore the partition, is there any way maybe i can get that into a jumpdrive and boot it off like that?

No need to go to those extreme lengths. Instead of a Live CD with ubuntu you can make a USB live edition. You can find it at System - Administration - USB Startup Disk Creator

Then boot up the netbook with it and use gparted like previously described. Also with various netbooks there are ways to restore the machine to the original state, just take a look in the manual that came with it (or online somewhere)


It's possible to make the windows bootloader override the GRUB one via windows commandline. Think the commands were MBR or something, just take a look around in windows command line.

---

### Post by itsvan on 2009-10-09
OK let me rephrase what exactly i want to do..I HAVE TWO PARTITIONS XP and UBUNTU,,What happened is. i installed ubuntu for my netbook**(ASUS eee 900HD...with a celeron processor 900mhz and 1 gig of RAM)** but the performance was to slow. problem is i gave it to much partition space. so now i want to give more to my main OS (XP) and have ubuntu as a backup, for the inevitable day windows crashes on me. and i know it will lol.

Now.. how can i reinstall ubuntu to reset the partition space  i want for it,,or on the other hand is there any other distro that whould run better for my netbook...

---

### Post by mike555 on 2009-10-09
There must be something wrong if Ubuntu doesn't run well on that machine ........ if you let us know the problems your having maybe we can help ....... there are lighter distro's , but they are harder to figure out (like Puppy Linux).

---

### Post by itsvan on 2009-10-09
The problem is that it lags,,i was surprised as well,, but it boots into the main menu and it lags the mouse cursor lags like a sec or two before moving,,once i open a screen usually mozilla it runs fine but the main desktop with all the menus and stuff runs slow...is something not activated a driver or someting? i checked the hardware drivers tab, and there was nothing i should enable...what can i do?

---

### Post by cholericfun on 2009-10-09
disabled compiz and all that jazz?
try some netbook-specific ubuntu maybe? 

other than that, how did you install ubuntu?
if via CD, put the CD in and wipe the ubuntu partition with gparted.
afterwards fix windows MBR... not sure
without cd i'd be at loss, but there has to be a way

---

### Post by itsvan on 2009-10-09
These are the specs of my netbook

ASUS eee 900HD...with a celeron processor 900mhz and 1 gig of RAM


the requirements say it needs at least an intel ATOM processor and i dont have that,,so im thinking that might be the problem,,thing is how is WINDOWS XP running fine over UBUNTU, i just dont get it...can i install the normal ubuntu edition not the netbook remix?? or will the problem only escalate?

---

### Post by Dangger on 2009-10-10
> **itsvan said:**
> IS there a way you can explain it in a bit more detail because im rather new at this stuff...also I heard that with the WINDOWS repair cd you can restore the partition, is there any way maybe i can get that into a jumpdrive and boot it off like that?

**To remove Ubuntu **

First, backup your data if you want to make changes in the Master Boot Record (MBR) or the partitions. 

Then, follow the instructions [here]("http://www.sysint.no/nedlasting/mbrfix.htm") to change your MBR.

Once you are able to boot directly into windows as when you originally had the computer, defragment your disk inside Windows (My PC, right click on drive, properties and find the defrag option).

After that, download [Gparted]("http://gparted.sourceforge.net/livecd.php") and run the LiveCD. Eliminate Ubuntu's partition and then simply allocate the free space into the Windows Partition. 

You should be able to boot into windows with no problems after that and have all your space. 

**Not to remove Ubuntu or linux**

You can try ligther distros, I suggest puppy linux or even xubuntu. If Ubuntu is running poorly it is probably because something is not well configured, it takes time to get your machine to work exactly how you want it to work, I also suggest not giving up on Ubuntu because it is worth it.

---

### Post by itsvan on 2009-10-10
ok thanks to all for the support..btw how can i install a live cd unto a jumpdrive to install any of these distros?

---

### Post by itsvan on 2009-10-10
on another note,,,,,//what problems could be causing ubuntu remix to be laggin on my netbook?? and what can ido about it?

---

### Post by bruce2000 on 2009-10-10
Compiz can be a major source of lag, have you tried cholericfun's suggestion and turned it off?

Go get live cd's onto a jump drive you can use unetbootin:

[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

---

### Post by itsvan on 2009-10-10
Cool so i got unetbootin how do i put a live ubuntu image on a usb so i can boot from it and install it on my netbook?

---

### Post by blackened on 2009-10-10
Using unetbootin is not really necessary if you already have a usable install of Ubuntu. Go to System -> Administration -> USB Startup Disk Creator and use that to load a current ISO onto your flash drive. From there you can boot into live mode and alter the partition table. You'll still be faced with fixing the master boot record though.

---

### Post by itsvan on 2009-10-10
well i dont have ubuntu im running windows,,and im trying to install it on my netbook..through windows put in a image ofthe live disc on my jumprdrive,,how to use unetootin?

---

### Post by Dangger on 2009-10-11
> **itsvan said:**
> well i dont have ubuntu im running windows,,and im trying to install it on my netbook..through windows put in a image ofthe live disc on my jumprdrive,,how to use unetootin?

[Here]("http://sourceforge.net/apps/trac/unetbootin/wiki/guide") are the instructions to create a livecd in your usb, try looking for info on the website, they have all the documentation there.

---

