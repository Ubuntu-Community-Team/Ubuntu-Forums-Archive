---
title: "Help with installing a new Broadcom WiFi module"
date: 2015-03-23
forum: Networking &amp; Wireless
---

### Post by lucian-iuga-gmail on 2015-03-23
Hi everybody!

I need some help with a topic that is beyond my knowledge.

I took a WiFi module out of a broken printer. I had the nice surprise that it was actually a USB interface so I said let's try to make it work. I made a cable for it and connected it to my PC and it is recognized. *lsusb* says:

```
Bus 002 Device 005: ID 0a5c:bd16 Broadcom Corp.
```

I really want to make it work under Linux. Ubuntu on a laptop is just the first step for me (I use 14.04). The end goal is to make it work with a Raspberry Pi.

I searched the web up and down but did not find a solution. It shows up under the USB ID list that's on the web as [COLOR=#000000]**bd16  BCM4319 802.11bgn Wireless Adapter** ([link]("http://www.linux-usb.org/usb.ids")). It also shows up in this list: [/COLOR][https://wikidevi.com/wiki/Broadcom](https://wikidevi.com/wiki/Broadcom)

By using this last link, I arrived to [this page ]("http://wikidevi.com/wiki/Brother_T77H228")with a suggestion that actually allowed me to find a driver for Windows Vista. And it worked.

This leads me to believe that there should be a method also under Linux, but the method to do that is currently beyond my skills. I tried all kinds of combinations with the Broadcom STA driver, with brcmfmac and various firmwares, but I was just shooting in the dark. Nothing came out of it.

I would like to avoid ndiswrapper, firstly because it looks really complicated (not that I am afraid of that, but I have the feeling that with the same kind of effort I may be able to get a proper driver working, which would be more efficient) and also is not supported by Openelec for Raspberry Pi.

I am thinking the driver is in one of those packages, but just does not associate with the HID:PID. But I don't know how to proceed further.

Can anyone suggest anything? I can provide any further information you think is necessary.

---

### Post by wildmanne39 on 2015-03-23
I do not have much time these days so I will give it one shot, usually broadcom usb adaptors need ndiswrapper but with the adaptor plugged in run the wireless script in my signature and post the results here between code tags or as an attachment.
Thanks

---

### Post by Hadaka on 2015-03-23
Hi, from a working wired connection (Ethernet) please do..
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source #Ignore any errors form this line
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```
Ignore any offer of proprietary or additionall drivers.

---

### Post by wildmanne39 on 2015-03-23
Hi Hadaka, I suspect that there is a small possiblity that might work but I just wanted to see all the other drivers he has installed first.
I figure since it is an usb device that the usb id will need to be added to the file then recompile the driver but not sure that would work either and I sure do not have the time to do that if needed.
I will just watch and hope it works the first time.

---

### Post by lucian-iuga-gmail on 2015-03-24
Hi!

Thanks for helping me! Let's take things one at a time. Firstly, here is the output of dmesg when I connect the device. You will see there is no driver loaded.

```
[  299.948237] usb 1-4: new high-speed USB device number 2 using ehci-pci
[  300.083970] usb 1-4: New USB device found, idVendor=0a5c, idProduct=bd16
[  300.083980] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  300.083987] usb 1-4: Product: Remote Download Wireless Adapter
[  300.083992] usb 1-4: Manufacturer: Broadcom
[  300.083998] usb 1-4: SerialNumber: 000000000001

```
Secondly, Wild Man, please find attached the output of the script. You will notice a wlan0 network in there, which is the embedded module from the laptop. For the one I am trying to run, no driver whatsoever seems to be loading.
[ATTACH]260879[/ATTACH]

Next, Hadaka, I also followed your instructions, but nothing seems to happen. At the end, I can see this:

```
$ lsmod | grep b43
b43                   356470  0 
bcma                   42043  1 b43
ssb                    51854  1 b43
mac80211              546067  3 b43,iwl4965,iwlegacy
cfg80211              409394  4 b43,iwl4965,iwlegacy,mac80211

$ dmesg | tail
[  792.756678] Broadcom 43xx driver loaded [ Features: PNL ]
[  801.448596] usb 1-4: USB disconnect, device number 2
[  806.784239] usb 1-4: new high-speed USB device number 3 using ehci-pci
[  806.920121] usb 1-4: New USB device found, idVendor=0a5c, idProduct=bd16
[  806.920131] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  806.920138] usb 1-4: Product: Remote Download Wireless Adapter
[  806.920144] usb 1-4: Manufacturer: Broadcom
[  806.920149] usb 1-4: SerialNumber: 000000000001

```



From what I had read, though, the b43 driver is supposed to only work with PCI cards, unless I am not mistaken.

Also, I am not able to see anything about this in additional drivers. It shows up as an unrecognized device. I had also read various instructions about b43, brcmfmac and the like and its HID : PID combination was not present in any of them, so I guess the current behavior is actually expected. But I am hoping it may be just a simple matter of associating its HID : PID with one of the already existing drivers. But that is advanced knowledge, afaict.

One reason why I think it may be easy is the following reasoning. Here is a list of the files in the driver that works on Windows:

```
-rwxrwxrwx 2 root root  10K Apr 10  2011 [B]bcmh43xx64.cat
[/B]-rwxrwxrwx 1 root root 9.2K Apr 10  2011 **bcmh43xx.cat**
-rwxrwxrwx 2 root root 3.8M Mar 29  2011 bcmihvsrv64.dll
-rwxrwxrwx 2 root root 3.7M Mar 29  2011 bcmihvsrv.dll
-rwxrwxrwx 2 root root 3.5M Mar 29  2011 bcmihvui64.dll
-rwxrwxrwx 1 root root 3.4M Mar 29  2011 bcmihvui.dll
-rwxrwxrwx 2 root root  94K Mar 29  2011 bcmwlcoi64.dll
-rwxrwxrwx 1 root root  90K Mar 29  2011 bcmwlcoi.dll
-rwxrwxrwx 2 root root 1.2M Mar 29  2011 bcmwlhigh664.sys
-rwxrwxrwx 2 root root 677K Aug 27  2013 bcmwlhigh6.inf
-rwxrwxrwx 2 root root 1.1M Mar 29  2011 bcmwlhigh6.sys
-rwxrwxrwx 2 root root 1.7M Jun 10  2010 WdfCoInstaller0100964.dll
-rwxrwxrwx 2 root root 1.4M Jun 10  2010 WdfCoInstaller01009.dll

```

What I can see here is a bunch of DLLs, sys and inf files, which are for Windows, and those .cat files, which I am therefore assuming contain the firmware. A similar file is also present in /lib/firmware/brcm. There is a huge difference of size between them, so I may be way off, but maybe not...

```
/lib/firmware/brcm$ ls -lh
total 4.4M
-rw-r--r-- 1 root root 264K Nov 24 16:42 bcm4329-fullmac-4.bin
-rw-r--r-- 1 root root  94K Dec  1 16:16 **bcm43xx-0.fw**
-rw-r--r-- 1 root root  180 Dec  1 16:16 bcm43xx_hdr-0.fw
-rw-r--r-- 1 root root 388K Dec  1 16:16 brcmfmac43143.bin
-rwxr-xr-x 1 root root 377K Dec  1 16:16 brcmfmac43143-sdio.bin
-rw-r--r-- 1 root root 340K Nov 24 16:42 brcmfmac43236b.bin
-rw-r--r-- 1 root root 446K Dec  1 16:16 brcmfmac43241b0-sdio.bin
-rw-r--r-- 1 root root 395K Dec  1 16:16 brcmfmac43241b4-sdio.bin
-rw-r--r-- 1 root root 248K Dec  1 16:16 brcmfmac4329-sdio.bin
-rw-r--r-- 1 root root 217K Dec  1 16:16 brcmfmac4330-sdio.bin
-rw-r--r-- 1 root root 441K Dec  1 16:16 brcmfmac4334-sdio.bin
-rw-r--r-- 1 root root 556K Dec  1 16:16 brcmfmac4335-sdio.bin
-rw-r--r-- 1 root root 215K Dec  1 16:16 brcmfmac43362-sdio.bin
-rw-r--r-- 1 root root 496K Dec  1 16:16 brcmfmac4354-sdio.bin

```

---

### Post by lucian-iuga-gmail on 2015-03-24
PS:

I also found some references to apparent drivers for the same BCM4319 chipset, at these locations:

[https://github.com/omegamoon/Rockchip-GPL-Kernel/tree/master/drivers/net/wireless/bcm4319](https://github.com/omegamoon/Rockchip-GPL-Kernel/tree/master/drivers/net/wireless/bcm4319)

[https://github.com/xndcn/veer-wifi-helper](https://github.com/xndcn/veer-wifi-helper)

[https://github.com/wendal/rk2918_uzone_f0_top/tree/master/drivers/net/wireless/bcm4319](https://github.com/wendal/rk2918_uzone_f0_top/tree/master/drivers/net/wireless/bcm4319)

But I am not sure what it means... Not sure it is the same chipset. Or, if it is perhaps a non-usb version of it...

---

### Post by wildmanne39 on 2015-03-24
If this can be made to work you will have to use ndiswrapper or compile a driver from source after making changes to some files but I do not have enough time and experience to help you with that. I have only seen usb broadcom adaptors work with ndiswrapper and I beleive that is your only option.
You have to use windows xp driver files.

---

### Post by lucian-iuga-gmail on 2015-03-24
I was afraid you were gonna say that.  :) 

Well,  I'd love to learn how to do that, but I need some guidance. Perhaps I will get lucky and someone will stumble across this who knows. 

Thanks for your help, though!

---

### Post by wildmanne39 on 2015-03-24
Some where around the 27th of this month chili555 will be back and he is the person for this issue.

---

### Post by lucian-iuga-gmail on 2015-03-25
OK. Let's hope he stumbles over this thread, then.

---

### Post by lucian-iuga-gmail on 2015-03-29
Is there any way to draw the attention of [COLOR=#000000]chili555 to this post?[/COLOR]

---

### Post by chili555 on 2015-03-29
> **lucian-iuga-gmail said:**
> Is there any way to draw the attention of [COLOR=#000000]chili555 to this post?[/COLOR]I am here, finally! Cold, wet and broke, but I'm here.

I also think ndiswrapper is your best chance. I suggest you install it first:```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```Next, ndiswrapper requires Windows XP (not Vista, not 7, not 3.1, etc.) .inf and .sys files. 

Moreover, it usually requires files appropriate to your architecture; either 32- or 64-bit. Find out:```
arch
```As you may suspect, these are the needed files, if they are XP:```
-rwxrwxrwx 2 root root 1.2M Mar 29  2011 bcmwlhigh6[COLOR="#FF0000"]64[/COLOR].sys
-rwxrwxrwx 2 root root 677K Aug 27  2013 bcmwlhigh6.inf
-rwxrwxrwx 2 root root 1.1M Mar 29  2011 bcmwlhigh6.sys
```Do you have the XP files on your Windows install? I suggest you copy them to the desktop of your Ubuntu machine and we'll proceed.

---

### Post by lucian-iuga-gmail on 2015-03-31
Hi!

Thanks for the tips. So I tried that, but didn't seem to work. Unfortunately I am at work now so I will tell the story from memory.

I installed ndiswrapper and I was able to load the inf for XP for my architecture. And then ndiswrapper was even reporting that it was seeing the hardware connected.

But then that was it. Whenever I was connecting the hardware, dmesg would show the same list of events as before

```
$ dmesg | tail
[  792.756678] Broadcom 43xx driver loaded [ Features: PNL ]
[  801.448596] usb 1-4: USB disconnect, device number 2
[  806.784239] usb 1-4: new high-speed USB device number 3 using ehci-pci
[  806.920121] usb 1-4: New USB device found, idVendor=0a5c, idProduct=bd16
[  806.920131] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  806.920138] usb 1-4: Product: Remote Download Wireless Adapter
[  806.920144] usb 1-4: Manufacturer: Broadcom
[  806.920149] usb 1-4: SerialNumber: 000000000001
```

There was no mention of loading a driver or whatever. And I think it should show something like that.

Of course, I would not get any connection.

I understand there is also some configuration to do in network management, because ndiswrapper does not work with the nm in Ubuntu.

But I think that from what I can see in dmesg, we are not at that step yet, right?

In any case, is there no chance to try a native driver? As I said, I would like to run this on Raspberry Pi later, which I am pretty sure excludes ndiswrapper. Funny thing is that in Windows you can try to force a driver on a piece of hardware (it's how I got it to work in Vista, because it would not load the driver automatically), but it does not seem possible in Linux.  :)

---

### Post by chili555 on 2015-03-31
> because ndiswrapper does not work with the nm in Ubuntu.That is not true. If ndiswrapper is working correctly, NM will show and allow connection to networks the same as any native driver.

Let's do some diagnostics. From a terminal:```
sudo modprobe ndiswrapper
ndiswrapper -l
dmesg | grep ndis
```> [  792.756678] Broadcom 43xx driver loaded [ Features: PNL ]
[  801.448596] usb 1-4: USB disconnect, device number 2
[  806.784239] usb 1-4: new high-speed USB device number 3 using ehci-pci
[  806.920121] usb 1-4: New USB device found, idVendor=0a5c, idProduct=bd16
[  806.920131] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  806.920138] usb 1-4: Product: Remote Download Wireless Adapter
[  806.920144] usb 1-4: Manufacturer: Broadcom
[  806.920149] usb 1-4: SerialNumber: 000000000001There is nothing unusual here except the absence of ndiswrapper grabbing the device and running.

---

### Post by lucian-iuga-gmail on 2015-04-13
Hi!

Sorry for the delay, I was out of town.

I followed the instructions and there is indeed progress.

When I connect the dongle now, I see this:

```
$ dmesg | tail
[  801.236929] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fb7fcc80, 16000, 5
[  801.236932] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fb800b00, 16000, 5
[  801.236935] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fb804980, 16000, 5
[  801.236938] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fb808800, 16000, 5
[  801.236942] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fb80c680, 16000, 5
[  801.253455] ndiswrapper (ndis_encode_setting:383): unknown type: 3
[  801.584092] wlan1: ethernet device c0:d9:62:84:d3:27 using NDIS driver: bcmwlhigh5, version: 0x564442e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0A5C:BD16.F.conf
[  801.592853] wlan1: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[  801.619923] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  801.620312] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready



```

To me it looks close but not quite there. Obviously, I do not have a connection in the end.

Still hoping for a native solution, that I can use on Rpi though. :)

---

### Post by chili555 on 2015-04-13
> Still hoping for a native solutionI never say never, but I suspect not in this decade. Broadcom has been quite supportive of PCI wireless devices and, as far as I have ever seen, not at all supportive of USB devices. I suspect, but don't know for sure, that Broadcom sells branded PCI cards to others, Dell, Apple, et al. The USBs are all branded by others, Netgear, NetComm, etc. Netgear, for example, is not at all supportive of Linux. 

[ATTACH=CONFIG]261255[/ATTACH]

May we see:```
ndiswrapper -l
rfkill list all
```Thanks.

---

### Post by lucian-iuga-gmail on 2015-04-14
> [COLOR=#000000]I never say never, but I suspect not in this decade.[/COLOR]

Well, that's encouraging.  :)))

I see what you mean, since I scavenged this out of a printer, so it is definitely an OEM unit. On the other hand, it was not supposed to be supported under Windows either. The driver I used is ostensibly for another chipset, but I forced it on the device and it worked. I was thinking about doing the same under Linux. Can't we find out if there is a native Linux driver for the same chipset, then use that one?

But since getting it to work with ndiswrapper would still be progress, here is the info:

```
$ ndiswrapper -l
bcmwlhigh5 : driver installed
    device (0A5C:BD16) present
$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by chili555 on 2015-04-14
> The driver I used is ostensibly for another chipset, but I forced it on the device and it worked.Which one? How did you force it? I have done a bit of 'forcing' in my work in Ubuntu and I'm interested in your process.> Can't we find out if there is a native Linux driver for the same chipset, then use that one?The usual process is to Google the usb.id, in your case, 0A5C:BD16:> Bus 002 Device 005: ID [COLOR="#FF0000"]0a5c:bd16[/COLOR] Broadcom Corp.Google away and I'm confident you'll find what I found: nothing. This is probably the most promising: [https://wikidevi.com/wiki/NetComm_NP920](https://wikidevi.com/wiki/NetComm_NP920) However, it says:> Probable Linux driver
noneIs this where you got the driver files? [http://www.netcommwireless.com/product/wifi/np920](http://www.netcommwireless.com/product/wifi/np920) If your bcmwlhigh5.inf isn't the same, I might try those instead.

---

### Post by lucian-iuga-gmail on 2015-04-14
> [QUOTE]The driver I used is ostensibly for another chipset, but I forced it on the device and it worked.

[COLOR=#000000]Which one? How did you force it? I have done a bit of 'forcing' in my work in Ubuntu and I'm interested in your process.[/COLOR][/QUOTE][COLOR=#000000]

I don't remember all the details, but it is pretty straightforward. You see the device in the Device Manager as unrecognized. You right-click and select Update Driver and then you just follow the steps that make sense. Firstly, you have an option to automatically search for or manually select the driver and choose the latter. Then, it asks whether you want to select the device from a list or select a specific driver. If you choose the latter, it will let you choose the .inf file of the driver from wherever. And then you keep your fingers crossed. :) Something like that.

I don't have access to my Windows machine right now, but if you need more details, I can come back with them in a day or so.

[/COLOR]> [COLOR=#000000]The usual process is to Google the usb.id, in your case, 0A5C:BD16:[/COLOR]

The thing is I googled the hell out of this topic before I came to post it here. I already knew there would be no easy way to do this and would probably require some hacking, but I needed some direction. I am prepared to add a few lines of code and build a new driver if needed, which is why I am hoping it is possible to use an already existing driver, by making it handle this USB ID. But if hacking goes beyond adding the USB ID to a list, that would be too much beyond my skills to even try.

For the Windows driver, I got the tip from here:

[https://wikidevi.com/wiki/Brother_T77H228](https://wikidevi.com/wiki/Brother_T77H228)

I noticed it says "nothing" under probable Linux driver, but I was hoping that was just because nobody cared enough to go deep into the topic. :)

Another thing that strikes me as a bit odd is that I also found some references to Linux drivers for a Broadcom chipset with the same name BCM4319 in a few places around the web. It should be the same one, since I doubt there are 2 chipsets with the same name, but I think these drivers are not for a USB interface to the module and I have no idea how to proceed.

[https://github.com/wendal/rk2918_uzone_f0_top/tree/master/drivers/net/wireless/bcm4319](https://github.com/wendal/rk2918_uzone_f0_top/tree/master/drivers/net/wireless/bcm4319)

[https://github.com/omegamoon/Rockchip-GPL-Kernel/tree/master/drivers/net/wireless/bcm4319](https://github.com/omegamoon/Rockchip-GPL-Kernel/tree/master/drivers/net/wireless/bcm4319)

[https://github.com/xndcn/veer-wifi-helper](https://github.com/xndcn/veer-wifi-helper)

---

### Post by chili555 on 2015-04-14
> **lucian-iuga-gmail said:**
> 
[https://github.com/wendal/rk2918_uzone_f0_top/tree/master/drivers/net/wireless/bcm4319](https://github.com/wendal/rk2918_uzone_f0_top/tree/master/drivers/net/wireless/bcm4319)

[https://github.com/omegamoon/Rockchip-GPL-Kernel/tree/master/drivers/net/wireless/bcm4319](https://github.com/omegamoon/Rockchip-GPL-Kernel/tree/master/drivers/net/wireless/bcm4319)

[https://github.com/xndcn/veer-wifi-helper](https://github.com/xndcn/veer-wifi-helper)None of these are able to be compiled on my 3.13.0-xx kernel. The first, I believe, is for an ARM processor, perhaps what was found in the donor printer! The second is written for a 3.0 kernel and, by me, indecipherable! The third appears to be written for a Palm device!!! 

The bcmwlhigh5.inf you downloaded is newer than the one I linked above. I'd think it has a better chance of working.

What does the system log tell us?```
cat /var/log/syslog | grep -e wlan1 -e ndis | tail -n20
```

---

### Post by lucian-iuga-gmail on 2015-04-15
Here it is.

```
$ cat /var/log/syslog | grep -e wlan1 -e ndis | tail -n20
Apr 15 13:49:53 pestisor kernel: [46111.764558] wlan1: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
Apr 15 13:49:53 pestisor kernel: [46111.767226] usbcore: registered new interface driver ndiswrapper
Apr 15 13:49:53 pestisor NetworkManager[777]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.0/net/wlan1, iface: wlan1)
Apr 15 13:49:53 pestisor NetworkManager[777]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.0/net/wlan1, iface: wlan1): no ifupdown configuration found.
Apr 15 13:49:53 pestisor NetworkManager[777]: <info> (wlan1): driver does not support SSID scans (scan_capa 0x00).
Apr 15 13:49:53 pestisor NetworkManager[777]: <info> (wlan1): using WEXT for WiFi device control
Apr 15 13:49:53 pestisor NetworkManager[777]: <info> (wlan1): new 802.11 WiFi device (driver: 'ndiswrapper' ifindex: 4)
Apr 15 13:49:53 pestisor NetworkManager[777]: <info> (wlan1): exported as /org/freedesktop/NetworkManager/Devices/2
Apr 15 13:49:53 pestisor NetworkManager[777]: <info> (wlan1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 15 13:49:53 pestisor NetworkManager[777]: <info> (wlan1): bringing up device.
Apr 15 13:49:53 pestisor NetworkManager[777]: <info> (wlan1): preparing device.
Apr 15 13:49:53 pestisor NetworkManager[777]: <info> (wlan1): deactivating device (reason 'managed') [2]
Apr 15 13:49:53 pestisor kernel: [46111.921448] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
Apr 15 13:49:53 pestisor kernel: [46111.921879] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
Apr 15 13:49:54 pestisor NetworkManager[777]: <info> (wlan1) supports 1 scan SSIDs
Apr 15 13:49:54 pestisor NetworkManager[777]: <info> (wlan1): supplicant interface state: starting -> ready
Apr 15 13:49:54 pestisor NetworkManager[777]: <info> (wlan1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Apr 15 13:49:54 pestisor NetworkManager[777]: <info> (wlan1): supplicant interface state: ready -> disconnected
Apr 15 13:49:54 pestisor NetworkManager[777]: <info> (wlan1) supports 1 scan SSIDs
Apr 15 13:50:04 pestisor NetworkManager[777]: <info> (wlan1): supplicant interface state: disconnected -> inactive

```

Funny that the drivers would be made for ARM. I thought this kind of stuff was supposed to be cross-platform. Maybe that means I get lucky and will be able to build them for Rpi. :D I will look into creating a cross-compile environment, but I will need some time for that.

In any case, I found it a bit odd that a dongle meant for embedding has a USB interface. I would have expected a simpler serial interface. I guess Linux makes many things easier that way.

---

### Post by chili555 on 2015-04-15
Actually, the syslog looks quite promising. Does the Network Manager icon pop up and tell you there are available networks? Does it scan?```
sudo iwlist wlan1 scan
```Even if it doesn't, are there any informative messages? May we see:```
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
nm-tool
```I think we're close.

---

### Post by lucian-iuga-gmail on 2015-04-15
> [COLOR=#000000]Actually, the syslog looks quite promising. 

[/COLOR]Oh, OK. See, that's why you need a knowledgeable person for such things. :)

Here goes

```
$ sudo iwlist wlan1 scan
wlan1     Interface doesn't support scanning.

```

```
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

```
$ cat /etc/NetworkManager/NetworkManager.conf


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


no-auto-default=26:10:2C:85:4E:20,


[ifupdown]
managed=false
myself@pestisor:~$ nm-tool


NetworkManager Tool


State: disconnected


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:1E:68:A2:D4:F9


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl4965
  State:             unavailable
  Default:           no
  HW Address:        00:21:5C:05:E9:37


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points

```

---

### Post by chili555 on 2015-04-15
> - Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl4965
  State:             **unavailable**
  Default:           no
  HW Address:        00:21:5C:05:E9:37How is your iwl4965 unavailable? Is the switch off?```
rfkill list all
```I have seen a few cases where the wireless switch also disables any USB wireless.

---

### Post by lucian-iuga-gmail on 2015-04-16
Yes, the switch is off. I figured it would be the only way to know which WiFi module I am connected through. Weird behavior to disable also USB dongles...

Here is what happens when the switch is on:

```
$ dmesg | tail
[ 9818.478657] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f975d980, 16000, 5
[ 9818.478663] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9761800, 16000, 5
[ 9818.478668] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9765680, 16000, 5
[ 9818.499507] ndiswrapper (ndis_encode_setting:383): unknown type: 3
[ 9818.827815] wlan1: ethernet device c0:d9:62:84:d3:27 using NDIS driver: bcmwlhigh5, version: 0x564442e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0A5C:BD16.F.conf
[ 9818.835504] wlan1: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[ 9818.838819] usbcore: registered new interface driver ndiswrapper
[ 9818.895085] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 9818.895612] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 9824.984057] mce: [Hardware Error]: Machine check events logged

```

```
$ rfkill list all0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:a2:d4:f9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3365 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3365 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:465175 (465.1 KB)  TX bytes:465175 (465.1 KB)


wlan0     Link encap:Ethernet  HWaddr 00:21:5c:05:e9:37  
          inet addr:192.168.100.9  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::221:5cff:fe05:e937/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3046859 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2588311 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3255646974 (3.2 GB)  TX bytes:2352218866 (2.3 GB)


wlan1     Link encap:Ethernet  HWaddr c0:d9:62:84:d3:27  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
```
$ sudo iwlist wlan1 scan
wlan1     Scan completed :
          Cell 01 - Address: 78:1D:BA:AA:F3:59
                    ESSID:"WirelessNet"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:62/100  Signal level:-56 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 000B576972656C6573734E6574
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1ACC131BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: 0706524F20010D14

```


```
$ nm-tool


NetworkManager Tool


State: connected (global)


- Device: wlan1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             disconnected
  Default:           no
  HW Address:        C0:D9:62:84:D3:27


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    WirelessNet:     Infra, 78:1D:BA:AA:F3:59, Freq 2412 MHz, Rate 54 Mb/s, Strength 69 WPA2




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:1E:68:A2:D4:F9


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




- Device: wlan0  [WirelessNet] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl4965
  State:             connected
  Default:           yes
  HW Address:        00:21:5C:05:E9:37


  Capabilities:
    Speed:           65 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *WirelessNet:    Infra, 78:1D:BA:AA:F3:59, Freq 2412 MHz, Rate 54 Mb/s, Strength 53 WPA2


  IPv4 Settings:
    Address:         192.168.100.9
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.100.1


    DNS:             192.168.100.1
    DNS:             198.41.0.4

```

---

### Post by chili555 on 2015-04-18
Would you please temporarily blacklist the driver for the internal device and see if Network Manager starts and runs the little USB?```
sudo -i
echo "blacklist iwl4965"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot and tell us if the USB works:```
iwconfig wlan1
dmesg | grep wlan
```After we finish our experiment, remove the blacklist line:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

---

