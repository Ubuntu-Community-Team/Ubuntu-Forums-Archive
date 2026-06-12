---
title: "Realtek RTL8192CU WLAN | Linux  2.6.32 | DELL CPx"
date: 2013-09-27
forum: Networking &amp; Wireless
---

### Post by xuan2 on 2013-09-27
[COLOR=#000000][FONT=arial]HELP NEEDED


I'm new to linux, I just installed it first time in my life.

Machine details:
DELL Latitude CPx, RAM = 256, HDD = 7GB, SWAP = 0.7GB

I am trying to someone who cant buy new machine. He was using windows xp on the same machine with WLAN USB to connect internet. Windows crashed and I cant install new windows on this machine again. 
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]
Limitations:
USB boot = not possible
CD/DVD more than 700MD = not possible
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]Ethernet = working but only wifi access is available
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]Hard drive = old IBM branded (not SATA )
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]Ubuntu new versions = not possible to burn within 700mb
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]
----------------------------------

[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]I have installed 
Lubuntu 10.04, 
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]Opera Browser
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]Audio and video are perfectly working
------------------------


Issues:

1) WLAN USB not working (*** NEED HELP *** )

2) Flash Player (Not much important)
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]3) Question :  Can i upgrade OS?

[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]========================

3)  Question :  Can i upgrade OS?

Can I upgrade Lubuntu 10.04 to new version? 
Will that support audio/ video hw ??
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]I tried to install 12.04 and 13 earlier, 
results of new lubuntu versions on this machine:
a) right after installation i cant find anything but black screen.
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]b) minimal installation bring shell but right after installation i cant see anything .. perhaps video hw doesnt work

-====================

[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]2) Flash Player

[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]Flash player v9 is working but doesn't show most of the new websites requiring v10 and above
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]When i install Flash player v11 (latest) = it shows plugin crash

=======================

[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]1) WLAN USB internet stick not working

Realtek RTL8192CU Wireless LAN 802.11n USB 2.0 Network Adapter
Driver Provider: Realtek Semiconductor Corp
Downloaded File: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105



[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]I tried to load this driver almost 4times on my machine and tried most the support available on this forum.

[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]Also checked [https://wiki.debian.org/WiFi]("https://www.google.com/url?q=https%3A%2F%2Fwiki.debian.org%2FWiFi&sa=D&sntz=1&usg=AFQjCNGci87yAV62jLl5jW64_n3WsIC24w") and installed wireless-tools by
aptitude install wireless-tools

I need help.. i want to help this old and poor guy to be online.




I have gone through this forum and tried many commands to get some information for experts to review and help.
I am first time using Linux, so pls try to reply in detail.

Thanks!




SYSTEM DETAILS
======================

[FONT=arial]LAPTOP:[/FONT][FONT=arial]
[/FONT][FONT=arial]DELL Latitude CPx, RAM = 256, HDD = 7GB, SWAP = 0.7GB[/FONT][FONT=arial]
[/FONT][FONT=arial]
[/FONT][FONT=arial]WLAN Driver: [/FONT][FONT=arial]
[/FONT][FONT=arial]Realtek RTL8192CU Wireless LAN 802.11n USB 2.0 Network Adapter[/FONT][FONT=arial]
[/FONT][FONT=arial]Driver Provider: Realtek Semiconductor Corp[/FONT][FONT=arial]
[/FONT][FONT=arial]Downloaded File: RTL8188C_8192C_USB_linux_v3.4.[/FONT][FONT=arial]4_4749.20121105[/FONT][FONT=arial]
[/FONT][FONT=arial]
[/FONT][FONT=arial]------------------------------[/FONT][FONT=arial]--------[/FONT][FONT=arial]
[/FONT][FONT=arial]<Command> [/FONT][FONT=arial]
[/FONT][FONT=arial]:~#l cat /proc/version[/FONT][FONT=arial]
[/FONT][FONT=arial]<Result>[/FONT][FONT=arial]
[/FONT][FONT=arial]Linux version 2.6.32-21-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010[/FONT][FONT=arial]
[/FONT][FONT=arial]------------------[/FONT]

----------------
<Command>: 
    :~#l lsusb |grep Realtek
<Result>
    Bus 001 Device 003: ID 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter
------------------------
<Command>: 
    :~#l lsb_release -a
<Result>
    No LSB mdules are available.
    Distributor ID: Ubuntu
    Description: 10.04
    Codename: lucid
-----------------------
<Command>: 
    :~#l lsmod |grep r81
<Result>
    r8192s_usb    346007 0
--------------------------
<Command>: 
sudo hwinfo --netcard
<Result>
39: USB 00.0: 0282 WLAN controller
    [Created at usb.122]
    UDI: /org/freedesktop/Hal/devices/usb_device_bda_8192_00e04c000001_if0
    Unique ID: ADDn.tkx5salVvV1
    Parent ID: k4bc.rkOBIHXr+aF
    SysFS ID: /devices/pci0000:00/0000:00:07.2/usb1/1-1/1-1:1.0
    SysFS BusID: 1-1:1.0
    Hardware Class:network
    Model: "RealtekRTL8192 WLAN Adapter"
    Revision: "1.0"
    Serial ID: "00e04c000001"
    Driver: "rtl819xU"
    Driver Modules: "rtl8192s_USB"
    Device File: WLAN
    Speed: 12Mbps
    HW Address: 00:e0:4c:81:92:00
    WLAN bitrates: 1 2 5.5 11 6 9 12 18 24 36 48 54
    WLAN encryption modes: TKIP CCMP
    WLAN authentication modes: open wpa-psk wpa-eap
    Module Allias: "usb:v0BDAp8192d0100dc00dsc00icFFiscFFipFF"
    Driver Info #0:
     Driver Status: r8192s_usb is active
     Driver Activation Cmd: "modprobe r8192s_usb"
    Config Status: cfg=new, avail=yes, need=no, active=unknown
    Attached to: #38 (Hub)


------------------------
<Command>: 
    :~#l ifconfig wlan0
<Result>
      Link encap:Ethernet  HWaddr 00:e0:4c:81:92:00
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 MB)  TX bytes:0 (0.0 MB)

-----------------
<Command>: 
    :~#l iwconfig wlan0
<Result>
      802.11b/g   Mode:Managed   Access Point: Not-Associated
      Bit Rate: 0 kb/s
      Retry min limit:7    RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
--------------------
<Command>: 
    :~#l  lshw -C network / Pasting only the USB
<Result>
    *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:e0:4c:81:92:00
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g
------------------------
<Command>: 
dmesg |grep -i -e r81 -e usb
<Result>
[    0.282398] usbcore: registered new interface driver usbfs
[    0.282450] usbcore: registered new interface driver hub
[    0.282559] usbcore: registered new device driver usb
[    1.413554] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.413628] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.413680] uhci_hcd: USB Universal Host Controller Interface Driver
[    1.414011] uhci_hcd 0000:00:07.1: new USB bus registered, assigned bus number 1
[    1.414472] usb usb1: configuration #1 chosen from 1 choice
[    1.414593] hub 1-0:1.0: USB hub found
[    1.860256] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    2.033482] usb 1-1: configuration #1 chosen from 1 choice
[   18.220855] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   18.281206] usbcore: registered, new interface driver rtl819xu
[   26.826042] usb 1-1: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   26.907016] usb 1-1: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   27.895899] usb 1-1: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   27.974899] usb 1-1: firmware: requesting RTL8192SU/rtl8192sfw.bin

--------------------[/FONT][/COLOR]

---

### Post by kurt18947 on 2013-09-27
On that machine I doubt anything other than Puppy or something like it (DSL, Tiny Core?) is going to work. Here is something that may or may not be helpful:

[http://www.techradar.com/us/news/software/operating-systems/8-of-the-best-tiny-linux-distros-683552](http://www.techradar.com/us/news/software/operating-systems/8-of-the-best-tiny-linux-distros-683552)

I wonder, if you're able to get an older plug 'n' play adapter you'd have better luck.  Adapters that use RTL-8192SU and RTL-8192CU & Ath9k chipsets seem to need recent kernels in order not require building a driver.  I'm thinking of something like TrendNet TEW-424UB.  It uses a RealTek 8187B chipset and has been plug 'n' play since Ubuntu 9.04 or 9.10, not sure what kernels those used.  You could download one or more of the tiny distros and check your wifi adapter(s) on your own machine.

---

### Post by xuan2 on 2013-09-27
Thanks Kurt, 
I realized that with all these machine limitations I can&#8217;t load windows or any new/ heavy versions of Linux. I did some internet research and picked up Lubuntu which is also one of the recommendations in your shared link. This decision/ recommendation was perfect as its iso file could fit within 700mb bootable CD and installation went very smooth. Audio/ Video are working fine, with Ethernet connection you can watch youtube as well.

Problem is.... this guy doesn&#8217;t have LAN connection available for internet he used to access wifi on windows with the same USB WLAN device which is not functioning or I am unable to make work at Linux. 

Since it was realtek chip so I downloaded driver directly from from RTL8192_USB&#8217;s driver [www.realtek.com.tw]("http://www.realtek.com.tw"). Now tell me do I still need to search from generic drivers?

Apparently wlan driver installation went smooth and I can even see this through commands that system has communicated with the device but I don&#8217;t know how to make it. I have tried this installation almost four times but no success.

I'm new to linux.. just wana make it working..  donno what to do next : (

Pls check all the system info .. 

Experts... I need help !!

---

### Post by kurt18947 on 2013-09-29
I'm no expert but I can see a couple issues:

> [COLOR=#000000][FONT=arial][FONT=arial]Linux  version 2.6.32-21-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu  4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010[/FONT][/FONT][/COLOR]

Using this kernel, I'm pretty sure you'd need to install the driver downloaded from RealTek's site. Even that may not work - if I recall correctly, the RealTek driver says kernel 2.6.**38**-3.0.8 or similar.   I'm using the included driver on the bleeding edge version - 13.10 - and it works pretty well with an 8192CU device.  I doubt that the driver included in a kernel from 2010 would.  I haven't tried Lubuntu recently.  I did install Ubuntu 12.04.3 and the included driver works pretty well with my 8192CU device.  This is one benefit to using current releases -- the built-in drivers have the best chance of working with recently released hardware.

> [COLOR=#000000][FONT=arial]<Command>: 
    :~#l  lshw -C network / Pasting only the USB
<Result>
    *-network DISABLED
[/FONT][/COLOR]

Question is why?  You could try this:
```
rfkill list
```

You should see something like this:

> ~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


Hard blocked usually means there's a switch turned off.  It may be a slide switch like on a laptop or a keystroke combination like alt-f?
If you get Soft blocked: yes, you can try
```
sudo rfkill unblock all
```
and see if that helps.

---

### Post by xuan2 on 2013-10-09
:(

no luck..  its still same

this is an old machine.. it doesn't have any built-in wifi, i'm trying to use USB wifi and it doesnt have any switch to turn on/off.

---

### Post by xuan2 on 2013-10-09
you said " RealTek driver says kernel 2.6.**38**-3.0.8 or similar "

Do you think i'll get audio/ video working if i try to upgrade kernel to whatever newer version?
Earlier I've tried 12.04 on this machine and couldn't get desktop after installation. This is the reason why I pickedup 10.04 on this machine and found everything working, except RTL USB wifi

---

### Post by mörgæs on 2013-10-09
Your best option is buying some used RAM blocks on Ebay or a similar second-hand market. After that a fresh install of Lubuntu 13.04.

---

### Post by xuan2 on 2013-10-09
I just found these links

[http://wireless.kernel.org/en/users/Drivers/rtl819x#rtlwifi](http://wireless.kernel.org/en/users/Drivers/rtl819x#rtlwifi)
[http://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/commit/?id=4844fa169c8d8562289243b54e822a00a0a01082](http://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/commit/?id=4844fa169c8d8562289243b54e822a00a0a01082)

is it safe to try updating this to kernel?
I have downloaded this bin file but i donno what to do with it? where to try and update?

---

### Post by kurt18947 on 2013-10-09
> **mörgæs said:**
> Your best option is buying some used RAM blocks on Ebay or a similar second-hand market. After that a fresh install of Lubuntu 13.04.

If additional RAM will enable a newer distro, I agree with mörgæs.  I recently bought a cheap generic rtl8192cu adapter off Ebay (I have a weakness for <$10 wifi adapters :redface:)  It seems to function very well on updated 12.04 and pretty well on 13.10 - some resolving issues when resuming from suspend there, it seems.  This is using the built-in driver, rtl8192cu.  There is a way to use newer kernels with older distros but if you can run a supported distro, why not?  Older machines are going to be graphics limited which is why Unity & Gnome-shell won't run, but Xubuntu & Lubuntu should work with older less capable graphics cards.  Actually, I think gnome-shell would revert to gnome classic/fallback/whatever-they-call-it if the installed graphics system wouldn't support the new UI.

---

### Post by xuan2 on 2013-10-09
Thanks, but right now it has 256MB RAM with 700MB SWAP and 7GB HDD ext4 partition. This should  work even for newer distro under same brand i.e. 13.04 but 13.04 or 12.04  got no support for this much older audio/video.. so with additional RAM  no desktop visual situation  (I have already tried it).

Additional RAM might not be an easy/ workable solution within this particular machine's limitations. (USB 1.0 old BIOS = usb boot not possible -|- Builtin CD ROM Can't read more than 700MB CD/DVD -|- new distro can't support older Audio/Video driver). 

Ive tried putting 8192cu's BIN file in /lib/firmware folder and then tried to install the RTL's driver.. Apparently this time i got driver installation with NO error and installation completion note. Unfortunately problem didn't resolve... its still disabled. :(

BIN file was downloaded from this site:
[http://wireless.kernel.org/en/users/...tl819x#rtlwifi]("http://wireless.kernel.org/en/users/Drivers/rtl819x#rtlwifi")
[http://git.kernel.org/cgit/linux/ker...822a00a0a01082]("http://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/commit/?id=4844fa169c8d8562289243b54e822a00a0a01082")

Got any idea where else do i need to add/update this bin file ??

---

### Post by xuan2 on 2013-10-09
recent run of same driver installation with pre-added bin file in /lib/firmware folder made two chages
1) no errors were found during installation
2) [COLOR=#000000][FONT=arial]
** NEW CHANGE **
[/FONT][/COLOR][COLOR=#000000][FONT=arial]<Command>:  :~#l lsusb |grep Realtek
<Result>  Bus 001 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. 
------------------------
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]** PREVIOUS **
[/FONT][/COLOR][COLOR=#000000][FONT=arial]<Command>:  :~#l lsusb |grep Realtek
<Result> Bus 001 Device 003: ID 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter
------------------------[/FONT][/COLOR]

---

### Post by xuan2 on 2013-10-09
correction

its now showing correct driver 8192

) [COLOR=#000000][FONT=arial]
** NEW CHANGE **
[/FONT][/COLOR][COLOR=#000000][FONT=arial]<Command>:  :~#l lsusb |grep Realtek
<Result>  Bus 001 Device 002: ID 0bda:8192 Realtek Semiconductor Corp. [/FONT][/COLOR]

---

### Post by xuan2 on 2013-10-09
Kurt 

your shared Commands didn't result anything
rfkill list

sudo rfkill unblock all

---

### Post by xuan2 on 2013-10-09
[**[COLOR=#C61919][B]mörgæs**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=939075")

Are you sure Bodhi supports old hardwares?

Do you think if try Bodhi Linux 2.4.. it will support old hardware like this machine?
I just found multiple iso files on this link [http://www.bodhilinux.com/about_news.php](http://www.bodhilinux.com/about_news.php)

If  bodhi works older hardwares as lubuntu 10.04 does, Could you help me in  understanding as which iso should i use for this old machine?
Apparently for 32 bit machines they have these four option at ([http://sourceforge.net/projects/bodhilinux/files/2.4.0/](http://sourceforge.net/projects/bodhilinux/files/2.4.0/)), 
which one should i select?
 [URL="http://sourceforge.net/projects/bodhilinux/files/2.4.0/bodhi-2.4.0-32.iso/download"]bodhi-2.4.0-32.iso
[/URL][bodhi-2.4.0-32.iso.md5]("http://sourceforge.net/projects/bodhilinux/files/2.4.0/bodhi-2.4.0-32.iso.md5/download")
[URL="http://sourceforge.net/projects/bodhilinux/files/2.4.0/bodhi-2.4.0-nonpae-32.iso/download"]bodhi-2.4.0-nonpae-32.iso
[/URL][bodhi-2.4.0-nonpae-32.iso.md5]("http://sourceforge.net/projects/bodhilinux/files/2.4.0/bodhi-2.4.0-nonpae-32.iso.md5/download")

Thanks!

---

### Post by mörgæs on 2013-10-09
Please run in your present installation

```
sudo lshw -sanitize > lshw.txt
```
and post lshw.txt in CODE tags.

---

### Post by xuan2 on 2013-10-09
Here it is

Command: sudo lshw -sanitize > lshw.txt

Result:


```

computer
    description: Portable Computer
    product: Latitude CPx J650GT
    vendor: Dell Computer Corporation
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
     configuration: boot=normal chassis=portable uuid=44454C4C-59BB-1058-8047-C2C04F31304A
  *-core
       description: Motherboard
       product: Latitude CPx J650GT
       vendor: Dell Computer Corporation
        physical id: 0
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A16 (03/05/2003)
          size: 64KiB
          capacity: 448KiB
           capabilities: isa pci pcmcia pnp apm upgrade shadowing cdboot  bootselect int13floppy720 int5printscreen int9keyboard int14serial  int17printer int10video acpi agp ls120boot smartbattery  biosbootspecification
     *-cpu
          description: CPU
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.8.6
          slot: Microprocessor
           size: 650MHz
          capacity: 750MHz
          width: 32 bits
          clock: 66MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pse36 mmx fxsr sse up
         *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back unified
        *-cache:1
              description: L2 cache
             physical id: 701
             size: 256KiB
             capacity: 256KiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal write-back unified
      *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 256MiB
          capacity: 512MiB
        *-bank:0
             description: DIMM DRAM Synchronous
              physical id: 0
             slot: DIMM_A
             size: 256MiB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous [empty]
             physical id: 1
              slot: DIMM_B
             width: 64 bits
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: 100
           bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel latency=32
          resources: irq:0 memory:f4000000-f7ffffff(prefetchable)
         *-pci
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
              version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:e000(size=4096) memory:fc000000-feffffff memory:10100000-101fffff(prefetchable)
            *-display UNCLAIMED
                description: VGA compatible controller
                product: Rage Mobility P/M AGP 2x
                vendor: ATI Technologies Inc
                physical id: 0
                 bus info: pci@0000:01:00.0
                version: 64
                width: 32 bits
                clock: 33MHz
                capabilities: agp agp-1.0 pm bus_master cap_list
                configuration: latency=32 mingnt=8
                 resources: memory:fd000000-fdffffff ioport:ec00(size=256) memory:fcfff000-fcffffff memory:10100000-1011ffff(prefetchable)
        *-pcmcia:0
             description: CardBus bridge
             product: PCI1225
              vendor: Texas Instruments
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
              configuration: driver=yenta_cardbus latency=176 maxlatency=5
             resources: irq:11 memory:10200000-10200fff ioport:1000(size=256) ioport:1400(size=256) memory:14000000-17ffffff(prefetchable) memory:18000000-1bffffff
         *-pcmcia:1
             description: CardBus bridge
             product: PCI1225
             vendor: Texas Instruments
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 01
              width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
             resources: irq:11 memory:10201000-10201fff ioport:1800(size=256) ioport:1c00(size=256) memory:1c000000-1fffffff(prefetchable) memory:20000000-23ffffff
         *-bridge:0 UNCLAIMED
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
              version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bridge bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
              product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 7.1
             bus info: pci@0000:00:07.1
             logical name: scsi0
             logical name: scsi1
              version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=32
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:860(size=16)
            *-disk
                description: ATA Disk
                product: IBM-DJSA-210
                vendor: IBM
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                 version: JS2O
                serial: [REMOVED]
                size: 9590MiB (10GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=79274114
               *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                    logical name: /
                   version: 1.0
                   serial: [REMOVED]
                   size: 7629MiB
                   capacity: 7629MiB
                   capabilities: primary bootable journaled  extended_attributes large_files huge_files dir_nlink recover extents  ext4 ext2 initialized
                    configuration: created=2013-10-07 05:36:38 filesystem=ext4 lastmountpoint=/gv&#65533;&#65533;];&#65533;H&#65533;[&#998;&#916;^E&#65533;u^ &#65533;f.&#65533;&#65533;W/&#65533;&#65533;^E&#912;Z&#976;Z&#65533;];&#65533;&#65533;^E&#944;^E&#65533;a modified=2013-10-07 06:32:24 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2013-10-09 21:43:00 state=mounted
               *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 667MiB
                    capacity: 667MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                       physical id: 5
                      logical name: /dev/sda5
                      capacity: 667MiB
                      capabilities: nofs
              *-volume:2
                   description: EXT4 volume
                    vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 1.0
                   serial: [REMOVED]
                    size: 1293MiB
                   capacity: 1293MiB
                   capabilities: primary journaled extended_attributes  large_files huge_files dir_nlink extents ext4 ext2 initialized
                    configuration: created=2013-09-29 21:21:02 filesystem=ext4  lastmountpoint=/home modified=2013-09-29 20:53:56 mounted=2013-09-29  20:53:56 state=clean
            *-cdrom
                description: DVD reader
                product: DVD-ROM DRN8080B
                vendor: LG
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                 logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.11
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
         *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 7.2
             bus info: pci@0000:00:07.2
              version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=32
             resources: irq:11 ioport:dce0(size=32)
         *-bridge:1
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 7.3
             bus info: pci@0000:00:07.3
              version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=piix4_smbus latency=0
             resources: irq:9
        *-multimedia
              description: Multimedia audio controller
             product: ES1983S Maestro-3i PCI Audio Accelerator
             vendor: ESS Technology
             physical id: 8
             bus info: pci@0000:00:08.0
              version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Maestro3 latency=32 maxlatency=24 mingnt=2
              resources: irq:5 ioport:d800(size=256) memory:faffe000-faffffff
     *-network
          description: Ethernet interface
          product: Cardbus Ethernet 10/100
          vendor: Xircom
          physical id: 1
           bus info: pci@0000:02:00.0
          logical name: eth0
          version: 03
          serial: [REMOVED]
          width: 32 bits
          clock: 33MHz
          capabilities: pm bus_master cap_list rom ethernet physical
           configuration: broadcast=yes driver=xircom_cb ip=[REMOVED] latency=64 maxlatency=40 mingnt=20 multicast=yes
          resources: irq:11 ioport:1000(size=128) memory:18000000-180007ff memory:18000800-18000fff memory:14000000-14003fff(prefetchable)
      *-communication
          description: Serial controller
          product: Cardbus Ethernet + 56k Modem
          vendor: Xircom
          physical id: 0.1
          bus info: pci@0000:02:00.1
          version: 03
           width: 32 bits
          clock: 33MHz
          capabilities: pm cap_list rom
          configuration: driver=serial latency=0
          resources: irq:11 ioport:1080(size=8) memory:18001000-180017ff memory:18001800-18001fff memory:14004000-14007fff(prefetchable)
   *-battery
       product: CGR-B/838
       vendor: Panasonic
       physical id: 1
       slot: Left Module Bay
       capacity: 59200mWh
       configuration: voltage=14.8V
  *-network DISABLED
        description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: [REMOVED]
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g



```

---

### Post by mörgæs on 2013-10-10
You have repeatedly mentioned that you are afraid of support problems, why? I don't see anything in your configuration which makes the alarm bells sound.

However, a Pentium 3 is simply too slow to be of practical use. If you nonetheless want to give it a try I point again to post #7.

---

### Post by varunendra on 2013-10-10
> **xuan2 said:**
> 
Downloaded File: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105
.....
    Bus 001 Device 003: ID **0bda:[COLOR="#FF0000"]8171[/COLOR]** Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter

> **xuan2 said:**
> 
** NEW CHANGE **
<Command>:  :~#l lsusb |grep Realtek
<Result>  Bus 001 Device 002: ID **0bda:[COLOR="#FF0000"]8172[/COLOR]** Realtek Semiconductor Corp.

> **xuan2 said:**
> correction

its now showing [COLOR="#FF0000"]correct driver 8192[/COLOR]

) 
** NEW CHANGE **
<Command>:  :~#l lsusb |grep Realtek
<Result>  Bus 001 Device 002: ID **0bda:[COLOR="#FF0000"]8192[/COLOR]** Realtek Semiconductor Corp. 

Are you changing the adapters? The emboldened parts are device IDs, not drivers, and they're fixed for a device. And by the way, the driver you downloaded initially was not going to support device **0bda:[COLOR="#FF0000"]8171[/COLOR]** anyway. The correct driver for that chip is 8192DU (RTL8192DU_linux_v4.0.0_5260.20120921.zip package) from Realtek's website (RTL8192DU-VC from [this page]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=53&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true")).

But I'd +1 to Lubuntu 12.04 or 13.04. If you have video issues with those, post a thread and I'm sure troubleshooting that one would be easier for such an old system. Also, the native drivers support all of the above chips, so you may not need the proprietary one in the first place.

---

### Post by kurt18947 on 2013-10-11
> **mörgæs said:**
> You have repeatedly mentioned that you are afraid of support problems, why? I don't see anything in your configuration which makes the alarm bells sound.

However, a Pentium 3 is simply too slow to be of practical use. If you nonetheless want to give it a try I point again to post #7.

I agree with all.  I have an R31 Thinkpad with similar specs except I bumped the RAM to 512 MB. via used SODIMMs off Ebay.  For now, I've settled on snowlinux.  It's Debian based so is pretty familiar to *buntu users. The latest version is using the 3.2.x kernel so I'd expect native RTL8192CU support.  I've had installer issues with many distros - I think video related - but Snowlinux installed as expected.

---

