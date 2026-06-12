---
title: "acer hot key compiling"
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by Luksion Knight on 2007-09-11
I have converted my dad to Ubuntu (Victory against the machine!) but he has a laptop with builtin wifi. i have the drivers installed, now all i need is to install acer hotkey. but when i run make in the terminal i get this error:
```
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/fred/Desktop/acerhk-0.5.34/acerhk.o
/home/fred/Desktop/acerhk-0.5.34/acerhk.c:38:26: error: linux/config.h: No such file or directory
make[2]: *** [/home/fred/Desktop/acerhk-0.5.34/acerhk.o] Error 1
make[1]: *** [_module_/home/fred/Desktop/acerhk-0.5.34] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [acerhk.ko] Error 2
```

---

### Post by noob12 on 2007-09-11
If you are running the Ubuntu 2.6.20-16-generic kernel you already have the acerhk module version 0.5.34 prebuilt in your distribution.   All you have to do is run **modprobe** to load it or put it in your **/etc/modules** file with the right options to load it at boot.  Using the right options is important depending on your laptop series.

I can give you instructions to build it if you really need to, but you shouldn't.

---

### Post by Luksion Knight on 2007-09-12
well when i run sudo modprobe acerhk like the howto tells me to, i get the return error
```
FATAL: Error inserting acerhk (/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/acerhk.ko): Cannot allocate memory
```

---

### Post by noob12 on 2007-09-12
Can you tell me what model of Acer laptop you have?

---

### Post by Luksion Knight on 2007-09-12
im actually using a compaq presario m2000. i heard that the acer hot-key wasnt just acer specific but worked on other laptops. like i said, i just need to turn the kill switch.

---

### Post by noob12 on 2007-09-12
OK.  The reason you're getting that message is that the acerhk module isn't able to initialize on that laptop.  The matrix here [http://rfswitch.sourceforge.net/?page=laptop_matrix](http://rfswitch.sourceforge.net/?page=laptop_matrix) has instructions for most, but I don't see the m2000 there.  Also not listed on the acerhk site [http://www.cakey.de/acerhk/](http://www.cakey.de/acerhk/).

I can try to provide a suggestion.

What is the wireless card that is in that and which driver are you using?  

Can you post the output of
```

lspci -nn

sudo lshw -C network

```

Also, what does
```

cat /sys/class/net/*/device/rf_kill 

```
say?

---

### Post by Luksion Knight on 2007-09-13
```
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02)
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02)
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 83)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 03)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 03)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 03)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:06.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG Network Connection [8086:4220] (rev 05)
02:09.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
02:09.2 FireWire (IEEE 1394) [0c00]: Texas Instruments OHCI Compliant IEEE 1394 Host Controller [104c:8032]
```

```
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:c5:de:11
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.96 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:3000-30ff iomemory:e0207800-e02078ff irq:18
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@02:06.0
       logical name: eth1
       version: 05
       serial: 00:15:00:3a:4c:24
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=Intel,04/29/2005,9.0.2.25 latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:e0206000-e0206fff irq:20

```

and 

```
fred@cruton:~$ cat /sys/class/net/*/device/rf_kill
cat: /sys/class/net/*/device/rf_kill: No such file or directory
```

---

### Post by noob12 on 2007-09-13
Does **iwconfig** show that the TX-Power is off or 0 dBm?  If it is nonzero, the radio isn't off.  

I notice you are using ndiswrapper, and I'm worried that the driver isn't looking at the hardware switch value.

Ubuntu ships with a pretty good driver (ipw2200) for this chipset.  Is there any reason you don't use the ipw2200 driver that is shipped with Ubuntu?   I have found that driver (different laptop same wireless device) has been pretty robust for me.

Can you try loading the ipw2200 driver with the led=1 option?  Use the following sequence.
This temporarily unloads ndiswrapper and loads the ipw2200 driver with the led=1 option.
```

sudo modprobe -r ndiswrapper
sudo modprobe -r ipw2200
sudo modprobe ipw2200 led=1

```


Note that the interface will probably be called eth1 instead of wlan0.  

Toggle the switch while looking at the output of any of the following.

You can look for nonzero TX-Power in **iwconfig**  or at the output of 
[B]
cat /sys/class/net/*/device/rf_kill
[/B]
which will appear when you have that driver loaded.  When the radio is off by the hardware switch, the value will be 2.  If it is 0 or 1, you are in good shape.    
Then enable wireless in the NetworkManager.

If you start seeing scan results from **sudo iwlist scan** you are also in good shape.

---

### Post by Luksion Knight on 2007-09-13
it worked! thanks a ton, now how do i make it permanent?

---

### Post by Luksion Knight on 2007-09-13
i guess it was a little too early to celebrate. i get the option to connect to my network, then it will be connecting or have just connected and the computer will hang. same screen, no movement, no mouse reaction.

---

### Post by noob12 on 2007-09-14
Let's try to have a clean boot with ipw2200 in the picture and not ndiswrapper.

Check if you blacklisted ipw2200
```

grep -e 'blacklist.*ipw2200' /etc/modprobe.d/*

```
If you find any lines then  edit the file that is shown and comment out that line by preceding it with a # sign.

Comment out the loading of ndiswrapper in /etc/modules.
```

sudo gedit /etc/modules

```
Find any line that says ndiswrapper and precede it with a # sign.

Now reboot.  If your wireless radio is disabled and your switch doesn't work, then do the following command.

This edits the /etc/modprobe.d/options file to tell the kernel to use the led=1 option on ipw2200 when loading it at boot.
```

echo "options ipw2200 led=1" | sudo tee -a /etc/modprobe.d/options

```
Then reboot once more.

Try things out.  If things are still unstable, we need to do more diagnostics.

---

### Post by Luksion Knight on 2007-09-15
same problem, hangs when connecting. the wireless LED is solid, but the LED that lets me know caps lock is on is flashing.

---

### Post by noob12 on 2007-09-15
When you went through the procedure, did you actually try the intermediate stage with no **led=1** option?  What was the behavior in that stage, was the radio just disabled and wouldn't turn on?

ADDED:  Also you say it hangs when connecting; do you mean that the whole machine freezes up still?

---

### Post by Luksion Knight on 2007-09-15
during the intermediate stage, the wireless was off, the killswitch didnt respond. and when i say it hangs i do mean the whole system freezes up. i have to force reset it because the mouse doesnt even move.

---

### Post by noob12 on 2007-09-15
That's bad.  

Not many avenues left.

The freeze sounds like a kernel conflict of some kind, like possibly an IRQ.  I think you should file a bug report on launchpad.  They might have other suggestions there.  Do you see anything in your **dmesg** output or your **/var/kern.log** file that might provide a clue?  Are you running any other drivers that didn't come with Ubuntu?

I found one blog entry from a compaq m2232 user on Ubuntu 6.10 that successfully used the ipw2200 with the **led=1** option just as we had configured it.  I've also helped some other users on other laptops that required the led=1 option, so I don't know what is going on with yours.

A more recent version of the ipw2200 driver from [http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/) might work, but I don't know for sure and I have never built that.  The version in Ubuntu 7.04 is 1.20, and they are up to 1.2.2.  I can try to help you if you want to go there, but I am not an experienced guide with that specific build.

You can also go back to the ndiswrapper + windows driver, but I'm afraid you will always find the radio disabled using that, unless there are some BIOS settings you can work with to get around that.   If you want to reverse the steps that we did to disable it, just put back the  **blacklist ipw2200** again in **/etc/modprobe.d/blacklist** and uncomment the **ndiswrapper** line in **/etc/modules**.  You can leave the **/etc/modprobe.d/options** file alone since the ipw2200 option settings won't be used if it is not loaded.

If you have other ideas that you would like my help with, let me know.

---

