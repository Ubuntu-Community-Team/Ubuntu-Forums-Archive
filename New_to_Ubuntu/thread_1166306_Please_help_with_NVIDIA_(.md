---
title: "Please help with NVIDIA :("
date: 2009-05-21
forum: New to Ubuntu
---

### Post by amsunshine0917 on 2009-05-21
Hello, 
I have just installed Ubuntu 9.04, and when I installed NVIDIA (713.14.16), it does not show up in System>Administration>Hardware Drivers. This is my main problem I think...I have several other problems that I think are linked to this...I have looked at many other forums on this particular problem, but none have been able to help me :confused:

Any help you can offer would be VERY much appreciated!

---

### Post by Cammy on 2009-05-21
I don't really understand the problem.  Are you talking about your video drivers for your NVidia card, or are you talking about something like nvidia-settings?

---

### Post by amsunshine0917 on 2009-05-21
> **Cammy said:**
> I don't really understand the problem.  Are you talking about your video drivers for your NVidia card, or are you talking about something like nvidia-settings?

The driver.

---

### Post by amsunshine0917 on 2009-05-21
> **mazterOFdizazter said:**
> [http://change.menelgame.pl/change_please/3328381/](http://change.menelgame.pl/change_please/3328381/)


...

---

### Post by amsunshine0917 on 2009-05-21
Hello, I have Ubuntu 9.04 and I installed NVIDIA 713 and it's not showing up in System>Administration>Hardware Devices.

When I click NVIDIA X Server Settings it tells me "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

I tried that and nothing happens. At all. NOW, when I start my computer it pops up with errors about not having a graphics driver installed and takes me to a command prompt, unless I tell it to start in safe graphics mode.

PLEASE HELP!

---

### Post by taurus on 2009-05-21
Did you install nvidia driver version 713 by hand?

Did you run **sudo nvidia-xconfig** from a terminal to configure your machine with the new nvidia driver that you have just installed?

---

### Post by Junkieman on 2009-05-21
Hi sunshine, what you want to do is reconfigure the xserver, if you google that you get plenty pages about it, in short do this: when you get to the terminal, log in with your username and password and enter this command...

```
sudo dpkg-reconfigure xserver-xorg
```

Hope this helps!

---

### Post by amsunshine0917 on 2009-05-21
> **taurus said:**
> Did you install nvidia driver version 713 by hand?

Did you run **sudo nvidia-xconfig** from a terminal to configure your machine with the new nvidia driver that you have just installed?


yes when I tried running sudo nvidia-xconfig this is what happened:

root@username-laptop:~# sudo nvidia-xconfig
root@username-laptop:~#

---

### Post by Eclipse. on 2009-05-21
> **amsunshine0917 said:**
> yes when I tried running sudo nvidia-xconfig this is what happened:

root@username-laptop:~# sudo nvidia-xconfig
root@username-laptop:~#

Now just restart and you should be fine.

---

### Post by amsunshine0917 on 2009-05-21
> **Junkieman said:**
> Hi sunshine, what you want to do is reconfigure the xserver, if you google that you get plenty pages about it, in short do this: when you get to the terminal, log in with your username and password and enter this command...

```
sudo dpkg-reconfigure xserver-xorg
```Hope this helps!

Thank you I am working on this right now- I'll let you know momentarily if it works.

---

### Post by amsunshine0917 on 2009-05-21
> **Eclipse. said:**
> Now just restart and you should be fine.

No. When I restarted it kept popping up telling me that I didn't have any drivers installed...

---

### Post by amsunshine0917 on 2009-05-21
> **amsunshine0917 said:**
> Thank you I am working on this right now- I'll let you know momentarily if it works.

I'm stuck on one of the screens- it won't let me proceed for some reason :(

For the X server to handle the keyboard correctly, a keyboard model must  &#8593; 
 &#9474; be entered.  Available models depend on which XKB rule set is in use.     &#9646; 
 &#9474;                                                                           &#9618; 
 &#9474;  With the "xorg" rule set:                                                &#9618; 
 &#9474;  - pc101: traditional IBM PC/AT style keyboard with 101 keys, common in   &#9618; 
 &#9474;           the United States.  Has no "logo" or "menu" keys;               &#9618; 
 &#9474;  - pc104: similar to pc101 model, with additional keys, usually engraved  &#9618; 
 &#9474;           with a "logo" symbol and a "menu" symbol;                       &#9618; 
 &#9474;  - pc102: similar to pc101 and often found in Europe. Includes a "< >"    &#9618; 
 &#9474; key;                                                                      &#9618; 
 &#9474;  - pc105: similar to pc104 and often found in Europe. Includes a "< >"    &#9618; 
 &#9474; key;                                                                      &#9618; 
 &#9474;  - macintosh: Macintosh keyboards using the new input layer with Linux    &#9618; 
 &#9474;               keycodes;                                                   &#8595; 
 &#9474;                                                                             
 &#9474;                                  <Ok>                                       
 &#9474;                                  

it won't let me hit ok/enter

---

### Post by Bodsda on 2009-05-21
> **amsunshine0917 said:**
> No. When I restarted it kept popping up telling me that I didn't have any drivers installed...

If the command
```
sudo dpkg-reconfigure xserver-xorg
```
doesnt fix the problem, you could try rebooting, choosing 'recovery' option from grub and then in the menu choose 'xfix'

---

### Post by taurus on 2009-05-21
Hit the Tab key to highlight the <OK> and then the Return key.

---

### Post by Bodsda on 2009-05-21
> **amsunshine0917 said:**
> I'm stuck on one of the screens- it won't let me proceed for some reason :(

For the X server to handle the keyboard correctly, a keyboard model must  &#8593; 
 &#9474; be entered.  Available models depend on which XKB rule set is in use.     &#9646; 
 &#9474;                                                                           &#9618; 
 &#9474;  With the "xorg" rule set:                                                &#9618; 
 &#9474;  - pc101: traditional IBM PC/AT style keyboard with 101 keys, common in   &#9618; 
 &#9474;           the United States.  Has no "logo" or "menu" keys;               &#9618; 
 &#9474;  - pc104: similar to pc101 model, with additional keys, usually engraved  &#9618; 
 &#9474;           with a "logo" symbol and a "menu" symbol;                       &#9618; 
 &#9474;  - pc102: similar to pc101 and often found in Europe. Includes a "< >"    &#9618; 
 &#9474; key;                                                                      &#9618; 
 &#9474;  - pc105: similar to pc104 and often found in Europe. Includes a "< >"    &#9618; 
 &#9474; key;                                                                      &#9618; 
 &#9474;  - macintosh: Macintosh keyboards using the new input layer with Linux    &#9618; 
 &#9474;               keycodes;                                                   &#8595; 
 &#9474;                                                                             
 &#9474;                                  <Ok>                                       
 &#9474;                                  

it won't let me hit ok/enter

Try to use the tab key to move the highlighted area to the ok button

---

### Post by amsunshine0917 on 2009-05-21
> **taurus said:**
> Hit the Tab key to highlight the <OK> and then the Return key.

okay, so I finished with that...now what?

---

### Post by Bodsda on 2009-05-21
> **amsunshine0917 said:**
> okay, so I finished with that...now what?

Log out log back in or reboot and see if the problem is solved, if not then we need to edit xorg.conf to load the driver

Regards,

Bodsda

---

### Post by amsunshine0917 on 2009-05-21
> **Bodsda said:**
> Log out log back in or reboot and see if the problem is solved, if not then we need to edit xorg.conf to load the driver

Regards,

Bodsda

WOW, I had a reallllllly hard time getting back into my computer :(

it just flashed back and forth thru screens saying that I didn't have a graphics driver, asking me to start in safe graphics mode, and it said something about the greeting crashing...????? FINALLY I got lucky and it let me thru...

---

### Post by Bodsda on 2009-05-21
> **amsunshine0917 said:**
> WOW, I had a reallllllly hard time getting back into my computer :(

it just flashed back and forth thru screens saying that I didn't have a graphics driver, asking me to start in safe graphics mode, and it said something about the greeting crashing...????? FINALLY I got lucky and it let me thru...

Ok, sounds like we are gonna have to edit xorg.conf

can you please paste the contents of /etc/X11/xorg.conf

remember its case sensitive (big)X11(one one)/xorg.conf

Regards,

Bodsda

---

### Post by amsunshine0917 on 2009-05-21
> **Bodsda said:**
> Ok, sounds like we are gonna have to edit xorg.conf

can you please paste the contents of /etc/X11/xorg.conf

remember its case sensitive (big)X11(one one)/xorg.conf

Regards,

Bodsda

Can you walk me thru that?

---

### Post by Bodsda on 2009-05-21
> **amsunshine0917 said:**
> Can you walk me thru that?

Sure, no problem

Open a terminal and paste the following command

```
gksudo gedit /etc/X11/xorg.conf
```

Then paste the contents here.

Regards,

Bodsda

---

### Post by amsunshine0917 on 2009-05-21
> **Bodsda said:**
> Sure, no problem

Open a terminal and paste the following command

```
gksudo gedit /etc/X11/xorg.conf
```Then paste the contents here.

Regards,

Bodsda
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
    Driver    "nvidia"
EndSection






sorry that took so long- had to take a shower lol

---

### Post by Bodsda on 2009-05-21
hmm, thats odd -- its loading the driver...

Try changine the line 

Driver 'nvidia'

to

Driver 'nv'

if that fails we might have to reinstall the driver.

Regards,

Bodsda

---

### Post by amsunshine0917 on 2009-05-21
> **Bodsda said:**
> hmm, thats odd -- its loading the driver...

Try changine the line 

Driver 'nvidia'

to

Driver 'nv'

if that fails we might have to reinstall the driver.

Regards,

Bodsda

Do I need to restart after I change that?

---

### Post by Bodsda on 2009-05-21
> **amsunshine0917 said:**
> Do I need to restart after I change that?

yeah, just log out and back in

---

### Post by skompier on 2009-05-21
A little more information would be helpful. Which Nvidia card are you using?

I have a 9800GT that will not work in 8.10 or 9.04. I can only get it to run with the 180.51, 180.60, or 185.xx drivers in 8.04. I've followed EVERY post and still no joy. I'm happy with 8.04.

Update: I found out that my TV card conflicts with Nvidia cards starting with the 2.6.27 kernel. I've blacklisted the CX18 module and all is well. I'm now running 9.04 on 180.51 drivers. Excellent.

---

### Post by taurus on 2009-05-21
> **Bodsda said:**
> yeah, just log out and back in

Log out and back in won't restart the X server.  Have to do <Ctrl><Alt>Backspace or reboot.

---

### Post by amsunshine0917 on 2009-05-21
> **taurus said:**
> Log out and back in won't restart the X server.  Have to do <Ctrl><Alt>Backspace or reboot.


I'm afraid to reboot, lol. I logged out and back in. When I press ctrl alt backspace is something supposed to happen? Cuz nothing happens, lol.

---

### Post by Bodsda on 2009-05-21
> **amsunshine0917 said:**
> I'm afraid to reboot, lol. I logged out and back in. When I press ctrl alt backspace is something supposed to happen? Cuz nothing happens, lol.

Oh yeah, reboot -- i automatically said log out because i log out with ctrl+alt+backspace -- which if enabled restarts the xserver. 

anywhoo, reboot then tell us whats happening

---

### Post by ibuclaw on 2009-05-21
Threads merged :)

---

### Post by amsunshine0917 on 2009-05-21
> **tinivole said:**
> Threads merged :)
  cool thanks :)

---

### Post by ibuclaw on 2009-05-21
> **amsunshine0917 said:**
> cool thanks :)

OK, Change of question:

How did you install the drivers? Manually?

Is anything shown in the output of this:
```
dpkg -l | grep nvidia | awk '{print $2}'
```

---

### Post by amsunshine0917 on 2009-05-21
> **tinivole said:**
> OK, Change of question:

How did you install the drivers? Manually?

Is anything shown in the output of this:
```
dpkg -l | grep nvidia | awk '{print $2}'
```

Haven't seen anything like that if that's what youre asking...

---

### Post by amsunshine0917 on 2009-05-21
Okay, so when I reboot my computer these are the messages that I get..

"Ubuntu is running in low graphics mode. The following error was encountered. You may need to update your configuration to solve this. (EE) No devices detected."

I click OK

"What would you like to do?
-run Ubuntu in low-graphics mode for just one session
-reconfigure graphics
-troubleshot the error
-exit to console login"

I've tried clicking OK (on the first option only) and Cancel and they both lead to the same message:

"There already appears to be an X server running on display :0..."  (there's alot more to that one- but that's the gist of it) I click yes to try a different display and get this:

"Stand by one minute while the display restarts" I click OK and it just cycles thru those last 3 msgs until I get lucky and it lets me thru :/

---

### Post by Bodsda on 2009-05-21
> **amsunshine0917 said:**
> Haven't seen anything like that if that's what youre asking...
> ```
dpkg -l | grep nvidia | awk '{print $2}'
```
tinivole means could you please run that command in a terminal and paste any output given.

Also please run

```
lspci
```

and paste all output

Regards,

Bodsda

---

### Post by amsunshine0917 on 2009-05-21
> **Bodsda said:**
> tinivole means could you please run that command in a terminal and paste any output given.

Also please run

```
lspci
```and paste all output

Regards,

Bodsda

dpkg -l | grep nvidia | awk '{print $2}'
nvidia-173-kernel-source
nvidia-173-modaliases
nvidia-180-modaliases
nvidia-71-modaliases
nvidia-96-modaliases
nvidia-common
nvidia-glx-173
nvidia-settings






 lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

---

### Post by amsunshine0917 on 2009-05-21
Thank all you guys so much for your help- I have to go for today (work, blah) I'll be back on tomorrow. Any further help would be much appreciated :)

---

### Post by Bodsda on 2009-05-21
> **amsunshine0917 said:**
> 
 lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

Hmm, maybe my eyes arent working correctly because its late but I cant actually see any nvidia graphics cards listed there. It looks more like intel integrated graphics controller

Can you make sure the bus is seated correctly and the power cord is attached securely.

Regards,

Bodsda

---

### Post by gkyasitha on 2009-05-22
I have the same problem and finally resolve it.
did you plug in any new hardware recently(i mean after fresh ubuntu installation).
I plug in my old dial-up pci modem just for fun and afterwards I face the same series of problems as you did.
I think the problem is that ubuntu conflict with the pci card and vga card.After removing it all work fine.
hope this will help you!
(sorry for my english)

---

### Post by amsunshine0917 on 2009-05-22
> **gkyasitha said:**
> I have the same problem and finally resolve it.
did you plug in any new hardware recently(i mean after fresh ubuntu installation).
I plug in my old dial-up pci modem just for fun and afterwards I face the same series of problems as you did.
I think the problem is that ubuntu conflict with the pci card and vga card.After removing it all work fine.
hope this will help you!
(sorry for my english)

No I haven't but thank you :)

---

### Post by amsunshine0917 on 2009-05-22
> **Bodsda said:**
> Hmm, maybe my eyes arent working correctly because its late but I cant actually see any nvidia graphics cards listed there. It looks more like intel integrated graphics controller

Can you make sure the bus is seated correctly and the power cord is attached securely.

Regards,

Bodsda

Lol, so now I feel kinda retarded...So I need to install the intel graphics driver? I just saw every where that when someone was having problems with not being able to use compiz because of their driver, they were told to install the nvidia driver... I'm so confused, lol. I can't find an intel driver that's compatible with linux/ubuntu. I know it exists, but I can't find it, lol.

---

