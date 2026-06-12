---
title: "WLAN USB card with out-of-the-box support"
date: 2007-01-01
forum: Networking &amp; Wireless
---

### Post by orkid on 2007-01-01
Does WLAN card with USB interface, that is natively supported (out-of-the-box) by Ubuntu, exist? (I mean that the driver is included in Ubuntu distribution by default so I can plug it in any Ubuntu 6.10 box and it will be automatically detected and configured ?) Any suggestions

---

### Post by DapperMe17 on 2007-01-01
Yes, the Linksys WUSB54G Version 4 has out-of-the-box connectivity in Ubuntu Edgy...for open, unencrypted connections. There is a built-in driver.

For secure, encryption (WPA, etc), the Linksys will work flawlessly, but will need some manual configuration. This requires the driver that came on the CD. I've just set it up & works like a charm.

---

### Post by orkid on 2007-01-02
> **DapperMe17 said:**
> Yes, the Linksys WUSB54G Version 4 has out-of-the-box connectivity in Ubuntu Edgy...for open, unencrypted connections. There is a built-in driver.

For secure, encryption (WPA, etc), the Linksys will work flawlessly, but will need some manual configuration. This requires the driver that came on the CD. I've just set it up & works like a charm.
 
Do you know which chipset does it have ? What does "lspci -v" return? What do you mean by "This requires the driver that came on the CD". Do the CD contains drivers for ubuntu? or windows drivers that can be used with ndiswrapper?


The main problem with Linksys WUSB54G is difficulties with availability. Only Linksys WUSB54GC are sold in shops nowadays :(

---

### Post by jamesstansell on 2007-01-02
DapperMe17 was talking about using the windows driver with ndiswrapper.  His post is in another thread here.

The WUSB54G is not a pci device.  /proc/bus/usb/devices shows 
```
 Vendor=13b1 ProdID=000d Rev= 0.04
```

The built-in driver is rt2570 but sometimes you'll see rtusb displayed.  I see rtusb0 in the devices list.

I was able to establish a WEP connection using the built-in driver but no luck with WPA so far.  I've read that wpa_supplicant won't work with this driver; some people have been able to use either rutilt or iwpriv but neither has worked for me so far.

I haven't tried ndiswrapper so far but that's probably my next step.

The WUSB54GC is probably a different chip.  I'm guessing it would use the rt71 driver.

HTH,

-james.

---

### Post by bikeboy on 2007-01-02
Any of the USB ones on here should work out of the box.
[http://ralink.rapla.net/](http://ralink.rapla.net/)

---

### Post by clemkonan on 2007-01-05
For DapperMe17 I have a Linksys USB54G version 4 and Edgy can you give me some  basic instructions for setting this up. I am totally new to this.

How do I :
1) locate a built in driver or install the driver on the CD
2) how do I do the minor tweaks needed to get it working''

I have  been at this for 4 weeks and still cannot get this PC for my 14 year old connected.

The information in the various posts is really conflicting, some say it can run out of the box,  some say I need Nddiswrapper or something like that. 

I have three PC  connecting through a Speedstream router from Bell Sympatico. PC # 1 is hard wired and runs XP, PC #2 has a the same linksys wireless card but runs XP , #3 runs Ubuntu CE.

---

### Post by ashrack on 2007-01-12
> **bikeboy said:**
> Any of the USB ones on here should work out of the box.
[http://ralink.rapla.net/](http://ralink.rapla.net/)

So per your page ASUS 	WL-167g should work out of the box

---

### Post by orkid on 2007-01-15
> **ashrack said:**
> So per your page ASUS 	WL-167g should work out of the box

I have bought ASUS WL-167g. However newer ASUS WL-167g uses rt73 drivers. It works under ubuntu but not out-of-the-box. I think that older version that uses rt2500 is supported out-of-the-box.

---

### Post by ashrack on 2007-01-15
aha, so if I bought one now it wont work out of the box and I will have to do some fidlling around?

---

### Post by Tavathlon on 2007-01-17
Oh, oh, oh! This seems to be just the thread I'm looking for!

I bought an Asus WL-167G a couple of days ago, and I have now installed the rt2570 driver for it - according to some other thread that should work. But it doesn't. Or does it? Is there anything I should do after installing the driver, or should the device get into the Networking box automatically after I've installed the driver? I have no clue, I'm not very good at this kind of stuff...

Anyway, if the rt2570-driver does not work with newer wl-167g, then how do I install the rt73 driver? And when installed, what should I do to get it working?

My new apartment _only_ has wireless network, so I have to get this working...  >.<
Help for a newbie, please?


Edit; I forgot to mention that I have downloaded the RT73_Linux_STA_Drv1.0.3.6 from Ralinks homepage, but when I try 'make install' it does not work. instead, I get this:

tavathlon@oskar-laptop:~/Desktop/RT73_Linux_STA_Drv1.0.3.6/Module$ sudo make install
install -m 755 -o 0 -g 0 -d /lib/modules/2.6.17-10-386/extra
install -m 644 -o 0 -g 0 rt73.o /lib/modules/2.6.17-10-386/extra
install: kan inte ta status på "rt73.o": Filen eller katalogen finns inte
make: *** [install] Fel 1

(the comments are in swedish, and on the 4:th line, it says: "install: cannot get status on "rt73.o": The file or the catalog does not exist")

So, what I really need is some help with how I should be able to install the driver properly. Although, it would of course be nice to know what should be done afterwards - if anything needs to be done.  =)

Thanks in advance, folks!

---

### Post by Tavathlon on 2007-01-18
Problem is solved, thanks to this excellent howto: [https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?action=show]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?action=show")

I have not yet been able to test whether the card actually works, since I am not yet in my new apartment, but now the dongle appears in the Networking box, anyway. Thanks again, everyone!  =)

---

### Post by orkid on 2007-01-19
> **Tavathlon said:**
> Problem is solved, thanks to this excellent howto: [https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?action=show]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?action=show")

I have not yet been able to test whether the card actually works, since I am not yet in my new apartment, but now the dongle appears in the Networking box, anyway. Thanks again, everyone!  =)

I compiled the driver too and it work for a one day :( It is strange case. It simply stop working (nothing was changed).  Both devices see each other, but there is not IP traffic on the connection (ip is correctly set). tcpdump do not shows anything. Maybe someone has any idea how to diagnose this kind of problem ?

---

### Post by Tavathlon on 2007-01-20
Well, obviously my problem wasn't solved either  =(

The device appears in the Network box and all that, but I can't reach the internet. Obviously, the usb-device does not communicate properly with the wireless router, although the computer communicates with the device.

I'm quite new to the whole thing about wireless network, but my administrator needed the MAC-address to my wireless device, which he got. According to him, the network should be like an open wireless network for my, once he has added the MAC-address. Which he has already done. 

As I have understood it, I need to do some adjustments in /etc/network/interfaces, but I have no idea about _what_ changes that need to be done. The configuration in the [howto]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?action=show") for installing the device does obviously not work...

Any ideas, anyone?

---

### Post by Tavathlon on 2007-01-26
Problem solved. It seemed that essid was not set properly, in spite of me editing the /etc/network/interfaces correctly. It did not work until I performed this command:

$ sudo iwconfig rausb0 essid ESSID-NAME

So, now let's just hope it won't shut down itself after a couple of hours (which happens, I've heard) or that it won't stop working after reboot...  =P


Edit: It seems that the command above have to be entered every time I start up the computer, and then I have to wait for a while before the network is available. Perhaps this is your problem as well, Orkid? Except for that, it seems to be working fine.

---

