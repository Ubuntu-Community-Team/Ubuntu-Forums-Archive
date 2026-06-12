---
title: "Having 2 monitors"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by anemone42 on 2011-07-11
Trying to have 2 monitors, showing the same.

```
lisea@ubuntu:~$ sudo lshw -c video
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:47 memory:90000000-903fffff memory:80000000-8fffffff ioport:70f0(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:90500000-905fffff
lisea@ubuntu:~$ 
```**Been using UNIX since 1988, been installing Ubuntu since, well, yesterday.** ;)

---

### Post by LowSky on 2011-07-11
Welcome to the forums. If you are using unity click th eubuntu logo at the top, type monitor, and open the app. Then change the settings to what you prefer.

---

### Post by anemone42 on 2011-11-21
> **LowSky said:**
> Welcome to the forums. If you are using unity click th eubuntu logo at the top, type monitor, and open the app. Then change the settings to what you prefer.

I am using 11.10 + Ubuntu Classic. Is that unity?

I don't see an ubuntu logo at the top.

I still have the problem with 2nd monitor only showing bright green.

---

### Post by F.G. on 2011-11-21
'classic' isn't 'unity', but the program is still there.
at the top left, if you go to:

System > Preferences > Monitors

you should get a handy GUI to configure them.

---

### Post by anemone42 on 2011-11-22
Ubuntu version: 11.10

Computer: HP620

I haven't changed xorg.conf or tried anything else.

The ubuntu classic is an odd, non standard thing, and I can't find "System". I have "Applications" and "Places" to the left, and a drop down on the right, including "System Settings".

---

### Post by F.G. on 2011-11-22
that's odd, i use the 'ubuntu classic' setting and it has a 'system' tab.  

anyhow, you can click on 'System Settings' from the drop down menu and a window should pop up called 'control center' if you scroll down you should under 'hardware' an icon with 'Monitors' next to it. click on that and it's the same monitor configuring GUI program.

---

### Post by gordintoronto on 2011-11-22
Actually, it is called "Displays."

---

### Post by anemone42 on 2011-11-22
This is what mine looks like. (See attached.)

I can click "Detect Displays", but it doesn't do anything.

---

### Post by F.G. on 2011-11-22
sorry, that one looks different to mine although it should do the same thing, so i don't know what's wrong and why your other monitor isn't showing up (at the risk of stating the obvious, you're sure it's plugged into the computer and plugged into the wall and turned ON, etc).

another option is to install something else to handle it. you could try grandr. that would go something like this:
```

sudo apt-get install grandr

```
then you have to enter your password, then:
```

grandr

```
all this from the command line. and you should see a GUI application popping up which can manage your monitors.

---

### Post by juliandracos on 2011-11-23
I, and many others, have had similar problems.  For whatever reason, it does not detect both monitors in the display options.  I have Nvidia cards and had to run the Nvidia controller to get the options.  I assume you will need to do the same with the Intel.

If you do not have the drivers for the Intel chip, you can download them here:

[http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Graphics&ProductLine=Laptop+graphics+controllers&ProductProduct=Mobile+Intel%C2%AE+4+Series+Express+Chipset+Family](http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Graphics&ProductLine=Laptop+graphics+controllers&ProductProduct=Mobile+Intel%C2%AE+4+Series+Express+Chipset+Family)

Good luck getting it fixed.  If not, then I suggest moving to an alternative Ubuntu based OS.  I can get dual monitors to work on them without problems.  
[]("http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Graphics&ProductLine=Laptop+graphics+controllers&ProductProduct=Mobile+Intel%C2%AE+4+Series+Express+Chipset+Family")

---

### Post by anemone42 on 2011-11-23
> **F.G. said:**
> sorry, that one looks different to mine although it should do the same thing, so i don't know what's wrong and why your other monitor isn't showing up (at the risk of stating the obvious, you're sure it's plugged into the computer and plugged into the wall and turned ON, etc).

another option is to install something else to handle it. you could try grandr. that would go something like this:
```

sudo apt-get install grandr

```then you have to enter your password, then:
```

grandr

```all this from the command line. and you should see a GUI application popping up which can manage your monitors.

grandr also shows 1 monitor only.

---

### Post by anemone42 on 2011-11-23
> **juliandracos said:**
> I, and many others, have had similar problems.  For whatever reason, it does not detect both monitors in the display options.  I have Nvidia cards and had to run the Nvidia controller to get the options.  I assume you will need to do the same with the Intel.

If you do not have the drivers for the Intel chip, you can download them here:

[http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Graphics&ProductLine=Laptop+graphics+controllers&ProductProduct=Mobile+Intel%C2%AE+4+Series+Express+Chipset+Family](http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Graphics&ProductLine=Laptop+graphics+controllers&ProductProduct=Mobile+Intel%C2%AE+4+Series+Express+Chipset+Family)

Good luck getting it fixed.  If not, then I suggest moving to an alternative Ubuntu based OS.  I can get dual monitors to work on them without problems.  


Oh dear. Which one is mine?

Should I get help from a windows forum for this?

---

### Post by juliandracos on 2011-11-23
> **anemone42 said:**
> Oh dear. Which one is mine?

Should I get help from a windows forum for this?

Given the info you posted, it looks like you have the Mobile 4 and the link I provided is to that.  The middle panel lists a lot of OS.  Scroll down until you find the one that says Linux.  Click to download the latest one.  It then takes you to another page with a link to a URL

Given the info Intel posted, you will want v. 10.3.1 (I Think).  One version works with Ubuntu and the other one does not have it listed.  

Another thing you can try is to click on hardware drivers.  It might list the Intel drivers there and you can install them that way.

---

### Post by anemone42 on 2011-11-23
Okay, so I get to this page (see attached). And then I don't know what to choose.

<select id="Chipset" name="Chipset" style="WIDTH: 600px"><option value="select...">select...</option>

<option value="1019">Intel&reg; Atom&trade; processor D400/500, N400/500 series</option>

<option value="1013">Intel&reg; Atom&trade; processor Z500 series with Intel&reg; System Controller Hub US15W/US15WP/US15WPT</option>

<option value="1020">Intel&reg; Atom&trade; Processor N270 with Mobile Intel&reg; 945GSE Express Chipset</option>

<option value="1009">Mobile Intel&reg; 945GME Express Chipset</option>

<option value="1004">Intel&reg; 945G Express Chipset</option>

<option value="1014">Intel&reg; Q45, G41 and G45 Express chipsets</option>

<option value="1015">Mobile Intel&reg; GM45, GL40 and GS45 Express chipsets</option>

<option value="1002">Intel&reg; Q35 Express Chipset</option>

<option value="1003">Intel&reg; Q965 Express Chipset</option>

<option value="1018">Mobile Intel&reg; 910GMLE and 915GME Express chipsets</option>

<option value="1005">Intel&reg; 915GV Express Chipset</option>

<option value="1016">Mobile Intel&reg; GME965 and GLE960 Express chipsets</option>


</select>

---

### Post by gordintoronto on 2011-11-23
I think the command: lspci
will help you determine which one to select.

---

### Post by anemone42 on 2011-11-23
> **gordintoronto said:**
> I think the command: lspci
will help you determine which one to select.

Uhm.

```
lise@lise-HP-620:~$ lspci | grep hips
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
lise@lise-HP-620:~$
```

---

### Post by BicyclerBoy on 2011-11-23
Ubuntu already has the open source intel driver..i915..

Do not try to install the code from intel..it takes a uber-geek to get it working..


Try this in terminal:
glxinfo | grep OpenGL
cat /var/log/Xorg.0.log | grep i915

Plug in the external monitor & then logout/login, then post the /var/log/Xorg.0.log file..

---

### Post by anemone42 on 2011-11-24
> **BicyclerBoy said:**
> Ubuntu already has the open source intel driver..i915..

Do not try to install the code from intel..it takes a uber-geek to get it working..


Try this in terminal:
glxinfo | grep OpenGL
cat /var/log/Xorg.0.log | grep i915

Plug in the external monitor & then logout/login, then post the /var/log/Xorg.0.log file..

```
lise@lise-HP-620:~$ glxinfo | grep OpenGL
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset x86/MMX/SSE2
OpenGL version string: 2.1 Mesa 7.11
OpenGL shading language version string: 1.20
OpenGL extensions:
lise@lise-HP-620:~$ 
lise@lise-HP-620:~$ cat /var/log/Xorg.0.log | grep i915
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
lise@lise-HP-620:~$
```Xlog attached. Please note the monitor wasn't unplugged prior to this log. The monitor is always attached in my setup.

Also, the monitor is plugged in through a docking station.

---

### Post by BicyclerBoy on 2011-11-24
Well your driver i965 is installed & loaded okay..
GLX & DRI are loaded.

The only detected display is the internal LDVS panel:
LG Display
LP156WH2-TLRB
Modeline "1366x768"x59.6

There is no other monitor connected/detected..

Can you connect the external monitor by DVI or HDMI or Displayport ?

Is this h/w a laptop ?
Does the keyboard monitor sw (<fn>+<f2> ?) do anything ?

---

### Post by anemone42 on 2011-11-24
Could this be because it's through the docking station? I also have trouble with my mouse, when it goes through there.

Can I somehow make ubuntu "forget" the docking station, and then try again? Maybe that would help.

Hardware = laptop.

fn + f2 = turn brightness down (I think).

---

### Post by BicyclerBoy on 2011-11-25
Could be the dock ..
Some new docking stations are optimus graphics video cards etc..

Do you think the laptop has nVidia graphics internally ?
Do you think the docking station could have GPU ?

---

### Post by anemone42 on 2011-11-25
> **BicyclerBoy said:**
> Could be the dock ..
Some new docking stations are optimus graphics video cards etc..

Do you think the laptop has nVidia graphics internally ?
Do you think the docking station could have GPU ?

It describes itself this way:

```
DisplayLink Software Release: External Release Note 
Software Package: HP USB Graphics 
Product Version: 5.5.27887.0 
Product Date: 12th October 2010 
DisplayLink Core Software Version: 5.5.27797.0 
DisplayLink Core Software Date: 21st September 2010
```

---

### Post by BicyclerBoy on 2011-11-25
That sounds very much like an external USB display adapter..
There is support for some USB displays..

Don't know if there is support..

---

### Post by anemone42 on 2011-11-26
It's this docking station:

[link]("http://www.nivo.co.za/#buy%7Ehp.usb.2.0.port.replicator.ay052aa.%7Ep21775")

---

### Post by BicyclerBoy on 2011-11-26
I found info on your device minutes after your previous post..
Marketing waffle does not help..
 
You could find the usd ids & search..
The sub devices could be used in some other h/w & have some support.
The device is likely a USB hub with a collection of sub devices..

lsusb

---

### Post by anemone42 on 2011-11-27
```
lise@lise-HP-620:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05c8:0403 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 002 Device 002: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 004 Device 002: ID 148f:1000 Ralink Technology, Corp. 
Bus 008 Device 002: ID 1bcf:0005 Sunplus Innovation Technology Inc. 
Bus 002 Device 004: ID 0424:9514 Standard Microsystems Corp. 
Bus 002 Device 005: ID 0d3d:0001 Tangtop Technology Co., Ltd HID Keyboard
Bus 002 Device 006: ID 0424:9904 Standard Microsystems Corp. 
Bus 002 Device 007: ID 17e9:01d6 Newnham Research 
Bus 002 Device 008: ID 04a9:1746 Canon, Inc. 
Bus 002 Device 009: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
lise@lise-HP-620:~$
```

Not sure what to do next?

---

### Post by BicyclerBoy on 2011-11-28
The Bus 002 Device 007: ID 17e9:01d6 Newnham Research
is a USB DisplayLink DL-160 chip ?

[http://libdlo.freedesktop.org/wiki/HowTo](http://libdlo.freedesktop.org/wiki/HowTo)

After plugging in the USB docking station...
dmesg | grep udlfb

---

### Post by anemone42 on 2011-11-28
```
lise@lise-HP-620:~$ dmesg | grep udlfb
[   20.346799] udlfb: DisplayLink HP USB Docking Video - serial #021ACA
[   20.346803] udlfb: vid_17e9&pid_01d6&rev_0110 driver's dlfb_data struct at f6d9f800
[   20.346805] udlfb: console enable=0
[   20.346807] udlfb: fb_defio enable=0
[   20.352982] udlfb: vendor descriptor length:22 data:22 5f 01 0020 05 00 01 03 04 02
[   20.352985] udlfb: DL chip limited to 2080000 pixel modes
[   20.353096] udlfb: allocated 4 65024 byte urbs
[   20.491916] udlfb: 1280x1024 valid mode
[   20.491920] udlfb: 720x400 valid mode
[   20.491922] udlfb: 640x480 valid mode
[   20.491925] udlfb: 640x480 valid mode
[   20.491926] udlfb: 640x480 valid mode
[   20.491928] udlfb: 640x480 valid mode
[   20.491930] udlfb: 800x600 valid mode
[   20.491931] udlfb: 800x600 valid mode
[   20.491933] udlfb: 800x600 valid mode
[   20.491936] udlfb: 800x600 valid mode
[   20.491938] udlfb: 832x624 valid mode
[   20.491939] udlfb: 1024x768 valid mode
[   20.491941] udlfb: 1024x768 valid mode
[   20.491943] udlfb: 1024x768 valid mode
[   20.491945] udlfb: 1280x1024 valid mode
[   20.491947] udlfb: 1152x864 valid mode
[   20.491949] udlfb: 1280x1024 valid mode
[   20.491951] udlfb: Reallocating framebuffer. Addresses will change!
[   20.495225] udlfb: 1280x1024 valid mode
[   20.495228] udlfb: set_par mode 1280x1024
[   20.505338] udlfb: DisplayLink USB device /dev/fb1 attached. 1280x1024 resolution. Using 5120K framebuffer memory
[   20.506324] usbcore: registered new interface driver udlfb
lise@lise-HP-620:~$ 
```

Not sure whether that means the answer is yes or no.

Oh wait! DisplayLink in next to last line! And elsewhere. But not sure about 160 ...

---

### Post by BicyclerBoy on 2011-11-29
This means the displaylink h/w is detected/recognized & the kernel driver has loaded.

The 2nd part of the driver is the xorg framebuffer driver must be configured to drive this device.

sudo apt-get install xserver-xorg-video-displaylink
You need something like displaylink_drv.so under /usr/lib/xorg/modules/drivers.

You need to create an /etc/X11/xorg.conf file..the default is no file..
sudo Xorg -configure

Now need to edit the xorg.conf file
gksudo gedit /etc/X11/xorg.conf

add ```

Section "Files"                                                   
   ModulePath  "/usr/lib/xorg/modules"
   ModulePath  "/usr/local/lib/xorg/modules"
EndSection

Section "Screen"
    Identifier      "DisplayLinkScreen"
    Device          "DisplayLinkDevice"
    Monitor         "DisplayLinkMonitor"
    DefaultDepth    16
    SubSection "Display"
        Depth   16
        Modes   "1280x1024"
    EndSubSection
EndSection

Section "Device"
    Identifier      "Configured Video Device"
    Driver          "displaylink"
    Option          "fbdev" "/dev/fb1"
EndSection

Section "ServerLayout"
    Identifier      "Server Layout"
    Screen  0       "Default Screen" Absolute 0 0
    Screen  1       "DisplayLinkScreen" Absolute 1366 0
    Option          "Xinerama"      "true"
EndSection

```

The "Default Screen" name may have to be changed to match the internal panel/display name.
The "Xinerama" option may need to be false (true may have no openGL h/w acceleration).

Read some of the mail archives here:
[http://lists.freedesktop.org/mailman/listinfo/libdlo](http://lists.freedesktop.org/mailman/listinfo/libdlo)

[http://www.pur3.co.uk/DisplayLink](http://www.pur3.co.uk/DisplayLink)

---

### Post by anemone42 on 2011-11-29
I assume this shouldn't be put in the file:

```
The internal device section needs to have the Driver option
(Choose your driver instead of intel)
```

I've put the rest in the file.

---

### Post by BicyclerBoy on 2011-11-29
Quite right...I amended the post..

Did this bit work okay ??
sudo apt-get install xserver-xorg-video-displaylink

logout/login
(hope for best, expect the rest)

post the /var/log/Xorg.0.log file

Just park this below information for later if required..
Your intel & displaylink driver(s) can be updated from x-swat launchpad ppa.. 
[https://launchpad.net/~ubuntu-x-swat/+archive/ppa](https://launchpad.net/~ubuntu-x-swat/+archive/ppa)
These packages are more cutting edge & there is a bit more risk of new bugs...this is not a one way irreversible step.

---

### Post by anemone42 on 2011-11-29
Okay, I think I kind of did things in the wrong order.

First I did the xorg.conf and booted.

Then after some hilarious moments, the /var/log/Xorg.0.log file revealed:

```
[    43.340] Data incomplete in file /etc/X11/xorg.conf
        Undefined Screen "Default Screen" referenced by ServerLayout "Server Layout".
```

Then I did sudo apt-get install xserver-xorg-video-displaylink, which worked fine.

Then:

```
lise@lise-HP-620:~$ sudo Xorg -configure

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log
lise@lise-HP-620:~$ 
```

I am a bit overwhelmed by the email archives and stuff ...

---

### Post by BicyclerBoy on 2011-11-30
Forget the Xorg -configure step..

was just a fast way to get a working /etc/X11/xorg.conf file..& you seem to have this file anyway..

Just need to fix the "Default Screen" label/tag.
In /etc/X11/xorg.conf file"
There needs to be a Device Screen & Monitor sections for each display.

The internal display just needs the basic stuff with "intel" driver.

This is an example of a working xorg.conf for "intel" 945GME i915 driver  on *buntu 11.04..
```

Section "Module"
        Load          "dri"
        Load          "glx"
EndSection

Section "DRI"
    Group "video"
    Mode 0660
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
        Option          "AccelMethod" "EXA"
#        BusID           "PCI:0:2:0"
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

Note: BusID           "PCI:0:2:0" will need to match your h/w..run lspci & find the PCI bus id from the VGA device..
I have this option commented out..
See if this works for internal panel only...
Then add the displaylink stuff & the serverlayout section.

---

### Post by anemone42 on 2011-12-02
I tried with only default screen, worked fine. Then I added the extra monitor stuff. No joy. Files attached.

---

### Post by BicyclerBoy on 2011-12-02
Replace 
```

Section "Device"
    Identifier      "Configured Video Device"
    Driver          "displaylink"
    Option          "fbdev" "/dev/fb1"
EndSection

with

Section "Device"
    Identifier      "DisplayLinkDevice"
    Driver          "displaylink"
    Option          "fbdev" "/dev/fb1"
EndSection

```

You need to remove "nomodeset" from the grub cmd-line..

The intel driver can not work with "nomodeset"..


Then reboot & check the Xorg.0.log file or errors/warnings.
Check if xorg complains about missing monitor section (for the USB displaylink)..

---

### Post by anemone42 on 2011-12-04
Good news: I can live with this xorg.conf. Bad news: still a bright green screen, and nothing else ...

See files attached.

Oh, and there was no nomodeset to remove.

Additional: tried switching the 2 screens in order, as that seems to be an issue. Result in 2nd attached file.

---

### Post by BicyclerBoy on 2011-12-05
[screens.zip] shows the intel driver loading correctly..
(no "nomodeset" in that grub cmd)

[screens2.zip] fails to load intel driver, some how grub was invoked with nomodeset...that what is in the log file..

The bright green screen means the kernel driver is working..

I don't have a displaylink device to play with, so can't help..

---

### Post by anemone42 on 2011-12-05
This is from booting with the xorg.conf from screens2.zip above.

---

### Post by BicyclerBoy on 2011-12-05
Some interesting config needed for w.r.t. xrandr in /etc/gdm/Init/Default:
(applies to older ubuntu ?)

[http://mulchman.org/blog/?tag=displaylink](http://mulchman.org/blog/?tag=displaylink)


May need to blacklist the fbcon driver..

---

### Post by anemone42 on 2011-12-07
This post just to remind myself what I've done so far.

```
sudo apt-get install xserver-xorg-video-displaylink
vi xorg.conf
```

---

### Post by anemone42 on 2011-12-07
> **BicyclerBoy said:**
> Some interesting config needed for w.r.t. xrandr in /etc/gdm/Init/Default:
(applies to older ubuntu ?)

[http://mulchman.org/blog/?tag=displaylink](http://mulchman.org/blog/?tag=displaylink)


May need to blacklist the fbcon driver..

xrandr-config:

> There is also a bug with the screen rotate not set normally when X has  fired up, resulting in that all menu bars and popups are displayed out  side the screen. To fix this  add the following lines to the file  /etc/gdm/Init/Default after the defintion of the gdmwhich() function.

This seems a minor issue, I can come back to.

Blacklisting fbcon driver? Like this?
[URL="http://www.nvnews.net/vbulletin/showpost.php?p=2219564&postcount=3"]
http://www.nvnews.net/vbulletin/showpost.php?p=2219564&postcount=3[/URL]

---

### Post by BicyclerBoy on 2011-12-07
I thought it read as xrandr was a problem..xrandr is an extension loaded by intel driver/Xorg.

Blacklist:
steps 1 & 4 should be sufficient for ubuntu.
You will find the fbcon & vga16b are blacklisted by the nVidia driver installer script.
Note important differnece ..ubuntu path is /etc/modprobe.d/blacklist.conf

Actually any/all blacklist entry in any /etc/modprobe.d/*.conf file is actioned.

---

### Post by anemone42 on 2011-12-14
Just a note to myself: also did:

```
sudo vi /etc/modprobe.d/blacklist.conf 
sudo update-initramfs -u
```

---

### Post by anemone42 on 2011-12-15
And that didn't have any effect either. Sigh ...

---

### Post by anemone42 on 2011-12-21
Okay, found a thread saying it will not work for me with this monitor.

[http://ubuntuforums.org/showpost.php?p=11471142&postcount=7](http://ubuntuforums.org/showpost.php?p=11471142&postcount=7)

I tried using read-edid, and it only finds the screen of the laptop.

[http://maxolasersquad.blogspot.com/2009/04/get-edid-information.html](http://maxolasersquad.blogspot.com/2009/04/get-edid-information.html)

```
lise@lise-HP-620:~$ sudo get-edid | sudo parse-edid
parse-edid: parse-edid version 2.0.0
get-edid: get-edid version 2.0.0

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
    Function supported
    Call successful

    VBE version 300
    VBE string at 0x2110 "Intel(R)Cantiga Graphics Chipset Accelerated VGA BIOS"

VBE/DDC service about to be called
    Report DDC capabilities

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
    Function supported
    Call successful

    Monitor and video card combination does not support DDC1 transfers
    Monitor and video card combination supports DDC2 transfers
    0 seconds per 128 byte EDID block transfer
    Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
    Read EDID

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
    Function supported
    Call successful

parse-edid: EDID checksum passed.

    # EDID version 1 revision 3
Section "Monitor"
    # Block type: 2:0 3:0
    # Block type: 2:0 3:fe
    # Block type: 2:0 3:fe
    Identifier "LGD:ad02"
    VendorName "LGD"
    ModelName "LGD:ad02"
    # Block type: 2:0 3:0
    # Block type: 2:0 3:fe
    # Block type: 2:0 3:fe
    # DPMS capabilities: Active off:no  Suspend:no  Standby:no

    Mode     "1366x768"    # vfreq 59.636Hz, hfreq 46.635kHz
        DotClock    69.300000
        HTimings    1366 1398 1430 1486
        VTimings    768 770 774 782
        Flags    "-HSync" "-VSync"
    EndMode
    # Block type: 2:0 3:0
    # Block type: 2:0 3:fe
    # Block type: 2:0 3:fe
EndSection
lise@lise-HP-620:~$ 
```Can anyone confirm I've read this info correctly? Before I buy a new monitor?

---

### Post by anemone42 on 2011-12-23
Okay, I've accepted that this will never work, and found a totally different solution. Thanks for all the help though!

---

