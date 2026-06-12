---
title: "i have a problem befor installing ubuntu on my Laptop?"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by goingin on 2011-01-13
Dear All
i want to install Ubuntu on my laptop,
after booting from ubuntu cd to install i see just this screen
[/COLOR][IMG]http://img407.imageshack.us/img407/6287/ubuntustarting.png[/IMG]
[COLOR=Navy]then i didn't  see any thing (just clear black screen) but when i changed the appearance of my display to external desktop monitor then i will see everything.
anyway i completed the ubuntu installation and after rebooting, same problem.
i don't know how to fix that problem but i think the problem is about resolution about my laptop display, my laptop display is 13"   !!!!!!!! 

please help me

---

### Post by amsterdamharu on 2011-01-13
Could you post the output of the following commands?

```
lspci -k
cat /var/log/Xorg.0.log | grep EE
cat /etc/X11/xorg.conf
```To execute the commands you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. [COLOR=Red]When pasting it here please wrap it in &#91;code] &#91;/code]  tags. In other words: ```
Your pasted stuff
```
[/COLOR]

---

### Post by overdrank on 2011-01-13
Hi and welcome, Moved to Absolute Beginner Talk

---

### Post by goingin on 2011-01-13
[SIZE=5][COLOR=Navy]thank you Amsterdamharu and overdrank

about my problem , here is the result :
after execute command lspci -k [/COLOR][/SIZE]
```

 [FONT=&quot]00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
                Subsystem: Sony Corporation Device 9069
                Kernel modules: intel-agp
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
                Kernel driver in use: pcieport
                Kernel modules: shpchp
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
                Subsystem: Sony Corporation Device 9069
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
                Subsystem: Sony Corporation Device 9069
                Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
                Subsystem: Sony Corporation Device 9069
                Kernel driver in use: HDA Intel
                Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
                Kernel driver in use: pcieport
                Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
                Kernel driver in use: pcieport
                Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
                Kernel driver in use: pcieport
                Kernel modules: shpchp
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
                Kernel driver in use: pcieport
                Kernel modules: shpchp
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
                Kernel driver in use: pcieport
                Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
                Subsystem: Sony Corporation Device 9069
                Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
                Subsystem: Sony Corporation Device 9069
                Kernel modules: iTCO_wdt
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
                Subsystem: Sony Corporation Device 9069
                Kernel driver in use: ahci
                Kernel modules: ahci
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
                Subsystem: Sony Corporation Device 9069
                Kernel modules: i2c-i801
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
                Subsystem: Sony Corporation Device 9069
                Kernel driver in use: intel ips
                Kernel modules: intel_ips
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)
                Subsystem: Sony Corporation Device 9069
                Kernel driver in use: nouveau
                Kernel modules: nouveau, nvidiafb
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
                Subsystem: Sony Corporation Device 9069
                Kernel driver in use: HDA Intel
                Kernel modules: snd-hda-intel
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
                Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN
                Kernel driver in use: iwlagn
                Kernel modules: iwlagn
03:00.0 SD Host controller: Ricoh Co Ltd Device e822
                Subsystem: Sony Corporation Device 9069
                Kernel driver in use: sdhci-pci
                Kernel modules: sdhci-pci
03:00.1 System peripheral: Ricoh Co Ltd Device e230
                Subsystem: Sony Corporation Device 9069
03:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832
                Subsystem: Sony Corporation Device 9069
                Kernel driver in use: firewire_ohci
                Kernel modules: firewire-ohci, ohci1394
03:00.4 SD Host controller: Ricoh Co Ltd Device e822
                Subsystem: Sony Corporation Device 9069
                Kernel driver in use: sdhci-pci
                Kernel modules: sdhci-pci
04:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
                Subsystem: Sony Corporation Device 9069
                Kernel driver in use: atl1c
                Kernel modules: atl1c
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
                Subsystem: Sony Corporation Device 9069
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
                Subsystem: Sony Corporation Device 9069
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
                Subsystem: Sony Corporation Device 9069
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
                Subsystem: Sony Corporation Device 9069
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
                Subsystem: Sony Corporation Device 9069
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
                Subsystem: Sony Corporation Device 9069
[/FONT]
  
```


[SIZE=5][COLOR=Navy]then i write in the terminal [/COLOR][/SIZE]
```

 [FONT=&quot]goingin@goingin-S:~$ cat /var/log/xorg.0.log | grep EE
cat: /var/log/xorg.0.log: No such file or directory
[/FONT]
    [FONT=&quot]goingin@goingin-S:~$ cat /etc/x11/xorg.conf
cat: /etc/x11/xorg.conf: No such file or directory
[/FONT]
  
```

---

### Post by amsterdamharu on 2011-01-13
Strange there is no xorg log and you don't have the nvidia driver installed.
What version of Ubuntu did you install?

If you're connected to the Internet you could try installing the drivers. press alt + F2, type jockey-gtk and press run. It should come up with a driver for your NVIDIA [FONT=&quot]GeForce 310M

I suggest gettining the nvidia-current.

Just follow the install and when it asks to reboot reboot. If it doesn't find the nvidia card you can try downloading the following file:
[http://us.download.nvidia.com/XFree86/Linux-x86/260.19.29/NVIDIA-Linux-x86-260.19.29.run](http://us.download.nvidia.com/XFree86/Linux-x86/260.19.29/NVIDIA-Linux-x86-260.19.29.run)
Copy that on your desktop and log out, now press control + alt + F1 and log in (no windows terminal only). Now type the following commands:
[/FONT]```
sudo service gdm stop
cd ~/Desktop
sudo chmod +x NVIDIA-Linux-x86-260.19.29.run
sudo ./NVIDIA-Linux-x86-260.19.29.run
(follow the install instructions and have it set up an xorg)
sudo service gdm start
```[FONT=&quot]
[/FONT]Now when you log in (gui and windows should be available) press alt + F2, type gnome-control-center and click run.
type "monitor" in the box under "Filter" and click on Monitors, after you click yes when it asks you to use your graphics card vendors tool instead it will show you the nvidia X server settings.
I don't have dual monitors but I'm sure you can find your way through the menus there.
After setting the resolutions and stuff make sure you click the "save to X configuration file" button.
[FONT=&quot]
If after reboot nothing has happened please post the output of the prefious commands again.

[/FONT]

---

### Post by amsterdamharu on 2011-01-13
After digging a little deeper I found some more info. Hope you don't have to go through that and installing latest drivers and setting up your monitors will work for you.  If it doesn't have a look at this: [http://ubuntuforums.org/showthread.php?t=1392766&page=4](http://ubuntuforums.org/showthread.php?t=1392766&page=4)  But you need a working Windows install to get the custom EDID

---

### Post by goingin on 2011-01-13
[SIZE=5][COLOR=Navy]Dear Amsterdamharu
thank you very much , i will try then i will tell you the results
thanks again

[/COLOR][/SIZE]

---

