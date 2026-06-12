---
title: "Stepping into the void"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by sophie2cu2 on 2011-07-20
Hi Guys,
I've been running on Wubi for a few days now and I think I want to move on to the full install. Thing is, I haven't been able to get the internet to work with Wubi and I'm hoping it will be better with the full install. I'm also wondering about drivers for my scanner (Epson Perfection 2480 Photo) and my old printer Canon LPB-1260 plus. Will I be able to run them on the full Ubuntu? I don't know how to write programs or add commands....
So, can anyone point me towards an idiots guide for setting up the internet and getting stuff like the above to work. Also, if I want to do the full install, should I erase my hard disk first? Format it? Anything in particular?
Many thanks,
Sophie

---

### Post by dasan on 2011-07-20
first of all you can boot in to live cd and check what and all are working fine..
I think LBP printer also should work cos one of my friend is using it from ubuntu

---

### Post by westie457 on 2011-07-20
While you were running the Wubi did you have a wired connection and no wireless or did you have neither of them working?
TBH at the moment if not working in Wubi then in all probability it still will not work in a full install.

In a (Wubi) terminal or LiveCD terminal run ```
lspci
```
Copy the text and in a new reply click on # and paste between the```
 
```tags.
This will let us know what the hardware is and to find a solution for you.

Once it is working it will have to be done again for the full install.

---

### Post by Paddy Landau on 2011-07-20
In addition to westie457's reply: When you install Ubuntu, ensure that you have a wired connection to the Internet. The installation should automatically download extra drivers if required.

---

### Post by westie457 on 2011-07-20
> Also, if I want to do the full install, should I erase my hard disk first? Format it? Anything in particular?

Before you do the full install there will be some cleaning to be done and some choices to be made.

First choice Dual-boot with Windows and Ubuntu or have just Ubuntu.
That can be either can be done from the LiveCD and choosing install. 
More on that later.

If dual booting then load Windows and remove Wubi using Control-Panel > Programs and Features. It (the Wubi) should be in the list as 'Ubuntu'.
When that has finished reboot into Windows if necessary and then Defragment the hard drive. Three times in a row should be enough to give you as much space as possible.

Then still in Windows right-click the 'My Computer' and select Manage.  In the window... Storage > Disc Management. Then right-click on the c:\ drive and select shrink volume. Choose by how much (10 GB as a minimum), yes to all questions and wait for it to finish. If you have a separate data partition you can shrink that too if you want.
With the space you have created [B][U]do nothing to it for now.[B][U] This will be your Extended partition for install Ubuntu.

I think everything is covered for the moment. 
Any questions, just ask.

---

### Post by sophie2cu2 on 2011-07-29
Hi everybody,
Thanks for your suggestions.
I'm obviously too much of a beginner for this. I'm sitting here clutching my brand new Ubuntu CD while I stare at the screen like a rabbit in the headlights.
I need to learn some basics - like just understanding the words.
Sorry,
S

---

### Post by Swagman on 2011-07-29
Hey Chill, Sophie.. It really isn't hard. Most of the stuff you are asked to do is simply copy & pasting into the terminal

So how do you do that.. Get into the terminal, that is ?

Boot into either your wubi version or from your live cd and when its loaded press ctrl + alt + t

that'll open a terminal (aka as a CLI or SHELL)

the copy & paste the command previously given you 

```
lspci
```

which is a command to list all the things we need to detect what chipsets etc are in your computer

lspci on mine reads

>   

paul@Main-Computer:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:09.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port E)
00:0a.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
00:15.1 PCI bridge: ATI Technologies Inc Device 43a1
00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 Ethernet controller: **Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)**
02:00.0 PCI bridge: PLX Technology, Inc. PEX8112 x1 Lane PCI Express-to-PCI Bridge (rev aa)
03:04.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
04:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
05:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
06:00.0 SATA controller: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02)
06:00.1 IDE interface: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02)
07:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 8800 GT] (rev a2)
paul@Main-Computer:~$



From that list propellor heads can see I don't have a wireless card installed but am using the bit in bold (Realtek ethernet)

It would probably be of help to enter this in the Terminal

```
sudo lshw -C network
```

If your in your wubi install then that sudo bit will require you to enter your password before it will go any further... You **WONT** see it as you type it

That command on my system gives this result..

[quote]
paul@Main-Computer:~$ sudo lshw -C network
[sudo] password for paul: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 06
       serial: e0:cb:4e:cd:c2:32
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.4 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:45 ioport:a800(size=256) memory:cffff000-cfffffff memory:cfff8000-cfffbfff memory:f9ce0000-f9cfffff
paul@Main-Computer:~$
[quote]

---

