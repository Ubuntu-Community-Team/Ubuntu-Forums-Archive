---
title: "Need drivers, help for Enuwi-SG USB Adapter"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by kstella on 2008-10-19
Hi, everyone. I'm using an MSI Wind U100, and although I compiled drivers for the built-in wireless card, I still can't access the Internet.

I decided to try Option 3 on the [User WIki]("http://tinyurl.com/57cdsp") - an external USB adapter - and bought an ENUWI-SG device. My search for install guides has come up with a lot of guides in Brazilian Portuguese and some in Spanish (I guess it's a popular device in South America?), but I did find [this]("http://tinyurl.com/6jlna6") right here in ubuntu forums.

Unfortunately, because the Wind has neither a CD drive nor Windows installed on it, I have no way of accessing the .inf files that I need:

athfmwdl.inf
net5523.inf

Does anyone know where I can download these? Or would anyone have these files and be willing to share? :)

---

### Post by kstella on 2008-10-20
Found it in [this post]("http://tinyurl.com/6lxzrd") for a different device with the same drivers.
[Direct link]("http://tinyurl.com/5knrcu") to drivers.

---

### Post by kstella on 2008-10-20
[COLOR="Gray"]I can't unmark my [previous thread]("http://ubuntuforums.org/showthread.php?t=953148") solved. :/[/COLOR] Thanks to whoever merged the threads. I have the drivers and installed them according to [this thread]("http://ubuntuforums.org/showpost.php?p=1966252") (posts 10 and 19).

Unfortunately, the device won't light up. I have rebooted, and I made sure to turn off the built-in wireless card like the MSI Wind [user wiki]("http://wiki.msiwind.net/index.php/Ubuntu_8.04_Hardy_Heron#Option_3:_Use_an_External_WiFi_USB_Adapter") said.

I did check the sticky on ndiswrapper at the top of this forum, but unfortunately, I didn't get past step one. So I'm posting the results to some commands in case anyone can help me. Thanks.

Results of ndiswrapper -l:

```
athfmwdl : driver installed
net5523 : driver installed
```

Results of lsusb:

```
Bus 005 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 005 Device 003: ID 0c45:62c0 Microdia 
Bus 005 Device 002: ID 0d8e:7802 Global Sun Technology, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

Realtek is the built-in wireless card, and Microdia is the built-in webcam. I'm not sure if Global Sun is the USB adapter. I seem to recall a fourth entry appearing in this list, but I unfortunately didn't take note of it.

EDIT: [Found info]("http://www.ubuntu-es.org/index.php?q=node/65830#comment-177970") related to what must have been in the fourth line:

[B]Encore Electronics ENUWI-SG 802.11g, Wireless LAN USB Adapter
Chipset: Atheros Communications Inc, AR5523
usbid: 0d8e:7801[/B]

Results of iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Frequency=2.412 GHz  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Also, here are the contents of /etc/network/interfaces:

[B]auto lo
iface lo inet loopback[/B]

---

### Post by dmizer on 2008-10-20
Merged your threads and marked this thread as unsolved.

In the future, you can just use the "report post" icon below your profile. This will aleart the staff that you are having difficulty and we will correct the situation.

Try posting the output of:
```
lshw -C network
```

---

### Post by kstella on 2008-10-20
Thanks, dmizer. :)

```
*-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:21:85:4d:e4:fe
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 22
       serial: 00:1d:92:cb:9e:15
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=0 module=r8180 multicast=yes wireless=802.11b/g
```

---

### Post by dmizer on 2008-10-20
You'll need to blacklist the native driver in order to use NDISwrapper.

Edit2: try this ...

```
echo "blacklist rtl8180" | sudo tee -a /etc/modprobe.d/blacklist
```

Reboot, and see if your wireless works.

---

### Post by kstella on 2008-10-20
Okay, I'll try it in a moment. What if, sometime in the future, I want to reverse the process?

---

### Post by dmizer on 2008-10-20
> **kstella said:**
> Okay, I'll try it in a moment. What if, sometime in the future, I want to reverse the process?

You will have to manually edit /etc/modprobe.d/blacklist and remove the "blacklist rtl8180" line.

---

### Post by kstella on 2008-10-20
It worked in that it did what you expected it to do, which I'm guessing was to prevent the built-in card from interfering with the adapter. But the adapter itself still won't light up or detect any networks.

To experiment, I tried using the built-in card again, which detected about five or six different networks in the area (it can't connect to any of them, though; that's why I'm trying things out with the USB adapter). However, with the blacklist thing on AND the built-in card off, wireless is still "on," but the adapter doesn't see any of those networks.

I think the problem lies in the device not being detected (see my previous post on the results of lsusb). :/

---

### Post by dmizer on 2008-10-20
I think you're going to have more luck getting your built-in wireless card because it's at least detected, and it can see other networks. There are plenty of reports of people who have gotten it to work.

I don't see anything that indicates your USB adapter has any hope of ever working.

My suggestion is to remove the rtl8180 from the blacklist, disable network-manager, and use another wireless manager like wicd. You should be able to connect with your built-in wireless card then.

---

### Post by kstella on 2008-10-20
Okay, thanks. Will let you know if it works.

I guess I'll return the adapter, or sell it to a friend who uses Windows. :p

---

