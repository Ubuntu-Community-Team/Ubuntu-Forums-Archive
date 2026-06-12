---
title: "Is there somewhere you can call to get Linux help?"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2009-02-28
I am at a crossroads. I don't see much future in attempting to resolve my Ubuntu monitor resolution problem through the use of this or other forums. Two weeks have passed without much progress.

My choices:

1. give up on using Linux and return to Microsoft OS. Booting up in XP my monitor is correctly configured.

2. Buy a seperate video card to circumvent my problem with the 610i 7050 motherboard chipset. More money for additional hardware seems silly.

3. Contact a Linux person who can provide direct one on one assistance.

If you know someone who might be able to give me assistance over the phone I am all ears.


Frustrated,

Ed

---

### Post by shane8002 on 2009-02-28
What is your problem exactly. Give me all the details and i might can help you.

---

### Post by steveneddy on 2009-02-28
Several places:

a web site: [https://help.ubuntu.com/](https://help.ubuntu.com/)

or pay for phone support: [http://www.ubuntu.com/support/paid](http://www.ubuntu.com/support/paid)

what is your issue - maybe someone can help you.

Is this an intel video chip issue?

---

### Post by SunnyRabbiera on 2009-02-28
Please keep in mind Ubuntu is mainly community driven, there is no real office to call, though Canonical does have commercial support.
I know the forums sometimes can be a bit much sometimes, so many topics and people here its easy to get lost.
But I rather stick with a forum such as this then deal with something like a M$ tech support line

---

### Post by lykwydchykyn on 2009-02-28
Whereabouts do you live?  There might be a linux user's group in the area where you could get some help.

Personally I'd much rather help someone over a forum than over a phone.  Doing phone support is a dreadful, clumsy experience.

Which OS do you WANT to run?

---

### Post by steveneddy on 2009-02-28
Dude. I just read one of your last posts.

Are you trying to run an Intel video chip from an Nvidia chip driver?

Your xorg.conf says you are using the VESA driver now, which will only give you a low resolution monitor.

Open a terminal and input this command

```
lspci
```and post the output of your terminal here in this thread.

This will tell us when video card you have in your machine and give us a starting place to try and start helping you.

EDIT:

I appoligize - I didn't realize that 610i was an Nvidia integrated Mobo.

---

### Post by rburkartjo on 2009-02-28
hey ed,
dont get frustrated. i am going to be 60 soon and i switched to ubuntu cold turkey after getting pis***  ** at vista. heck if i can learn so can you if you want to. try this download wubi (do a google search). this is and exe program that sets up a dual boot so you can try ubuntu. just make sure at the main window lower right hand that you enter a user name and password. any since it is an exe file you can delete and ubuntu will be gone if you so desire. wubi is the cats meow as far as i am concerned for people trying linux. also and i have advise others if you decide to install wubi and have problems you can pm me. my 2 cents but might be worth a shot

---

### Post by steveneddy on 2009-02-28
> **rburkartjo said:**
> hey ed,
dont get frustrated. i am going to be 60 soon and i switched to ubuntu cold turkey after getting pis***  ** at vista. heck if i can learn so can you if you want to. try this download wubi (do a google search). this is and exe program that sets up a dual boot so you can try ubuntu. just make sure at the main window lower right hand that you enter a user name and password. any since it is an exe file you can delete and ubuntu will be gone if you so desire. wubi is the cats meow as far as i am concerned for people trying linux. also and i have advise others if you decide to install wubi and have problems you can pm me. my 2 cents but might be worth a shot

I highly advise against using WUBI if can help it at all.

The OP already has the OS installed, let's not cripple him by having him use WUBI through Windows. 

Stick with me on this, Ed. We'll get there.

EDIT:

Have you tried enabling the restricted driver's yet?

System --> Administration --> Hardware Drivers

---

### Post by steveneddy on 2009-02-28
Which version of Ubuntu are you using?

---

### Post by steveneddy on 2009-02-28
I found your answer here:

[http://ubuntuforums.org/showpost.php?p=4436236&postcount=8](http://ubuntuforums.org/showpost.php?p=4436236&postcount=8)

Good luck - post back if you have any issues.

---

### Post by ozark_hillbilly on 2009-02-28
Steveneddy,

My  problem was submitted an hour or two ago in this forum with no responses:

Post:    resolving nvidia 610i graphics resolution

I spelled out my situation with log files, etc.
I guess I can copy and paste it here again if necessary.
I have already went thru the procedure you sent me a link to.

lspci:

ed@House:~$ lspci
00:00.0 Host bridge: nVidia Corporation Device 07c3 (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)
00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)
00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1)
00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP73 IDE (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)
00:10.0 VGA compatible controller: nVidia Corporation GeForce 7050/nForce 610i (rev a2)
01:06.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
ed@House:~$

---

### Post by ozark_hillbilly on 2009-02-28
Using version 8.10

---

### Post by ozark_hillbilly on 2009-02-28
hardware drivers tells me that nvidia accel. graphics driver (ver 173) is activated and currently in use....

---

### Post by ozark_hillbilly on 2009-02-28
running ubuntu 8.10

reference Absolute Beginner's forum post:

resolving nvidia 610i graphics resolution

Ed

---

### Post by Kellemora on 2009-02-28
Hi OH

Thats the same video card I have!

I had to download the newest driver for it, it wasn't in the repos!

Let me see if I can remember how I did it and I'll get right back with ya.

TTUL
Gary

---

### Post by ozark_hillbilly on 2009-02-28
Gary,

I don't have a seperate video card!

The 7050 610i chipset is "ON" THE ASUS P5N73-AM MOTHERBOARD. For some reason Linux has a hard time configuring nvidia onboard video chipsets.

I ran the procedure suggested but it still blows up on boot up.

See Absolute Beg. post:    resolving nvidia 610i graphics resolution

Ed

---

### Post by Kellemora on 2009-02-28
Hi OH

First go [HERE]("http://www.nvidia.com/Download/index.aspx?lang=en-us") to find out which exact driver you need and download it to your desktop.

Then use ```
sudo apt-get install Nvidiawhatevername
```

For me this just automatically connected to the Nvidia website and downloaded and installed it again.  Didn't use the one I had on the desktop I don't think.

Then go to system/administration/hardware drivers and select your video card from the list, the NEW driver should NOW be in that list.

I'm a noob too, and perhaps someone else can tell you an easier way to do this?

I didn't keep notes well enough to know if I had to do something else, like add Nvidia to the repositories first or not.

Good Luck

TTUL
Gary

---

### Post by tad1073 on 2009-02-28
Download and save the newest version to your desktop.

Make sure you deactivate the 173 driver.

Then
```

ctrl+alt+f1
```that will drop you to a shell

then
```

sudo /etc/init.d/gdm stop
``````
cd ~/Desktop
``````
sh ./[name-or-driver]
``````
sudo /etc/init.d/gdm start
```

---

### Post by novafluxx on 2009-02-28
have you tried the 'nv' driver instead? It will only provide 2d graphics, but it might be worth a shot!

---

### Post by steveneddy on 2009-02-28
> **tad1073 said:**
> Download and save the newest version to your desktop.

Make sure you deactivate the 173 driver.

Then
```

ctrl+alt+f1
```that will drop you to a shell

then
```

sudo /etc/init.d/gdm stop
``````
cd ~/Desktop
``````
sh ./[name-or-driver]
``````
sudo /etc/init.d/gdm start
```

This is the method I would recommend using.

I would go to the Nvidia website, DL the latest Nvidia driver for Linux and save it on your desktop, then follow the instructions above.

There is an application called Envy that some users use to install the Nvidia driver.

I'll look for it and get back to you.

---

### Post by steveneddy on 2009-02-28
That is the correct method according to this:

[http://ubuntuguide.org/wiki/Ubuntu:Intrepid#NVidia_Driver](http://ubuntuguide.org/wiki/Ubuntu:Intrepid#NVidia_Driver)

which is a link from my my sig. 

You must DL the Nvidia driver from Nvidia first and save it on your desktop.

There are some things you may find interesting right above that link, just scroll up on that page. Go to the top for the complete list.

*********************************

To use Envy to do this for you, first make sure that you have the universe repos activated.

Go to System --> Administration --> Software Sources

Check all of the boxes on the first tab.

Close the window and open a terminal and:

```
sudo apt-get update
sudo apt-get upgrade
```

This will update your sources and get you ready for

```
sudo apt-get install envyng-gtk
```

After that gets finished, just run

```
envyng
```

in a terminal and follow the directions.

Good Luck.

---

### Post by Kellemora on 2009-02-28
Hi OH

My video card is on-board also, not separate.
I have an ASUS M2N68-AM MOBO and had to download the new video driver for it from Nvidia to get it to work in Ubuntu.

Tad posted the way to do it, which is much better than the way I said to!

TTUL
Gary

---

### Post by ozark_hillbilly on 2009-02-28
Ran Envyng -t program.

It seemed to install Ok but Linux continues to boot up in low graphics mode.

What do i check next?

Ed

---

### Post by Kellemora on 2009-02-28
Hi Ed

Applications/Other/Screens n Graphics is what I use to set mine.

If you don't have screens and graphics showing under other.
Right click on Applications, then select Edit Menus, look for OTHER and check it, then in the right window select screens and graphics and check that.

CLOSE

Then you should be able to go to Applications/Other/Screens and Graphics and set the resolution you want so it will STICK.

After that, it should then work in System/Preferences too!

TTUL
Gary

---

### Post by ozark_hillbilly on 2009-03-01
Gary,

I do have the Screen and Graphics under OTHER. But when I change the screen setting to anything other than 800x600 / Plug n Play it asks for a new driver. Someone said the driver I have been trying to load from my LG cd is for Microsoft and not Linux. At any rate if I select Test the configuration check ALWAYS FAILS and it reverts back to the 800x600 setting. Even the 800x 600 Plug n Play Test configuration fails.

So I don't know. I've use Envy and through terminal mode invoked x86-180.29-pkg1.run
(latest driver from nvidia site). No luck so far.

Ed

---

### Post by Kellemora on 2009-03-01
Hi Ed

Under Screens n Graphics, the Driver window shows only the Word Nvidia
But I know I installed the GForce 7 driver, and that's listed above the window as the driver that is in use.

I don't know how to look to tell you exactly WHICH driver I downloaded.

If someone can tell me what to type to show this, or if I can figure it out on my own, I'll post back which driver I downloaded that worked for me.

Are you having a problem with a HUGE SCREEN at Log-In too?????

If so, you fix that by going
```
gksu gedit /etc/X11/xorg.conf
```
then change the 640 480 to 1024 768

My notes only show that I went to system/administration/hardware drivers and installed Nvidia, so apparently the one with just that word is the one I installed.  Just guessing though at which one, I may have gone through all of them myself too.  My memory's not all that hot anymore.

Here is something that might be of interest.
I DID have to load Windows XP in order to install the stuff from the CD into the Asus MOBO Bios.  I couldn't do it from Linux, so since I had to load windows to upgrade the Bios from the supplied CD, I just went ahead and made this machine dual boot also.  Even though I've never booted back into the DOZE on this machine, other than the first time to make sure Grub was working right.

So possibly, maybe your bios are not upgraded from the CD that comes with the MOBO??????

The particular monitor I'm using right now is not in any listing that I know of.  But my other monitor is a Samsung SyncMaster 955DF, so that's what monitor I set my display too, then switched it to this monitor and it worked OK without changing the settings.

Seems like I had to TURN ON or INSTALL the Nvidia web site or something in order for it to appear in the Hardware Drivers drop down lists in order to select it.  If you can see Nvidia in your hardware drivers then I guess you do have it turned on or installed.  Else it wouldn't be there at all.

When I go to system/administration/hardware drivers, a window opens that says Nvidia accelerated graphics driver (latest cards) ENABLED IN USE.

At the top it says Proprietary Drivers are in USE to make this system work properly.

Other than that, I really don't know what else to tell you to try.

Good Luck

TTUL
Gary

---

