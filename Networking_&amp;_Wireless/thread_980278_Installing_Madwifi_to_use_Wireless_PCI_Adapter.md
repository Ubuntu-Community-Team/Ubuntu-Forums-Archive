---
title: "Installing Madwifi to use Wireless PCI Adapter"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by fparedesg on 2008-11-12
Hello! I am running Ubuntu Intrepid Ibex, and I'm trying to get my Wireless Network Card to work. I'm using a Super G Wireless PCI Adapter AWLH4030.

This thread tells me that this driver can me installed using MadWifi: [http://ubuntuforums.org/showthread.php?t=156809&hilight=AWLH4030](http://ubuntuforums.org/showthread.php?t=156809&hilight=AWLH4030)

I've already downloaded the latest version of MadWifi, and I'm following the instructions on this page: [http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo) , but I'm kind of stuck...

Once I reach the "Building MadWifi" step, once I type in the "make" command, I get an error, this is what I get:

```
ubuntu@ubuntu:~/Desktop/madwifi-0.9.4$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/home/ubuntu/Desktop/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/ubuntu/Desktop/madwifi-0.9.4/net80211/ieee80211_power.o
/home/ubuntu/Desktop/madwifi-0.9.4/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave':
/home/ubuntu/Desktop/madwifi-0.9.4/net80211/ieee80211_power.c:240: error: implicit declaration of function '__skb_append'
make[3]: *** [/home/ubuntu/Desktop/madwifi-0.9.4/net80211/ieee80211_power.o] Error 1
make[2]: *** [/home/ubuntu/Desktop/madwifi-0.9.4/net80211] Error 2
make[1]: *** [_module_/home/ubuntu/Desktop/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [modules] Error 2

```

I already installed build-essential, and linux-headers-$(uname -r), which are both mentioned on the top of the page.

Thanks for anyone that helps!!

---

### Post by enigmageek on 2008-11-13
Hello. Try just typing
sudo make install
This is what I had to do, I received the same error when I tried just sudo make. Hope this helps. let me know.
Regards, Ray
Ubuntu Hardy 8.0.4.1-2.6.27.5

Also I have DKMS conf and instructions to use DKMS to rebuild the driver automatically when you upgrade the kernel.

---

