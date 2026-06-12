---
title: "Kubuntu: ndiswrapper installed driver, but device does not work"
date: 2007-04-13
forum: Networking &amp; Wireless
---

### Post by Sup3rkirby on 2007-04-13
I have installed my Belkin USB adapter on Ubuntu(Xubuntu) before and it worked fine, but I just switched to Kubuntu.

I used the same method and the exact same process to install it.  ndiswrapper says that the driver is installed and the hardware is present, but the wireless networking program does not recognize and wireless devices.

If i used 'iwconfig' it does not show the adapter, so something isn't right.

Both Xubuntu and Kubuntu use the same Ubuntu base files, it is just a difference in desktop management systems, correct?  So why doesn't the exact same installation method work for the exact same device?

---

### Post by EvanPMeth on 2007-04-13
A few questions:
What version of ndiswrapper are you using (is it from source or apt-get/synaptic)?
*I have had complete success with building from source. The ubuntu version is outdated and does not install correctly*
Did you set the mac address in iftab?
Did you configure your wlan0 with ifconfig or /etc/network/interfaces?
When did you plug the usb device in (sometimes its matters)?
Did you restart after installing ndiswrapper (this is to make sure the modules loaded) ?


***_FOR REFERENCE HERE IS PART OF WHAT I JUST RECENTLY POSTED ON ANOTHER THREAD._***

- Locate your drivers .inf file, DO NOT just copy the .inf file leave it in its directory, the inf just tells ndis what and how to use the other files, it is not the actual driver.
- install it **sudo ndiswrapper -i YOURINF.inf**
- update modules **sudo depmod -a**
- test ndis module **sudo modprobe ndiswrapper**
- initiate ndiswrapper as a system startup module **sudo ndiswrapper -m**

**sudo gedit /etc/modules/**

''...add to bottom of the listing...''
**ndiswrapper**

IF you are using a usb device you may have to set the mac address just to be safe
**sudo gedit /etc/iftab/**

''...add to bottom of the listing...''
**wlan0 mac 00:00:00:00:00:00**
[I](I dont think this is needed because I had a usb dongle installed and replaced it with a pci wireless card and updated the ndis wrapper drivers with the pci card drivers and I didnt change the mac address in iftab and it worked fine, i believe the newer versions of ndiswrapper handle mac address checking.)
[/I]

- now setup your wireless interface (wlan0): sudo gedit /etc/network/interfaces
in the interfaces file remove the "#" infront of 

```
# auto wlan0
# iface wlan0 inet dhcp

```

then add your wireless info bellow (essid is the name of your network):
THIS IS FOR A NETWORK WITHOUT  "WEP" for better trouble shooting turn off the wep. (will configure that later).
```

 auto wlan0
 iface wlan0 inet dhcp
        wireless_mode managed
        wireless-essid ACCESS_POINT_NAME

```

*I did this also just in case, dont know if it does anything different:*
**sudo iwconfig wlan0 essid ACCESS_POINT_NAME mode managed**

NOW shutdown the computer and unplug it and plug your wireless card back in.
IF USB do not plug it in now, wait till it starts up again.

Turn your computer back on wait till its done starting up (plug in your usb if not pci) and test that beast: **ndiswrapper -l**
Should look like the following with the driver installed and the device present.
```
mrv8000c : driver installed
        device (11AB:1FAA) present
```
*(yours will reflect the driver card and number of your device)*

test your internet: **ping [www.google.com](www.google.com)**

now if its working you can turn the routers wep back on and set the password by doing the following:
**sudo iwconfig wlan0 essid ACCESS_POINT_NAME mode managed key TEXT_WEP_KEY restricted**

Hope that helps correct me if i messed up on anything: :)

---

### Post by Sup3rkirby on 2007-04-13
Thank you.
I guess my problem was ndiswrapper.  I downloaded it and built it(from source) then installed it.  Then I restarted my computer(just to make sure).

From there I completed the rest of the steps to install my USB adapter and it worked.  It was recognized and connected immediately after installation.

---

