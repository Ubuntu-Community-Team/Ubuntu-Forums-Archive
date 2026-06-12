---
title: "How to install driver for USB wireless network adapter G54/N150 Wifi (WNA1000M)"
date: 2013-10-27
forum: Networking &amp; Wireless
---

### Post by likelinux on 2013-10-27
Hi,

     I am using Ubuntu 12.04 LTS Operating system in my desktop and I want to enable wireless network for it. So, I bought a USB wireless network adapter G54/N150 Wifi (Model no: WNA1000M). I wanted to install driver for this device. I tried following the instructions in this post.

[http://ubuntuforums.org/showthread.php?t=1806839&highlight=WNA1000M](http://ubuntuforums.org/showthread.php?t=1806839&highlight=WNA1000M)

But, it seems the 'compat' is changed to 'backports' and also the files in that tarball and I am stuck here. I am getting the following error message for the below command. 

*********@*********-PC:~$ cd Desktop/backports-3.11-rc3-1/
*********@*********-PC:~/Desktop/backports-3.11-rc3-1$ ./scripts/driver-select rtlwifi
bash: ./scripts/driver-select: No such file or directory

Can anyone please help me installing the driver for this device in my system. Thanks in advance.

---

### Post by chili555 on 2013-10-27
Please try:```
cd Desktop/backports-3.11-rc3-1/
[COLOR="#FF0000"]make defconfig-rtlwifi[/COLOR]
make
sudo make install
```And proceed as before.

EDIT: Which device do you have?```
lspci -nn | grep 0280
```

---

### Post by likelinux on 2013-10-27
[COLOR=#000000]*I performed the next following instructions as you suggested. After "sudo make install" command it asked me to reboot.When I gave reboot it got stuck on the ubuntu screen for a long time. I did a forced shutdown using power button. After starting again, I gave the command *[/COLOR][COLOR=#000000][COLOR=#000000][I][FONT=Ubuntu Mono]sudo modprobe rtl8192cu . 
[/FONT][/I][/COLOR][/COLOR]
[COLOR=#000000]*But I didn't get any message after issuing the command. And also I cannot see wireless connections enabled. *[/COLOR]

[COLOR=#000000]**********@********-PC:~$ sudo modprobe rtl8192cu*[/COLOR]
[COLOR=#000000]*[sudo] password for *******: *[/COLOR]
[COLOR=#000000]********@*****-PC:~$*[/COLOR]


[COLOR=#000000]*Please advise how I need to proceed from here.*[/COLOR]

[COLOR=#000000]*Thanks in advance.*[/COLOR]

---

### Post by chili555 on 2013-10-27
See my edit above. Which device do you have?

---

### Post by likelinux on 2013-10-27
[COLOR=#000000]Below is my system configuration.

USB wireless adapter: NETGEAR G54/N150 Wifi USB Micro Adapter. (Model No: WNA1000M)[/COLOR]
[COLOR=#000000]System configuration: Dell Optiplex 780 desktop. Dual boot with windows 7 and Ubuntu 12.04 LTS.[/COLOR]

---

### Post by chili555 on 2013-10-27
Please answer the exact question I asked:> EDIT: Which device do you have?

```
lspci -nn | grep 0280

```
The answer provides information you have not provided that I need.

---

### Post by likelinux on 2013-10-27
I entered the command you gave me. But its not showing any message.

******@*****-PC:~$ lspci -nn | grep 0280
*****@******-PC:~$

---

### Post by chili555 on 2013-10-27
Oops! Getting too close to naptime for old Chili! Sorry. Let's see:```
lsusb
```

---

### Post by likelinux on 2013-10-27
Below is the result of the command.

*****@*****-PC:~$ lspci -nn | grep 0280
******@*******-PC:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 004 Device 002: ID 413c:1005 Dell Computer Corp. Multimedia Pro Keyboard Hub
Bus 004 Device 003: ID 413c:2011 Dell Computer Corp. Multimedia Pro Keyboard
Bus 004 Device 004: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 002 Device 005: ID 04e8:6860 Samsung Electronics Co., Ltd GT-I9100 Phone [Galaxy S II]
*********@********-PC:~$

---

### Post by chili555 on 2013-10-27
rtl8192cu is correct for your device. Let's see some diagnostics:```
lsmod | grep rtl
modinfo rtl8192cu | grep filename
dmesg | grep -i rtl
```

---

### Post by likelinux on 2013-10-27
Below are the results of the commands.

********@*******-PC:~$ lsmod | grep rtl
rtl8192cu             103277  0 
rtl8192c_common        75767  1 rtl8192cu
rtlwifi               111269  1 rtl8192cu
mac80211              506862  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              205774  2 rtlwifi,mac80211
********@*******-PC:~$ modinfo rtl8192cu | grep filename
filename:       /lib/modules/3.2.0-55-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
*****@*****-PC:~$ dmesg |grep -i rtl
[   21.510910] rtl8192cu: MAC address: 28:c6:8e:fa:a1:7f
[   21.510916] rtl8192cu: Board Type 0
[   21.581038] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   21.619457] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   21.619921] usbcore: registered new interface driver rtl8192cu
[   27.441410] rtl8192cu: MAC auto ON okay!
[   27.489421] rtl8192cu: Tx queue select: 0x05
[   27.490172] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin
*********@*********-PC:~$

---

### Post by likelinux on 2013-10-27
Below are the results of the commands:

*******@*******-PC:~$ lsmod | grep rtl
rtl8192cu             103277  0 
rtl8192c_common        75767  1 rtl8192cu
rtlwifi               111269  1 rtl8192cu
mac80211              506862  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              205774  2 rtlwifi,mac80211
*********@*******-PC:~$ modinfo rtl8192cu | grep filename
filename:       /lib/modules/3.2.0-55-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
********@********-PC:~$ dmesg |grep -i rtl
[   21.510910] rtl8192cu: MAC address: 28:c6:8e:fa:a1:7f
[   21.510916] rtl8192cu: Board Type 0
[   21.581038] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   21.619457] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   21.619921] usbcore: registered new interface driver rtl8192cu
[   27.441410] rtl8192cu: MAC auto ON okay!
[   27.489421] rtl8192cu: Tx queue select: 0x05
[   27.490172] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin
********@********-PC:~$

---

### Post by chili555 on 2013-10-27
Please check two more things:```
modinfo rtl8192cu | grep -e version -e 9041
iwconfig

```We hope the version includes: backported from Linux (v3.11-rc3-0-g5ae90d8) using *backports v3.11-rc3-1*-0-g4e81a94

So far, we see nothing wrong.

---

### Post by likelinux on 2013-10-27
Below are the results of the command

********@*********-PC:~$ modinfo rtl8192cu | grep -e version -e 9041
srcversion:     7BCF53C3BB51058449CD6F8
alias:          usb:v9846p9041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9041d*dc*dsc*dp*ic*isc*ip*
vermagic:       3.2.0-55-generic SMP mod_unload modversions 
*********@*******-PC:~$ iwconfig
lo        no wireless extensions.


virbr0    no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.


*********@******-PC:~$

---

### Post by chili555 on 2013-10-27
We're getting closer all the time! We have a good driver and it loads the firmware and creates a wireless interface wlan0! Does it scan?```
sudo iwlist wlan0 scan
```If it scans, it should connect!

---

### Post by likelinux on 2013-10-27
Below is the result of the command

********@*******-PC:~$ sudo iwlist wlan0 scan
[sudo] password for *********: 
wlan0     Interface doesn't support scanning : Device or resource busy
******@********-PC:~$

---

### Post by chili555 on 2013-10-27
Busy? Busy doing what, we wonder. Let's go back to the message log again:```
dmesg | grep wlan
```

---

### Post by likelinux on 2013-10-27
Below is the result of the command

********@*******-PC:~$ dmesg | grep wlan
[   27.886967] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.887294] ADDRCONF(NETDEV_UP): wlan0: link is not ready
*******@*******-PC:~$

---

### Post by likelinux on 2013-10-27
My actual requirement is to connect an Android smartphone to my desktop in wireless mode and through that access the internet. I read somewhere that Android smartphone does not support Adhoc networks. So, I want to setup wifi hotspot in my desktop system.  For that I am trying to setup this wireless LAN adapter first. Hope, my direction is right. Please correct me if I am wrong or if there is any other way to achieve that. Thanks in advance.

---

### Post by chili555 on 2013-10-27
I haven't any idea how to do that; I'd assume somewhere in Network Manager. You have a working driver now, so I suggest you ask a new question about a hotspot. It's really beyond my experience.

---

### Post by likelinux on 2013-10-27
My driver is working?  But I can't see wireless connections enabled in my system. I am checking in the top right corner where it shows the status of the network connections. Please help.

---

### Post by chili555 on 2013-10-27
So you are* NOT* trying to set up a hotspot? You are trying to simply connect?? What have you set up in Network Manager? Ideally, nothing except Mode which should be set to Infrastructure. Everything else should be blank. Is that what you have?

---

### Post by likelinux on 2013-10-27
Yes. I didn't change any settings in the network manager.

---

### Post by chili555 on 2013-10-27
Please detach any ethernet cable. Reboot so we have a clean slate. Next, run:```
dmesg > like.txt
```Find the file like.txt in your user directory and paste it here and give me the link in your reply: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

---

### Post by likelinux on 2013-10-27
Disconnected the ethernet cable ---> restarted the system ----> Connected the ethernet cable again ----> Issued the above said command ---->Pasted the output in this link --------> [http://paste.ubuntu.com/6315877/](http://paste.ubuntu.com/6315877/)

---

### Post by chili555 on 2013-10-27
Off for the evening. I'll check in tomorrow.

---

### Post by kurt18947 on 2013-10-28
Have you considered using RealTek's 'official' driver?  It should work with 12.04/image 3.2.x. The current Realtek driver will not IME work with 13.04 kernel 3.8 or later.  If the command "uname -a" returns something like "3.2.0-12-generic" I'd think RealTek's driver should work.  I too have an RTL8188CUs device and it sorta works with 13.10 using the 'baked-in' driver, fairly well on a desktop, not as well on a Thinkpad R61i running Ubuntu-Gnome

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true).

---

### Post by chili555 on 2013-10-28
Let's double-check our compile:```
cd Desktop/backports-3.11-rc3-1/
make clean
make defconfig-rtlwifi
make
sudo make install
```Are there any errors or warnings? If so, please post them. If not, reboot and post:```
modinfo rtl8192cu | head -n10
```When I compile the exact same package, the version is:> chili@Think410:~/backports-3.11-rc3-1$ modinfo drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
filename:       /home/chili/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
[COLOR="#FF0000"]version:        backported from Linux (v3.11-rc3-0-g5ae90d8) using backports v3.11-rc3-1-0-g4e81a94[/COLOR]
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
Is that what you get?

---

