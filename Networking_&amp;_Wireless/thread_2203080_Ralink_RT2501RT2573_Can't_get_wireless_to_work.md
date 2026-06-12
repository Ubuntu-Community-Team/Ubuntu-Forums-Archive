---
title: "Ralink RT2501/RT2573: Can't get wireless to work"
date: 2014-02-01
forum: Networking &amp; Wireless
---

### Post by audun2 on 2014-02-01
Hello everyone!

I recently installed Ubuntu desktop 12.04 LTS. However i can not for the life of me get the wireless internet connection to work. 
I might add that I am a complete noob when it comes to Ubuntu.
The usb-wireless thingy I'm usin connects just fine in windows 7, so its not a hardware related problem. 
I am also fairly certain that the correct driver is installed.

I have no idea what to type in the different fields in the Network Connections window.


Network Connections window:
[http://i.imgur.com/Z9OHuKq.png](http://i.imgur.com/Z9OHuKq.png)
[http://i.imgur.com/6FEG9rb.png](http://i.imgur.com/6FEG9rb.png)
[http://i.imgur.com/YC9c7Yw.png](http://i.imgur.com/YC9c7Yw.png)
[http://i.imgur.com/KUvfLql.png](http://i.imgur.com/KUvfLql.png)

ifconfig, iwconfig
[http://i.imgur.com/fsxCjHh.png](http://i.imgur.com/fsxCjHh.png)
[http://i.imgur.com/qv17sh3.png](http://i.imgur.com/qv17sh3.png)
[http://i.imgur.com/TxUU553.png](http://i.imgur.com/TxUU553.png)

Can anyone help?

---

### Post by PotatoHead007 on 2014-02-01
When you click on the Connections menu top right of your screen, do you see your router? By your description, i am not sure if your usb-wireless thingy is a dongle that supports wireless connection, or one of those USB devices you plug into a Desktop to connect to a wireless connection. Can you please be speciefic?

---

### Post by audun2 on 2014-02-01
It says CNet Wireless-G Long Range USB Adapter? It
It connects to the usb-port and connects to the internet :p
Yes I do see the router.
When I try to connect to it nothing happens and after i while it requests the password again :/

---

### Post by audun2 on 2014-02-01
This is what it looks like
[IMG]http://i.imgur.com/rk4S04U.jpg[/IMG]

---

### Post by PotatoHead007 on 2014-02-01
Sounds like you wrote the password wrong first time round. In the Network tab(the top right of your screen), click on "Edit connections". From there, navigate to the wireless tab. Your router should be listed, select it and click Edit. It will open a new window, from which you go to the "Wireless Security" tab. Click "Show password", and check if you wrote it right. Gotta go to bed now, will check again tomorrow :)

---

### Post by wildmanne39 on 2014-02-01
Please use thumbnails or url's when posting images because many people have slow internet connections and cannot load pages with large images.
Thanks

---

### Post by wildmanne39 on 2014-02-01
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by audun2 on 2014-02-04
Here's the contents of the wireless-info.txt

```


*************** info trace ***************


***** uname -a *****


Linux spaken-To-be-filled-by-O-E-M 3.8.0-29-generic #42~precise1-Ubuntu SMP Wed Aug 14 16:19:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise


***** lspci *****


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
    Kernel driver in use: r8169


***** lsusb *****


Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter
Bus 002 Device 003: ID 0781:5575 SanDisk Corp. 
Bus 005 Device 002: ID 093a:2521 Pixart Imaging, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


***** rfkill *****


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


***** lsmod *****


rt73usb                31676  0 
crc_itu_t              12707  1 rt73usb
rt2x00usb              20779  1 rt73usb
rt2x00lib              55503  2 rt73usb,rt2x00usb
mac80211              630977  2 rt2x00usb,rt2x00lib
cfg80211              525244  2 rt2x00lib,mac80211


***** nm-tool *****


NetworkManager Tool


State: disconnected


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt73usb
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off






***** NetworkManager.state *****


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****




[main]
plugins=ifupdown,keyfile
dns=dnsmasq


no-auto-default=<MAC address removed>,


[ifupdown]
managed=false


***** interfaces *****


auto lo
iface lo inet loopback




***** iwlist *****




***** resolv.conf *****




***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


***** modinfo *****


filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
license:        GPL
firmware:       rt73.bin
description:    Ralink RT73 USB Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     246FEEC23EA0D5DB663C1D3
alias:          usb:v0586p3415d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CDEp001Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7167p3840d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB50d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB01d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p200Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v6933p5001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0769p31F3d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p9712d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p90ACd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p002Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0027d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0024d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p7100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04E8p4471d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18E8p6238d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18E8p6229d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18E8p6196d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0812p3101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp2671d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp2573d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp093Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B75p7318d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0pA874d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0pA861d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p6874d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p6877d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p4600d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p0028d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p0023d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p0020d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE020d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1472p0009d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1044p800Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1044p8008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15A9p0004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p3701d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7618d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7318d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C07d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C06d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C04d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C03d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp002Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C22d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1371p9032d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1371p9022d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v178Dp02BEd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0137d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0119d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0116d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p00F4d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p00E6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p00D9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p00D8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v08DDp0120d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1631pC019d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp905Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp905Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp705Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp7050d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1724d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1723d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0722d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18C5p0002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0EB0p9021d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp9021d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C10d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8pB21Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8pB21Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8pB21Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8pB21Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8pB21Bd*dc*dsc*dp*ic*isc*ip*in*
depends:        rt2x00lib,rt2x00usb,crc-itu-t
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)


filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     B2734411C831D4AF35167D6
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 


filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     F3B7F97865D53E7B0E71194
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 




***** udev rules *****


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:09.0/0000:03:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x148f:0x2573 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


***** dmesg *****


[  334.193860] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  382.263788] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


****************** done ******************

```

---

### Post by wildmanne39 on 2014-02-04
Hi please copy and paste for accuracy all commands one line at a time:

```
sudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default power management behavior) and enter the following: 
```
#!/bin/sh

/sbin/iwconfig wlan0 power off
``` 
above exit0, then save gedit, close.

Then:
```
echo "options rt73usb nohwcrypt=1" | sudo tee /etc/modprobe.d/rt73usb.conf
sudo modprobe -rfv rt73usb
sudo modprobe -v rt73usb
```
Reboot
Does it connect now?
Thanks

---

### Post by audun2 on 2014-02-04
It didn't work :/

But now I see this in the taskbar:
[https://i.imgur.com/ILOBbZy.png](https://i.imgur.com/ILOBbZy.png)

---

### Post by westie457 on 2014-02-04
> **audun2 said:**
> It didn't work :/

But now I see this in the taskbar:
[https://i.imgur.com/ILOBbZy.png](https://i.imgur.com/ILOBbZy.png)

It is working. You are connected wirelessly to your router and probably the internet as well.

---

### Post by audun2 on 2014-02-04
But I can't actually access the internet. When I open Firefox and try to open a website it says "server not found".

I should mention that I can't access the internet via wired either. My desktop that runs Windows7 accesses the internet via  wireless and I have a bridged connection and connect the windows7 computer to the Linux-computer by cable. This connection works when I connect it to my Wondows laptop though.

---

### Post by Iowan on 2014-02-04
CTRL-ALT-t should open a terminal. From there, can you ping the internet?
```
ping -c3 8.8.8.8
```
You can also check interface status:
```
ifconfig -a
```

---

### Post by audun2 on 2014-02-04
When  I try the ping-thing it says "Net work is unreachable"??

Is it possible I need to fill in some more stuff like BSSID and MAC??

---

### Post by wildmanne39 on 2014-02-04
Set your wireless settings in network manager to match the screenshots.

If it still does not connect run the wireless script again now that your device is scanning and post the file here so we can get a better look at your network settings.
Thanks

---

### Post by audun2 on 2014-02-07
I think im giving up on trying to get the wireless to work. 
The ethernet does not work either though. I am trying to connect to the internet through my Windows7 computer. It it connects to the internet via wireless and has a bridged connection to the ethernet port. I can access the internet through the windows7 desktop on my windowsXP laptop, but it doesn't work on my Linux machine. 
Is there something I can try to make it work?

---

### Post by wildmanne39 on 2014-02-07
Please do what I asked in post 15.

Your ethernet does not work because it is using the wrong driver but it is hard to fix without wireless working so lets try to fix it first.
Thanks

---

### Post by audun2 on 2014-02-07
Am I also supposed to type something under BSSID?

---

### Post by audun2 on 2014-03-06
Yay!
I somehow got the wireless connection to work, though it is very unstable and will only connect for 10 minutes at a time or so, and then refuse to connect for hours.
 Thanks for all the help! :D

---

### Post by varunendra on 2014-03-06
> **audun2 said:**
> I somehow got the wireless connection to work, though it is very unstable and will only connect for 10 minutes at a time or so, and then refuse to connect for hours.

Can we see a fresh report of the wireless_script please?

---

### Post by hebrewofyhwh on 2014-03-06
I would have liked to see more information here from the main questioner. I would ilke to know more how this problem got solved if it even got solved.

---

### Post by Javelin Dan on 2014-03-06
Audun - 

Here's one more easy thing you can try IF your tentative connection will allow it...Click on Applications ("Start" button lower left), click on System Tools, click on Synaptic Package Manager. Enter your password and in the search window type "Wicd". Right click, then "mark for installation". In the window that opens click "Mark". Then click "Apply" (check mark at top of page). Wait until installation is complete. Next, re-open Synaptic and type "Network Manager". Right click and choose "Mark for Removal". You'll see a number of other dependencies also checked, but scroll down and mark for removal anything that says "Network Manager-Whatever" and has a green box next to it, then click "Apply". This will completely remove the native "Network Manager" which lately has been somewhat problematic in Ubuntu and replace it with Wicd, a much more stable manager. Reboot your computer, wait 30 seconds or so, and when you see two little computer screen icons in the task bar (bottom panel), click on that and try to configure your new network. No guarantees, but it worked for me. Good luck!

NOTE: Do it in this order! If you un-install network manager first, you'll have no way to download necessary software. You might try installing any random piece of software first just to see if your connection is strong enough to allow this.

Edit:  I fumbled a little and forgot to say that after you re-boot, click Applications, Internet, and Wicd to launch for the first time. When you configure your account, make sure you check "Always connect to this network". It'll connect automatically from then on. Sorry for the oversight.

---

### Post by varunendra on 2014-03-06
> **Javelin Dan said:**
> This will completely remove the native "Network Manager" which lately has been somewhat problematic in Ubuntu and replace it with Wicd, a much more stable manager.
Wicd is simpler than Network Manager, but stability is definitely not a problem with Network Manager. If configured properly, I can't think why NM can't be as good as Wicd or other methods. (I know about two common bugs in NM, but those aren't related to OP's problem).

But yes, if ALL our attempts with NM fail and trying out other connection managers seems like a reasonable alternative, here is a safer way to try Wicd : [https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)

Basically, it shows how to download and keep NM packages ready so that one can easily revert back if Wicd doesn't seem to help.

@audun2,
I'd like to see the report I asked in my previous post before you try anything else. It may be driver or router related, in which case changing the Network Manager won't help.

---

### Post by Javelin Dan on 2014-03-07
Actually, I've switched from Network Manager to Wicd in two of my computers due to connectivity problems; my Compaq Presario CQ61-313US, and my Sony Vaio VPCEB11X. Wicd has proven to be rock solid where I had numerous problems with Network Manager in both - no other changes. Oddly enough, I've had no problems with Network Manager in my Samsung 10" netbook, so go figure. FYI, all three are running Ubuntu 12.04 cloned with the same back-up, and all are under one roof accessing the same wireless net.

---

### Post by varunendra on 2014-03-08
> **Javelin Dan said:**
> Actually, I've switched from Network Manager to Wicd in two of my computers due to connectivity problems; my Compaq Presario CQ61-313US, and my Sony Vaio VPCEB11X. Wicd has proven to be rock solid where I had numerous problems with Network Manager in both - no other changes.

Since you didn't mention exactly what problems they were, and whatever you tried, I can't comment on what might have made a difference (not that I'm an expert on either NM or Wicd, just some experience with posts here..).

But I'd like to mention that I myself tend to suggest Wicd whenever all my attempts to solve a problem with NM fail, and so far, the problem always remained the same with either NM or Wicd (except maybe a couple of cases when I was new to Linux and my knowledge about wireless was next to nothing).

Whenever a problem was solvable, we could do it with either NM or Wicd. Since NM is deeply integrated with Ubuntu, it is usually easier to pin-point the problem and solve it with NM - is all why I prefer NM till the end of my wits.

Like my wireless-guru chili555 sometimes says - "Try Wicd" is just another way of saying "I'm clueless, and maybe my next suggestion would be to try changing your mouse!". :p

---

### Post by Javelin Dan on 2014-03-08
Didn't mean to get in the way. In both cases of the computers mentioned, I HAD been running NM for over a year with no problems. Suddenly (after an update?) both developed a problem where they would log onto my wireless net normally, then after maybe 30 minutes connectivity would cut in and out and eventually cut out completely until I rebooted, then the problem would recycle. Other computers on the premises were unaffected, so I don't believe it was my internet connection. I next did what I always do, I checked these forums for information. What I read was that people other than me were having connectivity issues with NM. It was suggested there, more than once, to try Wicd. Since it was something easy enough to try, I decided to at least try it. Once I changed over to Wicd, all problems stopped - COLD. I only meant to pass on a possibly helpful suggestion - sorry if it wasn't. And you're right, I did change the mouse and it didn't help at all.

---

### Post by Iowan on 2014-03-08
Perhaps this would be a good time to return to the OP's problem... :)

---

### Post by amith3 on 2014-03-11
may be you should move this thread to wireless section. Then you may get more help

---

### Post by mörgæs on 2014-03-11
Done.

---

