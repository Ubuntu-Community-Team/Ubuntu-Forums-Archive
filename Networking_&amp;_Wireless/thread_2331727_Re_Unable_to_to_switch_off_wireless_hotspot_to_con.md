---
title: "Re: Unable to to switch off wireless hotspot to connect to a wireless network"
date: 2016-07-25
forum: Networking &amp; Wireless
---

### Post by boxcorner on 2016-07-25
Hello 

I have been using Xubuntu 14.04LTS
My computer is a Lenovo Z570
It is configured for dual-boot Windows 7 which I hardly ever use.
I have been using a wireless connection to a SilverCrest repeater.
Normally this usually works fine, but sometimes it disconnects, even though the signal strength is excellent.
While trying to resolve this problem I have somehow inadvertently ruined my network connection.

All Settings > Network now shows Wireless Hotspot ON & Aeroplane Mode OFF
Whenever I try to switch Wireless Hotspot from ON to OFF the Network window closes. 
Consequently I am unable to get online wirelessly via Xubuntu.

I can get online via Windows 7 when it is connected to the main modem router.

I have updated the BIOS to version 45CN38WW

I am using another computer running Windows to get online, so I can type this.

On my Lenovo I have tried following : Wireless connection troubleshooter

```
Terminal > nm-tool
wlan0
Type: 802.11 WiFi
Driver: brcmsmac
State: disconnected
Default: no
```

```
sudo lshw -C network
descritption: Network controller
product: BCM4313 802.11bgn Wireles Network Adaprer
vendor: Broadcom Corp
```

```
sudo apt-get install lshw
lshw is already newest version

System Settings > System > Software & Updates > Additional Drivers
Broadcom Corportation: BCM4313 802.11b/g/n Wirless LAN Controller
This device is not working
```
Clicking on radio button Using Broadcom 802.11 Linux STS wireless driver source from bcmwl-kernel-source(propietary) > Apply Changes
jumps back to > Do not use the device

Could someone please tell me what I need to do to resolve this problem?

Addendum

```
sudo lshw -C network
network
description: Wireless interface
configuration: broadcast=yes driver=brcmsmac
 driverversion=3.13.0.92-generic firmware=610.812 link=no multicast=yes wireless=IEE 802.11bgn
```

---

### Post by jeremy31 on 2016-07-25
Can you delete Hotspot from the wireless network list in Network Manager?

---

### Post by boxcorner on 2016-07-25
Addendum

```
sudo lshw -C network
network
description: Wireless interface
configuration: broadcast=yes driver=brcmsmac
 driverversion=3.13.0.92-generic firmware=610.812 link=no multicast=yes wireless=IEE 802.11bgn
```

```
lspci -nn -d 14e4
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adaptor [14e4:4727] (rev 0.1)
```

Thanks for your reply.
I'm not sure I undestand what you mean by "Network Manager".
Are you referring to the Network window GUI, or something via Terminal?

---

### Post by jeremy31 on 2016-07-25
Network Manager GUI

---

### Post by boxcorner on 2016-07-25
Xubuntu 14.04
Applications > Administration > Network <== not called "Network Manager"
there isn't a wireless network list

---

### Post by jeremy31 on 2016-07-25
Click on the network icon in the taskbar, click Network Connections and see if you can click on hotspot and then delete

---

### Post by boxcorner on 2016-07-25
I would try following these steps :
[http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)
but I am stuck as I can't run apt-get without an Internet connection.

There isn't any network icon in the taskbar.
If that's an option which can be turned on, then how can I do that, please?

---

### Post by jeremy31 on 2016-07-25
Moved to networking
I will be unavailable for the next 8 hours due to work.  I am sure somebody will be able to assist you in installing bcmwl-kernel-source offline

---

### Post by boxcorner on 2016-07-25
Thank you

Trying to create a bootable USB stick on Windows
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

**Addendum**
I have now created a bootable USB from Xubuntu 16.04 LTS download.
Lenovo booted Xubuntu 16.04 LTS from the USB key.
With Xubuntu 16.04 LTS running on my Lenovo from the USB (not installed), I can connect to the Internet via wireless connection.
After removing the USB key, when booting back into Xubuntu 14.04 LTS from the HDD, then I am unable to disconnect the Hotspot
So the problem remains as before.

So, if I install Xubuntu 16.04 LTS from the USB key, will it automatically recognize that the Xubuntu 14.04 LTS is already installed?
Will it provide an upgrade path, so I don't lose any data?
My data is backed up, but I'm not sure whether I would be able to restore it after installing a newer version.

Meanwhile, I have installed Xubuntu 16.04 LTS on the Toshiba computer that I used when I started typing this request for help.
It automatically detected that Windows was already installed, created a partition for itself and installed all right.
During installation, it displayed a line with a checkbox to check for updates while installing. Clicking on the box didn't do anything.
So, I can now get online with the Toshiba notebook, connected wirelessly to either the modem router or the repeater.

[B]Addendum
[/B]I now realize that clicking on the checkbox didn't do anything because the computer wasn't online.

Having successfully installed Xubuntu 16.04 LTS on the Toshiba, I tried installing it on my Lenovo.
However, it didn't detect that Windows was already installed and only offered the choice of installing after reformatting the HDD.
So I cancelled the installation process. 
Is there any way of forcing the install process to detect the existing dual boot, recognize that Windows is installed & just updating Xubuntu?

**Addendum**
I still cannot get online when using the Lenovo with Xubuntu 14.04 LTS.
I would appreciate any assistance on installing bcmwl-kernel-source offline

Via Windows, I downloaded the latest driver v6.30.223.271 for the Broadcom BCM4313 wireless modem in my Lenovo.
I read elsewhere that I need to put the driver files in Home and then from Terminal run :
dpkg -i *.deb
Is this correct?
I have unpacked the .tar.gz which contains two folders: lib & scr plus a file called Makefile
What do I need to do next?

```
pspci -vnn | grep 14e4
Broadcom Corp BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
Subsystem: Broadcom Corp Device [14e4:051b]
```

```
sudo -i
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit
```

---

### Post by jeremy31 on 2016-07-25
It should work after blacklisting those modules

---

### Post by boxcorner on 2016-07-26
Thank you, I will try that now.
This morning I had difficulty getting online via Xubuntu 16.04 LRS that I installed on the Toshiba yesterday.
Then it dawned on me that I should check the Windows dual boot.
Windows ran chdsk then reported a connectivity problem.
I used the Windows diagnostic & can now access either the modem router or repeater from Windows.
Will check that Xubuntu can now be connected later.
Keen to try what you suggested for Xubuntu 14.04 LTS on the Lenovo.

I started doing 
```
uname -r 
then 
dpkd --get-selections ... etc
``` 
on the Lenovo when the Toshiba suddenly restarted Xubuntu for no apparent reason. Now I can't find the rest of what you suggested :~/ Did your remove it? 
Blacklisting those modules didn't seem to make any difference yesterday, though I will try again, in case I made an error.

I did this again
```
sudo -i
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit
```
but it did not make any difference. I checked before & after reboot.
So, Xubuntu 14.04 LTS on the Lenovo remains stubbornly locked on Hotspot.

---

### Post by jeremy31 on 2016-07-26
Can it scan for wifi ```
iwlist scan
```
You may need to ```
sudo rm /etc/NetworkManager/system-connections/Hotspot
```
Reboot and see if the hotspot is gone

---

### Post by boxcorner on 2016-07-26
```
lspci -vvnn | grep -A 9 Network
So, I know:
Chip ID : BCM4313
Wireless Network Adapter ID : [14e4:4727]
Kernel driver in use : bcma-pci-bridge
```

```
iwlist scan
wlan0 No scan results
lo Interface doesn't support scanning.
eth0 Interface doesn't support scanning.
```

```
sudo rm /etc/NetworkManager/system-connections/Hotspot
```
Now rebooting ...

---

### Post by boxcorner on 2016-07-26
Yes!!! Success. That did the trick. 
Sorry about the delay, but the only way of telling whether it is online is to open a tab in Firefox browser, 
as there is not any icon on the taskbar.
Now able to get online from the Lenovo via Xubuntu 14.04 LTS 
Wireless connections modem router & repeater both work.
Many thanks indeed :~)
Having installed Xubuntu 16.04 LTS on the Toshiba, I would like to update the Lenovo to same version.
What is the best way to do that, please?

---

### Post by jeremy31 on 2016-07-26
That question should be posted in the installation subforum

---

### Post by boxcorner on 2016-07-26
All right, I  will do that and mark this thread resolved. Thank you.I

---

