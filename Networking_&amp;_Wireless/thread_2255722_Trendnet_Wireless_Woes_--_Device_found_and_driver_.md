---
title: "Trendnet Wireless Woes -- Device found and driver installed, but no wlan0 listing"
date: 2014-12-07
forum: Networking &amp; Wireless
---

### Post by Aubrey_Lavigne on 2014-12-07
Hello everyone!

I am working with a fresh install of Ubuntu 14.10, and I have been unable to get my wireless card (TRENDnet TEW-6431, which is a PCI card) to show up in my list of active wireless devices.

I am attempting to use dniswrapper to import a Windows XP driver that came with the wireless card itself (using this tutorial: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)). This installation of this card seems to be going smoothly, but I am encountering the following apparent contradiction.

```

root@aubrey-desktop:/home/aubrey# ndiswrapper -l
net819xp : driver installed
    device (10EC:8190) present

root@aubrey-desktop:/home/aubrey# iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.


```


For additional information about my PC (list of answers pulled from the sticky). This is just me pulling the relevant information, so let me know if you need it to be more verbose.


```

root@aubrey-desktop:/home/aubrey# lspci
05:05.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8190 802.11n PCI Wireless Network Adapter

root@aubrey-desktop:/home/aubrey# lspci -nn | grep 'Wireless'
05:05.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8190 802.11n PCI Wireless Network Adapter [10ec:8190]

root@aubrey-desktop:/home/aubrey# lsmod | grep "wlan_module_name"
[No Response]

root@aubrey-desktop:/home/aubrey# lshw -C network
  *-network UNCLAIMED
       description: Network controller
       product: RTL8190 802.11n PCI Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:05:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32 maxlatency=64 mingnt=32
       resources: ioport:c000(size=256) memory:fe700000-fe700fff

root@aubrey-desktop:/home/aubrey# iwlist scan
[No Response]

root@aubrey-desktop:/home/aubrey# sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

root@aubrey-desktop:/home/aubrey# lsb_release -d
Description:    Ubuntu 14.10

root@aubrey-desktop:/home/aubrey# uname -mr
3.16.0-23-generic x86_64

root@aubrey-desktop:/home/aubrey# sudo service networking restart
stop: Job failed while stopping
start: Job is already running: networking

```

Thank you for any help that anyone can provide.

---

### Post by praseodym on 2014-12-07
Tried this driver?

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=9&PFid=9&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8192E](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=9&PFid=9&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8192E)

I recommend the XP one

---

### Post by Aubrey_Lavigne on 2014-12-07
Thank you prasodym.

I have installed the new driver from that link, but I am still getting the same result.

```

root@aubrey-desktop:/home/aubrey/# ndiswrapper -e net819xp
root@aubrey-desktop:/home/aubrey/# cd ..path_to_driver..
root@aubrey-desktop:/home/aubrey/..path../# ndiswrapper -i net819xp.inf
root@aubrey-desktop:/home/aubrey/..path../# ndiswrapper -l
net819xp : driver installed
    device (10EC:8190) present
root@aubrey-desktop:/home/aubrey/..path../# iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.


```

I renamed the contents of the zip file downloaded to /home/aubrey/Documents/Drivers/rtl8192e/RTL819xP/

and I found the new driver in: /RTL819xP_Driver/WinXP/

---

### Post by praseodym on 2014-12-07
Try
```

sudo ndiswrapper -ma
sudo modprobe -v ndiswrapper
dmesg | grep ndis
iwconfig
iwlist chan
sudo iwlist scan
```

---

### Post by Aubrey_Lavigne on 2014-12-07
Thank you once again, praseodym.

Unfortunately, it seems that I'm worse off than I was yesterday when I started the topic.

I followed the first couple instructions in your most recent reply, and `dmesg | grep ndis` seemed to indicate a conflict between the 64-bit kernal of my install and the seeming 32-bit nature of the drivers. I was trying to install from the WinXP driver folder, rather than the WinX64 folder. For this reason, I'm going to mark this topic as solved.

The unfortunate part is something happened and the computer froze. I tried restarting, but the system failed to boot to the Desktop, so I had to reinstall Ubuntu. Now that I'm actually further back than when i started. (I could run `modprobe ndiswrapper`, but now it freezes every time I try)

At this point, I'm probably just going to go to the store to grab a copy of Windows 8.1. Thank you for your efforts, though, I really appreciate them.

---

### Post by chili555 on 2014-12-07
Or you could go to the store and grab a supported device. There are many threads about them here.

---

### Post by Aubrey_Lavigne on 2014-12-08
Further attempts to get this working, I was able to get past modprobe freezing, but now I'm functionally back to where I started. I'm not getting the 64-bit/32-bit compatitbility error anymore, but I am getting the following message on dmesg | grep ndis

```

root@aubrey-desktop:/home/aubrey# dmesg | grep ndis
[  129.175157] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[  129.177028] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[  129.271289] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[  129.271297] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[  129.271306] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[  129.271313] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[  129.271326] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[  129.271338] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[  129.271344] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[  129.271359] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[  129.271365] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[  129.271370] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[  129.271379] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[  129.271391] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[  129.271404] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[  129.271410] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[  129.271416] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[  129.271422] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[  129.271428] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[  129.271434] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[  129.271440] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[  129.271446] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[  129.271452] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[  129.271458] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[  129.271464] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[  129.271470] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[  129.271479] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[  129.271485] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[  129.271491] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[  129.271501] ndiswrapper (load_sys_files:200): couldn't prepare driver 'net819xp'
[  129.271926] ndiswrapper (load_wrap_driver:103): couldn't load driver net819xp; check system log for messages from 'loadndisdriver'
[  129.271996] usbcore: registered new interface driver ndiswrapper

```


As best as I can tell (and I would appreciate confirmation of this if I am correct here, or maybe other ideas if I'm not), this is because I did not compile ndiswrapper myself. It's strange that the package version of ndiswrapper wouldn't work, but that's what I'm getting from this.

Also, unfortunately, this is the only card that's immediately available to me. At best I can start shopping around and see if I find something to arrive in the next couple days.

---

### Post by chili555 on 2014-12-08
Did you erase the incorrect 32-bit inf before you installed the 64-bit? May we see:```
ndiswrapper -l
ls /etc/ndiswrapper
```

---

### Post by Aubrey_Lavigne on 2014-12-08
I will be out all day today, so it will be difficult for me to run the specific commands to check specifically.  

I did continue to look into it yesterday, so I have the following additional notes.

I do not believe that this is currently a 32/64-bit compatibility issue. I have started from a completely new Ubuntu install, and I have not installed the 32-bit drivers on this machine.

I did compile ndiswrapper for my computer, and now I do not have any issues running `modprobe ndiswrapper` (it completes near instantly, rather than the 10+ minutes it was taking when it would work before hand). 

I am still not getting it to work, and I'm still seeing the previously-posted set of errors in dmesg. I am mostly curious about the first line of the response "module verification failed: signature and/or  required key missing - tainting kernel". From doing a bit of reading, it seems that some distros might require any modules to be appropriately signed before they can be used by the system. I feel like I need to verify the produced .ko file before I can continue. (This is where I left off last night, I haven't looked into how to get the modules signed yet).

---

### Post by chili555 on 2014-12-08
> I am mostly curious about the first line of the response "module verification failed: signature and/or required key missing - tainting kernel". From doing a bit of reading, it seems that some distros might require any modules to be appropriately signed before they can be used by the system.The message is harmless and may safely be ignored. In this context, it means that the module will be used but the kernel is no longer assumed to be fully pure. The assumption is that if you are astute enough to compile this from scratch, you are also astute enough to be careful about where you got the package; no iffy torrents from who knows where. 

The system *IS* using the module ndiswrapper, but the combination of it and the XP inf file are making it choke.

I worked on a case with similar messages in dmesg: [http://askubuntu.com/questions/446708/unable-to-get-wireless-netgear-wnda3100v2-to-work](http://askubuntu.com/questions/446708/unable-to-get-wireless-netgear-wnda3100v2-to-work) As you can see, the solution was a different, known working inf file.

Having said that, I know of no other or better files for your device.

In a while, I am going to try to compile this and I'll advise. [https://github.com/lwfinger/rtl8190p](https://github.com/lwfinger/rtl8190p)

---

### Post by Aubrey_Lavigne on 2014-12-08
> 
The message is harmless and may safely be ignored. In this context, it means that the module will be used but the kernel is no longer assumed to be fully pure. The assumption is that if you are astute enough to compile this from scratch, you are also astute enough to be careful about where you got the package; no iffy torrents from who knows where. 


Thank you for advising on that.  I will be getting home in a couple (5+) hours, but I will check back later tonight.  Thank you.

---

### Post by chili555 on 2014-12-08
> In a while, I am going to try to compile this and I'll advise. [https://github.com/lwfinger/rtl8190p](https://github.com/lwfinger/rtl8190p)It 'makes' with a couple of warnings on my 14.10 system using a 3.16.0-xx kernel. I suggest you try it. With a temporary internet connection:```
sudo apt-get install git
git clone https://github.com/lwfinger/rtl8190p.git
cd rtl8190p
make
sudo make install 
sudo depmod -a
```Now we unload ndiswrapper:```
sudo modprobe -r ndiswrapper
```And, crossing our fingers, load the new one:```
sudo modprobe r8190_pci
```Does it correctly drive your device?```
iwconfig
```If it does, we'll need to, in a second step, remove ndiswrapper as the two drivers will conflict.

---

### Post by Aubrey_Lavigne on 2014-12-08
Ok, great!

This seems to be the right track.  I followed your instructions, installed the driver, then ran iwconfig. I could see wlan0 (!)

I tested it by removing the ethernet and was able to load two pages before the network dropped again, and I was unable to get it running again.

Restarting the computer cleared wlan0 from iwconfig. 

But definitely! This is progress!

---

### Post by chili555 on 2014-12-09
> Restarting the computer cleared wlan0 from iwconfig. I strongly suspect that this is because of the conflict between the compiled driver and ndiswrapper, as I warned. Until we get any further, I suggest you unload ndiswrapper and blacklist it. Then we can troubleshoot the compiled driver:```
sudo -i
modprobe -r ndiswrapper
echo "blacklist ndiswrapper"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot and check if ndiswrapper is loaded:```
lsmod | grep -e ndis -e r819
```Is there a wlan0?```
iwconfig
```Errors, warnings, etc. showing?```
dmesg | grep -e r819 -e wlan
```

---

### Post by Aubrey_Lavigne on 2014-12-10
I've reinstalled Ubuntu again, this time as a dual boot with Windows 8.1. I'm still intending to use Ubuntu as my primary OS, but this gave me the opportunity to go into this without any worrying about ndiswrapper still lying around. 

Going in, things were looking great, but the Wireless Connection started to drop and it would reprompt me for my password.  I checked dmesg and found thousands and thousands of lines of 

```

[26610.535303] rtl819xP 0000:05:05.0: PCI-DMA: Out of IOMMU space for 9100 bytes.
[26610.537111] rtl819xP 0000:05:05.0: PCI-DMA: Out of IOMMU space for 9100 bytes.
[26610.546070] rtl819xP 0000:05:05.0: PCI-DMA: Out of IOMMU space for 9100 bytes.

```

At first the wireless was working, then it would stop working intermittently, and it would come back after a bit, but after a while (maybe an hour), the wireless would stop reconnecting, and eventually, my ethernet would stop working as well. 

I'm out of time during my lunch break, but I hope to get this resolved tonight.

---

### Post by chili555 on 2014-12-10
> [COLOR="#FF0000"]rtl819xP[/COLOR] 0000:05:05.0: PCI-DMA: Out of IOMMU space for 9100 bytes.Old Chili smells a great big rat! Let's see:```
lsmod | grep ndis
cat /etc/modules
ls /etc/ndiswrapper
```Thanks.

---

### Post by Aubrey_Lavigne on 2014-12-10
Sure.

```

aubrey@aubrey-desktop:~$ lsmod | grep ndis
aubrey@aubrey-desktop:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

aubrey@aubrey-desktop:~$ ls /etc/ndiswrapper
ls: cannot access /etc/ndiswrapper: No such file or directory
aubrey@aubrey-desktop:~$ 


```

I"m up for ideas, but in the meantime, I'm looking into this issue as well (of course)

---

### Post by Aubrey_Lavigne on 2014-12-11
Ok, new update.

I looked at my bios and I saw that IOMMU was set to disabled. I enabled it and chose the available setting of using 64MB for IOMMU. I restarted the server, and it's no longer prompting me to reenter the information. Before I made this change, the ethernet would eventually go out as well, but now that's not happening.

When I am using ethernet, everything appears to be fine. After using the wireless for a couple minutes, Requests seem to go unanswered. I might request a page (say google), and the response times out, and ping returns with a 100% failure rate, but the wireless icon seems to imply that everything is looking good.  I have to disconnect from the wireless connection and reconnect. to be able to use it again, but then it falls back into the same issue pretty quickly.

I'm going to search through the forums to find any related issues tomorrow evening.

---

### Post by Aubrey_Lavigne on 2014-12-11
Woke up to lots of this message in dmesg:

```

[30611.215217] rtl819xP:No more TX desc@6, ring->idx = 0, idx = 0,52

```

---

### Post by chili555 on 2014-12-11
> **Aubrey_Lavigne said:**
> Woke up to lots of this message in dmesg:

```

[30611.215217] rtl819xP:No more TX desc@6, ring->idx = 0, idx = 0,52

```Aside from the obvious, a different supported device, all I can suggest is to file an issue with the developer: [https://github.com/lwfinger/rtl8190p](https://github.com/lwfinger/rtl8190p)

You might also experiment with settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router. You might also try with and without N speeds.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

---

