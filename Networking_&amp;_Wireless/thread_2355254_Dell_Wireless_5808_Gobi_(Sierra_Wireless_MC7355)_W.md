---
title: "Dell Wireless 5808 Gobi (Sierra Wireless MC7355) WWAN Driver"
date: 2017-03-10
forum: Networking &amp; Wireless
---

### Post by johnathanamber on 2017-03-10
Hey all,

Has anyone been able to get the Dell Wireless 5808 Gobi WWAN card working?

I can see that if I run ```
LSHW
``` I can see it as an USB device (Dell Wireless 5808 Gobi using driver "cdc-mbim"), but it doesn't show in ```
LSUSB
``` or ```
LSPCI
```. Ideas?

On top of that, I can't seem to find any drivers for Sierra Wireless cards specifically.

I do know that it is physically connected and work since I am dual booting Windows 10 and use it.

Thanks everyone!

---

### Post by jeremy31 on 2017-03-10
Please post the results of the terminal commands that you have listed.

---

### Post by johnathanamber on 2017-03-14
@jeremy31,

Thanks for the reply. On top of the Sierra Wireless Dell Gobi device, I need to get the drivers for my Wifi card as well.

Here are the results (Apologies, but the length gave me an error, thus I had to use the Ubuntuforums paste link.):
**LSHW**
[https://paste.ubuntu.com/24176693/](https://paste.ubuntu.com/24176693/)

**LSPCI**
[https://paste.ubuntu.com/24176698/](https://paste.ubuntu.com/24176698/)

**LSUSB**
[https://paste.ubuntu.com/24176737/](https://paste.ubuntu.com/24176737/)

The help is much appreciated.

---

### Post by chili555 on 2017-03-14
It clearly shows is *lsusb*:```
Bus 003 Device 003: ID 413c:81a8 Dell Computer Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x413c Dell Computer Corp.
  idProduct          0x81a8 
  bcdDevice            0.06
  iManufacturer           1 Sierra Wireless, Incorporated
  iProduct                2 [COLOR="#FF0000"]Dell Wireless 5808 Gobi™ 4G LTE Mobile Broadband Card[/COLOR]
  iSerial                 3 
  bNumConfigurations      2
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          204
    bNumInterfaces          4
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              500mA
<snip>
```It appears, from *lshw*, to have a driver; cdc_mbim. Are there any clues in the log?```
dmesg | grep cdc
```

---

### Post by johnathanamber on 2017-03-15
@chili555,

Thanks for the reply.

Here are the results of the command given:
```

[    5.624477] usbcore: registered new interface driver cdc_ncm
[    5.625709] usbcore: registered new interface driver cdc_wdm
[    5.675036] cdc_mbim 3-10:2.12: cdc-wdm0: USB WDM device
[    5.675250] cdc_mbim 3-10:2.12 wwan0: register 'cdc_mbim' at usb-0000:00:14.0-10, CDC MBIM, 8a:64:ac:f6:1b:b5
[    5.675284] usbcore: registered new interface driver cdc_mbim
[    5.871623] cdc_mbim 3-10:2.12 wwp0s20u10c2i12: renamed from wwan0

```

---

### Post by chili555 on 2017-03-15
> [    5.871623] cdc_mbim 3-10:2.12 wwp0s20u10c2i12: renamed from wwan0You have an interface name. Are there any further clues in the log?```
dmesg | grep wwp
```When you click the Network Manager icon, does any reference to the device or WWAN in general appear? What does this tell us?```
cat /avr/log/syslog | grep etwork | tail -n20
```As the result will be lengthy, 20 lines, paste the result here and give us the link: [http://paste.ubuntu.com](http://paste.ubuntu.com)

---

### Post by johnathanamber on 2017-03-20
@chili555,

Here are the results:
[http://paste.ubuntu.com/24218759/](http://paste.ubuntu.com/24218759/)

---

### Post by johnathanamber on 2017-03-25
@chili555,

It didn't show up on the list. When adding a mobile broadband connection, it doesn't ask which device to use.

---

### Post by chili555 on 2017-03-25
Is it by chance soft blocked?```
rfkill list all
```If it is, does it help to do:```
sudo rfkill unblock all
rfkill list all
```Is WWAN enabled in Network Manager?```
cat -s /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by johnathanamber on 2017-03-26
@chili555,

Oddly enough, once I restarted again, it connected. All I've done thus far is check logs, etc. as you've suggested. Thank you for the help.

But, to answer your questions:
```

$ rfkill list all
1: dell-wifi: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: dell-bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no

```

I didn't run the 'unblobk' command as it didn't seem needed. But, here is the last command:
```

$ cat -s /var/lib/NetworkManager/NetworkManager.state
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

```

Is there a way to see if the previous "WWANEnabled" was disabled previously for not?

Again, Thanks for all of the help. I'm not sure why it is working now and not before as nothing was changed, etc.

---

### Post by chili555 on 2017-03-26
> Oddly enough, once I restarted again, it connected.Awesome, glad it's working.>  Is there a way to see if the previous "WWANEnabled" was disabled previously for not?  None that I know of.

Literally, all I know about WWAN is the usual stuff, if there is a driver and it isn't switched off, it ought to work. I'm happy that my first WWAN case accidentally turned out successfully.

---

### Post by johnathanamber on 2017-04-01
@chili555,

Hmm, for some reason, I can't get it to connect again. Is there a command to get the Mobile Broadband device to force connect to T-Mobile?

Also, when I check the "rfkill list all", I see that some devices are disabled. I then do the "sudo rfkill unblock all" to unblock them. Can this be cone automatically during boot?

Your advice is much appreciated.

---

