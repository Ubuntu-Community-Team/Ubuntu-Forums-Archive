---
title: "Connecting to a Wireless Network"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by Jesdisciple on 2008-07-26
I can't figure out how to even search for a network.  Help!

---

### Post by robert.wolfe on 2008-07-26
> **Jesdisciple said:**
> I can't figure out how to even search for a network.  Help!

If your wireless adapter is supported, you can left click on the networking icon (next to the speaker icon which is next to the clock on the upper left hand corner of the desktop)  and you will be presented with a listing of wireless networks.  Just left click on the network that you want to connect to.

---

### Post by Jesdisciple on 2008-07-26
I see> Enable Networking
Connection Information
Edit Wireless Networks
About

I think I had it working before I reinstalled Ubuntu to get rid of the broken Windows XP that I had tried to dual-boot.

---

### Post by falcon61102 on 2008-07-26
If you had to reinstall then your network card may not have the proper drivers installed to work.  Try running:
```
lshw -C network
```
And posting the results.

---

### Post by Jesdisciple on 2008-07-26
```
$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:1b:24:51:d1:a5
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.1.64 latency=0 module=sky2 multicast=yes
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=iwl3945 latency=0 module=iwl3945
```

---

### Post by falcon61102 on 2008-07-26
Based on that it looks like your wireless card may not be configured or it may need a new driver.  

Have you attempted to install a driver for your card since reinstalling Ubuntu?

Also, if you go to Hardware Drivers under the System menu, is your card listed there?

---

### Post by Jesdisciple on 2008-07-26
No, I don't recall ever attempting to install drivers for it.

The Hardware Drivers dialog lists nothing.

Thanks a bunch for your time.

---

### Post by Jesdisciple on 2008-07-27
Is there no known solution for this then?  Just to be sure...

---

### Post by falcon61102 on 2008-07-27
I wouldn't give up quite yet.  Try downloading the newest version of the drivers and installing them.

---

### Post by Jesdisciple on 2008-07-27
What drivers?  I'm clueless.

EDIT: [http://intellinuxwireless.org/?p=iwlwifi](http://intellinuxwireless.org/?p=iwlwifi)  The kernel in Hardy Heron is 2.6.24-19-generic so how do I use the driver?

---

### Post by falcon61102 on 2008-07-27
You can try those, but I recommend getting the drivers from your manufacture, which would be intel.  

From what I've heard, the drivers that should work with your card normally come with Ubuntu but for some reason it doesn't seem that yours are loaded.  Have you done a search in the forum for other threads with people having trouble with Intel wireless cards?

---

### Post by falcon61102 on 2008-07-27
Ok, I did some looking around myself and I see that it's not uncommon to have trouble with this card. Check out this thread, and take a look at the third post, the one from chili555.  This may be able to help you.

[http://ubuntuforums.org/showthread.php?t=820297](http://ubuntuforums.org/showthread.php?t=820297)

---

### Post by Jesdisciple on 2008-07-27
That project is from Intel; see the deprecated predecessor at [http://ipw3945.sourceforge.net/]("http://ipw3945.sourceforge.net/").

No, I didn't think to search here; I used Google.

What "switch" is gryzzly referring to in that thread?  Mine seems to be off.```
$ sudo iwlist wlan0 scan
[sudo] password for chris: 
wlan0     Interface doesn't support scanning.
```

linux-backports-modules-hardy-generic installed.  When I went to copy the appropriate command from gryzzly's post, Firefox gave me a strange new error followed by the image (rather than text) context menu???  **EDIT: This problem was caused by my concurrent update and fixed by restarting Firefox as was prescribed by the update mechanism.**  ```
ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],hidden)
5:()
6:()
7:currentEngine()
8:()
9:CM_initMenu([object XULElement],[object XULElement])
10:nsContextMenu([object XULElement],[object XULElement])
11:onpopupshowing([object MouseEvent])
```

Anyway,...```
$ dmesg | grep -i iwl
[   29.273866] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   29.273870] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   29.274064] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   30.119088] iwl3945: Radio Frequency Kill Switch is On:
[   30.124397] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   30.134405] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   30.154322] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   30.181713] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   30.202768] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.
```

I obeyed chili's next post and reaped a slight improvement:  I now see a grayed "Enable Wireless" checkbox below the "Enable Networking" **only when the latter is checked** (i.e. I can't use it).  When it worked before, it was present always and full-color when "Enable Networking" was unchecked.

I'm not sure where to go from here...

---

### Post by falcon61102 on 2008-07-27
Well, that's a really good sign, that means that your card is installed and recognized and now we just need to get it working fully.  Did you try this:

```
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
```

---

### Post by Jesdisciple on 2008-07-27
Yup, I did that two or three times, as it was mentioned in the thread.

My Firefox error was unrelated to this thread.

---

### Post by falcon61102 on 2008-07-27
Ok... it looks like some people are having problems with a switch on their laptop.  Do you have a wireless switch that allows you to turn your wireless on or off?

Also, have you tried adding this to your modprobe file with:
```
sudo su
echo -e 'alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1' > /etc/modprobe.d/iwl3945
reboot
```
Note: that will reboot your system when entered.

And one other thing.  It seems that there is a better driver in the restricted repostitories that you can get.  If you have a wired connection you can take advantage of this:
```
sudo apt-get install linux-backports-modules-hardy-generic
```

Supposedly that has fixed the problem for some people.

---

### Post by Jesdisciple on 2008-07-27
I guess I don't have a switch anymore: [http://ubuntuforums.org/showthread.php?t=41823](http://ubuntuforums.org/showthread.php?t=41823)  (I have an Acer TravelMate 3260.)

I executed that command but saw no changes.

I already installed that package as instructed by the other thread.

---

### Post by falcon61102 on 2008-07-28
> **Jesdisciple said:**
> I guess I don't have a switch anymore: [http://ubuntuforums.org/showthread.php?t=41823](http://ubuntuforums.org/showthread.php?t=41823)  (I have an Acer TravelMate 3260.)


What do you mean by that?

---

### Post by Jesdisciple on 2008-07-28
That thread describes the Windows-only Acer eManagement(I think?) program that apparently contains the switch.  When I reinstalled Ubuntu, I erased every remnant of Windows off my computer.

---

