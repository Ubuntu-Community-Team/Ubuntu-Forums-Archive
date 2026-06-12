---
title: "feisty and usb wireless"
date: 2007-04-15
forum: Networking &amp; Wireless
---

### Post by murlosad on 2007-04-15
So, I've got a dlink dwl-g132 wireless usb adapter. Obviously feisty doesn't recognize it by itself so I am forced to use ndiswrapper.  I've got everything installed as best I can using various guides and howto's (best so far was the ndiswrapper wiki).  The problem I'm having is that the adapter won't activate, no lights at all.

lsusb see's it and ndiswrapper -l gives me:
> athfmwdl : driver installed
        device (2001:3A03) present
neta5agu : driver installed
        device (2001:3A03) present
I've gotta use both drivers according to [this]("http://sourceforge.net/project/shownotes.php?release_id=376633&group_id=93482"), one is a firmware driver and the other is a card specific driver.  But this is as far as I can get. 'dmesg | grep ndiswrapper' gives me: 
> [   28.448000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[   28.524000] usbcore: registered new interface driver ndiswrapper
[ 1660.016000] usbcore: deregistering interface driver ndiswrapper
[ 1664.180000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[ 1664.532000] ndiswrapper: driver athfmwdl (,12/05/2003,1.00.001) loaded
[ 1664.532000] ndiswrapper (miniport_init:265): assuming WDM (non-NDIS) driver
[ 1664.532000] usbcore: registered new interface driver ndiswrapper
which I think means everything is ready to go.  

Any suggestions?

---

### Post by murlosad on 2007-04-25
*bump....

anybody?

---

### Post by panty31772 on 2007-07-20
--------------------------------------------------------------------------------

I dont know if this will help any .. but ... i could not get the drivers to work under dapper .. now that i ugraded to edgy thoguh it all works ( havent tried actually connecting to a wireless network but all signs show the device to work 
i dowloaded the newest drivers form d-link's website , extracted to my home folder ... used the kmenu/settings/windows wireless driver to install both .... then in terminal set ndiswrapper to use netAAGU as the device driver .... followed the steps in this : How to install Windows Wireless Drivers (Ndiswrapper)

* Read #General Notes
* In order to install ndiswrapper you need a copy the windows drivers for your Wireless ethernet device.
* This is only meant to be installed if your card isn't supported by Ubuntu, check Ubuntu's list of natively supported wireless cards.
* Check ndiswrapper's list of supported wireless cards if your card isn't supported natively, please visit Ndiswrapper's official supported cards list 

* Find out if you have acx module loaded. Because acx module interferes with windows driver, we need to remove it if it is found. 

lsmod | grep acx

* Remove the acx module if found. It could also be acx_pci or similar. Please Note: New kernel updates will auto load the acx module again. So repeat the following two commands every time the kernel is updated. 

sudo rmmod acx
sudo mv /lib/modules/2.6.15-26-386/kernel/drivers/net/wireless/acx /root/

* Install ndiswrapper and drivers (due to a bug in Edgy, you need to specify ndiswrapper-utils-1. 

sudo apt-get install ndiswrapper-utils-1.8
sudo ndiswrapper -i /location_of_your_wireless_driver/your_driver.inf
sudo ndiswrapper -l
sudo modprobe ndiswrapper

* Set ndiswrapper to load on startup 

sudo ndiswrapper -m
gksudo gedit /etc/modules

* Add the following module to the list 

ndiswrapper

* Now you can configure your wireless card with ifconfig and iwconfig. 

e.g. Supposing wlan0 is your wireless device. 

sudo iwconfig wlan0 essid "AP" key ababababababababab mode Managed
iwconfig

* You sould now be able to see the MAC address of the access point and signal rate. 

[edit]

rebooted with dongle connected . seemed to have worked for me ... hope it helps

 sometimes certain setups lock up with the dongle conected at boot up , in which case i plug in the dongle at the login screen instead... its a copy paste from another post of mine !

---

### Post by murlosad on 2007-07-21
thanks for the reply, I haven't had time to try this yet, but it definetly seems promising.

I will let you know how it works out.

---

### Post by Oen386 on 2007-07-28
Did it work?

I have a DWL-G122.

I followed the directions here and got:

```
[102125.101783] usb 5-6: USB disconnect, address 30
[102126.346718] usb 5-5: new high speed USB device using ehci_hcd and address 35
[102126.486274] usb 5-5: configuration #1 chosen from 1 choice
[102126.913353] usb 5-5: reset high speed USB device using ehci_hcd and address 35
[102127.177355] ndiswrapper: driver netrtusb (D-Link,04/01/2004, 1.00.00.0000) loaded

```

When I type iwconfig though...

```
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

vmnet8    no wireless extensions.

vmnet1    no wireless extensions.

```

Anyone have any ideas?

---

### Post by murlosad on 2007-07-28
no love for me either. The only difference in this guide from what I've used before is the 'acx' section, which doesn't seem to be loading anyway.  This is what I get for iwconfig
```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.
```

and lsusb:
```
Bus 001 Device 006: ID 2001:3a03 D-Link Corp. [hex] 
```

I do have a link light now, but nothing else has changed

:( I'm stumped but I do appreciate the reply **panty31772**

---

### Post by kevdog on 2007-07-28
Are you guys using ndiswrapper???  This creates an interface under wlan0.  What does your /etc/iftab show??  Is the ndiswrapper module loaded:
lsmod | grep ndiswrapper

What about changing your previous wireless interface name (eth0, eth1 or whatever it is) to wlan0 in the /etc/network/interfaces file???

---

### Post by murlosad on 2007-07-29
Ok, I kinda got mine working. Here's what I did:

I completely removed anything to do with ndiswrapper.

```
sudo modprobe -r ndiswrapper
ndiswrapper -l
sudo ndiswrapper -r "anything listed above"
sudo apt-get remove ndiswrapper
```

Then I rebooted with the dongle connected, and reinstalled ndiswrapper.

I got the newest drivers from dlinks website: [ftp://ftp.dlink.com/Wireless/dwlg132/Driver/dwlg132_drivers_121.zip](ftp://ftp.dlink.com/Wireless/dwlg132/Driver/dwlg132_drivers_121.zip)

and extracted them to my home folder.

I only installed the neta5agu driver (which is the only one that comes with the newest drivers)

ran ```
sudo modprobe ndiswrapper
sudo ndiswrapper -m
```

Then like magic 'ifconfig' shows a wlan0 device and using the network icon in my system tray I was able to find and connect to my wireless network.

After all this I was able to connect to anything on my side of the router, but no WAN connectivity. This could be something simple on my end that I'm missing, but I really don't need to connect to the internet on the laptop this is for so it's not a deal breaker.

Now the real test will be whether or not I can duplicate this on the laptop (I've been testing this on my desktop)... 

Hope this helps

---

### Post by murlosad on 2007-08-05
Just a quick update:

It worked on the laptop with Kubuntu :)

The trick seems to be to only use the neta5agu.inf and not the atheros driver.

Also I managed to set up wpa with wpa_supplicant using mostly this guide: [http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136) and this: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,wpa/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,wpa/)

Good luck to anyone else still working on this, I'll keep an eye on the thread.

---

