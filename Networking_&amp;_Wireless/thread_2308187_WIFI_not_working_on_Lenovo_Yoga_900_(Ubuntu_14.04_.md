---
title: "WIFI not working on Lenovo Yoga 900 (Ubuntu 14.04 and 15.10)"
date: 2015-12-31
forum: Networking &amp; Wireless
---

### Post by Zack_Neff on 2015-12-31
Hi,

I'm new to Ubuntu/Linux and wanted to give it a shot on my Lenovo. I recently tried both the 14.04 and 15.10 versions, both resulting in my WIFI being disabled. I've found many answers online and have tried them all (rfkill unblock all, modprobe -r ideapad laptop, blacklist ideapad laptop in etc/modprobe.d/blacklist). Nothing is working. My wireless LAN in BIOS is enabled. I had Windows 10 installed initially and used the option to keep them both installed. My wifi works perfectly fine when I boot in Windows.

Details on the problem and output from Terminal are below. If it helps, I also don't have a mouse (invisible cursor) and am using a wired mouse to get it to show up. When I installed Ubuntu, I was not connected to the internet and therefore it didn't download the updates as the installation happened. I don't know how to download it without WIFI.

Sorry for the long post, wanted to give as many details as possible. Please let me know if there's any more information I can provide or suggestions anyone has.

When I click on the WIFI logo in the top right corner the dropdown menu says. 

[COLOR=#ff0000]No network devices available[/COLOR]
VPN Connections
(Checkmark) Enable Networking
Edit Connections...

TERMINAL COMMANDS:

rfkill list all
0: hci0: Bluetooth
     Soft blocked: yes
     Hard blocked: no
1: ideapad_wlan: Wireless LAN
     Soft blocked: no
     [COLOR=#ff0000]Hard blocked: yes[/COLOR][COLOR=#ffff00]
[/COLOR]2: ideapad_bluetooth: Bluetooth
     Soft blocked: yes
     Hard blocked: yes

iwconfig
lo     no wireless extensions.


ifconfig
lo     Link encap:Local Loopback
       inet addr:127.0.0.1 Mask:255.0.0.0
       inet6 addr: ::1/128 Scope:Host
       UP LOOPBACK RUNNING  MTU:65536 Metric:1
       RX Packets:197 errors:0 dropped:0 overruns:0 frame:0
       TX Packets:197 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:0
       RX bytes:14289 (14.2 KB) TX bytes:14289 (14.2 KB)

lspci (some abbreviated, can give full output if needed)
00:00.0 Host bridge: Intel Corporation Device 1904 (rev 08)
00:02.0 VGA compatible controller: Intel Corporation Device 1916 (rev 07)
00:04.0 Signal processing controller: Intel Corporation Device 1903 (rev 08)
00:14.0 USB controller: Intel Corporation Device 9d2f (rev 21)
signal processing controller.......
signal processing controller......
signal processing controller ......
Communication Controller: Intel Corporation Device 9d3a (rev 21)
SATA controller: Intel Corporation Device 9d03 (rev 21)
PCI bridge: Intel Corporation Device 9d14 (rev f1)
PCI bridge: Intel Corporation Device 9d15 (rev f1)
ISA bridge: Intel Corporation evice 9d48 (rev 21)
Memory controller...
audio device....
SMBus: Intel Corporation Device 9d23 (rev 21)
01:00.0 Network Controller: Intel Corporation Wireless 8260 (rev 3a)
02:00.0 SD Host Controller: 02 Micro, Inc. Device 8620 (rev 01)

---

### Post by Elishasmantle on 2016-01-01
Hello,

I have installed both versions of ubuntu mentioned and did not have an issue with wifi, but I was not using your same laptop model. Mine is a Dell e4300.

I have a suggestion, but please: 1) Make a copy of the files I am suggesting you modify to be able to revert back changes if this does not work.

In /etc/network/interfaces I have the following setup in my file:

#Loopback Config
auto lo
iface lo inet loopback
#Note-The Networking Manager Systray icon may be disabled or not appear 
#when having anything other than the 2 loopback lines above.
#Uncomment any settings you want active
#
# The primary network interface
#

#auto eth0
#allow-hotplug eth0
#iface eth0 inet dhcp

#
#Wifi Config
#

#auto wlan0
#allow-hotplug wlan0
#iface wlan0 inet dhcp

So, you would want to go to /etc/network/interfaces, view file, see how your file currently looks. Make a copy ( cp interfaces interfaces.bak )
Then copy the lines I have in this post. Now, by default, just as the lines are, you should have internet if connected to hard wired via Ethernet cable.
Try it, yes or no to internet?
Also, do you have network-manager installed and can see if wireless is available or you have options for wired or wireless in network-manager profile manager?
Next I would uncomment out the lines( Remove the # before auto, allow, iface) for wireless if you still did not have wireless.
You have to stop and restart NM after each change.
I think that is sudo service nmbd restart

If this does not work, I would leave the files as they are but keep the .bak files in case you need to revert back or you can revert back immediately by using the .bak files and possibly someone else will help you with more expertise.

Thank You,
Elishasmantle

---

### Post by chili555 on 2016-01-01
> **Elishasmantle said:**
> 
In /etc/network/interfaces I have the following setup in my file:

<snip>

Thank You,
ElishasmantleChanging /etc/network/interfaces will do *nothing whatever* to help get his wireless working if there is an rfkill problem AND there is no associated driver!

@Zack_Neff

Please open a terminal and run and post:```
lspci -nnk | grep 0280 -A2
```We need the exact identity of your wireless device including the subsystem numbers.

If you manipulate the Airplane Mode button on the laptop, does the rfkill status change?```
rfkill list all
```If, as I suspect, we need to compile a new driver, are you able to get a temporary internet connection by ethernet from a friend? That will turn a five day frustrating job into a five-minute job.

---

### Post by johnholbrook on 2016-01-02
I got a new Y700 ideapad and have the same issue. it's a conflict with the ideapad_laptop module. System thinks you have a hardware switch to disable wifi but there isn't onee. Blacklist it and reboot and you'll have wifi working.

# echo 'blacklist ideapad_laptop' > /etc/modprobe.d/blacklist-ideapad_laptop.conf

---

### Post by Zack_Neff on 2016-01-02
Hi @chili555 

Thanks for the response. Airplane Mode toggle on F7 doesn't change anything in rfkill. List all is still the same. Unfortunately, the new Lenovo doesn't even have an Ethernet plugin. I could maybe find a converter for an input this has, however, I'm not sure.

Output from lspci -nnk | grep 0280 -A2 is below

01:00.0 Network Controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
Subsystem: Intel Corporation Device [8086:1130]
02:00.0 SD Host Controller [0805]: 02 Micro, Inc. Device [1217:8620] (rev 01)

Thanks again, hopefully some of that info helps.

---

### Post by Zack_Neff on 2016-01-02
Installing a new driver seems to be the right fix. Just tough without an Ethernet port. I have a really old IBM Thinkpad from the Windows XP era that I installed Ubuntu on. Maybe there's a way to transfer the packages from there?

I also have Windows 10 on here still - maybe could do it through that and transfer.

---

### Post by jeremy31 on 2016-01-02
> **Zack_Neff said:**
> Installing a new driver seems to be the right fix. Just tough without an Ethernet port. I have a really old IBM Thinkpad from the Windows XP era that I installed Ubuntu on. Maybe there's a way to transfer the packages from there?

I also have Windows 10 on here still - maybe could do it through that and transfer.

First try blacklisting the ideapad-laptop module with ```
echo "blacklist ideapad-laptop" | sudo tee /etc/modprobe/blacklist-ideapad-laptop.conf
```

Reboot and then you should be able to get rid of the hard block on wifi, the soft block can be removed with the FN keyboard combo

---

### Post by Zack_Neff on 2016-01-03
Thanks @jeremy31

i gave this a try already, and unfortunately since I have no Ethernet port, my computer didn't download the latest updates from Ubuntu which install a second wireless driver. When I blacklist Ideapad laptop, I have no drivers left and no way to connect to wifi. I need to install the packages on another computer and transfer them, or find a way to connect to wireless via a USB adapter or some sort to download it on mine. I just don't know what packages I need to fix my problem

---

### Post by jeremy31 on 2016-01-03
You have that issue, it is corrected in a newer 15.10 kernel

Download [https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/20/backports-20151120.tar.gz](https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/20/backports-20151120.tar.gz) and transfer it to Ubuntu desktop, right click on the file and choose 'extract here'
Then in terminal ```
cd ~/Desktop/backports-20151120
make defconfig-iwlwifi
make
sudo make install
```
Reboot and with any luck wireless will work

If it doesn't post results for ```
rfkill list all; lspci -nnk | grep -iA2 net; dmesg | grep iwl
```

---

