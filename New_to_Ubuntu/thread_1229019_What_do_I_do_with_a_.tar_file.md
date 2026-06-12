---
title: "What do I do with a .tar file?"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by StevenD on 2009-08-01
I have a file named linus_wlan_ng_0114_pre1_dr.tar_0. It is supposed to be a Linksys driver file for my Linksys WUSB11 wireless adapter.:confused:

What do I do with it? Or how do I get it installed?

Steven

---

### Post by JohnnySage50307 on 2009-08-01
A .tar file is a general encapsulation tool.  You should use the following command:
```
tar -xvf [tarfile]
```
where [tarfile] is the name of your .tar file.  Note, usually these files are compressed with either gzip or bzip2 and therefore their extentions are .tar.gz or .tar.bz2.  In either case you want
 
```
tar -xvjf [tar.bz2 file] 
``` for .tar.bzip2 files or
```
tar -xvzf [tar.gz file] 
``` for .tar.gz files.
 
Hopefully this helps!  When in doubt, look at tar's manpage!

---

### Post by cariboo on 2009-08-01
Before trying to install any drivers, I would suggest you check and see if the driver is already loaded. Open an Applications-->Accessories-->Terminal and type:

```
sudo lshw -C network
```

The above command will list your network devices and whether it has been detected and the driver loaded. You can pipe the output to a text file if you need to move to a computer with a network connection, to do this run the following command:

```
sudo lshw -C network > network,txt
```

---

### Post by Sealbhach on 2009-08-01
You can also double-click on a tar file and select "extract here".

.

---

### Post by StevenD on 2009-08-01
[FONT=&quot]Ok I ran the first option sudo lshw -C network and got this as a result but since I am new to all this stuff I can't tell what I am looking for. Am I supposed to see the Linksys WUSB11 USB adapter listed here? It is connected.[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot]steven@steven-laptop:~$ sudo lshw -C network
[sudo] password for steven: 
  *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 83
       serial: 00:08:0d:1f:4d:cb
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 3e:49:27:85:b9:8c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:06:25:a5:b3:51
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-DS[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot]I ran the second option in the terminal and got this as a result.[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot] steven@steven-laptop:~$ sudo lshw -C network > network, txt
Hardware Lister (lshw) - B.02.13
usage: lshw [-format] [-options ...]
       lshw -version

      -version        print program version (B.02.13)

format can be
      -html           output hardware tree as HTML
      -xml            output hardware tree as XML
      -short          output hardware paths
      -businfo        output bus information

options can be
      -class CLASS    only show a certain class of hardware
      -C CLASS        same as '-class CLASS'
      -c CLASS        same as '-class CLASS'
      -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
      -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
      -quiet          don't display status
      -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
      -numeric        output numeric IDs (for PCI, USB, etc.)[/FONT]

[FONT=&quot][/FONT]
[FONT=&quot]Also the original driver file that I downloaded from the web (from my Window Vista machine and copied the download to my memory stick and put it on my Ubuntu laptop) was a .gz file which I extracted. According to what is being said here I need to extract it again which I did. so now I have a file named linux_wlan-ng-0.1.14-pre1.[/FONT]

[FONT=&quot][/FONT]
[FONT=&quot]I have been spending most of this week trying to get some use out of the USB adapter with no such luck so far. I have tried consulting several documents online but have had no luck so far. The one I was hoping would help hasn't been too much of a help.[/FONT]

[FONT=&quot][/FONT]
[FONT=&quot]https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB11[/FONT]

[FONT=&quot][/FONT]
[FONT=&quot]So I thought I would try and get a driver for it as was suggested in the page at the above link.[/FONT]

[FONT=&quot][/FONT]
[FONT=&quot]I appreciate the help so far and any further help.[/FONT]

[FONT=&quot][/FONT]
[FONT=&quot]Steven
[/FONT]

---

### Post by StevenD on 2009-08-01
I forgot to ask now that I have the linux-wlan-ng-0.0.14-pre1 folder extracted and assuming it is not already installed how do I get it installed. I'm so used to using .exe files in Windows that all I have to do is double click on it to get the installer running that I don't know what the proceedure is for Ubuntu.:confused:

---

### Post by Sealbhach on 2009-08-01
This is what the lshw command says about your wireless interface:

```
*-network:1
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:06:25:a5:b3:51
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-DS
```[FONT=&quot]
[/FONT]Normally, it would show a product and vendor if it recognised the device. Can you tell us want make and model your computer is? Just to ensure we find teh right driver for you.

EDIT: I got that from your other thread


steven@steven-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 066b:2212 Linksys, Inc. WUSB11v2.5 802.11b Adapter
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 2222:3080 MacAlly 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
steven@steven-laptop:~$


OK, well this device should work out of the box with Ubuntu since Ubuntu 8.04
[I]
Since Ubuntu 8.04, the driver works out of the box without installing any packages and the linux-wlan-ng package is only needed if you use the firmware RAM loading for "updating" firmware on-the-fly.[/I]

from here:

[https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb)

The driver it uses is "prism2_usb".

What happens if you try to load the module using this command in the terminal?

```
sudo modprobe prism2_usb
```


.

---

### Post by StevenD on 2009-08-02
I tried "sudo modprobe prism2_usb" and nothing happened.

last night when I came to shut the Ubuntu machine down for the night all of a sudden the network icon at the top right of the screen indicated that it was trying to connect to the wireless network. That is the first time that happened and I have no idea how it happened. It never did connect and I kept getting a message come up that wanted me to type a password into it. I tried some passwords but nothing seemed to work. I can't duplucate it now.

My Netgear wireless router uses a WPA & WPA2 for the security setting. Maybe I need to use something different for this wireless usb adapter.

I get nothing this morning. Most of the time when I hover over the icon it says "No network connection". Last night when I clicked on the icon I did see that my wireless network was showing up.

I read in the help that "If you have a wired network connection as well as an wireless connection, the wired connection will be used by default." When I open up Network Connections dialog there are two connections listed in the Wired tab ie. Auto eth0 and Auto wlan0. Most of the time in the Wireless tab there is nothing listed. I have tried to add something before but end up deleting anything I add. Last night there was one listed there. But since nothing is working I have deleted all listings in the Wireless tab.

Should I get rid of the two connection listed in the Wired tab?

Steven :(

---

### Post by StevenD on 2009-08-02
I can also see when I click on the network icon at the top right of the screen that "Wired Network (Linksys WUSB11v2.5 802.11b Adapter)" is grayed out as is "Wired Network (Toshiba America Info Systems 82801DB Pro/100 VE (MOB) Ethernet Controller)".

Steven

---

### Post by Sealbhach on 2009-08-02
It looks like your wireless is working but I don't understand why sometimes there is no wireless visible. Have you entered the WPA password in your Edit Connections? The password you got from your ISP? 

Another thing to try, when you see a wireless connection avialable, is enter this in a terminal:
```

sudo dhclient wlan0
```
If it doesn't connect, copy and paste here the reply you get from the terminal. You're really close I think, it just takes a little more tinkering. Another good idea is to read the documentation that came with your router, the connection details you enter will be pretty much the same as for Windows (passwords etc).

.

---

### Post by StevenD on 2009-08-02
Thanks for all the help. One more thing before I try anything else. I just tried setting up or adding a new connection in the Network Connections and when I typed in the password for the WPA & WPA2 Personal setting I get a message asking for a password for default keyring to unlock. What is this default keyring?

Steven

---

### Post by bkratz on 2009-08-02
> **StevenD said:**
> Thanks for all the help. One more thing before I try anything else. I just tried setting up or adding a new connection in the Network Connections and when I typed in the password for the WPA & WPA2 Personal setting I get a message asking for a password for default keyring to unlock. What is this default keyring?

Steven



StevenD


The keyring password would most likely be the same as your sudo password (main password) . Once you finally get logged in there is a checkbox ( I think it says something like---make available to all users or some such--not on my Ubuntu system right now--which will make this not a problem).  You might want to temporarily go to an open network connection until all this gets resolved.  Also make sure it is not a hidden network.  You might do a "iwlist scan wlan0" command and see it you see some networks.

---

### Post by Sealbhach on 2009-08-02
> **StevenD said:**
>  What is this default keyring?


Yeah, just use your main Ubuntu administrator password for the keyring.

.

---

### Post by StevenD on 2009-08-02
> **Sealbhach said:**
> Yeah, just use your main Ubuntu administrator password for the keyring.

.

I tried that and I keep getting asked to enter a password. This happens over and over.:(

Steven

---

### Post by Sealbhach on 2009-08-02
> **StevenD said:**
> I tried that and I keep getting asked to enter a password. This happens over and over.:(

Steven

I think I got that happening to me at one time, just enter the password once and press enter, if it asks again just click cancel or what ever it was. There's a way to stop that keyring message coming up that we can look at later.

.

---

### Post by StevenD on 2009-08-02
Nothing is working. I wonder if the USB Adapter is not working. I get nothing showing in the NetworkManager icon when I either left click on it. I have fiddled with this stuff for several days now. I am thinking about reinstalling Ubuntu and starting over from the beginning. Every time I read directions in the help or online articles parts of the directions work but some of the others don't.:(:(:(

Steven

---

### Post by Sealbhach on 2009-08-02
> **StevenD said:**
> Nothing is working. I wonder if the USB Adapter is not working. I get nothing showing in the NetworkManager icon when I either left click on it. I have fiddled with this stuff for several days now. I am thinking about reinstalling Ubuntu and starting over from the beginning. Every time I read directions in the help or online articles parts of the directions work but some of the others don't.:(:(:(

Steven

It's strange that you can sometimes see a network but sometimes not. A re-install is not a bad idea, go for it and start a new thread if you still have problems with the wireless. Also, can you test the USB adapter on a Windows machine, to make sure it's not faulty?

.

---

### Post by StevenD on 2009-08-02
> **Sealbhach said:**
> It's strange that you can sometimes see a network but sometimes not. A re-install is not a bad idea, go for it and start a new thread if you still have problems with the wireless. Also, can you test the USB adapter on a Windows machine, to make sure it's not faulty?

.

Thanks for the help so far. I am going to do that. I am in the process now of downloading Ubuntu 9.04 and will make another disc. I did a scan of the original disc to see if it was good and got the message that there was one item that failed. We shall see if this new one is better. That is a good idea to test the adapter on a windows machine. I am also going to check with the guy who gave me this USB adapter and see if he has anything else to try. I really want this to work so I can give Ubuntu a fair shake.

As a side note I'm still not sure how to install a driver. I have the driver I got from the Linksys site for this USB adapter and extracted it so it is sitting on the desktop.

I right clicked this file "linux_wlan_ng_0114_pre1_dr.tar_0.gz" and selected Extract Here which gave me this file "linux_wlan_ng_0114_pre1_dr.tar_0" I then right clicked it and it got this folder "linux-wlan-ng-0.1.14-pre1" on the desktop that is just sitting there and I have no idea what to do with it not that I have it.

I want to get connected to web so I can install stuff like Inkscape and Scribus.

---

### Post by Sealbhach on 2009-08-03
> **StevenD said:**
> 
As a side note I'm still not sure how to install a driver. I have the driver I got from the Linksys site for this USB adapter and extracted it so it is sitting on the desktop.


You don't need to install a driver for that model of USB adaptor. 

There's already a driver for that included in the Linux kernel. It's called **prism2_usb**. So for most people who install Ubuntu, the USB adapter already works right out of the box.

.

---

### Post by 3rdalbum on 2009-08-03
Try moving the computer closer to the router. The driver in Ubuntu isn't exactly the same as the one in Vista, and you might have a reduced range in Ubuntu, or the driver might be set up to use a lower transmission power by default.

---

### Post by StevenD on 2009-08-04
> **3rdalbum said:**
> Try moving the computer closer to the router. The driver in Ubuntu isn't exactly the same as the one in Vista, and you might have a reduced range in Ubuntu, or the driver might be set up to use a lower transmission power by default.

It has been less than 3 feet away from the router the whole time I have been working on this. I have begun to wonder about the transmission power issue you mention.

---

### Post by StevenD on 2009-08-04
[SIZE=2]Okay here is a new one. The same guy at work just gave me a US Robotics 54Mbps USB Adapter to try out and see if that makes a difference. I looked it up at,

[http://linux-wless.passys.nl/query_alles.php](http://linux-wless.passys.nl/query_alles.php)

and found it listed but it looks like it may not work. Here is the info it gives.

Manufacturer:
US Robotics

wlan type:
802.11g

Product ID:
USR5422

Vendor & product code:
Nothing listed

Host I/F:
USB

Chipset:
Prism GT

Driver:
Prism54

Works with Linux:
Grey (which according the legend at the top of the page means unknown)

Since it doesn't say anything about prism2 then it looks like it may not work on what I have. Anyone care to confirm what I am thinking is right or wrong?
[/SIZE]

---

### Post by StevenD on 2009-08-05
Well it didn't work. So I finally hooked the thing up to a wired connection by pulling off the cable and plugging it in to the laptop and downloaded and installed what I needed. Worked like a charm. This doesn't mean I am giving up on the wireless scene. But for now I have been appeased some what.:)

---

### Post by bkratz on 2009-08-05
> **StevenD said:**
> Well it didn't work. So I finally hooked the thing up to a wired connection by pulling off the cable and plugging it in to the laptop and downloaded and installed what I needed. Worked like a charm. This doesn't mean I am giving up on the wireless scene. But for now I have been appeased some what.:)



Was that the original adapter or the second one.  You might want to tell us what you did to get it to work, there may be others in the same condition.

---

### Post by StevenD on 2009-08-05
Sorry I don't think I explained it clearly. The second adapter (US Robotics) didn't work and the Linksys one still doesn't either. In fact I can't get any wireless connections. I unplugged the cable that goes into my Netgear wireless router and plugged it into my Ubuntu laptop and was able to get my connection. I then unplugged it from the laptop and plugged it back into the Netgear router. So I am still without wireless capability. I am still going to work on getting the Linksys USB adapter to work before giving up on it completely.

Again thanks for the help on this. I am going to give it a rest and my nerves for a few days before working on it again. I am going to try and learn some about working with Ubuntu in the mean time.

Steven

---

