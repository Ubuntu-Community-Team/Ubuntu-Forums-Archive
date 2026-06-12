---
title: "[SOLVED] tosh A210 / ndiswrapper / wicd help"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by digitalhillbilly on 2008-02-06
Hello fellow forum miners! I was wondering if any here could give a hand with a Toshiba A210 wirelss problem. The device is a Realtek 8187b USB adapter and I'm using wicd cause it's wicked as well as ndiswrapper. I had read (somewhere) the linux 8187 driver would not work with the "b" version of the device so I loaded the XP driver into ndiswrapper with no luck. Further reading said the problem was with the "b" versions device ID of 0bda:8197 and needed to modify the driver. Thats a little beyond me but luckily found an already modified one - can't remember the URL at the moment but will find it if it's important. Loaded the modified driver into ndiswrapper and the device was found. Ya!

I opened up wicd and there before my eyes was a list of about 20 wireless networks in my neighbourhood. I tried to connect to my WEP network and it just hung on "Obtaining IP" for about a minute then "Not Connected". I turned off encryption on my network (connected from another computer to ensure the setting took) tried again to connect from the A210 and still no dice. 

I've been reading the forums for the last couple days and have tried a bunch of different things. I'm a little lost at this point and could use a little direction.

Thanks!
dh




some outputs:
```
$ lsusb
Bus 006 Device 003: ID 0bda:8197 Realtek Semiconductor Corp. 
```

```
$ ndiswrapper -l
net8187b : driver installed
        device (0BDA:8197) present
```

```
$ dmesg
[   21.100000] ndiswrapper version 1.45 loaded (smp=yes)
[   21.284000] usb 6-6: reset high speed USB device using ehci_hcd and address 3
[   21.508000] ndiswrapper: driver net8187b (Realtek Semiconductor Corp.,07/18/2007,5.1097.0718.2007) loaded
[   25.024000] wlan0: ethernet device 00:16:44:6a:b1:ba using NDIS driver: net8187b, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8187 Wireless LAN USB NIC                                     ', 0BDA:8197.F.conf
[   25.024000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   25.024000] usbcore: registered new interface driver ndiswrapper
[   26.444000] NET: Registered protocol family 17
[   67.608000] NET: Registered protocol family 10
[   67.608000] lo: Disabled Privacy Extensions
[   67.608000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

---

### Post by digitalhillbilly on 2008-02-11
Well, I've made progress. I've come full circle - twice! I did initially try the modified drivers found [here]("http://www.datanorth.net/~cuervo/rtl8187b/") but they didn't work for me. Exhausted everything else so tried the modified driver again and whaddaya know, it works! I've been able to connect to WEP and open networks w/ wicd but have not tried WPA yet. Maybe later.

I do still have two issues that I could use a bit of help with. First is the card's name is wlan1 instead of wlan0 - may not be a big deal but I wonder if this ties into my second problem...

Second, I have to run the script "wlan0up" (provided with the modified driver package) to load the driver. No big deal except I can only run it as root whereas in the provided docs it's only run as a regular user. I really want this to start automatically at boot but cannot figure out how to get my script to run.

in /etc/init.d I created the script wlan_det.sh (I did chmod +x) and it contains a pointer to the provided script:

```
#!/bin/bash

cd /home/dani/Documents/drivers/rtl8187b-modified
./wlan0up

exit
```


It runs fine from the terminal but won't load automatically. ```
sudo /etc/init.d/wlan_det.sh
``` 

I could use a hand either getting the script to run as a regular user or getting the script to load automatically as root.

Thanks for any help that can be offered!
dh

---

### Post by digitalhillbilly on 2008-02-11
Well, it's all working now. Thought I would post here so the thread is complete in case some one is searching the forums for some help. 

First, The laptop is a Toshiba A21-MS4 with a Realtek 8187b device - rtl8187b

The only way to get this card to work is to download the [modified drivers]("http://www.datanorth.net/~cuervo/rtl8187b/") and build 'em as per the included readme. there is also a FAQ on the site with some other tips and info. 

In the FAQ there are instructions to get the card to load at each boot by adding some lines to your /etc/network/interface . Never worked for me and I'm using wicd so prefer to keep my interfaces file to :
```
auto lo
iface lo inet loopback
```

Instead I added a file called wlan_det to my /etc/init.d   

use gedit or nano or whatever you prefer ( sudo gedit /etc/init.d/wlan_det OR sudo nano /etc/init.d/wlan_det )
```
#!/bin/bash

cd /home/username/wherever/rtl8187b-modified #change to the path to the modified driver folder
./wlan0up

exit
```

save and close the file - save button in geit ten close OR Ctrl+o to save, press Return to accept then Ctrl+x to close

The file must be executable so:

```
sudo chmod +x /etc/init.d/wlan_det
```

Now to make the start-up script actually work! A brain fart caused my post previous to this one. Links need to be generated for the scripts in the init.d folder to load. To generate, in your console type:

```
sudo update-rc.d wlan_det defaults
```

you'll see and few lines print in the terminal and your done! Reboot and then  type in your console dmesg, ifconfig, lshw -C network, maybe some others to see if it loaded ok.

Install wicd for easy network selection - I like it, you might too.

These are the steps that got it going for me. It's not new information - I found it in the forums and such - but maybe it'll help someone out there.

dh

---

