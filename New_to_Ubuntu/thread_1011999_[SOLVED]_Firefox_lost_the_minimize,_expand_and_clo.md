---
title: "[SOLVED] Firefox lost the minimize, expand and close buttons"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by acreech on 2008-12-15
Today my firefox 3.0.4 has lost the top brown bar where the minimize, expand and close buttons are located. it also covers the Ubuntu menu bars that are usually at the top and bottom of my desktop (applications, places, system...... and on the bottom my open windows and the trash folder).

I found that there was a temporary fix for this problem by hitting F11 twice, but I have not been able to permanent fix. I have attached a screen shot so that you can see the problem. 

do you have any ideas of a permanent fix for this problem. 

thanks.

---

### Post by dorkdork777 on 2008-12-15
What video card are you using, with what drivers? I had some very strange experiences with the proprietry nVidia drivers for my GeForce 6200, mostly title bar issues.

---

### Post by Therion on 2008-12-15
You need to prevent Emerald from loading at startup.  That's what causing that.  It's happened to me countless times.

Easiest path to a fix is to go into the Session manager, untick Emerald and restart.

There's also a Terminal command that will stop Emerald from loading along with Compiz at restart, but I'm behind my Windows machine at my office at the moment.  If someone else doesn't post it, I'll see if I can't dig it up for you.

---

### Post by Pconfig on 2008-12-15
Try to press alt+f2 and then type

```
metacity --replace
```

---

### Post by acreech on 2008-12-15
> **dorkdork777 said:**
> What video card are you using, with what drivers? I had some very strange experiences with the proprietry nVidia drivers for my GeForce 6200, mostly title bar issues.

I have a nVidia. I am on an Acer Aspire 7520-5185 laptop. I have attached a screen shot of my hardware drivers (System>Administration>Hardware Drivers)

Here is the output of lspci
```

00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:04.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:04.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:04.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

---

### Post by acreech on 2008-12-15
> **Pconfig said:**
> Try to press alt+f2 and then type

```
metacity --replace
```


Thanks that looks like it fixed it. I just restarted the computer and firefox and the problem is fixed. 

Thanks for the help. 

acreech

---

### Post by acreech on 2009-01-04
Call it dumb luck or whatever you would like but I have lost the top buttons on my firefox that minimize, expand and close the program again. 

I tried both suggestions posted here with no avail. I looked in System-> Preferences-> Sessions and could not find anything labeled "Emerald". I also tried alt+F2 then metacity --replace . This does not fix the problem either. This was how I fixed the problem last time. 

I don't know if it was coincidental or not, but at the time that I lost this I was attempting to get a projector to work with my linux computer. There was two methods that I tried. 

The first method was at the following site [http://www.len.ro/2007/03/external-monitor-on-linux-laptop-nvidia-/](http://www.len.ro/2007/03/external-monitor-on-linux-laptop-nvidia-/)

> 

The solution

Using the idea which I found on the forums I created a second configuration file /etc/X11/xorg.conf.external with the following device configuration:

Section "Device"    Identifier     "NVIDIA Corporation NV34M [GeForce FX Go5200]"    Driver         "nvidia"    Option         "NvAgp"      "1"    Option "TwinView" "Yes"    Option "TwinViewOrientation" "Clone"    Option "MetaModes" "1680x1050,1680x1050"EndSection

Then I realized I can start a new X server on :2

Xorg :2 -ac -config /etc/X11/xorg.conf.external

And then in a new terminal start a window manager (I used WindowMaker as you cannot start gnome twice)

export DISPLAY=localhost:2 (here is where the -ac is used)wmaker

I then switch to the new X with CTRL-ALT-F8 do my work and then finally when not needed anymore I close it without affecting my running X. In fact I found this method even handier as it&#8217;s a sandbox for all the applications I want to show and I will not get disturbed during the presentation by an incoming mail or message.



The second method was by editing the xorg.conf file. The file was edited in the following manner. I added the following lines to the bottom of the file under "Section Device"

```

#        Option  "TwinView"               "Yes"
#        Option  "TwinViewOrientation"    "Clone"
#        Option "MetaModes"    "1400X1050,1680X1050,1680X1050"

```

I found that by commenting out these codes I can use my monitor on my laptop, but when I remove the "#" from each line, save and exit (both gedit and the terminal), then ctl+alt+backspace it will switch to the external monitor. 

The last method should not have effected firefox. I believe that the first method should not have affected firefox either. To add to this, the problem only exists on my laptop monitor. When opening firefox on my projector the top bar is there. 

I tried re-installing metacity through the synaptic package manager and I tried re-installing natilus through the synaptic package manager. I also checked the specs on my monitor to verify that the correct resolution is 1440X900. My screen resolution is currently set at 1440X900. I also tried re-installing firefox. Firefox seems to be the only thing affected by this problem. 

Does anyone have any suggestions to this problem?

Thanks for the help.

---

### Post by zika on 2009-01-05
permanent solution:                                                       > System->Preferences->CompizConfig_Settings_Manager->Utility->Workarounds->**uncheck**_Legacy_FullScreen_Support

---

### Post by Abu_Dayya on 2009-01-05
close firefox
remove the .mozilla folder from your home folder
start firefox again


This will remove all firefox settings from your machine. Starting firefox again after removing .mozilla folder will create a new .mozilla folder with default settings

---

### Post by acreech on 2009-01-05
> **Abu_Dayya said:**
> close firefox
remove the .mozilla folder from your home folder
start firefox again


Thanks that worked. I lost all my settings........ but it worked. I can put the bookmarks back from an old backup.

---

### Post by zika on 2009-01-05
> **Abu_Dayya said:**
> close firefox
remove the .mozilla folder from your home folder
start firefox again
This will remove all firefox settings from your machine. Starting firefox again after removing .mozilla folder will create a new .mozilla folder with default settings

don't have to remove ~/.mozilla, just rename it ... ;)

---

### Post by Vladislav Mkrtychev on 2009-01-12
> **zika said:**
> permanent solution:

That worked for me!
Thanks!

---

