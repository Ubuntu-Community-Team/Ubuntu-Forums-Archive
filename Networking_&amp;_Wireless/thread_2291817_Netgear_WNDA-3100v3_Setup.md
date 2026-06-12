---
title: "Netgear WNDA-3100v3 Setup?"
date: 2015-08-23
forum: Networking &amp; Wireless
---

### Post by colmeweb on 2015-08-23
So the wifi card on my new computer isn't supported yet.
Bug report if any coders want to solve it and make my life better: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1436940](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1436940)
So I bought a Netgear wnda3100v3 wifi usb. From what I can tell the fastest way to get it running is to install the ndiswrapper. But the main problem that I am having is that all of the instructions I have found didn't work. So now I am asking for direct instructions.

I am running Ubuntu 15.04 on a Lenovo Edge 15
I am trying to install ndiswrapper-1.59
and my lsusb is 
```
Bus 001 Device 006: ID 0846:9014 NetGear, Inc. 
```
Any help would be much appreciated.

---

### Post by kurt18947 on 2015-08-23
Glutton for punishment?:D.  People seem to think that NDISwrapper is a great solution. It's not. It's more of a last ditch 'nothing else has worked so lets try this' solution. Also, the last I knew it works best with Windows XP windows drivers. I expect new hardware to not have Windows XP drivers. You also need to use the correct 32 bit/64 bit driver. Ubuntu 64 bit is common, 64 bit Windows XP drivers may not be. If you're going to buy a new device, why not buy one known to be plug 'n' play?  They're out there, a search in this networking & wireless forum should show some recommendations.  

A commonly available adapter - though not the fastest - is Netgear WNA1100 aka N150. Another I've had good luck with is TrendNet TEW-649UB v1.0 which is a bit faster - 300 down/150 supposedly. It can be risky to recommend wifi adapters because Linux WiFi cares mostly about the chipset, not brand/model. Some manufacturers, D-link seems to be good at this - will change chipsets within a model, changing only a model suffix which is not shown on the package. Model USBabc v.1 will be plug 'n' play, works great. Model USBabc v.2 may not work at all. The only way to tell whether USBabc is v.1 or v.2 is to open the package and read the label on the device, unfortunately. There's no indication on the packaging. 

Lest you think I'm being a negative Nancy, here is what Wikidevi has to say about WNDA-3100 v.3

[https://wikidevi.com/wiki/Netgear_WNDA3100v3](https://wikidevi.com/wiki/Netgear_WNDA3100v3)

**Probable Linux driver**
unknown
**[USB ID not yet observed in any mainline kernel / this list]("https://wikidevi.com/wiki/List_of_Wi-Fi_Device_IDs_in_Linux")**

WNDA-3100 v3. appears to use a MediaTek MT7632U chip. Here is MediaTek's download page:

[http://www.mediatek.com/en/downloads1/downloads/](http://www.mediatek.com/en/downloads1/downloads/)

The closest I see is MT7630 and it's Windows only. MediaTek used to be Ralink and they used to be pretty linux friendly. I expect we'll see support for this chipset eventually.

Edit: if you're knowledgeable and adventurous, there may be something here from Larry Finger:

[https://github.com/lwfinger/mt7630](https://github.com/lwfinger/mt7630)

If you go down this road, would you let us know how you make out?

I hope this is of some help to you.

---

### Post by colmeweb on 2015-08-23
I have the driver, but I have never installed a windows driver into ubuntu. Does anybody have a link to a quick guide or know the terminal commands. 
Everything is in the Downloads folder by the way.

---

### Post by chili555 on 2015-08-24
> **colmeweb said:**
> I have the driver, but I have never installed a windows driver into ubuntu. Does anybody have a link to a quick guide or know the terminal commands. 
Everything is in the Downloads folder by the way.Do you have the Windows ***XP*** drivers, .inf and .sys matching your architecture; either 32- or 64-bit?

---

### Post by colmeweb on 2015-08-24
The driver is 7/8/8.1 all 32 and 64

My computer is 64

---

### Post by praseodym on 2015-08-24
Try win7 64bit

---

### Post by chili555 on 2015-08-24
From *man ndiswrapper-1.9*:> DESCRIPTION
       ndiswrapper is two parts: user space tool that is used to install  Win&#8208;
       dows  XP drivers and kernel module to load the Windows XP drivers. Both
       are called ndiswrapper.
I will be very interested to see the result with Windows 7.

---

### Post by colmeweb on 2015-08-24
My problem now is that I have never installed a windows driver and am not sure how to go about it with or without the ndiswrapper.

---

### Post by chili555 on 2015-08-24
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

You can probably start at item 3.6.

---

### Post by colmeweb on 2015-08-24
So I think I installed it, but still no reaction, did I do something wrong, or is a w7 driver just not doing it?

```

@Lenovo-Edge:~$ cd Downloads/Disk1/drivers/Win7/x64@Lenovo-Edge:~/Downloads/Disk1/drivers/Win7/x64$ sudo ndiswrapper -i netr28x.inf
[sudo] password for : 
installing netr28x ...
@Lenovo-Edge:~/Downloads/Disk1/drivers/Win7/x64$ ndiswrapper -1
install/manage Windows drivers for ndiswrapper


usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information


where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
@Lenovo-Edge:~/Downloads/Disk1/drivers/Win7/x64$ 



```

---

### Post by chili555 on 2015-08-26
> @Lenovo-Edge:~/Downloads/Disk1/drivers/Win7/x64$ ndiswrapper -1It is not 1 (one); it is l (L for 'list'). Please try again:```
ndiswrapper -l
```Also let us see:```
sudo modprobe ndiswrapper
dmesg | grep ndis
```

---

### Post by colmeweb on 2015-08-27
Sorry about that
```

colin@Lenovo-Edge:~$ ndiswrapper -lnetr28 : invalid driver!
netr28x : driver installed

```

and

```

@Lenovo-Edge:~$ sudo modprobe ndiswrapper
[sudo] password for : 
@Lenovo-Edge:~$ dmesg | grep ndis
[ 8864.735262] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[ 8864.774324] usbcore: registered new interface driver ndiswrapper

```

---

### Post by chili555 on 2015-08-27
> colin@Lenovo-Edge:~$ ndiswrapper -lnetr28 : invalid driver!Did you type:```
ndiswrapper -lnetr28
```Or did you type  the correct command:```
ndiswrapper -l
```And the terminal returned:```
netr28 : invalid driver!
```If the latter, then I suspect we now know that Windows 7 drivers will not work.

---

### Post by colmeweb on 2015-08-27
Yeah thats what I figured.

@Lenovo-Edge:~$ ndiswrapper -l
netr28 : invalid driver!
netr28x : driver installed

---

### Post by chili555 on 2015-08-27
Please see: [http://ubuntuforums.org/showthread.php?t=2233349](http://ubuntuforums.org/showthread.php?t=2233349) 

[http://www.htpcbeginner.com/5-best-ubuntu-compatible-wireless-cards-usb/](http://www.htpcbeginner.com/5-best-ubuntu-compatible-wireless-cards-usb/)

[http://askubuntu.com/questions/458774/usb-wifi-adapter-compatibility](http://askubuntu.com/questions/458774/usb-wifi-adapter-compatibility)

---

### Post by colmeweb on 2015-08-31
Sorry everybody, I took the cowards way out.

[http://ubuntuforums.org/showthread.php?t=2235778](http://ubuntuforums.org/showthread.php?t=2235778) (and I am responding with it now)

One way or another chili555 always ends up helping. Thanks everybody.

---

### Post by john551 on 2016-05-10
Hate to resurrect an old thread, but has this ever been resolved? I am currently facing the same issue and have found solutions for v1 and v2 WNDA3100, but not v3. The online drivers only have an exe setup file, and the files in Windows/System32 are sys and bin with no INF (probably because windows 10). Any other suggestions?

---

### Post by chili555 on 2016-05-10
> **john551 said:**
> Hate to resurrect an old thread, but has this ever been resolved? I am currently facing the same issue and have found solutions for v1 and v2 WNDA3100, but not v3. The online drivers only have an exe setup file, and the files in Windows/System32 are sys and bin with no INF (probably because windows 10). Any other suggestions?Can you confirm that you have the exact same device as in post #1? If so, this may be your lucky day.


--------------
Possible references: [https://wikidevi.com/wiki/Netgear_WNDA3100v3](https://wikidevi.com/wiki/Netgear_WNDA3100v3)
[https://github.com/jurobystricky/Netgear-A6210](https://github.com/jurobystricky/Netgear-A6210)

```
$ modinfo os/linux/mt7662u_sta.ko
filename:       /home/chili/Desktop/Forum/Netgear-A6210/os/linux/mt7662u_sta.ko
version:        3.0.0.1
license:        GPL
description:    Ralink Wireless Lan Linux Driver
author:         Ralink
srcversion:     D5F92FD6B0AB783A35795FA
alias:          usb:v0E8Dp7662d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0E8Dp7632d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0E8Dp7612d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v045Ep02E6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17EBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9053d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p180Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v[COLOR="#FF0000"]0846[/COLOR]p[COLOR="#FF0000"]9014[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*
depends:        cfg80211
vermagic:       4.4.6-040406-generic SMP mod_unload modversions 
parm:           mac:rt_wifi: wireless mac addr (charp)
parm:           mode:rt_wifi: wireless operation mode (charp)

```

---

### Post by john551 on 2016-05-10
The model number on the box says Netgear WNDA3100 v3 and output when running lsusb shows the same device id:
0846:9014 Netgear, Inc.

I first followed one of the steps using ndiswrapper and installed one of the [COLOR=#000000][FONT=Ubuntu Mono]bcmn43xx64 inf and sys files given in one of the posts. That didn't work so i removed that bcmn43xx64 file.
[/FONT][/COLOR]
I then followed these steps from [http://ubuntuforums.org/showthread.php?t=2321779&page=2&highlight=wnda3100v3](http://ubuntuforums.org/showthread.php?t=2321779&page=2&highlight=wnda3100v3) (I am currently connected with ethernet while trying to get the usb adapter to work) and did the given commands:
```

git clone https://github.com/jurobystricky/Netgear-A6210
cd Netgear-A6210
make
sudo make install

```

Still no difference, I checked the file [COLOR=#333333][FONT=Helvetica Neue]rtusb_dev_id.c to make sure the device id is there, it is.

i did:
```

sudo service network-manager restart

```
but Wifi still not detected.

P.S: This Ubuntu community seems wonderful. Going through the different topics in regards to the wnda3100, there are so many helpful responses to each issue. I know I will love it here, and hope to one day contribute and get some bug fixes in![/FONT][/COLOR]

---

### Post by chili555 on 2016-05-10
> git clone [https://github.com/jurobystricky/Netgear-A6210](https://github.com/jurobystricky/Netgear-A6210)
cd Netgear-A6210
make
sudo make installDid it actually clone??

I think you actually want:```
git clone https://github.com/jurobystricky/Netgear-A6210.git
cd Netgear-A6210
make
sudo make install

```

---

### Post by john551 on 2016-05-10
My first attempt, I used the git clone command on a laptop with internet access connected to my router. I then copied the folder that it cloned onto the Ubuntu Desktop. This should be the same, right? After that didn't work, I decided to wire my Desktop with Ubuntu and run the git command. Git was not installed and code:
```
 sudo apt-get update 
```
was needed to install git. I then redid the clone and did commands posted in comment #19. The Netgear-A6210 folder was there on my Desktop(although it could have been the file I copied over from my laptop) I can delete it and redo it if that could make a difference.

---

### Post by chili555 on 2016-05-11
> **john551 said:**
> My first attempt, I used the git clone command on a laptop with internet access connected to my router. I then copied the folder that it cloned onto the Ubuntu Desktop. This should be the same, right? After that didn't work, I decided to wire my Desktop with Ubuntu and run the git command. Git was not installed and code:
```
 sudo apt-get update 
```
was needed to install git. I then redid the clone and did commands posted in comment #19. The Netgear-A6210 folder was there on my Desktop(although it could have been the file I copied over from my laptop) I can delete it and redo it if that could make a difference.So you redid the steps and all of them went without error. After a reboot, the wireless does or does not work? Did the correct module mt7662u_sta load? Check:```
lsmod | grep mt76
```If not, load it:```
sudo modprobe mt7662u_sta
```Any complaints or errors? Are there any clues in the logs?```
dmesg | grep mt76
```

---

### Post by john551 on 2016-05-11
There were no errors when running the make and sudo make install command. The wireless still does not work after restart.

lsmod | grep mt76 outputs nothing,

sudo modprobe mt7662u_sta outputs: Modprobe: ERROR: coult not insert 'mt7662u_sta' : required key not available

dmesg | grep mt76 outputs nothing.

---

### Post by chili555 on 2016-05-11
> ERROR: coult not insert 'mt7662u_sta' : required key not availableUh, oh!

Please see: [http://askubuntu.com/questions/770490/broadcom-wireless-drivers-unclaimed-after-installing-update-16-04/770774#770774](http://askubuntu.com/questions/770490/broadcom-wireless-drivers-unclaimed-after-installing-update-16-04/770774#770774)

You may not need to rebuild the driver. Just try turning off Secure Boot.

---

### Post by john551 on 2016-05-12
You sir, are my hero! Everything is up and running with no problems. After I disabled Secure Boot on the BIOS, Ubuntu booted up and WiFi networks were found and I was able to connect to my access point! Thank you so much!

---

