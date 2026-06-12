---
title: "Unstable Bluetooth audio while Wifi is enabled"
date: 2020-07-09
forum: Networking &amp; Wireless
---

### Post by oak-tree on 2020-07-09
Hello everyone,


[LIST]
[*]I'm having some trouble with the BCM43142A0 chip (Toshiba Satellite Pro C70-B-13W). On my fresh 18.04 installation, I got Wifi to work with *bcmwl-kernel-source* and eventually figured out how to get the *.hex* files from the windows installation and got Bluetooth to work with *hex2hcd*. Now I've upgraded to 20.04 (in case that matters) and the issue is still the same: 
[*]Most of the time, everything works. But sometimes, the Bluetooth connection (or the audio really) skips. These interruptions seem to be connected to Wifi, since disabling it seems to eliminate the issue. 
[*]Also, when turning Wifi on/off, the Bluetooth audio interrupts for a short period. 
[*]This has never been the case on windows, so I am pretty confident that this must be a software issue. 
[*]Sometimes, web browsing (opening pages or pages updating themselves) seem to trigger the skips in the audio as well 
[/LIST]

I would be thankful for any help with troubleshooting since I have no idea what the source of the problem might be ;) 


The device's output section of *usb-devices*:
```

T:  Bus=01 Lev=02 Prnt=02 Port=05 Cnt=02 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0930 ProdID=0225 Rev=01.12
S:  Manufacturer=Broadcom Corp
S:  Product=BCM43142A0
S:  SerialNumber=645A04D4A9FA
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#=0x0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=01 Prot=01 Driver=btusb
I:  If#=0x1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=01 Driver=btusb
I:  If#=0x2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=btusb
I:  If#=0x3 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=01 Driver=(none)

```

Output of *lsusb -t*:

```

/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 5000M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/9p, 480M
    |__ Port 1: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 1: Dev 2, If 1, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 1: Dev 2, If 2, Class=Human Interface Device, Driver=usbhid, 12M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/8p, 480M
        |__ Port 5: Dev 3, If 0, Class=Video, Driver=uvcvideo, 480M
        |__ Port 5: Dev 3, If 1, Class=Video, Driver=uvcvideo, 480M
        |__ Port 6: Dev 4, If 3, Class=Application Specific Interface, Driver=, 12M
        |__ Port 6: Dev 4, If 1, Class=Vendor Specific Class, Driver=btusb, 12M
        |__ Port 6: Dev 4, If 2, Class=Vendor Specific Class, Driver=btusb, 12M
        |__ Port 6: Dev 4, If 0, Class=Vendor Specific Class, Driver=btusb, 12M


```

Output of lsmod | grep -E 'b(t|lue)' (format: Module Size  Used by)


```

btusb                  57344  0
btrtl                  24576  1 btusb
btbcm                  16384  1 btusb
btintel                24576  1 btusb
bluetooth             581632  47 btrtl,btintel,btbcm,bnep,btusb,rfcomm
ecdh_generic           16384  2 bluetooth
toshiba_bluetooth      20480  0

```

Let me know whether I should include anything else,
Thanks in advance!

---

