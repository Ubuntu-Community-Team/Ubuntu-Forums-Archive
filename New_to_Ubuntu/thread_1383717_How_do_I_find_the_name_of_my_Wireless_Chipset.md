---
title: "How do I find the name of my Wireless Chipset?"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by gmf64 on 2010-01-17
I have finally got my wireless up and running on my Toshiba Satellite L555D-103. Now, I want to find out what chipset my wireless is using. I have searched the Toshiba website, googled and used the forums. Can anyone point me in the right direction? And can I find out by using commands in the terminal?

Here is what I can find as of now.

lshw gives me (have taken away what I don't think is needed.
*-network
                description: Wireless interface
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:0e:00.0
                logical name: wlan0
                version: 10
                serial: 70:1a:04:29:74:76
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl819xSE driverversion=V 1.1 firmware=49 ip=192.168.1.4 latency=0 link=yes multicast=yes wireless=802.11bgn
                resources: irq:18 ioport:a000(size=256) memory:f0200000-f0203fff


 *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:14:00.0
                logical name: eth0
                version: 02
                serial: 00:26:22:37:03:61
                size: 10MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:29 ioport:b000(size=256) memory:f0410000-f0410fff(prefetchable) memory:f0400000-f040ffff(prefetchable) memory:f0420000-f043ffff(prefetchable)


lspci gives me (I have taken away things I don't believe is needed)

0e:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
14:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by nick_goodfate on 2010-01-17
try this in terminal  > lspci | grep Network

sorry you already done it , i didnt noticed :P

---

### Post by lotharmat on 2010-01-17
if that doesn't find it try 

```
lsusb | grep network
```

Damn - I need to learn to read too!

But yeah - You have a realtek rtl8172

---

### Post by mgmiller on 2010-01-17
```
sudo lspci
```
is what shows me mine:

```
marty@marty-laptop:~$ sudo lspci
[sudo] password for marty: 
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
07:00.0 Network controller: RaLink RT2561/RT61 802.11g PCI

```

In my case, it's the last line:
07:00.0 Network controller: RaLink RT2561/RT61 802.11g PCI

This is a cardbus device (pcmcia).  If yours is a built in, i'm not sure how it would show up.  If it's a USB device, the lsusb should show it to you.

---

### Post by gmf64 on 2010-01-17
Funny thing this Linux. After using 2 days I finally got the wireless working. Now, it doesn't want to connect again. I try to connect and after the "spinning wheel" finishes on top, it just states it has disconnected. Yikes. Linux ! Yes I know, It's not Linux, but myself who needs to learn more. (Now I am on my other Windows laptop).
 
That aside, and back to the point. I still can't find out what chipset my wireless uses. Any search ablilities through google I haven't thought about or any other commands I can use on the terminal ?

---

### Post by chili555 on 2010-01-17
> I still can't find out what chipset my wireless uses.> 0e:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)That's it!

---

### Post by gmf64 on 2010-01-17
Ok. I might be too much of a newbie here. As you say:

"That's it !
0e:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)"

I thought Device was used when the commands didn't find the name. Like a John Doe kind of thing.

Looking through the Realtek homepage "Device 8172", "8172" etc. doesn't give any hits. When I search for "chipset", I get a lot of series and names but not 8172. But when I look at their FAQ I see near identical numbers/names referred to as drivers.

So just to clarify, so I don't need to go through this when I start looking around to see if this chipset can be used for wardriving etc (part of my bachelor project), what you are telling me is that my chipset is called Device 8172 ?

---

### Post by bkratz on 2010-01-17
Here is someone with the same chipset (see where it shows up red), I did a search (above) for 8172 in the networking and wireless section and found quite a few entries.

[http://ubuntuforums.org/showthread.php?t=1377532&highlight=8172](http://ubuntuforums.org/showthread.php?t=1377532&highlight=8172)
Here is the search results

[http://ubuntuforums.org/search.php?searchid=69201678](http://ubuntuforums.org/search.php?searchid=69201678)

---

### Post by bkratz on 2010-01-17
Also here is one with directions

[http://ubuntuforums.org/showthread.php?t=1367871&highlight=8172](http://ubuntuforums.org/showthread.php?t=1367871&highlight=8172)

---

### Post by gmf64 on 2010-01-17
"Here is someone with the same chipset"

Yup, ;) that's my first post, while trying to get the drivers for the wireless to work.

And the other link you posted is the one I used when installing the drivers. It worked. But thanx.

I guess my problem is that what I keep thinking of as drivers are the name of the chipset.

---

### Post by falconindy on 2010-01-17
The answer is right in your first post.

> **gmf64 said:**
> *-network
                description: Wireless interface
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:0e:00.0
                logical name: wlan0
                version: 10
                serial: 70:1a:04:29:74:76
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes **driver=rtl819xSE** driverversion=V 1.1 firmware=49 ip=192.168.1.4 latency=0 link=yes multicast=yes wireless=802.11bgn
                resources: irq:18 ioport:a000(size=256) memory:f0200000-f0203fff

---

### Post by bkratz on 2010-01-17
> **falconindy said:**
> The answer is right in your first post.

That is the driver that is highlighted-- the chipset is the 8172 mentioned earlier in Chili555's posting

---

### Post by chili555 on 2010-01-17
> I thought Device was used when the commands didn't find the name. Like a John Doe kind of thing.'Device' is used when the card doesn't report exactly what it is, i.e., Network Controller, sound card, video card, etc. > what you are telling me is that my chipset is called Device 8172 ? Your chipset is Realtek 8172. Why in the world Realtek identifies it in the card's lspci as an 8172 but it needs 8192SE drivers, I couldn't tell you. However, you know it does:> driver=rtl819xSE driverversion=V 1.1 firmware=49 ip=192.168.1.4An interface, wlan0, has been created, the driver, rtl819xSE has grabbed your card and you are connected and have an IP address.

If I were searching, I'd check every variation of Realtek: 8172, 8192SE and 819xSE. 

As I've said before, you are treading new ground here. As far as I know, no one has tried injection with this device. I wouldn't be a bit surprised to find no previous posts on wardriving with this device. I'd suggest you learn all you can about the general subject of wardriving and injection and simply try with your card.

If you get nowhere, you can always buy an external card after researching known, working...dare I say it?...devices.

---

### Post by chili555 on 2010-01-17
Here are two links that will be useful:

[http://www.thinkwiki.org/wiki/ThinkPad_11b/g/n_Wireless_LAN_Mini-PCI_Express_Adapter_II](http://www.thinkwiki.org/wiki/ThinkPad_11b/g/n_Wireless_LAN_Mini-PCI_Express_Adapter_II)

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=226&DownTypeID=3&GetDown=false&Downloads=true#2281](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=226&DownTypeID=3&GetDown=false&Downloads=true#2281)

---

### Post by mgmiller on 2010-01-18
I'm not saying you should stop trying to get your existing hardware working.  Sometimes, that's half the fun.  

But....if you want a simple and cheap 802.11 b/g card that "just works", you can try this one....[http://www.newegg.com/Product/Product.aspx?Item=N82E16833315047&Tpk=33-315-047](http://www.newegg.com/Product/Product.aspx?Item=N82E16833315047&Tpk=33-315-047)

I use it in an old Dell notebook and it's very reliable and required no setup at all.  Truly plug and play.  And only about $18.00 US.  Sometimes it's offered with free shipping.

---

