---
title: "Ethernet / LAN Keeps disconnecting roughly 5 or 6 mins after plugging it in"
date: 2016-08-25
forum: Networking &amp; Wireless
---

### Post by 0N3 on 2016-08-25
As the title says my ethernet keeps disconnecting roughly 5 mins after plugging in the ethernet cable. If I plug it out and back in again it works perfectly for another 5 mins. I have a USB to LAN connection when I use that I have no connections whatsoever, it only happens when I plug the ethernet cable into the on board ethernet port on my laptop. The connection isn't loose and the wire isn't damaged in any way. Any ideas what's causing this? I read somewhere TLP was causing LAN issues and so I uninstalled TLP yet the issue is still their. grateful for any help received on the matter.

Here is the output of lspci:

```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Thames [Radeon HD 7500M/7600M Series]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Turks/Whistler HDMI Audio [Radeon HD 6000 Series]
07:00.0 Ethernet controller: Qualcomm Atheros AR8161 Gigabit Ethernet (rev 10)
08:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)


```

Here is the output of lspci -knn | grep Eth -A2:

```
07:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
    Subsystem: Toshiba America Info Systems AR8161 Gigabit Ethernet [1179:ff1e]
    Kernel driver in use: alx
    Kernel modules: alx
```

An update to this I wouldn't say "solved" but by disabling wifi from the network manager app-indicator my LAN never disconnects now. Must be conflicting issue between enabling wifi and enabling networking

---

### Post by jeremy31 on 2016-08-25
If the issue returns try the module from my github site as I used Ubuntu 4.4 kernel source code and added some patches from the upstream kernel
```
sudo apt-get install git linux-headers-generic build-essential
git clone https://github.com/jeremyb31/alx.git
cd alx
cp /usr/src/linux-headers-`uname -r`/.config ./
cp /usr/src/linux-headers-$(uname -r)/Module.symvers ./
make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
sudo cp alx.ko /lib/modules/$(uname -r)/kernel/drivers/net/ethernet/atheros/alx/alx.ko
```
Reboot and it should work until you get a kernel update then you need to 
```
cd alx
make -C /lib/modules/$(uname -r)/build M=$(pwd) clean
cp /usr/src/linux-headers-`uname -r`/.config ./
cp /usr/src/linux-headers-$(uname -r)/Module.symvers ./
make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
sudo cp alx.ko /lib/modules/$(uname -r)/kernel/drivers/net/ethernet/atheros/alx/alx.ko
```

Reboot.

Another option is to just go into Network Manager settings for the wired and change the MTU setting to 8192 and see if it works

---

### Post by 0N3 on 2016-08-25
Ok I tried your first suggestion I have absolutely no internet connection now via ethernet only via wireless now after enabling wifi. How can I undo what you suggested?

Had Git already installed after running the first command:

```
E: Unable to locate package build
E: Unable to locate package essential

```

git & build-essential are already the newest versions spotted the typo

---

### Post by jeremy31 on 2016-08-25
I missed a - it is supposed to be ```
sudo apt-get install build-essential
```

---

### Post by 0N3 on 2016-08-25
OK performed the above solution and have ethernet back again wil post back shortly if the issue doesn't happen again. Thanks for your help much appreciated!

---

### Post by jeremy31 on 2016-08-25
Which solution?  My github module or the MTU change?  Use just one or the other

I should have had you file a bug report on launchpad but that can be done after the next kernel update.  That way we can get Ubuntu to use the upstream fix in this kernel

---

### Post by 0N3 on 2016-08-25
I used your github so far so good!

Nope still happening I'll try solution 2 whats really weird is that if I  am on YouTube say playing a playlist my internet is fine ...... but if I  try load a different site say Facebook or whatever it just won't open a  new page / tab unless I plug the ethernet cable out and in again

I go into network settings / edit connections but I don't see any option to change the MTU setting to 8192

By disabling wifi all is perfect again

To be honest I 99.9% of the time use LAN / Ethernet so it's not a big issue for me

I tried

```
sudo subl /etc/network/interfaces

I didn't see any any option to change mtu

```

Also tried 

```
sudo ifconfig eth0 mtu 8192

and got 

SIOCSIFMTU: No such device


```

Hope that helps!

---

### Post by jeremy31 on 2016-08-25
If my code is used, setting the MTU to 8192 is likely to cause issues

---

### Post by 0N3 on 2016-08-25
So how to undo your code? Or file a bug report? As I said not a major issue cause it's 99.9% of the time connected via ethernet but if it helps someone else with the issue I'm happy to file a bug report. I'd like to undo your code and maybe try the MTU 8192 setting. Bit of a noob but not afraid to get down and dirty with Ubuntu.

---

### Post by jeremy31 on 2016-08-25
What kernel are you using? ```
uname -a
```

---

### Post by 0N3 on 2016-08-25
4.4.0-34-generic

---

### Post by jeremy31 on 2016-08-25
Only use this if you have the 64 bit install
Try this one to replace yours.  Download, click on file and choose extract here.  Then you should be able to 
```
cd Downloads
sudo cp alx.ko /lib/modules/4.4.0-34-generic/kernel/drivers/net/ethernet/atheros/alx/alx.ko
```

Reboot

[http://i1275.photobucket.com/albums/y452/Jeremy53561/Screenshot%20from%202016-08-25%2016-54-58_zpsm7vavhty.png](http://i1275.photobucket.com/albums/y452/Jeremy53561/Screenshot%20from%202016-08-25%2016-54-58_zpsm7vavhty.png)
It is an image of my Network Manager settings after clicking the edit connections for wired.  I don't care if my MAC address is listed as I rarely use ethernet as I connect to a cellular wifi hotspot.

---

### Post by 0N3 on 2016-08-25
Rest assured I have zero intentions of exposing anyone via the internet especially not anyone who is helping me....... I have done that and will post back if the issue arises again! I hope you can delete that file please do as I don't want anyone compromised! What I downloaded has been deleted before I even replied! Thank you!

---

### Post by 0N3 on 2016-08-25
Same problem just happening a lot quicker now! Only taking a minute or less!

---

### Post by jeremy31 on 2016-08-25
Is that with the MTU set to 8192?

---

### Post by 0N3 on 2016-08-25
Won't let me set it to 8192

```
sudo ifconfig eth0 mtu 8192

SIOCSIFMTU: No such device
```

---

### Post by SeijiSensei on 2016-08-25
> **0N3 said:**
> By disabling wifi all is perfect again

I encountered what I believe is the same problem as yours earlier today.  Usually my laptop is connected by Ethernet to my network, but today I'm using wifi. I had to disable the Ethernet port to get the OS to route packets correctly through the wifi adapter.  In your case you want the reverse which you can do by running
```
sudo ifconfig wlan0 down
```
in a terminal. You can probably also turn off the radio entirely with an Fn-key combination.

---

### Post by 0N3 on 2016-08-25
My wifi is fine it works perfectly if I disable the wifi completely by unchecking it via the network app indicator I have no issues via ethernet enablin wifi causes an issue with the ethernet connection if that makes sense.

---

### Post by 0N3 on 2016-08-25
Only way my ethernet remains stable is b disabling the wifi via the network app indicator

---

### Post by jeremy31 on 2016-08-25
What Ubuntu version are you using and post the results for ```
ifconfig; iwconfig
```

---

### Post by 0N3 on 2016-08-25
Ubuntu 16.04 64bit

ifconfig; iwconfig:

```
ifconfig; iwconfig
enp7s0    Link encap:Ethernet  HWaddr 00:26:6c:1d:c9:d1  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::5a8f:bcf3:1344:94a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:187459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104328 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:106717764 (106.7 MB)  TX bytes:18612720 (18.6 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2085 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2085 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:198797 (198.7 KB)  TX bytes:198797 (198.7 KB)

enp7s0    no wireless extensions.

lo        no wireless extensions.

wlp8s0    IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


```

---

### Post by jeremy31 on 2016-08-25
Well with the current renaming of devices ```
sudo ifconfig eth0 mtu 8192
```
Isn't going to work instead try ```
sudo ifconfig enp7s0 mtu 8192
```

---

### Post by 0N3 on 2016-08-25
ughhh!!! I remember my conky config I had to change the same eth0 and wlan0 to what you posted! I am now more hopeful! Thank you again!

---

### Post by 0N3 on 2016-08-25
No joy! Still the same issue! Only way my ethernet works is by disabling wifi via the network manager!

---

### Post by jeremy31 on 2016-08-25
See the wireless script link in my signature and post results as it may show some other issue

---

### Post by SeijiSensei on 2016-08-25
Why don't you just disable wifi and leave it at that?  There's no performance benefit to having both interfaces on the network unless you use "bonding," and that's not worth the effort.  When you don't need wireless, just turn it off.  Otherwise the DHCP client will eventually ask the router to assign the wifi adapter an IP address, and once it gets one, all the packet routing is screwed up because the networking system doesn't know which interface to use.  

In general, you should only make one of the ethernet or wifi interfaces active on your computer at any one time unless they will be on separate IP subnets.  The machine I'm using right now has a wifi connection to my home network, and an Ethernet connection to my TV.  They have addresses in separate IP subnets, and I'm "masquerading" the TV's traffic (for Netflix, etc.) out to the Internet via wifi the way a home router does. If I weren't supporting the TV, I'd disable the Ethernet connection and rely entirely on the wifi adapter.

---

### Post by 0N3 on 2016-08-26
Thanks to both of you for your help. Although my issue in general is solved I still feel as though it's a bug as I've never had this issue before I was always able to have both connections connected at the same time with no issue. If one had a problem the other kicked in. Just strange it's starting happening now. Again thanks both of you for your help it's greatly appreciated.

---

