---
title: "setting up wireless"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by dogstar55 on 2009-02-01
Hi guys,

I am an absolute beginner and need you help to setup my wireless on my laptop.

I have a broadcom card, but beyond this i have no clue where to start or what to do to get the wireless working.

Please help.

Thanks

---

### Post by dogstar55 on 2009-02-01
oh, its an hp laptop G5055ea, and using hardy heron ubuntu

---

### Post by dogstar55 on 2009-02-01
i believe this information will be useful

lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
06:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by ugm6hr on 2009-02-01
```
06:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
```
Thats your wifi card.

Have you got wired internet access?

If yes - got to System -> Administration -> Hardware Drivers

See if wl or b43 are listed.  If not - you need to install it.  It should offer to do that for you if you are online with a wire.

If not - there is a workaround...  I will find it if necessary.

I did find this: [http://ubuntuforums.org/showpost.php?p=4017142&postcount=6](http://ubuntuforums.org/showpost.php?p=4017142&postcount=6) (although I hope this is no longer necessary).

---

### Post by dogstar55 on 2009-02-01
no dont even have wired access. I put the lan cable in and nothing happends. Yellow light on the card just burns constant.

---

### Post by ugm6hr on 2009-02-01
You have a supported ethernet card.  It should work just by plugging in.

Are you running the latest 8.10 kernel?  I have read that it has made a mess of networking.

Do you have an unusual network setup (proxy etc)?

---

### Post by EMR on 2009-02-01
I remember this problem from when I first started using Ubuntu.  I fixed it by installing the wireless drivers with *Ndswrapper*, after downloading them over a wired connection.

    Look for *NetworkMangier*.  Make sure that wired networking is enabled-it will sometimes end up shut off after unsuccessful tries to get wireless working.

    If it is in "on" mode, the next step would be to locate the problem.  Do you have a computer that usually works?  If so try to connect it to the wired connection that won't work with your laptop.  If that works, then you know that its the laptop's problem, right?

    I hope I can be of some help.

---

### Post by dogstar55 on 2009-02-02
> **ugm6hr said:**
> You have a supported ethernet card.  It should work just by plugging in.

Are you running the latest 8.10 kernel?  I have read that it has made a mess of networking.

Do you have an unusual network setup (proxy etc)?

No unsual network setup - normal at home type of thing.

Okay how do i use ndiswrapper? I am a begginer, and am not sure about how to do a lot of the stuff you guys are suggesting. Also without a working network connection in ubuntu (wireless or otherwise) i have to swap between vista and ubuntu on the one notebook in order to post on this forum or to read other articles.

---

### Post by ugm6hr on 2009-02-02
Given you only have the one computer, I don't want to frustrate you with different things to try.

I am a little concerned that your wired connection doesn't work either, since this suggests a problem with the networking as a whole, rather than just a driver issue for the wifi (which should be easy enough to resolve once you can get a wired connection).

If I could ask you one thing: does your home network use DHCP or static IP?

If you don't know the answer - just describe how you connected with Vista the first time (did the wired work straight away just by plugging in - or did you have to set an IP address etc).

Then, do the following:

Plug the wired ethernet in, and reboot into Ubuntu.

Run the following commands in Terminal, and then copy and paste everything into a text file, and save to a USB stick.  Then upload or paste the results back here.  Hopefully one of these commands will give a clue as to what is happening.

```
lshw -class network
ifconfig
iwconfig
```

I do have one other thing for you to look at - see the Wifi help link below in my signature.  Number 9 there talks about power-saving functions in Windows which will turn off your network cards - not sure how it applies to Vista, but I'm sure it should be similar.  make sure you don't have that turned on (it seems pretty pointless anyway).

---

### Post by dogstar55 on 2009-02-02
My home network uses DHCP ( it connected straight away, no need to set the IP address etc).

Will try out the reboot with the wired internet. Will also give you the output you require, got to do it all later, cause i am at work now. Thanks though, i think this is a good start:)

---

### Post by dogstar55 on 2009-02-02
success with the wired connection to my lan. Rebooting with the lan cabe connected worked thanks guys.

Now onto the wireless.

Your requested the following output

 lshw -class network
> WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:e9:6e:4f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.104 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:47:eb:7f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


 ifconfig
> eth0      Link encap:Ethernet  HWaddr 00:16:d4:e9:6e:4f  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fee9:6e4f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2385 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1943 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2647377 (2.5 MB)  TX bytes:266028 (259.7 KB)
          Interrupt:18 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1452 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1452 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:72600 (70.8 KB)  TX bytes:72600 (70.8 KB)


iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"TopDog"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


So where to next?

---

### Post by mgw2008 on 2009-02-02
I came across several entries indicating that these cards are having trouble. You may want to search the forums for "broadcom" I remeber seeing a resolution guide somewhere.

---

### Post by dogstar55 on 2009-02-02
> **mgw2008 said:**
> I came across several entries indicating that these cards are having trouble. You may want to search the forums for "broadcom" I remeber seeing a resolution guide somewhere.

I been through quite a few threads already and tried what they suggested, however as a noob to ubuntu/linux i have no idea what i am doing, i might be doing things wrong. If possible step  by step would really help

---

### Post by dogstar55 on 2009-02-02
i am trying the steps on this page:
[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)

i am getting stuck on the step 2. I dunno what its doing

---

### Post by stchman on 2009-02-02
You can try the Broadcom cutter.

```

sudo apt-get install b43-fwcutter

```

If that give no joy then use the ndisgtk package


```

sudo apt-get install ndisgtk

```

This will allow you to use the Windows .inf to get that card working.

---

### Post by dogstar55 on 2009-02-02
> **stchman said:**
> You can try the Broadcom cutter.

```

sudo apt-get install b43-fwcutter

```

If that give no joy then use the ndisgtk package


```

sudo apt-get install ndisgtk

```

This will allow you to use the Windows .inf to get that card working.

I am using vista, will i still be able to find a .inf file?

As for b43-fwcutter, i tried it but i am not sure if the installation was correct. The link i posted above specifically states to not use it.

---

### Post by smothpocket on 2009-02-02
With broadcom cards I've always had good luck with this guide:

[http://linuxwireless.org/en/users/Drivers/b43#firmwareinstallation](http://linuxwireless.org/en/users/Drivers/b43#firmwareinstallation)

It has links for the driver files as well...

---

### Post by ugm6hr on 2009-02-02
OK. At least you are online now.  Makes things a lot easier.

First:

Let us know exactly what you have done so far, since everything you do can impact on future advice.

Then try and install the b43 driver:

> **ugm6hr said:**
> If yes - got to System -> Administration -> Hardware Drivers

See if wl or b43 are listed.  If not - you need to install it.  It should offer to do that for you if you are online with a wire.

If not - there is a workaround...  

That workaround: [http://ubuntuforums.org/showpost.php?p=6028741&postcount=4](http://ubuntuforums.org/showpost.php?p=6028741&postcount=4)

---

