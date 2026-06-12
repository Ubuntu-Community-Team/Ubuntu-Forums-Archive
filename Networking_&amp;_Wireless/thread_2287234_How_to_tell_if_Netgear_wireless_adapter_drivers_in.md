---
title: "How to tell if Netgear wireless adapter drivers installed correctly?"
date: 2015-07-17
forum: Networking &amp; Wireless
---

### Post by PsychedelicWonders on 2015-07-17
I didn't do anythign special, just booted up Ubuntu with my Netgear wireless adapter installed.  I also have it hooked up via hardline right now.

Is there anything special I need to do to get the wireless adapters drivers to download or does Ubuntu do it automatically?

how do i check/verify that it's been downloaded and working properly?

I also set WPA2 security inside of windows, how do I go about setting that up/connecting to those networks with the correct passwords?

Thanks.

---

### Post by weatherman2 on 2015-07-17
The Linux kernel includes many drivers for different wireless cards.  If your Netgear's wireless chipset is supported by a built-in kernel driver, then it should just work.  Wireless networks will be listed in Network Manager as options to connect to.  You choose the network you want and it will ask you for the password (WPA2 figured out automatically).  

If there are no wireless networks (when there should be), then obviously it didn't install correctly.  In that case, find the wireless script linked in the "sticky" post at the top of the forum and post the output here, so people can see exactly what Netgear card you have and offer a way to make it work for you.

---

### Post by Bucky Ball on 2015-07-17
Pull the ethernet cable out, plug in the wireless if it is a USB dongle, reboot. Click the Network Manager icon. Are there available networks? If so, it is working. No need to do anything else. Connect to your network. To check wireless you need to have the cable out. Can't run both at the same time.

Whatever you set up in Windows has nothing to do with your Ubuntu install. If you try to connect to your network in Ubuntu and successfully do so, security will be set up appropriately when you put in the security key for your router/access point.

Please tell us which release of Ubuntu you are using.

---

### Post by PsychedelicWonders on 2015-07-18
Hmm when I unplug the network cable and leave the adapter in, I get disconnected and the wifi/internet icon at the top right gives me the following options when I hover over it:

Ethernet Network Disconnected (ghosted out)
VPN Connections
Enable Networking (This has a check next to it)
Connection Information (ghosted out)
Edit Connections

I don't see anything else bringing up any available wifi networks, am I looking in the wrong place, or is my adapter just not working yet and not able to see the available networks?

Even though I may have set the passwords up in windows, I sent the WPA2 security within the router, so I shouldn't need to create new wireless networks with new passwords, i should just be able to join my already existing ones correct?

---

### Post by chili555 on 2015-07-18
Please insert the device and open a terminal Ctrl+Alt+t and run and post:```
lsusb
```When your device turns out to be a WDNA3100 or a WNA3100, old Chili will sob like a baby and then help.

---

### Post by PsychedelicWonders on 2015-07-18
I will run that code now, just need to reboot back to Ubuntu

But my Netgear wireless adapter is in fact the WNDA3100

Is this bad? lol  I take it these drivers aren't part of the Ubuntu Kernal?  What are my options?

Thanks.

---

### Post by PsychedelicWonders on 2015-07-18
my results after running lsusb:

```
Bus 002 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0403:fc60 Future Technology Devices International, Ltd 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:008a Microsoft Corp. Wireless Keyboard and Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Thoughts?

---

### Post by chili555 on 2015-07-18
Please check here: [http://askubuntu.com/questions/568056/usb-wireless-netgear-adapter](http://askubuntu.com/questions/568056/usb-wireless-netgear-adapter)

You have the exact same device and require the same driver.

---

### Post by PsychedelicWonders on 2015-07-18
I'll look into that now, thank you!

---

### Post by PsychedelicWonders on 2015-07-18
Ok I got pretty far, then the end part, nothing seemed to be right to me, what did I do wrong?

```
ndiswrapper:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.16.0-30-generic/updates/dkms/

depmod.....

DKMS: install completed.
Setting up ndiswrapper-utils-1.9 (1.59-2) ...
johnnyscience@SpaceStation:~$ cd ~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2
johnnyscience@SpaceStation:~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2$ sudo ndiswrapper -i bcmn43xx64.inf
couldn't find SourceDisksFiles section - continuing anyway...
installing bcmn43xx64 ...
johnnyscience@SpaceStation:~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2$ sudo ndiswrapper -ma
module configuration information is stored in /etc/modprobe.d/ndiswrapper.conf
johnnyscience@SpaceStation:~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2$ sudo depmod -a
johnnyscience@SpaceStation:~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2$ sudo modprobe ndiswrapper
johnnyscience@SpaceStation:~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2$
```

---

### Post by PsychedelicWonders on 2015-07-18
So whatever I did seemed to work as I can now see wireless networks available without the hardline plugged in.

For  some reason it's giving me an issue with my network password though,  I'm positive I'm imputing it right, but it keeps kicking it back to me.

I also have a dual network router, but only seeing 1 of the 2 networks for some reason.

And  tinkering around in the network/wireless icon in the top left, I came  across "Connect to hidden wifi network" - what's that all about and is  it something you setup inside of Ubuntu or in your router settings?

---

### Post by PsychedelicWonders on 2015-07-24
So I can pull up the wireless networks, but I can NOT get on my network no many how many times I try the password.  I've entered the password without it being hidden too so I was 110% sure I was trying it right, but it still will not connect.

I just re-set the network up in windows 7 a few weeks ago, would I need to reset the network again, but under Ubuntu for it to be able to work on all OS?  I just don't understand why it won't connect like any other devices, phone tablets etc all have no issue connecting.

---

### Post by Vladlenin5000 on 2015-07-24
In a nutshell: Obtain a new, better, cheaper and natively supported dongle.
Even if you manage to make it work you never know for how long... The question isn't "if it breaks", it's when.

---

### Post by chili555 on 2015-07-25
> **Vladlenin5000 said:**
> In a nutshell: Obtain a new, better, cheaper and natively supported dongle.
Even if you manage to make it work you never know for how long... The question isn't "if it breaks", it's when.By 'breaks,' I assume my colleague Vladlenin5000 means the software, not the hardware. I think he means that ndiswrapper and its ancient Windows XP driver are a bit of a compromise and a kludge. He's correct. The fact that it works at all, ever, is a surprise.> I also have a dual network router, but only seeing 1 of the 2 networks for some reason.I doubt that the XP driver does N speeds and maybe not 5 gHz. If your second network is set to either, I suspect ndiswrapper doesn't see it.> And tinkering around in the network/wireless icon in the top left, I came across "Connect to hidden wifi network" - what's that all about and is it something you setup inside of Ubuntu or in your router settings?You set it up in the router. Most Linux drivers don't like it. It doesn't help much and often hurts. Please see: [https://en.wikipedia.org/wiki/Service_set_(802.11_network)#Service_set_identification_.28SSID.29](https://en.wikipedia.org/wiki/Service_set_(802.11_network)#Service_set_identification_.28SSID.29)> As a purported security enhancement, some access points allow a user to inhibit the broadcasting of their SSIDs, a tactic known as network cloaking; a station may then only join a BSS after the associated SSID has been specified explicitly. This tactic acts as a deterrent to the extent that it impedes casual wireless snooping but **useless against widely available network scanners. **Network cloaking is a form of security through obscurity and offers no protection against even the most basic attacks against a wireless network. Does your network use TKIP or AES? AES is greatly preferred.

---

### Post by PsychedelicWonders on 2015-07-25
I think it is AES, would it help if I provided my router model # also?  I can get all the info later, I'm in a rush to a cookout at the moment.

Can I keep my router & just get a new wireless adapter or would a new router be needed too?  Either way my current setup is not that good huh?

I've seen some really interesting encrypted ones, does anyone know about them?  I think they're about $200

---

### Post by chili555 on 2015-07-25
> I think it is AES, Why don't we ask it what it is:```
sudo iwlist wlan0 scan
```You will see some details on all the routers in range. Yours will report either:> Frequency:5.805 GHz (Channel 161)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"GBR1"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b63331d347
                    Extra: Last beacon: 108ms ago
                    IE: Unknown: 000447425231
                    IE: Unknown: 01088C129824B048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        [COLOR="#FF0000"]Group Cipher : CCMP[/COLOR]
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
CCMP is another designation for AES. Otherwise, it will report:> Group Cipher: TKIPTKIP is insecure as well as troublesome to many Linux drivers.

AES vs. TKIP is a setting you can change in the router: [http://cdn3.howtogeek.com/wp-content/uploads/2014/12/ximg_548366be9a8c9.png.pagespeed.ic.F324VO6Xj6.png](http://cdn3.howtogeek.com/wp-content/uploads/2014/12/ximg_548366be9a8c9.png.pagespeed.ic.F324VO6Xj6.png)

You needn't consider a new router. You might, however, consider a different USB wireless. There are many threads here about supported USB devices.

I recently bought and tested this: [http://www.newegg.com/Product/Product.aspx?Item=N82E16833704045](http://www.newegg.com/Product/Product.aspx?Item=N82E16833704045) It worked perfectly!

---

### Post by PsychedelicWonders on 2015-08-02
I'm going to run all of those codes soon once I fire Ubuntu back up (on windows right now)

But I see that TP link adapter you suggested also has a "Nano" version that is just a tiny thumb nail USB, do you think this is as good as the N150 High gain?  (I assume you got the High gain version?)

Any links to a list of other very compatible USB/Ubuntu wifi adapters?  I won't have any problems syncing any adapter up to my Netgear router?  (I thought I had to match the router & USB wifi dongle with the same company)

---

### Post by Bucky Ball on 2015-08-02
> **PsychedelicWonders said:**
> (I thought I had to match the router & USB wifi dongle with the same company)

No. Not required. They do not rely on each other that way. All the dongle needs is a wifi single, doesn't matter from where or what brand of access point. All that matters is you are using the same security encryption and can get into the network.

It is the chip inside that is more important than the brand of the dongle so we can recommend brands we know work as they have compatible wireless chips. The chips in some brands remain a mystery until someone actually has one and can take a look at 'what's in the box'. ;)

In other words, an obscure dongle brand might contain a very well-known and Linux-compatible wireless card.

---

### Post by chili555 on 2015-08-02
> Any links to a list of other very compatible USB/Ubuntu wifi adapters? There are many threads here and on askubuntu.com about compatible USB wireless devices. 

As for the Nano, it is impossible to tell without examining the device hands-on. Manufactures are famous for changing the chipset without notice. A few years ago, I worked on a case involving a Linksys device. We determined that various versions were sold using any of *four* different chips!

When we have the device in hand, we plug it in and ask it to tell us its details with a terminal command:```
lsusb
```We get details like this:> Bus 002 Device 027: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11nWe can then Google the usb.id; in this case 0cf3:9271, and see that its supported: [https://wikidevi.com/wiki/Atheros_AR9271](https://wikidevi.com/wiki/Atheros_AR9271)> **Linux support**
Built-in Linux kernel support:

Linux kernel module: ath9k_htc
in backports
Linux kernel version: v2.6.35
Linux kernel date: 2010-08-01

---

