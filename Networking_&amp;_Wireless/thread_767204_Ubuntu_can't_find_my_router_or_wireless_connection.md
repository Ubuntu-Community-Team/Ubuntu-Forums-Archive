---
title: "Ubuntu can't find my router or wireless connection"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by Jonas Wakefield on 2008-04-25
Ok, my friend convinced me to move to Ubuntu from Windows, so I put in a Live Disc, installed it and all, and Ubuntu is there running...but it cannot locate my router or any wireless connection or anything to do with the Internet. What do I do?!?

I still have Vista on my Dell Inspiron 6400 and it connects no problem. Now I'm not advanced with all this, but my friend told me that Windows has Drivers, whil Ubuntu doesnt. I was so confused. Then he said I needed a new Network Card because I had faulty hardware, but it works with Vista no problem. 

Can anyone help, if not I'll have to go back to Windows, at the moment it seems easier to use. Everyone says Linux is better, if the Internet worked I can believe it...PLEASE HELP!!! 

Thank You

---

### Post by Jonas Wakefield on 2008-04-25
Also my connection is fine on everything else and its a belkin54g. I'm so frustrated.:mad:

If nobody knows, can somebody tell me how can I delete Ubuntu...if things have to come to this...:(

---

### Post by chili555 on 2008-04-25
> Windows has Drivers, whil Ubuntu doesntQuite the reverse! Windows has drivers on the install disk, but not many built in the operating system. Ubuntu has hundreds built in . The question is whether it has the exact driver you need. Open a terminal (Applications -> Accessories -> Terminal) and type:```
sudo lshw -C network
```I know it's a pain to transfer this information from Ubuntu to Windows so you can post it, so let's just copy the basics. You will see data about your ethernet and your wireless. Skip the ethernet, and, under the wireless, we want the description of the card, the logical name and the driver, if any. Here's an example with the essentials bolded:```
 *-network
       description: Wireless interface
    **product: PRO/Wireless 3945ABG Network Connection**
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
    **logical name: wmaster0**
       version: 02
       serial: 00:19:d2:c2:1b:8d
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes **driver=iwl3945** ip=192.168.1.104 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
```Please post and we'll do our best to get you going.

---

### Post by Jonas Wakefield on 2008-04-26
Ive tried that code and it comes up with lots of 0's, I think I have to do what this link below says, whatever it means:

[https://help.ubuntu.com/community/WifiDocs/Driver/1390](https://help.ubuntu.com/community/WifiDocs/Driver/1390)

I think this is my driver because when I open Device Manager (on Windows Vista)and go under Network Adapters it says I have:

Broadcom 440x10/100 intergrated Controller
Dell Wireless 1390 WLAN Mini-card

---

### Post by Jonas Wakefield on 2008-04-26
Ok I type down this in Terminal:

sudo lshw -C network

and I got all this when I typed down my password:

*-network DISABLED      
       description: Wireless interface 
       product: BCM94311MCG wlan mini-PCI 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:0b:00.0 
       logical name: eth1 
       version: 01 
       serial: 00:1e:4c:67:b8:72 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=0 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g 
  *-network 
       description: Ethernet interface 
       product: BCM4401-B0 100Base-TX 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:1d:09:b1:41:77 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=64 link=no module=b44 multicast=yes port=twisted pair speed=10MB/s 

Now I no nothing but I believe it may be to do my bcm43xx driver...

I went to System > Administration > Restricted Drivers(I think thats what its called) and try to enable it but it wouldn't let me. It says for my wireless card to work I need to enable it which I can't.

So I think I need to do what this link says I have to do:

[https://help.ubuntu.com/community/WifiDocs/Driver/1390](https://help.ubuntu.com/community/WifiDocs/Driver/1390)

But I have problems with this:
When I get rid of the old ndiswrapper and bcm43xx driver, does affect my computer or Windows Vista at all?
Also in the link it says: 
Get the latest version of ndiswrapper 
$wget [http://nchc.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.42.tar.gz](http://nchc.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.42.tar.gz)
But to get this I need to be on the Internet which is the main problem.

I know that this is a long message that doesnt make sense to me or you, but can anyone help?

Cheers

---

### Post by chili555 on 2008-04-26
> *-network DISABLED Let's take one step at a time. Your setup looks pretty good, except your wireless card is evidently *turned off!*

No need to download or install anything yet, because it won't work on a turned-off card. Is there a physical switch or key combination, Fn+F5 maybe, on your Dell that turns off the wireless so you don't use up all your battery while playing solitaire at the airport? Open a terminal and do:```
sudo tail -f /var/log/messages
``` while you manipulate the switch and key combination. When you get it, the kernel might give a message.

Post back and let us know.

> When I get rid of the old ndiswrapper and bcm43xx driver, does affect my computer or Windows Vista at all?Not in the least. Don't do step 4 before we solve step 1, however.

---

### Post by wilsonmuse on 2008-04-26
You have a working driver, your interface just isn't configured.

To enable your wireless try this:

```
sudo ifconfig eth1 up
```

See if that removed "DISABLED" from the output of

```
lshw -C network
```

also check to see if eth1 shows up in the output of this command now:

```
ifconfig
```

---

### Post by Jonas Wakefield on 2008-04-27
chill555 my card isn't switched of when on Vista and I know not of any switch or key combination. I typed down what you siad in Terminal and received this if it means anything you:

Apr 27 10:41:58 caelan-laptop kernel: [   19.664000] Bluetooth: RFCOMM TTY layer initialized 
Apr 27 10:41:58 caelan-laptop kernel: [   19.664000] Bluetooth: RFCOMM ver 1.8 
Apr 27 10:42:03 caelan-laptop kernel: [   24.256000] [drm] Initialized drm 1.1.0 20060810 
Apr 27 10:42:03 caelan-laptop kernel: [   24.260000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16 
Apr 27 10:42:03 caelan-laptop kernel: [   24.260000] [drm] Initialized i915 1.6.0 20060119 on minor 0 
Apr 27 10:44:09 caelan-laptop kernel: [  150.172000] NET: Registered protocol family 10 
Apr 27 10:44:09 caelan-laptop kernel: [  150.172000] lo: Disabled Privacy Extensions 
Apr 27 10:44:09 caelan-laptop kernel: [  150.172000] ADDRCONF(NETDEV_UP): eth0: link is not ready 
Apr 27 10:47:40 caelan-laptop syslogd 1.4.1#21ubuntu3: restart. 
Apr 27 11:01:56 caelan-laptop -- MARK -- 

-----------------------------------------------------------------
wilsonmuse I typed what you said and received this (In bold is what you told me to type):

caelan@caelan-laptop:~$ **sudo ifconfig ethl up** 
ethl: ERROR while getting interface flags: No such device
 
caelan@caelan-laptop:~$ **lshw -C networkifconfig** 
WARNING: you should run this program as super-user. 

caelan@caelan-laptop:~$ **ifconfig** 
eth0      Link encap:Ethernet  HWaddr 00:1D:09:B1:41:77  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:3824 (3.7 KB)  TX bytes:3824 (3.7 KB) 

Hope this means something to each of yous.

---

### Post by wilsonmuse on 2008-04-27
> **Jonas Wakefield said:**
> 
caelan@caelan-laptop:~$ **sudo ifconfig ethl up** 
 
caelan@caelan-laptop:~$ **lshw -C networkifconfig** 

caelan@caelan-laptop:~$ **ifconfig** 


Ok, the first command should be:

```
sudo ifconfig eth1 up
```

the "eth" is followed by a 1 (number) and the second:

```
sudo lshw -C network
```

---

### Post by unMourned on 2008-04-27
Jonas,

You're not alone here.  As you will see below, my wireless is disabled, too.  HP laptop zd8000, with the following network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02).

I'll be stepping through the recommended fixes with you--so we'll be working in parallel to fix this problem.

-Paul 


  *-network:0
 description: Ethernet interface 
 product: RTL-8139/8139C/8139C+
 vendor: Realtek Semiconductor Co., Ltd.
 physical id: 2
 bus info: pci@0000:0b:02.0
 logical name: eth0
 version: 10
 serial: 00:c0:9f:d0:be:4d
 width: 32 bits
 clock: 33MHz
 capabilities: bus_master cap_list ethernet physical
 configuration: broadcast=yes driver=8139too driverversion=0.9.28 
latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:0b:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: MA: CA: DD: RE: SS: 00
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by Jonas Wakefield on 2008-04-27
I'm guessing Broadcom doesnt let Ubuntu on or just doesnt distribute the info, but at least other people like you have this problem i thought it was just me...

I'll try some of those methods tomorrow, but I'll probably end up having to get a new driver or something along those line.
I'll be back at 6:00pm probably

---

### Post by Jonas Wakefield on 2008-04-28
Ok I've seen several links of how to get wireless to work with Broadcom, so I'll upgrade to verion 8.04 (Is that what Hardy is...?) Anyway I'll get the Live Disc and follow the rules, fingers crossed it works.

If not then I'll get my friend who is a big Ubuntu supporter (he introduced me to it)and he says he'll figure it out.

---

### Post by Jonas Wakefield on 2008-04-30
Got Hardy installed and the b43fwcutter installed fine, but yet another problem arises for me...

My Internet worked after getting the b43fwcutter, but the next day after switching on my laptop and going onto Ubuntu, I couldn't get on the internet, yet it could see my wireless router (belkin54g) and its signal. Yet it still cannot connect...

I put a Monitor Network applet in my panel, and it was set to wlan0 when it was working. Now it stays at either: lo or wlan0-aviste or something. When at lo it status is idle, when at wlan0-aviste (something along those lines) its idle, but wlan0 is disconnected.

Does anyone what I have to set this to and what do I have to do. Do I have to configure? Why?

---

### Post by lrbradford on 2008-04-30
HI guys!  Can I jump in here with my issues?  I have tried some of these commands and saved my terminal's output.  First, some background:

Toshiba A215 AMD 64 2x with a Realtek 

snip 8<--------------------

lynn@lynn-laptop:~$ sudo lshw -C network 
[sudo] password for lynn: 
  *-network               
       description: Ethernet interface 
       product: RTL8101E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:08:00.0 
       logical name: eth0 
       version: 01 
       serial: 00:a0:d1:84:8a:26 
       capacity: 1GB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair 
lynn@lynn-laptop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

lynn@lynn-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:84:8a:26  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:252 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:262 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:262 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:14300 (13.9 KB)  TX bytes:14300 (13.9 KB) 
snip 8<-------------------------

Any ideas, please enlighten me.  This is a dual boot with Vista and Ubuntu 8.04.

---

### Post by chili555 on 2008-05-01
@Irbradford

I think you are better to start your own thread. When you do, post all you have here and try to get at least some information about your wireless card, with *lspci* or *lsusb* or, worst case, tell us whatever you can by looking at it: make, model, version, etc. 

It *is* your wireless you are trying to get going, isn't it?

---

### Post by lrbradford on 2008-05-01
Both!  Wired and wireless.  But since I am on the road, I'll have to wait until I get back home to my home system and run a wire to the router.  After I do that, I assume I run the same commands?

Thanks in advance,

LB

---

### Post by chili555 on 2008-05-02
Irbradford-

Please start a new thread with:```
sudo lshw -C network
ifconfig
```Let's start with wired.

---

### Post by SonicReducer on 2008-05-02
Just like to add that I'm having some similar issues though I've posted a new thread.

---

