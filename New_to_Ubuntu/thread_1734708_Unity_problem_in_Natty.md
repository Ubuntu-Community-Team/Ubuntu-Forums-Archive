---
title: "Unity problem in Natty"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by computerandu on 2011-04-20
Upgarded to Natty but still Unity config is not showing in system. When I checked the system settings it still says Gnome 2.32, not Natty. Any suggestions?

---

### Post by mikewhatever on 2011-04-20
Try to log out and select 'Ubuntu' under Session at the login screen.
Ubuntu is the Unity interface, Ubuntu Classic - Gnome2+Compiz, and Ubuntu Classic (no effects) is just Gnome2.

---

### Post by wojox on 2011-04-20
And make sure your video driver is activated.

---

### Post by computerandu on 2011-04-20
> **mikewhatever said:**
> Try to log out and select 'Ubuntu' under Session at the login screen.
Ubuntu is the Unity interface, Ubuntu Classic - Gnome2+Compiz, and Ubuntu Classic (no effects) is just Gnome2.


I logged out. Then I checked it again. Its Ubuntu (No Ubuntu classic). On the User Login box "Unity development version " is written. 

Just to add some more info, I can see the side task bar. But they are not functioning properly. I mean if you hover the cursor over them they should show options (I saw a you tube video of it). More over when I check in System Monitor, it says Gnome 2.3.

---

### Post by computerandu on 2011-04-20
> **wojox said:**
> And make sure your video driver is activated.


I am not sure how to do that...but i can play videos..so i guess the video drivers are installed

---

### Post by mikewhatever on 2011-04-20
> **computerandu said:**
> I logged out. Then I checked it again. Its Ubuntu (No Ubuntu classic). On the User Login box "Unity development version " is written. 

Just to add some more info, I can see the side task bar. But they are not functioning properly. I mean if you hover the cursor over them they should show options (I saw a you tube video of it). More over when I check in System Monitor, it says Gnome 2.3.

Natty has Gnome 2.32 as the base for its Desktop Environment. Apparently, the Unity interface is not working properly in your case, so the question is - what's the graphics card?
Can you post the output of lspci.

---

### Post by computerandu on 2011-04-20
> **mikewhatever said:**
> Natty has Gnome 2.32 as the base for its Desktop Environment. Apparently, the Unity interface is not working properly in your case, so the question is - what's the graphics card?
Can you post the output of lspci.


Here is the output of the lspci command:

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
04:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

---

### Post by mikewhatever on 2011-04-20
So, an unknown integrated GPU from Intel.:P
How about **sudo lshw -C display**?

---

### Post by terry_gardener on 2011-04-20
unity is a compiz pluigin, ubuntu natty is built on gnome 2.32.  

the options you speak off from the launcher icons is by right clicking them not just hovering. if you hover over the icons it should just display the name.

for helpful tips on unity check out the following sites. 

[http://askubuntu.com/questions/28086/unity-keyboard-mouse-shortcuts]("http://askubuntu.com/questions/28086/unity-keyboard-mouse-shortcuts")

[http://askubuntu.com/questions/29553/how-can-i-configure-unity]("http://askubuntu.com/questions/29553/how-can-i-configure-unity")

---

### Post by computerandu on 2011-04-20
> **mikewhatever said:**
> So, an unknown integrated GPU from Intel.:P
How about **sudo lshw -C display**?

Here you go..

*-display               
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 12
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:41 memory:f0000000-f03fffff memory:d0000000-dfffffff ioport:1800(size=8)

---

### Post by computerandu on 2011-04-20
> **terry_gardener said:**
> unity is a compiz pluigin, ubuntu natty is built on gnome 2.32.  

the options you speak off from the launcher icons is by right clicking them not just hovering. if you hover over the icons it should just display the name.

for helpful tips on unity check out the following sites. 

[http://askubuntu.com/questions/28086/unity-keyboard-mouse-shortcuts](http://askubuntu.com/questions/28086/unity-keyboard-mouse-shortcuts)

[http://askubuntu.com/questions/29553/how-can-i-configure-unity](http://askubuntu.com/questions/29553/how-can-i-configure-unity)

True...right click works...
But..i can still not find compiz config setting manager...:(

---

### Post by grahammechanical on 2011-04-20
You need to select Unity 2D to use Unity. You will also need to install the compiz settings manager through the software centre or synaptic. Then it will appear the System Settings selection page that you get when you click on the shutdown icon and then select System Settings. When you are in the CompizConfigSettings Manager page you can also tick the box Ubuntu Unity Plugin to get extra settings,

Regards,

---

### Post by Random21 on 2011-04-20
> **computerandu said:**
> True...right click works...
But..i can still not find compiz config setting manager...:(

You need to grab it yourself (or at least I had to).

```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by 3rdalbum on 2011-04-20
If Unity doesn't appear to be working correctly, go into a terminal and type:

```
unity --reset
```

---

### Post by computerandu on 2011-04-21
Thanks everyone for their suggestion. 

I had to download the config manager (strange why it was not provided by default )....

---

