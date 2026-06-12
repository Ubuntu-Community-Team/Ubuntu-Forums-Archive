---
title: "How do I get a higher resolution than 800X600?"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by shawndh on 2009-03-19
I just installed Ubuntu 8.10 and it's working fine so far. But the highest resolution available in the system is 800X600. How can I get higher resolution? I can't tell what kind of video card is in this machine, it was there when we got it (old Compaq Evo desktop). And the monitor is some no name CRT I got from CompUSA about 10 years ago.

---

### Post by Paqman on 2009-03-19
If you go to System > Admin > Hardware drivers, are there any drivers waiting to be activated? If so, do it and reboot. You should get higher resolutions.

---

### Post by shawndh on 2009-03-19
> **Paqman said:**
> If you go to System > Admin > Hardware drivers, are there any drivers waiting to be activated? If so, do it and reboot. You should get higher resolutions.

Yea, I've tried looking there. No drivers at all.

---

### Post by Paqman on 2009-03-19
If you install hardinfo it should tell you what kind of graphics card you have.

---

### Post by shawndh on 2009-03-20
I did a sudo lspci and I saw "01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)" 
So I guess it's an old NVidia card. I just don't know how to find the right driver for it. I looked for some program called EnvyNG, but I couldn't find it in the Add/Remove Prog section. And I opened a terminal and typed sudo nvidia-settings, but I get a warning pop up that says the following:

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

I don't know what I'm doing at this point.

---

### Post by pbpersson on 2009-03-20
Go to System-->Administration--->Synaptic Package Manager and look for Envy there.  Sometimes it is better for searching for packages

---

### Post by shawndh on 2009-03-20
> **pbpersson said:**
> Go to System-->Administration--->Synaptic Package Manager and look for Envy there.  Sometimes it is better for searching for packages

I did some searching and I found out that my card is not supported. So off to Microcenter I go.

---

### Post by coolbrook on 2009-03-20
Are you positive?  I see Linux drivers (32 and 64 bit) for Legacy "Vanta Series"

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Before that, consider

```
sudo apt-get install nvidia-glx-legacy
sudo nvidia-glx-config enable
```

Try restarting and see if there's a difference.

---

### Post by shawndh on 2009-03-20
> **coolbrook said:**
> Are you positive?  I see Linux drivers (32 and 64 bit) for Legacy "Vanta Series"

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Before that, consider

```
sudo apt-get install nvidia-glx-legacy
sudo nvidia-glx-config enable
```

That just came out on March 9th, so I guess that's why I couldn't find any posts on it. Thanx for the link. I've downloaded the driver but I'm still trying to figure out how to install it. When I type the command:  sh NVIDIA-Linux-x86-71.86.09-pkg1.run
I get:
sh: Can't open NVIDIA-Linux-x86-71.86.09-pkg1.run

---

### Post by coolbrook on 2009-03-20
If adding sudo to the beginning of your line doesn't work then 

Try this

[https://help.ubuntu.com/8.10/add-applications/C/install-file.html#runpackages](https://help.ubuntu.com/8.10/add-applications/C/install-file.html#runpackages)

---

### Post by bumanie on 2009-03-20
If you have downloaded it to your desktop you need to change the directory to desktop prior to executing the .run command. Open terminal > cd ~/DesktopThen execute the .run with root privileges ie add sudo in front of the command. However from my memory (which isn't always perfect) I think nvidia .run needs to be run from console mode with gdm stopped. 

1. Hit Ctrl + Alt + F1 and got to the tty login screen.
2. Log in and type > sudo /etc/init.d/gdm stop  this will stop gdm and x-server
3.>  cd ~/Desktop Or wherever you have the file stored
4. Type > sudo sh NVIDIA-Linux-x86-71.86.09-pkg1.run and ran through the installer.
5. > sudo /etc/init.d/gdm start to restart the gdm and x-server.
6. > sudo shutdown -r now this will reboot your system and hopefully the card will work. 

Alternatively you could try booting into safe mode and choosing xfix from the menu and see if configures things for you.

Hope this helps, it's a long time since I needed to install a GPU this way, so I hope I have recalled the steps correctly. You could google an answer to make sure.

---

### Post by coolbrook on 2009-03-20
> **bumanie said:**
> I think nvidia .run needs to be run from console mode with gdm stopped. 

Correct.

---

### Post by shawndh on 2009-03-20
> **bumanie said:**
> If you have downloaded it to your desktop you need to change the directory to desktop prior to executing the .run command. Open terminal Then execute the .run with root privileges ie add sudo in front of the command. However from my memory (which isn't always perfect) I think nvidia .run needs to be run from console mode with gdm stopped. 

1. Hit Ctrl + Alt + F1 and got to the tty login screen.
2. Log in and type   this will stop gdm and x-server
3. Or wherever you have the file stored
4. Type  and ran through the installer.
5.  to restart the gdm and x-server.
6.  this will reboot your system and hopefully the card will work. 

Alternatively you could try booting into safe mode and choosing xfix from the menu and see if configures things for you.

Hope this helps, it's a long time since I needed to install a GPU this way, so I hope I have recalled the steps correctly. You could google an answer to make sure.

I did everything you said and the install process process ran but nothing seems to have changed. It tried to build a Kernal or something but it said the install was sucessful. thanx for all your help. Really. But I think I'm going to use this as an excuse to buy a new video card.

---

### Post by shawndh on 2009-03-20
I'm back at it again. I'm just curious as to when I go to System/Admin/Hardward Drivers, the NVIDIA driver dosen't show up. But when I go through the instructions to stop the gdm and install, it says the driver is already present. Do I have to activate this driver or associate it with the device?

---

### Post by shawndh on 2009-03-21
I just wanted to follow up and let you know that I solved my resolution problem. I had to add the HorizSync & VertRefresh manually because of incorrect monitor auto-detection. I used the instructions from post #3

[http://ubuntuforums.org/showthread.php?t=1002460&highlight=higher+resolution](http://ubuntuforums.org/showthread.php?t=1002460&highlight=higher+resolution)

---

### Post by manolomanolo on 2010-07-11
Hi to all.

I upgraded from 9.10 to 10.04 and my video card is not working smoothly

```
VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)

```

I removed the noveau drivers and installed those
[http://www.nvidia.com/object/linux_display_ia32_71.86.13.html]("http://www.nvidia.com/object/linux_display_ia32_71.86.13.html")

less /etc/X11/xorg.conf
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

Any suggestion, please?
Thanks.

---

### Post by techunit on 2010-07-11
How old is this computer again? it could be that it is just the highest possible screen resolution... Also how are you connecting your computer to the monitor? if you are using a vga cable this why your screen resolution is so low. VGA can only transfer 800x600 and XVGA can transfer 1024x800. So I am guessing that your graphics card only supports VGA and thus can't broadcast higher. This is why many laptops could achieve higher screen resolutions than there monitors could support back in the old days (15 years ago) the screen was actually hard-wired to the graphics card.

---

### Post by manolomanolo on 2010-07-11
techunit, thanks for yor reply.
I am not sure it is a cable issue, taking in account that everything worked fine before upgrading. My computer is quite old: Pentium III 500 MHz

---

### Post by techunit on 2010-07-11
> **manolomanolo said:**
> techunit, thanks for yor reply.
I am not sure it is a cable issue, taking in account that everything worked fine before upgrading. My computer is quite old: Pentium III 500 MHz
yikes thats pretty old to be running even ubuntu on, but I suppose that 8.10 will work. 

Alright can you tell me the color of the cable connecting your computer to the monitor?

How are you connected to the Internet so I can help you install drivers as well.

Um I would recommend that you try 8.04 because it is still supported or you try xubuntu 8.04 (xubuntu is designed for lower powered systems) if you have performance problems.

---

### Post by techunit on 2010-07-11
> **techunit said:**
> yikes thats pretty old to be running even ubuntu on, but I suppose that 8.10 will work. 

Alright can you tell me the color of the cable connecting your computer to the monitor?

How are you connected to the Internet so I can help you install drivers as well.

Um I would recommend that you try 8.04 because it is still supported or you try xubuntu 8.04 (xubuntu is designed for lower powered systems) if you have performance problems.
  does the cable plug into a port like this? [IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/9/92/SVGA_port.jpg/250px-SVGA_port.jpg[/IMG]

---

### Post by techunit on 2010-07-11
Alright looks like its an error with xorg.config... this code my fix the problem but you can never be sure 

```
xrandr --output VGA --mode 1024x768
```


It appears to have been fixed in the latter versions of ubuntu. So I would like to know what your system specs are to see if xubuntu 9.04 will work?

Xubuntu 9.04 should work on your computer if Ubuntu 8.10 works of your computer...

[http://cdimage.ubuntu.com/xubuntu/releases/9.04/release/](http://cdimage.ubuntu.com/xubuntu/releases/9.04/release/)

Burn it to a disk and boot from it and see if the screen resolution is better. Also 9.04 is still supported..

---

### Post by manolomanolo on 2010-07-11
Yes, it looks like that.
But I can do switch from 800x600 to higher resolutions!
the problem is that playing videos on youtube is slow and scratchy

---

### Post by techunit on 2010-07-11
Ok that was hard to understand could you clarify? Were you able to increase the resolution from 800x600 to a higher resolution?

---

### Post by manolomanolo on 2010-07-11
I have no problems with resolution. My problem is I cannot see clearly videos on youtube.

---

### Post by techunit on 2010-07-11
Ok well that is a performance issue... and that is because your trying to run ubuntu on  a system that shouldn't be able to run it in the first place. 

Open up System Monitor and tell me what the cpu load and memory usage are.

if you don't get better performance you could install Xubuntu 8.04 which will run ok on your system.

[http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/](http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/)

This should work...

---

