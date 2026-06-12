---
title: "Ubuntu 10.10 Won't Suspend or Hibernate"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by MandoJM on 2011-01-30
Hello, I have an Asus U43F With Ubuntu 10.10 Installed and Everytime I  Try To Suspend Or Hibernate The Screen Turns Of And Quickly Gets Back  On.. I Read it was something about the USB 3.0 But I Don Know How to  solve it. Can Anybody Help Me? I Tried Doing The Option of When I Close It That It Does Suspend But It Doesn't Work...

---

### Post by MandoJM on 2011-01-30
Anybody???

---

### Post by Habeouscorpus on 2011-01-30
Umm.... acpitool has a hibernation feature. 

acpitool -s (for suspend)

acpitool -S (for hibernation. note the capital.)

You can alias the commands to make things easier.

---

### Post by MandoJM on 2011-01-30
i dont understand this... what is acpitool? how do i get it?

---

### Post by diablo75 on 2011-01-30
A spec sheet I found for that laptop shows it to come with 4 GB of RAM.  It's possible that your swap partition isn't large enough to store the entire 4 GB of info upon hibernation, but this is just a novice guess; I don't know much about how suspend/hibernate are supposed to work and what common issues it might have.  But this is just a thought.

If you go to a terminal and type in (to get to terminal click Applications> Accessories >Terminal):

```
sudo fdisk -l
```

That will show you partitions and their sizes, including the swap.  Copy and paste the output of that command back here; I'm just curious to see if the swap is large enough.

---

### Post by MandoJM on 2011-01-30
This Is What It Says:

```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006400d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       76296   612842496   83  Linux
/dev/sda2           76296       77826    12286977    5  Extended
/dev/sda5           76296       77826    12286976   82  Linux swap / Solaris
```

---

### Post by Habeouscorpus on 2011-01-30
>  what is acpitool? how do i get it?

From the manpage: 

>  acpitool is  a  Linux  ACPI  client.  It  simply  reads  /proc/acpi  or
       /sys/class  entries  and  presents  the output in a meaningfull, human-
       readable format.

       It provides a.o. information on battery status,  AC  adapter  presence,
       thermal  reading,  etc.  This command is most useful on laptops with an
       ACPI compliant BIOS and a Linux kernel, preferably from the 2.6 series,
       with ACPI enabled.

       Acpitool also allows the machine to be put into standby, if your laptop
       supports it.

       If your laptop is a Toshiba , it allows you to set  the  LCD  brighness
       level and toggle the fan on/off.

       If  you  have an Asus laptop, it can also set the LCD brightness level,
       switch the LCD panel on or off, and control the mail led  and  wireless
       led.

       If  you  have  an  IBM  Thinkpad  laptop, it can once again set the LCD
       brightness level, and also eject the ultrabay device. 

To get it, just type ```
 sudo apt-get install acpitool 
```

---

### Post by MandoJM on 2011-01-30
i tried using acpitool but it says: 
```
 Function Do_Suspend : could not open file : /sys/power/state. 
 You must have write access to /sys/power/state to suspend your computer.

```

---

### Post by Habeouscorpus on 2011-01-30
Use sudo. (Sorry, forgot about that.)

---

### Post by MandoJM on 2011-01-30
I Tried to Do It and It Didn Work It Game Me Some Message that said something about Device usb3 failed to freeze async: error -2

---

### Post by MandoJM on 2011-01-30
Has Anybody ever seen this??

---

### Post by MandoJM on 2011-01-31
bump........

---

### Post by Mr.Carramba on 2011-02-15
I had the same problem with suspend, issuing the command only "rebooted" me back. 
the acpitool did not helped either or other solution using gnomeconf.

What I did was to enable pre-release repositories in source manager and upgrade to 2.6.35-26-generic kernel. This solved my problem and I can suspend successfully now.

---

### Post by Vitalius on 2011-02-15
I have the similar issue. In /var/log/kern.log I see the following error messages:

```
kernel: [108133.856310] parport_pc 00:0b: disable failed
kernel: [108133.856320] legacy_suspend(): pnp_bus_suspend+0x0/0x70 returns -5
kernel: [108133.856326] PM: Device 00:0b failed to freeze: error -5

```

I'll try to upgrade tomorrow and see if it solves the problem

---

### Post by netgrazer on 2011-03-10
Same thing here: failed to freeze.

Any luck yet?

Oh well, 11.04 will probably have that fixed... [-o<

---

### Post by gufide on 2011-03-23
I got an asus too and suspend/hibernate don't work at all. I made a little script here for an asus G60Jx (my computer)

 **[COLOR=Red]**Be careful!**[/COLOR]** It install a script to get keyboard light work too. If you didn't have it one, just delete the section keyboard light


**IF IT DIDN'T WORK**
go here:[http://ubuntuforums.org/showthread.php?p=9261807](http://ubuntuforums.org/showthread.php?p=9261807)


else

download here:
[ATTACH]186912[/ATTACH]

---

