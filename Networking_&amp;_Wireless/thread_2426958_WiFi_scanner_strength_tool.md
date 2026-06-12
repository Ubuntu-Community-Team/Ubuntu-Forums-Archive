---
title: "WiFi scanner strength tool"
date: 2019-09-16
forum: Networking &amp; Wireless
---

### Post by Drenriza on 2019-09-16
Hi all

I run a Ubuntu installation 16.04 through Virtualbox with I3 WM as my desktop manager.
I have invested in a **_Alfa APA-M25 dual band 2.4GHz/5GHz 10dBi high gain directional indoor panel antenna with RP-SMA connector_** to locate indoor access points.

What i would ultimately really like to do, is get a list of all  available access points, select one in the list and get a full screen view of its  signal strength, so when i point my directional antenna around i can  easily see if the signal strength is going up or down
along with a decimal value, so i can determine in what direction the access point is.

A device finder feature, with a horizontal bar value as a live signal strength value.

[IMG]https://i.stack.imgur.com/IgEzC.png[/IMG]

My device is found in dmesg as a "usb 1-2" device which is a metageek WiSpy DBx with the above connected antenna.

Edit: Updated this post as i got a better idea of what i was looking for.

Thanks in advance
Best regards

---

### Post by chili555 on 2019-09-16
You might like wifi-radar or the simple command line tool:```
nmcli device wifi list
```nmcli is a snapshot and I believe wifi-radar is dynamic.

[IMG]https://wifi-radar.tuxfamily.org/images/wr-v2.x-25-main_win.png[/IMG]

---

### Post by Drenriza on 2019-09-17
Thanks for the reply @chili555 I was hoping that there was a wifi-scanner/radar program that had a more fine grained signal strength view.
What i would ultimately really like to do, is get a list of all   available access points, select one in the list and get a full screen  view of its  signal strength, so when i point my directional antenna  around i can  easily see if the signal strength is going up or down
along with a decimal value, so i can determine in what direction the access point is.

A device finder feature, with a horizontal bar value as a live signal strength value.
[IMG]https://i.stack.imgur.com/IgEzC.png[/IMG]

Do you know of anything that sound like this? I have tried to search the web for something kinda like this, but aren't having much luck.

---

### Post by chili555 on 2019-09-17
> Do you know of anything that sound like this? Sorry, but I've exhausted my limited knowledge.

nmcli gives fine-grained signal information:```

IN-USE  SSID                   MODE   CHAN  RATE        SIGNAL  BARS  SECURITY  
        GBR1                   Infra  1     195 Mbit/s  85      &#9602;&#9604;&#9606;&#9608;  WPA2      
*       GBR5                   Infra  149   405 Mbit/s  80      &#9602;&#9604;&#9606;_  WPA2      
        nx2.4                  Infra  11    195 Mbit/s  55      &#9602;&#9604;__  WPA1 WPA2 
        MC1                    Infra  11    130 Mbit/s  45      &#9602;&#9604;__  WPA2      
        MC5                    Infra  153   195 Mbit/s  29      &#9602;___  WPA2      
        DIRECT-X7-FireTV_69ab  Infra  153   130 Mbit/s  24      &#9602;___  WPA2

```As you can see, the access point to which I'm connected is at 80%. However, again, nmcli is a snapshot and to guage the changes as the antenna rotates, you'd need to run the command again and compare the results from each.  

I regret that I haven't any better tools to suggest.

---

### Post by CatKiller on 2019-09-17
Kismet is probably what you want to be looking at.

---

### Post by Drenriza on 2019-09-23
Thanks for the suggestions! I have installed kismet on Ubuntu 18.04.

@[**[COLOR=#DD4814][B]chili555**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=35909") @CatKiller

sudo lshw shows me that my usb metageek antenna is found as
*-usb:1
                   description: Human interface device
                   product: Wi-Spy DBx3
                   vendor: MetaGeek
                   physical id: 2
                   bus info: usb@1:2
                   version: 3.04
                   serial: 217040709630
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=12Mbit/s

dmesg
[  896.042882] usb 1-2: new full-speed USB device number 14 using xhci_hcd
[  896.194755] usb 1-2: New USB device found, idVendor=1dd5, idProduct=5002, bcdDevice= 3.04
[  896.194763] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  896.194768] usb 1-2: Product: Wi-Spy DBx3
[  896.194772] usb 1-2: Manufacturer: MetaGeek
[  896.194775] usb 1-2: SerialNumber: 217040709630
[  896.199881] hid-generic 0003:1DD5:5002.000B: hiddev0,hidraw0: USB HID v1.11 Device [MetaGeek Wi-Spy DBx3] on usb-0000:00:14.0-2/input0

But how do i make kismet see it as a data source?

Thanks in advance
Best regards!

---

