---
title: "Belkin F5D7050"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by Jolicoeur on 2010-08-23
I loaded the new Ubuntu on my old (2001) laptop and all went well except wifi.  I tried to use my wireless card and tried over and over to get it to work through online help and could not.  So, I went online to see if any wireless devices work out of the box. Found that the Belkin F5D7050 is supposed to.  Just won it cheap on Ebay.  What do I do just put it in the usb without loading any drive?  What do I do if this one does not work either? Thanks

---

### Post by lkraemer on 2010-08-23
[B]

How do I know if I have Broadcom, Atheros, or other Wifi Hardware?[/B]

Open a Terminal Window and use these commands to get more information
on your hardware, wireless, Windows loaded drivers, and Linux drivers
that are currently blacklisted. Copy & Paste to prevent errors!
```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
iwconfig
dmesg | tail

```
iwconfig will show what the wireless is detected as......wlan0, ath0, etc.
If you are requesting help, post the output of each command........

Your options that can be used to get the Wifi functional: (B43 is the preferred Broadcom Driver for 10.04)

1. Ndiswrapper and a Windows Driver....Broadcom = bcmwl5.inf & sys
The correct 32/64 Bit drivers must be used to match Ubuntu 32/64 Bit.

2. B43 and some Firmware that was downloaded/extracted when you
enabled the Broadcom Driver.

3. Madwifi Drivers or Default Ubuntu Drivers for Atheros Hardware.

**#1 - NDISWRAPPER**
To install the Windows Drivers that are located on your Desktop in a
folder named broadcom (.sys & .inf files):
```

cd ~/Desktop/broadcom
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
lsmod
ifconfig
iwconfig

```
To make sure it starts on boot:
```

echo ndiswrapper | sudo tee -a /etc/modules

```
Then I'd reboot or try:
```

sudo /etc/init.d/networking restart

```
SKIP to FINISH below.......


**REMOVE WINDOWS DRIVERS:**
If you want to REMOVE the Windows Drivers:...............
If the output of ndiswrapper -l shows any drivers loaded,
remove ALL of them. If memory serves me correctly the command is:
```

sudo ndiswrapper -e bcmwl5
sudo ndiswrapper -e ssb

```
This should clean up nidswrapper & drivers and:
```

ndiswrapper -l

```
should return nothing as being loaded.

Then remove ndiswrapper:
```

sudo modprobe -r ndiswrapper

```
Remove from startup file by editing:
```

sudo nano /etc/modules

```
to remove ndiswrapper.

SKIP to FINISH below.......


**#2 Use DEFAULT B43 Driver in 10.04**
The Firmware is missing and you just need to have an Ethernet Connection
and ENABLE the B43 Driver, or if you don't have an Ethernet Connection,
you can just copy the Firmware to the proper folders.

Download the Firmware files located at:
[http://www.omattos.com/node/6](http://www.omattos.com/node/6)
to a USB Flash Drive and copy them to your Desktop, and Extract.
You should have two folders b43 & b43legacy. You will be copying
these folders to /lib/firmware/b43 and /lib/firmware/b43legacy

Here are the commands I used on my old Compaq V5201US, running the
10.04 LiveCD to get it working: (Open a Terminal Window)
```

cd /
cd /lib
cd firmware
pwd
ls
sudo cp -r /home/loginname/Desktop/b43* .
cd b43
ls
cd ..
cd b43legacy
ls
exit

```
Now you just have to Enable the B43 Driver:
SYSTEM -> ADMINISTRATION ->HARDWARE DRIVERS
should have a B43 Driver listed a driver listed for your wireless,
if so enable it. (If by chance you have already ENABLED it, go ahead
and let it try to uninstall, then install it again by clicking again.
It should find the drivers and load them, because the Firmware is where
it needs to be.

Check Network Manager (right click on the icon) to be sure the "Enable Wireless"
box is checked (It should be ENABLED already by default.)

Check to see if you have wireless now. If not, you might need to
check the Loaded Modules, making sure there are no conflicts with other
Wifi drivers that might have been loaded, or others that cause conflicts.
```

lsmod

```
Post the output of lsmod.

You can check for errors with:
```

dmesg tail

```
You may have to remove other modules depending on what lsmod shows:.... ..
What you will REMOVE depends on what you post as output from your commands.

If lsmod shows module bcm43xx and other conflicts installed you will
need to blacklist them, since you are going to be using B43.
You may have to remove the following depending on what lsmod
shows:
```

modprobe -r b44
modprobe -r ndiswrapper

```
You can use sudo nano /etc/modprobe.d/blacklist.conf
and add the necessary modules to blacklist.

Once this is all straightened up..........
I'd reboot or try:
```

sudo /etc/init.d/networking restart

```

SKIP to FINISH below.......

[B]
3. Madwifi or Deafult Ubuntu Drivers for Atheros.[/B]
My suggestion is to use the Default Drivers for 10.04 as they appear to work just
as good as the Madwifi drivers.


**FINISH:**
Click on the Wifi Icon in the top right toolbar and select the Network.

**Manual Wifi Setup:**
If you know the routers essid and the correct <interface>,
shown by using iwconfig ie wlan0, ath0, etc.... replace that
as the <interface> below:
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```
example......for Airlink and Wlan0
sudo iwconfig Wlan0 essid "Airlink"

It shouldn't take more than about 15 minutes......


lk

---

### Post by Paul820 on 2010-08-23
> Belkin F5D7050

I have exactly the same one, USB, i just plugged it in and i was on the net after entering my router password.

---

