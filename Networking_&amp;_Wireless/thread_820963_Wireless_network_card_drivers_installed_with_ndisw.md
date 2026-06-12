---
title: "Wireless network card drivers installed with ndiswrapper, but wont connect?"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by Cup of Squirrels on 2008-06-06
Hello all,

When I initially installed Ubuntu a few days ago, I eventually managed to connect to my wireless network for internet access with little problems, using the drivers that came with the distro.


After that, I went about the task of installing my video drivers. After much installing and uninstalling of various restricted drivers and offical NVIDIA drivers, I managed to get it working following the instructions from [this]("http://ubuntuforums.org/showthread.php?t=797270&highlight=here%2C+download+173.14+driver+%28first+listed%29.+Save%2Fmove+home+directory.") thread. After rebooting and finding the drivers working (and my desktop in a nice resolution for once ;p) I noticed that I could no longer connect to the internet. I did lshc -C network or whatever it is, and found my wireless card was now unclaimed, with no drivers.

There was nothing in the restricted drivers list, so I was forced to use ndiswrapper to install the windows drivers for my card. ndiswrapper -l shows "drivers installed, device present", and the network probe command shows my card with the drivers installed.

However, my distro still refuses to connect to the network and internet. I have tried using both admin --> network and iwconfig to insert the info needed, but still nothing: sudo dhclient wlan0 does not show my card responding, as it did before.


This is very frustrating after how easy it was to get it working in the first place. Is there anybody who could lend me a helping hand?

Thanks :)

(I am using a Texas Instruments U.S. Robotics 22Mpbs Wireless PCI card)

---

### Post by pytheas22 on 2008-06-06
If the card worked initially, there's no reason it shouldn't still be working; graphics drivers shouldn't have anything to do with it.  I suspect that the "restricted drivers" utility just made some mistake; quite possibly it removed the firmware for your wireless card.

Instead of trying to troubleshoot ndiswrapper, I'd advise you to try to get the card working again with the native Linux driver.  Please post the output of these commands so that we'll have a better idea of what to do:
```

lspci
iwconfig
cat /etc/modprobe.d/options
```

---

### Post by Cup of Squirrels on 2008-06-06
Hi there, thanks much for lending a hand


lspci:

```
00:00.0 Host bridge: ATI Technologies Inc Radeon 9100 IGP Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP PCI/AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc Unknown device 4367 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc Unknown device 4368 (rev 01)
00:13.2 USB Controller: ATI Technologies Inc Unknown device 4365 (rev 01)
00:14.0 SMBus: ATI Technologies Inc SMBus (rev 03)
00:14.1 IDE interface: ATI Technologies Inc Unknown device 4369 (rev 01)
00:14.2 RAID bus controller: ATI Technologies Inc 436E Serial ATA Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 436c (rev 01)
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4362 (rev 01)
00:14.5 Multimedia audio controller: ATI Technologies Inc Unknown device 4361 (rev 03)
01:05.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)
02:07.0 Multimedia audio controller: Creative Labs SB Audigy LS
02:0a.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface
02:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
```


iwconfig;

```
wlan0     IEEE 802.11b  ESSID:"BTHomeHub-8937"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power:0 dBm   Sensitivity=1/3  
          RTS thr=2432 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:43/100  Signal level:-68 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```



cat /etc/modprobe.d/options

```
# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2
```


All of the info for iwconfig seems to be in order - the router mode is Managed and channel 0.... it just refuses to associate, as you can see.


It certainly seems to be a driver issue.

I look forward to your next response, thankyou :)

---

### Post by pytheas22 on 2008-06-06
Thanks for the information.  I'm going to ask for a little more, however.  Please run these commands:
```

sudo -s
echo 'blacklist ndiswrapper' >> /etc/modprobe.d/blacklist
exit
```

And then post the output of these commands:
```

iwconfig
ls /lib/firmware/$(uname -r)/acx/1.0.9
iwlist wlan0 scan
cat /etc/modprobe.d/blacklist
```

Also, the card definitely worked when you first installed Ubuntu, right?  i.e. you were able to connect to networks and load web pages?

---

### Post by Cup of Squirrels on 2008-06-07
Yes, the card worked without much effort, allowing me to browse the internet with the firefox client.

It's important to note that initially I had some difficulty, as network manager would keep locking up the entire OS whenever I attempted to connect (A problem other users experienced), and so I had to enter the details through the terminal with iwconfig. I initiated the connection by making the card get an ip from the DHCP configuration with "sudo dhclient wlan0", which usually sends the packet and immediately receives the sufficient data, allowing me to browse the web, download packages through the terminal etc.


However, as I stated, when I installed the graphics card drivers, the card then had no drivers for some reason, forcing me to use ndiswrapper.

Anyway, I typed in the commands as you requested, and here are the outputs from the second lot of commands you asked for:

iwconfig

```
wlan0     IEEE 802.11b  ESSID:"BTHomeHub-8937"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power:0 dBm   Sensitivity=1/3  
          RTS thr=2432 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:45/100  Signal level:-67 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```



ls /lib/firmware/2.6.24-18-generic/acx/1.0.9

```
ls: cannot access /lib/firmware/2.6.24-18-generic/acx/1.0.9: No such file or directory

```


iwlist wlan0 scan

```
wlan0     Scan completed :
          Cell 01 - Address: 00:14:7F:38:4D:3E
                    ESSID:"BTHomeHub-8937"
                    Protocol:IEEE 802.11FH
                    Mode:Managed
                    Channel:0
                    Quality:100  Signal level:0  Noise level:160
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=0
                    Extra:atim=0
          Cell 02 - Address: 02:14:7F:38:4D:3F
                    ESSID:"BTOpenzone"
                    Protocol:IEEE 802.11FH
                    Mode:Managed
                    Channel:0
                    Quality:100  Signal level:0  Noise level:160
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=0
                    Extra:atim=0
```


cat /etc/modprobe.d/blacklist

```
cat /etc/modprobe.d/blacklist

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

blacklist ndiswrapper

```


Please say if I entered the incorrect firmware directory; although, I did poke about /lib/firmware/ and could not find any sort of acx file or folder myself, though it was just a brief scan.

Also, I am not sure what exactly BTOpenZone is - a neighbour's network perhaps - I have attempted to connect to that, but again it yielded no success.


Sorry for the late response, it was getting late over here and I decided to call it a night ;)

Thankyou very much for your help, I look forward to your next response!

---

### Post by pytheas22 on 2008-06-07
Thanks again for the information.  The potential source of your problem is that your card is in 11b mode, which would explain why it's not seeing your home network, which is probably on 11g mode (almost all are these days; you can access your router's configuration page to check).  Try running:
```

sudo iwpriv wlan0 mode 11g
```

and then check the output of "iwconfig" again.  You want the first line to start with "wlan0     IEEE 802.11g ..." not "wlan0     IEEE 802.11b."  Hopefully changing the mode will be as simple as using the command above; different kinds of cards require different procedures, however, so I'm not sure.  If it doesn't work for your acx chipset, we can figure out what does.

A second problem is that you don't seem to have the firmware where it should be.  To see if it exists at all, please post the output of:
```

ls -R /lib/firmware/$(uname -r)
```

I have the acx firmware on my machine, which has never come close to a wireless card with an acx chipset, so apparently the acx firmware should come by default with every Ubuntu system.  If yours got lost somehow, that would explain a lot, but so would the 11b mode issue.  Once we deal with both of these things, you should be all set.

Also, you're running Ubuntu 8.04 (Hardy Heron), right?

---

### Post by chili555 on 2008-06-07
> sudo iwconfig wlan0 mode 11gI think 'mode' is for *managed, monitor,* etc. What is 11g?

I might want a bit more Tx-power than zero, so please try:```
sudo iwconfig wlan0 txpower 20
```You might play around with the '20' until you get good connectivity yet the card does not run hot.

---

### Post by pytheas22 on 2008-06-07
> I think 'mode' is for managed, monitor, etc. What is 11g?

Thanks for the correction; you're right.  I was mistaking iwconfig for iwpriv.  I'll edit my post above.  iwpriv changes the 802.11x mode of the card, at least with my Atheros drivers, e.g.:
```

iwpriv ath0 mode 11g
```

I'm doubtful that this works on other chipsets, however, as Atheros usually does stuff in non-standard ways.

---

### Post by Cup of Squirrels on 2008-06-07
Hi there folks


A slight realisation and hitch I noticed in my previous response after adding ndiswrapper to my blacklist - it was only after rebooting that I discovered the blacklisting came into effect. This mean that the wireless drivers are now unclaimed again.

Sorry if this has skewed your response ><


Anyway, I tried starting ndiswrapper again (It is still blacklisted) for that session, and tried the iwprive wlan0 mode 11g - this however gave me a "mode command not recognised" echo.


Also, here is my firmware directory:

ls -R /lib/firmware/2.6.24-18-generic

```
/lib/firmware/2.6.24-18-generic:
aic94xx-seq.fw                      ipw2200-sniffer.fw
atmel_at76c502_3com.bin             isl3877
atmel_at76c502_3com-wpa.bin         isl3886
atmel_at76c502.bin                  isl3887usb_bare
atmel_at76c502d.bin                 isl3890
atmel_at76c502d-wpa.bin             isl3890usb
atmel_at76c502e.bin                 iwlwifi-3945-1.ucode
atmel_at76c502e-wpa.bin             iwlwifi-3945.ucode
atmel_at76c502-wpa.bin              iwlwifi-4965-1.ucode
atmel_at76c503-i3861.bin            iwlwifi-4965.ucode
atmel_at76c503-i3863.bin            ql2100_fw.bin
atmel_at76c503-rfmd-0.90.2-140.bin  ql2200_fw.bin
atmel_at76c503-rfmd-acc.bin         ql2300_fw.bin
atmel_at76c503-rfmd.bin             ql2322_fw.bin
atmel_at76c504_2958-wpa.bin         ql2400_fw.bin
atmel_at76c504a_2958-wpa.bin        rt2561.bin
atmel_at76c504.bin                  rt2561s.bin
atmel_at76c504c-wpa.bin             rt2661.bin
atmel_at76c505a-rfmd2958.bin        rt73.bin
atmel_at76c505-rfmd2958.bin         v4l-cx2341x-dec.fw
atmel_at76c505-rfmd.bin             v4l-cx2341x-enc.fw
atmel_at76c506.bin                  v4l-cx2341x-init.mpg
atmel_at76c506-wpa.bin              v4l-cx25840.fw
ipw2100-1.3.fw                      v4l-pvrusb2-24xxx-01.fw
ipw2100-1.3-i.fw                    v4l-pvrusb2-29xxx-01.fw
ipw2100-1.3-p.fw                    zd1201-ap.fw
ipw2200-bss.fw                      zd1201.fw
ipw2200-ibss.fw                     zd1211

/lib/firmware/2.6.24-18-generic/zd1211:
zd1211b_ub   zd1211b_uphm  zd1211b_ur  zd1211_uph   zd1211_uphr
zd1211b_uph  zd1211b_uphr  zd1211_ub   zd1211_uphm  zd1211_ur
```


And yes, I am using the latest 8.04 Hardy Ubuntu.


edit: I also played about with txpower, but I didn't seem to get any results (After each change to txpower, iwconfig's overview still stated the card was giving out 0 dbm anyway).

---

### Post by pytheas22 on 2008-06-07
Yeah, you're definitely missing the firmware directories that should be there.  I can copy my /acx firmware and give it to you if you're running a 64-bit kernel, but if you're on 32-bit, that wouldn't work.

Another thing that I've just realized that you may want to keep in mind is that the acx driver isn't going to support WPA, apparently.  If you need to use WPA, ndiswrapper is the only answer, so let us know.

Otherwise, for the time being, the only thing I can recommend is to do this:

1. unplug your wireless card
2. run and post the output of:
```

sudo modprobe --verbose acx
```
3. plug the card back in
4. post the output of:
```
dmesg | grep acx
```

this should give a better idea of why the acx driver isn't working or doesn't want to recognize your card.

I also admit that I'm a little perplexed by what's going on...I don't know how the firmware directories could have just disappeared, and if dmesg doesn't provide useful information, I don't really know where to look next.  I thought that the problem would have been clearer by this point.  So depending on how much trouble you had getting Ubuntu installed the first time, it could make more sense now to just do a reinstall.  I don't know how you configured the nvidia driver the first time, but if you use [envy]("http://www.albertomilone.com/nvidia_scripts1.html"), it's really easy, and I'm happy to help there (where fortunately I have my experience than with acx wireless cards).

---

### Post by Cup of Squirrels on 2008-06-07
Sadly no, I do not use a 64-bit CPU =P

Before I go through the process of plugging and unplugging my card etc, could you recommend anywhere that I could obtain the 32bit firmware drivers for my acx chipset? Google doesn't exactly yield many helpful results.

Failing that, I think I will take your latter advice and simply reinstall (And hope my graphics drivers installation will go a little smoother this time round ;p)

---

### Post by pytheas22 on 2008-06-07
> Before I go through the process of plugging and unplugging my card etc, could you recommend anywhere that I could obtain the 32bit firmware drivers for my acx chipset?

The quickest way that I can think of is to boot to the Ubuntu live CD and browse to the /lib/firmware/<kernel> directory of the live session.  Make an archive of the acx subdirectory (you can make an archive by right clicking the acx folder and selecting "Create Archive"--use whichever compression scheme you like the most).  Then save it to your hard drive, a USB stick or whatever's handy, or email it to yourself (it's only 1.2 megabytes on my machine).  Then simply unpack and copy it into the appropriate place in /lib/firmware on your installed Ubuntu system.  In principle this should all work.

---

### Post by chili555 on 2008-06-07
The acx firmware is found in linux-restricted-modules. If you installed the kernel specific package, it may have not upgraded the package when you got a new kernel. If you do:```
sudo apt-get install linux-restricted-modules-generic
```It will install the version matching your kernel _and_ update it when a new kernel is installed.

---

### Post by Cup of Squirrels on 2008-06-08
Hi there guys

After trying both of your suggestions with no avail, I decided to do a fresh reinstall. Oddly enough, once I came back to the fresh system, I still had issues with the network until I uninstalled network-manager again - I can now happily connect to the internet through the terminal and iwconfig. Odd stuff.

Anyway, all that remains now is for me to try and get these video drivers working again, hopefully without destroying my drivers this time ;)


Thanks for all your help.

---

### Post by akhtet on 2008-06-08
Just saying that I could successfully use my wireless card Netgear Wg511v2 card using Ndiswrapper. I had troubles and hassles installing this with the previous releases (such as adding prism54 to the blacklist). Now all I needed to do is install 3 packages, ndiswrapper-commons, ndiswrapper-utils, and ndis-gtk, and then install the INF file , then the card flashes.

---

### Post by pytheas22 on 2008-06-08
> Anyway, all that remains now is for me to try and get these video drivers working again, hopefully without destroying my drivers this time

Sorry the process got so messy--I thought we could have figured out what was going on much more easily--but at least you're back with a fresh system.  As I mentioned before, I highly recommend trying envy to get your nvidia card working.  Just run:
```

sudo apt-get install envyng-gtk
```

and after it finishes installing, run envy with:
```

sudo envyng
```

It has a nice graphical interface and has never failed me in getting nvidia cards configured properly.

---

