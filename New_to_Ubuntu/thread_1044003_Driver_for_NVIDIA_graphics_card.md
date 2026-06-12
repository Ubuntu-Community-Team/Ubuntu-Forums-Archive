---
title: "Driver for NVIDIA graphics card"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by ronelc on 2009-01-19
Hi everyone!

I'm new in Linux as well as here in the forum. Can anyone please help me where to get driver for NVIDIA GeForce 9800 GT. I have already tried the driver version 177 from the repository but to no avail. Also I have downloaded the driver from the nvidia site, disable the x server but I am getting an error regarding the precompiled kernel. 

Anyone's help would be very much appreciated.

Thanks in advance...

---

### Post by nhasian on 2009-01-19
to try to get your video adaptor working go to System &#8594; Administration &#8594; Software Sources click on the Updates tab, then check the box for Unsupported updates (intrepid-backports). after you've enabled the backports update your ubuntu software from a terminal with the commands:

sudo apt-get update
sudo apt-get upgrade

you may need to reboot. after that go to System->Administration->Hardware Drivers and enable any restricted drivers you have available.

---

### Post by hyper_ch on 2009-01-19
(1) download the according driver

[ftp://download.nvidia.com/XFree86/Linux-x86_64/180.18/NVIDIA-Linux-x86_64-180.18-pkg2.run](ftp://download.nvidia.com/XFree86/Linux-x86_64/180.18/NVIDIA-Linux-x86_64-180.18-pkg2.run) (64bit)
[ftp://download.nvidia.com/XFree86/Linux-x86/180.18/NVIDIA-Linux-x86-180.18-pkg1.run](ftp://download.nvidia.com/XFree86/Linux-x86/180.18/NVIDIA-Linux-x86-180.18-pkg1.run) (32bit)

and make them executable

(2) boot into the terminal (or logout, then press Alt-F3)

(3) then remove the current nvidia drivers installed
```

sudo apt-get remove --purge nvidia/*

```

--> it it try to remove things that are not nvidia related, post the output here of what it wants to remove

(4) install the new drivers
```

sudo ./NV.......

```

---

### Post by ronelc on 2009-01-19
Thanks for the reply.

[SIZE="2"]I've tried your suggestion but I still get the same driver. The version 177 driver.


[I]Re: Driver for NVIDIA graphics card
to try to get your video adaptor working go to System &#8594; Administration &#8594; Software Sources click on the Updates tab, then check the box for Unsupported updates (intrepid-backports). after you've enabled the backports update your ubuntu software from a terminal with the commands:

sudo apt-get update
sudo apt-get upgrade

you may need to reboot. after that go to System->Administration->Hardware Drivers and enable any restricted drivers you have available.
__________________
If your issue is resolved: Thread Tools>Mark as solved
Thank those who help you: Click on the medal icon underneath posts [/I][/SIZE]

---

### Post by Noblacktie on 2009-01-19
nVidia 180.11 drivers are in the main repos.

Get them through Synaptic.

System > Admin > Synaptic (not sure of the name, I'm not running Ubuntu)

Then search for 'nvidia'.

You'll see 173., 177., and 180.11 listed. Find the one that says for Geforce 6 and newer.

Synaptic will uninstall your 177. and replace them with 180.11.

---

### Post by ronelc on 2009-01-19
How do I know its already working?

[SIZE="1"][I]nVidia 180.11 drivers are in the main repos.

Get them through Synaptic.

System > Admin > Synaptic (not sure of the name, I'm not running Ubuntu)

Then search for 'nvidia'.

You'll see 173., 177., and 180.11 listed. Find the one that says for Geforce 6 and newer.

Synaptic will uninstall your 177. and replace them with 180.11.
__________________
The Last Car on Earth [/I][/SIZE]

---

### Post by Leo Dragonheart on 2009-01-19
This is what worked for me. Maybe it will help you also...I got this info from someone else and it worked for me...


Nvidia Fixes:

I've had the exact same problem with NVIDIA cards and the restricted driver. I searched for months to find an answer and I must tell you it was a painful runaround. The good news is I was able to fix it easily, simply by manually editing my xorg.conf file. In my case the problem was not with the NVIDIA driver at all. The problem was that my monitor was not correctly recognized by the X-server system. Once I identified my monitor specs in the xorg.conf file, everything worked perfectly. This is how I did it.

First you need to open your xorg.conf file in Gedit, like this:

Go to Main Menu>Accessories>Terminal...then cut and paste, or type in the (Bold Type)code below...

Code:

**sudo gedit /etc/X11/xorg.conf**

You'll have to enter your password to gain editing privileges.

Some say you should back up the file first, but I found gedit does this automaticaliy, and right now your original file isn't doing you much good anyway.

Next, you have to add a few lines to specific sections of your xorg.conf file. BUT DO NOT CHANGE ANYTHING ELSE!

In the Monitor section add the lines that appear in bold:
Code:

Section "Monitor"
    Identifier     "Configured Monitor"
[B]    HorizSync       31.0 - 65.0
    VertRefresh     51.0 - 90.0	[/B]
EndSection

Note that these are the specs that fit my particular monitor. They'll probably work for yours also - but if you want to you can replace the VertRefresh and HorizSync values with your monitor's actual data if you know what they are.

Next, in the Screen section add the lines that appear in bold, right before the EndSection line.

Code:

[B]    SubSection     "Display"
       Depth       24
        Modes      "1280x1024_60"
    EndSubSection[/B]

This set my monitor to my desired resolution which is 1280X1024. You can substitute the resolution data to suit your needs. Reboot your computer and you should have a high resolution display. Next, you should run the NVIDIA settings program to fine tune your system.

If this doesn't work, then you can boot in recovery mode and select the fix x-server option. This will give you a high resolution display but no special effects, etc.

I hope this helps.

---

### Post by ronelc on 2009-01-19
I tried it but when I changed my directory to /etc/x11 it says 'No such file or directory'. 

I hope you can bear with me because I'm really new in here. But i'm willing to try anything to solve this.


[SIZE="1"][I]This is what worked for me. Maybe it will help you also...I got this info from someone else and it worked for me...


Nvidia Fixes:

I've had the exact same problem with NVIDIA cards and the restricted driver. I searched for months to find an answer and I must tell you it was a painful runaround. The good news is I was able to fix it easily, simply by manually editing my xorg.conf file. In my case the problem was not with the NVIDIA driver at all. The problem was that my monitor was not correctly recognized by the X-server system. Once I identified my monitor specs in the xorg.conf file, everything worked perfectly. This is how I did it.

First you need to open your xorg.conf file in Gedit, like this:

Go to Main Menu>Accessories>Terminal...then cut and paste, or type in the (Bold Type)code below...

Code:

sudo gedit /etc/X11/xorg.conf

You'll have to enter your password to gain editing privileges.

Some say you should back up the file first, but I found gedit does this automaticaliy, and right now your original file isn't doing you much good anyway.

Next, you have to add a few lines to specific sections of your xorg.conf file. BUT DO NOT CHANGE ANYTHING ELSE!

In the Monitor section add the lines that appear in bold:
Code:

Section "Monitor"
Identifier "Configured Monitor"
HorizSync 31.0 - 65.0
VertRefresh 51.0 - 90.0
EndSection

Note that these are the specs that fit my particular monitor. They'll probably work for yours also - but if you want to you can replace the VertRefresh and HorizSync values with your monitor's actual data if you know what they are.

Next, in the Screen section add the lines that appear in bold, right before the EndSection line.

Code:

SubSection "Display"
Depth 24
Modes "1280x1024_60"
EndSubSection

This set my monitor to my desired resolution which is 1280X1024. You can substitute the resolution data to suit your needs. Reboot your computer and you should have a high resolution display. Next, you should run the NVIDIA settings program to fine tune your system.

If this doesn't work, then you can boot in recovery mode and select the fix x-server option. This will give you a high resolution display but no special effects, etc.

I hope this helps.[/I][/SIZE]

---

### Post by abyssius on 2009-01-19
> I tried it but when I changed my directory to /etc/x11 it says 'No such file or directory'.

Actually the directory path is /etc/X11. Note the capitalized 'X'. Linux is case-sensitive.

If you want to fing out if the driver is installed, right-click at an empty-space on your desktop (like in Windows). Select Change desktop Background. Click the Visual Effects tab. try to enable either Normal or Extra. If you can select either of these options, you've installed the driver. The commands in your post, will only be relevant if you have successfully installed the driver. Furthermore, the suggested xorg.conf edit addresses a problem with Ubuntu not properly recognizing your connected monitor. It has nothing to do with the nvidia driver specifically. The 'no recognition' problem would be encountered no matter what video card/driver you had installed.

---

### Post by ronelc on 2009-01-19
Thanks! I think the previously installed nvidia driver don't work because I still can't select any in the Visual Effects tab. Maybe I'll have to wait until the driver for my video card becomes available in the repository but i'm still willing to try any suggestions.

Actually the directory path is /etc/X11. Note the capitalized 'X'. Linux is case-sensitive.

[I][SIZE="1"]If you want to fing out if the driver is installed, right-click at an empty-space on your desktop (like in Windows). Select Change desktop Background. Click the Visual Effects tab. try to enable either Normal or Extra. If you can select either of these options, you've installed the driver. The commands in your post, will only be relevant if you have successfully installed the driver. Furthermore, the suggested xorg.conf edit addresses a problem with Ubuntu not properly recognizing your connected monitor. It has nothing to do with the nvidia driver specifically. The 'no recognition' problem would be encountered no matter what video card/driver you had installed.
__________________
...and so castles made of sand fall in the sea - eventually... Jimi Hendrix [/SIZE][/I]

---

### Post by toptorps on 2009-01-20
I had a problem after installing the nvidia driver..
Before installing, I was using the resolution, 1152x768..
I wanted to use Compiz, so i installed the nVidia driver which came as default when I clicked the hardware like in system->administration..
After installing, I m getting a max resolution of only 800x600..
The windows of different applications are not completely visible.. 
Can any1 tell me a method to solve it..

---

### Post by Leo Dragonheart on 2009-01-20
Yea TopTorps, Try my post earlier in this thread, should work for you...

---

### Post by richlowe101 on 2009-01-20
The best method I've found is to use Envy which can be found [[COLOR="Blue"]Here[/COLOR]]("http://albertomilone.com/nvidia_scripts1.html").
It automatically downloads and configures your NVIDIA and ATI graphics drivers. Quick fix if you're struggling.

---

