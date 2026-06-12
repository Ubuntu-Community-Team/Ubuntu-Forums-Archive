---
title: "NEWBIE needs help desperately"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by mrfotheringham on 2009-06-10
[B]HELP!!!

[/B]I've been using ubuntu for 3 days and very much enjoying it - i think. Obviously v different from XP more nuts and bolts to fiddle with everything is fine but i can't get my ip1900 to work or Nvidia geforce 4mmx agp8x and i'd like to remove my xp installation or atleast make t very small. I've been round and round nvidia, canon forums etc can't seem to get my head around it - i'm a bit frazzled!

mrfotheringham

---

### Post by Therion on 2009-06-10
Mmmmkay, so lets see if I've got this list of issues down straight...  Your printer, a Canon Pixma ip1900, is not working properly.  Your video card, an nVidia gForce MX440 is not working properly and lastly you want to remove Windows XP from your system entirely or else shrink the Windows XP partition as much as possible.

Is that pretty much the story then?

---

### Post by glennric on 2009-06-10
Have you tried going to System->Administration->Hardware Drivers and seeing if it detects your nvidia card?  If so it will recommend a driver to install and install it for you.

---

### Post by sandyd on 2009-06-10
> **mrfotheringham said:**
> [B]HELP!!!

[/B]I've been using ubuntu for 3 days and very much enjoying it - i think. Obviously v different from XP more nuts and bolts to fiddle with everything is fine but i can't get my ip1900 to work or Nvidia geforce 4mmx agp8x and i'd like to remove my xp installation or atleast make t very small. I've been round and round nvidia, canon forums etc can't seem to get my head around it - i'm a bit frazzled!

mrfotheringham
1. [http://ubuntuforums.org/showthread.php?t=980735](http://ubuntuforums.org/showthread.php?t=980735)
read post #6

2. I don't believe its supported any more. so...
can you type this in the terminal and post the output please? (i have to do some edits for ya)
```

cat /etc/X11/xorg.conf

```

3. resizing can be done with a program called gparted.
Type this in terminal to install and run it.
```

sudo apt-get install gparted&&sudo gparted

```

The terminal can be accessed through Menu -> Accessories -> Terminal.

Just copy and paste the code.

---

### Post by mrfotheringham on 2009-06-10
Er yeah pretty much - sounds a bit lame of course but hey gotta start somewhere

---

### Post by mrfotheringham on 2009-06-10
> **carlee said:**
> 1. [http://ubuntuforums.org/showthread.php?t=980735](http://ubuntuforums.org/showthread.php?t=980735)
read post #6

2. I don't believe its supported any more. so...
can you type this in the terminal and post the output please? (i have to do some edits for ya)
```

cat /etc/X11/xorg.conf

```

3. resizing can be done with a program called gparted.
Type this in terminal to install and run it.
```

sudo apt-get install gparted&&sudo gparted

```

The terminal can be accessed through Menu -> Accessories -> Terminal.

Just copy and paste the code.
Thanks heres it is

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---

### Post by mrfotheringham on 2009-06-10
> **mrfotheringham said:**
> Thanks heres it is

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
Hope this is correct 

artintudor@ubuntu:~$ sudo apt-get install gparted&&sudo gparted
[sudo] password for martintudor: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gparted is already the newest version.
The following packages were automatically installed and are no longer required:
  nvidia-180-libvdpau
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
======================
libparted : 1.8.8
======================
martintudor@ubuntu:~$ 


In GParted the partition for FAT32 was smaller if that makes any sense

---

### Post by Sarai the Geek on 2009-06-10
> **carlee said:**
> 
sudo apt-get install gparted&&sudo gparted
[/code]

That one's a no-go: gparted won't let you edit partitions on a hard drive that's currently mounted. The easier way would be to download an .iso from [here]("http://gparted.sourceforge.net/livecd.php"), burn it to a cd just like you did when you made the live cd for your install, then boot into that and use it to edit your partitons. It works exactly the same as the non-live version that's in the repos.

Also, just to be absolutely sure, you did not install Ubuntu using Wubi, did you? It's a different process if you did...

---

### Post by mrfotheringham on 2009-06-11
> **Sarai the Geek said:**
> That one's a no-go: gparted won't let you edit partitions on a hard drive that's currently mounted. The easier way would be to download an .iso from [here]("http://gparted.sourceforge.net/livecd.php"), burn it to a cd just like you did when you made the live cd for your install, then boot into that and use it to edit your partitons. It works exactly the same as the non-live version that's in the repos.

Also, just to be absolutely sure, you did not install Ubuntu using Wubi, did you? It's a different process if you did...
**YUP - **Wubi it was have i wrecked it???

---

### Post by Sarai the Geek on 2009-06-11
> **mrfotheringham said:**
> **YUP - **Wubi it was have i wrecked it???

I don't think you *can* bork a wubi install by playing with partitions (someone correct me here if I'm wrong) because the install doesn't live in its own partition, it's inside a virtual disk on your windows partition.

You can use the lvpm tool to move a wubi install to a dedicated partition, there's an easy to follow screen-shot based how-to located at their sourceforge page: [Lubi, LVPM, UNetBootin]("http://lubi.sourceforge.net/lvpm.html"). 

Cheers-

---

### Post by mrfotheringham on 2009-06-11
Thanks offline for ages wil try and get back liwm

---

### Post by mrfotheringham on 2009-06-11
Can ant one help with the ip1900 prob - seems to have been well discusses on the pages but who knows?

---

### Post by mrfotheringham on 2009-06-11
The ip1099 prob seems to be perenial any news? Much appreciated

---

### Post by master_kernel on 2009-06-11
You'll need the **1800** series driver for the 1900 to work. You can find it here: [http://www.openprinting.org/show_printer.cgi?recnum=Canon-ip1800](http://www.openprinting.org/show_printer.cgi?recnum=Canon-ip1800)

You want either of these:
32-bit computer: [http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/main/binary-i386/openprinting-gutenprint_5.2.3-1lsb3.2_i386.deb](http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/main/binary-i386/openprinting-gutenprint_5.2.3-1lsb3.2_i386.deb)
64-bit computer: [http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/main/binary-amd64/openprinting-gutenprint_5.2.3-1lsb3.2_amd64.deb](http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/main/binary-amd64/openprinting-gutenprint_5.2.3-1lsb3.2_amd64.deb)

Then go to System > Administration > Printing and set up the printer with the IP1800 driver.

---

### Post by sandyd on 2009-06-15
> **mrfotheringham said:**
> Thanks heres it is

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Lets replace it with
```

Section "Device"
Identifier "Configured Video Device"
        Driver         "nv"
        VendorName     "NVIDIA Corporation"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection
 
Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

Section "ServerFlags"
        Option  "DontZap"       "False"
EndSection

Section "Module"
 Load           "glx"     
EndSection  

```
you can replace it by 
```

sudo gedit /etc/X11/xorg.conf
```

remove the "Modules" section if your computer fries shortly after replacing the code.

---

