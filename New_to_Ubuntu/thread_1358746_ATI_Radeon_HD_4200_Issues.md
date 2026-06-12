---
title: "ATI Radeon HD 4200 Issues"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by ovid9 on 2009-12-18
Ok, I've done it now.   In attempting to install drivers for my ATI Radeon HD 4200 gpu on my [SIZE=1]GIGABYTE GA-MA785G-UD3H motherboard, I've now gotten Hardy to only boot in low graphics mode.  I'm farther behind than I was prior to attempting to use the GPU.  

So, I went here[ http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.1&lang=English]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.1&lang=English") and followed the instructions to install.

I rebooted, checked my hardware drivers, it wasn't enabled yet, so I enabled it, rebooted and ran into "low graphics mode" or choose my setup.  I tried to choose my setup, to no success.

Any suggestions?  I'd like to get the drivers installed, but heck, if I can't get them to work, how do I make them go away?

What do you helpful folks need to know?
[/SIZE]

---

### Post by ovid9 on 2009-12-18
Ok, well, I used EnvyNG to get my normal screen back.  BUT, I'd still like to know how to config my computer to use the ATI drivers for my GPU.   Since, currently I can't use compiz and any 3d game looks like utter and complete crap.

Any suggestions?

---

### Post by ovid9 on 2009-12-21
Still no luck actually "using" the drivers that are installed.   Any help?  I've poked around some more and it seems I did things correctly, but apparently I haven't

---

### Post by nishant.singh28 on 2009-12-21
I have an HD 4570 mobility Radeon. I downloaded the driver ati******.run from the ATI site and typed in Terminal:
sudo sh <path to driver>/ati*****.run
Then Reboot.

---

### Post by ovid9 on 2009-12-21
Thanks, I'll give that a shot.  Can't do any worse than I'm already doing!

---

### Post by adam814 on 2009-12-21
Enabling fglrx in the Hardware/Drivers wizard uses the version shipped with Ubuntu.  Since you're using Hardy I imagine the included version is from early 2008 before the HD 4200 was supported by the drivers.  If I recall from when I used Hardy fglrx at the time didn't support direct rendering (3D support) and compositing (Compiz) at the same time.  The newer drivers should.

You should be able to run the .run file from the AMD site to get it working though.  You might need to uninstall the xorg-driver-fglrx package(s) through Synaptic first just to be sure.

---

### Post by ovid9 on 2009-12-21
> You should be able to run the .run file from the AMD site to get it working though. You might need to uninstall the xorg-driver-fglrx package(s) through Synaptic first just to be sure.
 
I believe I did that, since it did say on the AMD site that you should have all the other drivers uninstalled. I'll double-check though. 
 
What might be causing it to not recognize the newer drivers on startup though?
 
edit:  Also, thanks for the info.  I really just need to get around to making /home its own partition and upgrade to 9.04 or 9.10 but I'm finally getting 8.04 mostly how I like it.  lol

---

### Post by adam814 on 2009-12-23
Maybe you're specifying the wrong driver in /etc/X11/xorg.conf?  Post the output from this:
> grep Driver /etc/X11/xorg.conf
If it's not fglrx it should be to use ATI binary drivers.  If it's ati or radeon or radeonhd it won't work as the ATI binaries overwrite parts of the mesa libraries i believe.

---

### Post by ovid9 on 2009-12-23
> **adam814 said:**
> Maybe you're specifying the wrong driver in /etc/X11/xorg.conf?  Post the output from this:

If it's not fglrx it should be to use ATI binary drivers.  If it's ati or radeon or radeonhd it won't work as the ATI binaries overwrite parts of the mesa libraries i believe.

Here it is!

>     
    Driver        "kbd"
    Driver        "mouse"
    Option        "VendorName"    "ATI Proprietary Driver"
    Driver        "vesa"


---

### Post by adam814 on 2009-12-23
Edit the file and change the line that reads Driver "vesa" to read Driver "fglrx"

That will use the ATI driver if you have it installed.

---

### Post by kronictokr on 2010-01-06
just finished this, i have an ati radeon hd 4200 mobile, ive tested this quite a few times to get it right. there is a big diference in graphics quality and color.

BACK UP ANY IMPORTANT INFO!!!!!!!!!!!!!

BACK UP ANY IMPORTANT INFO!!!!!!!!!!!!!

[COLOR="black"][COLOR="Green"]**Install the fglrx Driver from ATI Catalyst 9.12 For Ubuntu 9.10 Karmic**[/COLOR][/COLOR]


We have to create a folder to enable the instalation process
          location  filename
            VVVV       VVV
create /usr/share/ati "ati"

to do this, enter in a terminal the following command

sudo nautilus

then click "file system" from the left side of the window, then double click the file "usr" and the same with "share". once inside the "share folder, right click on a blank space, click create file, name it "ati".  

leave the nautilus window open while you do the next step

download the 64bit driver from this link
VVVVVVVV
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-12-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-12-x86.x86_64.run)

now copy the downloaded file, or drag it into the file you created , (/usr/share/ati  <location reminder )still open in your nautilus window.

when you have placed the "ati-driver-installer-9-12-x86.x86_64.run" file into /usr/share/ati , close your nautilus window, and type the next command into a terminal.

sudo sh /usr/share/ati/ati-driver-installer-9-12-x86.x86_64.run --buildpkg Ubuntu/karmic

this will take a couple minutes as it gathers the proper pakages for your ati gpu. it will create debs and a change log , that will install with the following method

sudo dpkg -i *

there will be missing dependancies, go to SYSTEM>>>SYNAPTICS , and select edit top left , scroll down to and click on fix broken pakages. the click on apply, and lastly click on reload.

now go back to your terminal (to ensure ALL neded pakages are installed, and correctly follow this process exactly)
so, like i was saying, in your terminal, enter the following commands

sudo dpkg -i *

sudo aticonfig --initial

sudo sh /usr/share/ati/ati-driver-installer-9-12-x86.x86_64.run --buildpkg Ubuntu/karmic


sudo dpkg -i *

sudo aticonfig --initial

sudo reboot

MAKE SURE TO COMPLETE ALL THE STEPS BEFORE YOU REBOOT!!

AFTER YOU REBOOT
vvvvvv
to confirm , in a terminal type

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4200
OpenGL version string: 3.2.9232

if you get errors, 
do this again, but i suggest you get it right the first time

sudo sh /usr/share/ati/ati-driver-installer-9-12-x86.x86_64.run --buildpkg Ubuntu/karmic

sudo dpkg -i *

sudo aticonfig --initial

sudo reboot



references
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_910_linux.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_910_linux.pdf)

---

### Post by kronictokr on 2010-01-06
im going to test this all one more time, i have already done it at least 3.
there are easier ways to do this, this is how to build a driver specific to your system.

---

### Post by frikker on 2010-02-07
Hey guys.  Installing Ubuntu 9.10 from scratch and selecting "Use ATI Proprietary Drivers" from the driver screen that pops up on first login worked fine for me.  I have the same motherboard as you - the Gigabyte MA785G-UD3H.

Any luck on dual output? HDMI output would be nice.

Blaine

---

### Post by kronictokr on 2010-02-23
[http://swiss.ubuntuforums.org/showthread.php?p=8873144#post8873144](http://swiss.ubuntuforums.org/showthread.php?p=8873144#post8873144)

---

### Post by kronictokr on 2010-02-23
hdmi works

sorry double post

---

### Post by lovswr on 2010-04-23
> **nishant.singh28 said:**
> I have an HD 4570 mobility Radeon. I downloaded the driver ati******.run from the ATI site and typed in Terminal:
sudo sh <path to driver>/ati*****.run
Then Reboot.

I have a HD4200 built into a msi 785GTM-E45 motherboard.  I tried to make the normal ubuntu supported ati driver work, but it failed.  Loaded lateset driver from amd's site & voila!  Thanks for that suggestion.

---

### Post by kronictokr on 2010-04-29
you can try this method for some ati amd users in the radeon hd 3xxx/4xxx series


[http://ubuntuforums.org/showthread.php?t=1464748](http://ubuntuforums.org/showthread.php?t=1464748)

---

### Post by kronictokr on 2010-04-29
you may want to look here


[B][http://ubuntuforums.org/showthread.php?t=1464748](http://ubuntuforums.org/showthread.php?t=1464748)


[/B]

---

### Post by PlanetT on 2010-11-10
Hi all,

I have just bumped into the following problem:

Up to now my ATI Radeon HD 4200 graphics card worked fine enough in 1366x768 mode.
I tried to connect my laptop to my plasma TV by using the HDMI connection. This hasn't really worked so far and it has a side effect. Now I cannot utilize the full resolution of my laptop screen (1366x768), the maximum resolution is 1280x720. In the "Monitor Preferences" window this is the maximum resolution that is offered. I have activated the ATI proprietary FGLRX graphics driver but the maximal resolution hasn't changed. 
I have a faint suspicion that some config file got rewritten but I am not an expert in Ubuntu and just guessing...
I am using Ubuntu 10.04. Does anyone has some idea?

Thanks in advance!

---

### Post by coffeecat on 2010-11-10
> **PlanetT said:**
> I tried to connect my laptop to my plasma TV by using the HDMI connection.

.....

Does anyone has some idea?

The OP of this thread from another forum...

[http://www.linuxformat.com/forums/viewtopic.php?t=12958](http://www.linuxformat.com/forums/viewtopic.php?t=12958)

... managed to get a resolution other than 1280x720 by using a VGA cable (presumably) instead of a HDMI one. True he was  using an older ATI card than you but it might be worth a try.

---

### Post by PlanetT on 2010-11-10
> **coffeecat said:**
> The OP of this thread from another forum...

[http://www.linuxformat.com/forums/viewtopic.php?t=12958](http://www.linuxformat.com/forums/viewtopic.php?t=12958)

... managed to get a resolution other than 1280x720 by using a VGA cable (presumably) instead of a HDMI one. True he was  using an older ATI card than you but it might be worth a try.

thanks for the fast reply but actually a bigger problem now is that I cannot use maximal resolution of my laptop screen even if the TV is disconnected! This effect appears after I tried to connect the laptop to the TV. Earlier the maximal resolution worked fine.

---

### Post by coffeecat on 2010-11-10
> **PlanetT said:**
> thanks for the fast reply but actually a bigger problem now is that I cannot use maximal resolution of my laptop screen even if the TV is disconnected! This effect appears after I tried to connect the laptop to the TV. Earlier the maximal resolution worked fine.

Sorry I missed that - you did make that clear in your earlier post. I notice you are using the proprietary driver. With that you should have somewhere in one of the System menus the Catalyst Control Centre. I'm not sure where exactly - I avoid the ATI proprietary driver with a proverbial barge-pole. Can you adjust the resolution there?

If not, the installation of the fglrx driver would have produced an xorg.conf file which the system may have tweaked when you connected the TV. Post the contents of your /etc/X11/xorg.conf file so that we can see if anything there might be the problem.

Lastly, why are you using the proprietary driver? Your HD4200 card should be capable of giving you adequate 3d accleration for compiz effects and should be capable of HD video playback with the default open-source ATI driver. If all else fails you might want to consider reverting back to the OS driver.

---

### Post by PlanetT on 2010-11-10
> **coffeecat said:**
> Sorry I missed that - you did make that clear in your earlier post. I notice you are using the proprietary driver. With that you should have somewhere in one of the System menus the Catalyst Control Centre. I'm not sure where exactly - I avoid the ATI proprietary driver with a proverbial barge-pole. Can you adjust the resolution there?

If not, the installation of the fglrx driver would have produced an xorg.conf file which the system may have tweaked when you connected the TV. Post the contents of your /etc/X11/xorg.conf file so that we can see if anything there might be the problem.

Lastly, why are you using the proprietary driver? Your HD4200 card should be capable of giving you adequate 3d accleration for compiz effects and should be capable of HD video playback with the default open-source ATI driver. If all else fails you might want to consider reverting back to the OS driver.

yes, I have found the ATI Catalyst Control under System->Preferences but the highest resolution offered there is the same that I could find under System->Preferences->Monitors: 1280x720

Here is the content of my /etc/X11/xorg.conf file:


Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "0-LVDS"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1280x720"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-LVDS" "0-LVDS"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Configured Screen Device"
	Device     "Configured Video Device"
	DefaultDepth     24
	SubSection "Display"
		Virtual   2560 720
	EndSubSection
EndSection
3
Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Actually I installed the ATI proprietary driver after this problem with the resolution turned out, because I thought it might help. So I am not sure if simply deactivateing can help but I can give it a shot...

I tried to hack the /home/myName/.config/monitors.xml file (I am not sure, it was just a risky guess) and changed the resolution data that I found to the values that I'd like to have. After rebooting I got an error message in a popup window in the upper-right corner that says resolution settings cannot be applied and after that Ubuntu uses the 1280x720 setting. Afterwards Ubuntu most likely rewrites that file w/ the resolution it is actually using. Here is the content of the monitors.xml file:

<monitors version="1">
  <configuration>
      <clone>no</clone>
      <output name="VGA-0">
      </output>
      <output name="LVDS">
          <vendor>CMO</vendor>
          <product>0x1680</product>
          <serial>0x00000000</serial>
          <width>1280</width>
          <height>720</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
      <output name="HDMI-0">
          <vendor>MEI</vendor>
          <product>0xa081</product>
          <serial>0x01010101</serial>
          <width>1280</width>
          <height>720</height>
          <rate>50</rate>
          <x>1280768</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
  </configuration>
  <configuration>
      <clone>no</clone>
      <output name="VGA-0">
      </output>
      <output name="LVDS">
          <vendor>CMO</vendor>
          <product>0x1680</product>
          <serial>0x00000000</serial>
          <width>1366</width>
          <height>768</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
      <output name="HDMI-0">
      </output>
  </configuration>
  <configuration>
      <clone>no</clone>
      <output name="LVDS">
          <vendor>???</vendor>
          <product>0x0000</product>
          <serial>0x00000000</serial>
          <width>1366</width>
          <height>768</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
      <output name="DFP1">
      </output>
      <output name="CRT1">
      </output>
  </configuration>
</monitors>

---

### Post by coffeecat on 2010-11-10
Well - this is interesting from your xorg.conf:

> **PlanetT said:**
> ```

    Option        "PreferredMode" "1280x720"
```

I don't know whether changing that would help, or be even safe. You could comment it out with a # at the beginning of the line and see if that helps.

As far as ~/.config/monitors.xml is concerned I've never had to edit one. In fact until this moment I didn't know one existed. I should imagine that xorg.conf is taking precedence, so you could  edit xorg,conf and then zap monitors.xml by renaming it. If the system needs a monitors.xml file it will create one.

This is all speculation but I'm confident that renaming/removing monitors.xml is safe. removing config files in one's home folder is a frequently used way of getting back defaults.

---

