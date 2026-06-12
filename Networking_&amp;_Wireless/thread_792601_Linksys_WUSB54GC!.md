---
title: "Linksys WUSB54GC!"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by Milardo on 2008-05-13
I wonder how can I get my linksys wusb54gc compact wireless g usb adapter to work in latest ubuntu? I've been trying to get it to work ever since 3 older ubuntu releases, tried following other peoples' scripts, etc. but don't work. I also need to enable wpa2 support if possible. Also my password is long, does that matter? What to do?

---

### Post by chili555 on 2008-05-13
Is this an rt73 chipset? You can confirm with one of these, with the device plugged in:```
sudo lsusb -vv
sudo lshw -C network
```If you need to post these, please omit any details not related to your wireless. If it is an rt73, you might try:```
sudo apt-get install linux-backports-modules-hardy-generic
```It includes a newer, improved rt73usb driver.

Please post your progress.

---

### Post by IamAcoconut on 2008-05-13
```
sudo lsusb -vv
```gives me anything but chipset name
```
sudo lshw -C network
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan2
       serial: 00:1e:e5:9f:24:00
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT73 WLAN

``` Indeed, it's a Ralink chipset.

Here's a script that's supposed to handle driver installation: [http://ubuntuforums.org/showthread.php?t=516649&highlight=WUSB54GC&page=12](http://ubuntuforums.org/showthread.php?t=516649&highlight=WUSB54GC&page=12)
Yup, page 12. First refers to ndiswrapper.
You may as well DIY using the same SerialMonkey drivers, or original ones.
Both described here:
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73)
And just the latter also here:
[http://wiki.archlinux.org/index.php/RT73_Wireless](http://wiki.archlinux.org/index.php/RT73_Wireless)

I tried it with newst SerialMonkey drivers, but to no avail. Still gotta check a few things though, then I'll go the other way.

---

### Post by Tom--d on 2008-05-13
When I had that wireless usb, I installed ndiswrapper and used the rt73 windows driver.

Works perfect with it! :)

---

### Post by IamAcoconut on 2008-05-13
[QUOTE="Tom--d"]When I had that wireless usb, I installed ndiswrapper and used the rt73 windows driver.
[/QUOTE]Well, fine, but it's not a way. It's a workaround. Which you can easily setup with backtracing the thread I linked. 
I need monitor mode for instance, which is not supported by ndiswrapper.

---

### Post by Milardo on 2008-05-14
Still can't get it to work. Looking at the adapter itself, from time to time it flashes really fast like it is trying to get recognized. I have to connect to router that has a pretty long password/key for wpa/wpa2 personal. i find that i can't really type it in all the way at least i think. Anybody know of that problem? What else can I do?

---

### Post by IamAcoconut on 2008-05-19
I'm sorry for being so late!

**Milardo**, does your Linksys work with unencrypted networks, or not at all? What's the driver you use.

My WUSB54GC works ok as far as I checked - managed mode, no encryption and monitor mode. It works with the standard Ubuntu 7.10 rt73usb driver everyone told  me to blacklist in favor of others. I ran the uninstall script (serial monkey drivers) and just used the system driver. Major downside is the adapter not being recognized by Wicd or network-manager.

Maybe I still could have run it on those drivers I mentioned earlier - could have fu*ked something up - but I don't have all the time to just sit and work on it... Yet I hope this post will be at least slightly helpful.

*Update*
Is Master mode supposed to work with this adapter? I've been told so, but it doesn't. With neither SM rt73 nor rt73usb. 
*Update*
The original driver (RT73_Linux_STA_Drv1.0.4.0) only makes it worse (no monitor mode).

---

### Post by Milardo on 2008-05-19
Doesn't work at all. I've tried many different installation methods, like trying to install ndiswrapper which couldn't install. Tried to compile the ralink driver didn't work.

---

### Post by IamAcoconut on 2008-05-19
> **Milardo said:**
> Doesn't work at all. I've tried many different installation methods, like trying to install ndiswrapper which couldn't install. Tried to compile the ralink driver didn't work.
But you tried it from the terminal? ifconfig, iwconfig, iwlist
Just to make sure - I didn't see anything with GUI tools, yet the card was working.

---

### Post by Milardo on 2008-05-26
okay I installed ndisgtk like and a rt73.inf for the driver as documented here.  

[https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html)

But how to connect to nonbroadcasting router, tried to type in ssid and have to choose wpa personal and type password but didn't work. What should I do?:confused:

---

### Post by IamAcoconut on 2008-05-27
> **Milardo said:**
> okay I installed ndisgtk like and a rt73.inf for the driver as documented here.  

[https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html)

But how to connect to nonbroadcasting router, tried to type in ssid and have to choose wpa personal and type password but didn't work. What should I do?:confused:
I take it you answer positively to my previous question. First try Wicd.
Go to preferences, and set wext as wpa_supplicant. Then click "network"->"hidden network".  [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,wpa/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,wpa/)

---

### Post by LordDijon on 2008-05-28
I am trying to up-date my WUSB54GC, but im a noob with limited knowledge and I have a few questions, first my WUSB54GC fails to show a Version #, how might I find this out, second how can I be sure I have the latest drivers and firmware installed from Ralink tech.. also how to install these would be nice.  I currently am running Xubuntu 8.0.4 HH on an old P3 laptop I want to develop as a wireless security self-education rig...Here is what I have....

lorddijon@lorddijon-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 41
       serial: 00:02:a5:b6:48:96
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1c:10:63:90:aa
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=10.0.0.5 multicast=yes wireless=IEEE 802.11g

---

### Post by IamAcoconut on 2008-05-29
> **LordDijon said:**
> I am trying to up-date my WUSB54GC, but im a noob with limited knowledge and I have a few questions, first my WUSB54GC fails to show a Version #, how might I find this out, second how can I be sure I have the latest drivers and firmware installed from Ralink tech.. also how to install these would be nice.
Pal, it's all been said! Save for the chipset version - why do you need to know that? It's RT73 in every model AFAIK. 
```
lsmod |grep rt73
modinfo <drivername>
```
It's likely you just have the rt73usb, probably not loaded as your card wasn't recognized.
In such case ```
sudo modprobe rt73usb
``` no matter if it's SerialMonkey or system provided. Should GUI tools fail to recognize any networks try ```
iwlist wlan0 scan
```

---

### Post by scottslinux on 2008-05-29
I have a wusb54G and have been unable to get it to work until.....last night!!

I installed wicd and in preferences chose the WEXT driver. Then to my amazement..it worked.  I tried all of the suggestions that everyone has made  to no avail.  

I hope this works for you.  Check the wiki page for wicd for the download.

Good luck!

Scott

---

### Post by IamAcoconut on 2008-05-30
> **scottslinux said:**
> I installed wicd and in preferences chose the WEXT driver. Then to my amazement..it worked.  I tried **all** of the suggestions that **everyone** has made  to **no avail**.
as I had posted above:
> **IamAcoconut said:**
> First try [COLOR="Red"]Wicd.[/COLOR]
Go to preferences, and set [COLOR="Red"]wext[/COLOR] as [COLOR="Red"]wpa_supplicant[/COLOR].
;) Thanks anyway. 
Then again, ndiswrapper is just a workaround - no Master, no Monitor.

---

### Post by Milardo on 2008-05-30
Okay I got internet working by using this article.

[https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html)

I used the cd to install ndiswrapper.

Tried using wicd but doesn't seem work or seem to have an option for encryption. Anyways I got internet to work by using nmapplet, you left click on top right icon that has dual monitors. Works well. However network manager doesn't work there isn't even an option to enter correct encryption! 

My question now is where can I make a profile or save internet ssid/encryption/password so I can just click on it and get on the internet and not have to reenter settings everytime?

---

