---
title: "Can't fix screen resolution"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by valero80 on 2011-05-09
I just installed Ubuntu 11.4 on my widescreen desktop. Problem is it gives this horrible 640x480 and gives me no other options when I go into system setting and try to change it. Help?

---

### Post by Blasphemist on 2011-05-09
In a terminal, run this code please.
```
sudo lshw -class Display
```

The current kernel uses kernel mode settings and you may have to use one or more of them. You'll also need to ensure you run the right gpu drivers which is why I ask that you start with this command.

---

### Post by valero80 on 2011-05-09
When I run that command I get this

  *-display               
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:dc100000-dc17ffff ioport:1800(size=8) memory:c0000000-cfffffff memory:dc180000-dc1bffff

---

### Post by Blasphemist on 2011-05-09
Here are my results:
```
jim@jim-Satellite-L505:~$ sudo lshw -class Display
[sudo] password for jim: 
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
       resources: irq:45 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:5110(size=8)
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
       resources: memory:d3500000-d35fffff

```

My version shows 7 and yours is 3 and mine is Mobile 4 Series. See the following link that shows Intel after the 950 works.

[https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)

I _think_ your driver differs and your gpu does. I'm also on 64 bit Ubuntu but that likely isn't involved. 

See this page.
[https://wiki.edubuntu.org/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.edubuntu.org/HardwareSupportComponentsVideoCardsPoulsbo)

Particularly the following:
> Emgd drivers (currently supported)
Drivers are available in the gma500 PPA repository for Natty, Maverick and Lucid

Repository page: [https://launchpad.net/~gma500/+archive/emgd](https://launchpad.net/~gma500/+archive/emgd)


Instructions for Natty only. Open a terminal and type:

sudo add-apt-repository ppa:gma500/emgd 
sudo apt-get update
sudo apt-get install xorg-emgd emgd-dkms
sudo emgd-xorg-conf
reboot for the changes to take effect.

I haven't done enough research to know if this will work for your gpu and it looks like to me you'll need to downgrade xorg. I think you'll need to try and sort this out. I also don't know what the result of that downgrade would be in limitations if any.

---

### Post by nalle on 2011-05-27
I also have the same problem, but the solution you gave ended up breaking ubuntu so that I had to reinstall. By now I've tried many things

- using xrandr in 32 bit -> i can get the resolution but half the desktop goes black (the mouse moves over it so it renders in some way)
-tryng to update xserver-xorg-video drivers -> boot started hanging on "checking memory state"

- installing 64 bit
- using xrandr to get the right resolution worked a couple of times, then stopped 
- tried adding the xrandr commands to /home/user/.profile -> no go
- and then the right resolutions by making a xorg.conf file -> didn't work.
-> Now the xrandr commands give me the same half screen jumbo
(checked update log, xserver-xorg drivers were updated)
- tried downgrading xserver-xorg-video-intel, but it didn't help, let it upgrade again
- turning compiz off, then xrandr and compiz on -> got the right resolution to work proper. But unity crashed.

So I guess it's back to the classic desktop to try out if I can get it to work better.. :( if anyone doesn't have any other solutions?

Oh, and for easy reference for xrandr my desired resolution is 1368 x 768:
```
$ cvt 1368 768
output: # 1368x768 59.88 Hz (CVT) hsync: 47.79 kHz; pclk: 85.25 MHz
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
```
*(copy everything after modeline after the command --newmode)*
```
$ xrandr --newmode "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync2

$ xrandr --addmode VGA1 "1368x768"
```

And info on the screen:
```
$ xrandr

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
   1368x768       59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)

```

```
$ sudo lshw -class Display
  *-display               
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:42 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:1170(size=8)

```
My screen is a widescreen 19' Samsung UE-19C4000

---

### Post by Grenage on 2011-05-27
Are you sure that your TV can handle 60 as a refresh rate?  I could only find one tech list for the TV, and it specified it as 50.

---

### Post by nalle on 2011-06-01
True, thanks for the tip! I'll change it to 50. But the monitor doesn't seem to have any problem with the settings whereas ubuntu won't automatically use them even without the modeline setting (with Xorg.conf) and breaking completely when Unity is in use. So the solution I have now, is having the xrandr commands in the end of .profile file in my home folder, which changes the resolution when I log in.

---

### Post by Grenage on 2011-06-01
Well we would use an xorg.conf and we'd probably got it sorted, but if it's working ok with xrandr in your .profile, it's probably not worth it.

---

