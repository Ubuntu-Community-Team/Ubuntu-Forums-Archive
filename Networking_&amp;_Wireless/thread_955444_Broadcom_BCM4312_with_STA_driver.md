---
title: "Broadcom BCM4312 with STA driver"
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by _Q_ on 2008-10-22
Hello everyone :)

I just recently bought a new laptop - HP Compaq 6820s, and it has the Broadcom's WiFi chipset. I installed the latest Hardy and updated all packages, so the new STA driver became active. I searched the forums & the web for some solutions to these problems, but no luck ... :/

So, whats the problem?
[LIST]
[*]I can only see WiFi networks if using the "roaming mode" in Network manager, so they are listed in the nautilus-panel (next to the clock - nm_applet) + using iwlist tool, but only as sudo 
=> doesn't work if using the Network manager itself (btw. is there a "more intelligent" applet than nm_applet for this sort of thing?)[/LIST][LIST]

[*]I can't change the mode to "Monitor", which I really find useful, nor use the tools which use this mode (such as airodump). Here's the error message:
```
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211
or ARPHRD_IEEE80211_PRISM instead. Make sure RFMON is enabled:
run 'ifconfig eth1 up; iwconfig eth1 mode Monitor channel <#>'
Sysfs injection support was not found either.
```[/LIST]
Here is some information:
```
**lspci | grep Broadcom**
10:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)
```
```
**lshw -C network**
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth1
       version: 02
       serial: 00:21:00:51:5d:47
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11abg
```

P.S. does anyone know, is the 802.11a part of the WiFi working with STA driver? (it doesn't work with [b43/b43legacy driver]("http://linuxwireless.org/en/users/Drivers/b43"))

---

### Post by Sam Lars on 2008-10-22
I don't think I understand exactly what you're saying here.  You said nm works?  What do you mean it doesn't work "by itself"?
If you're looking for an alternative to nm-applet, you can check out wicd.  From seeing screenshots it looks more intelligent to me.
I think I have a 4312 also, and I tried the monitor mode with both ndiswrapper and the wl (STA?) at the time, and neither one said it was supported.

---

### Post by _Q_ on 2008-10-22
Hey Sam,

thanks for your reply :)

Sorry if I wrote it a bit fuzzy - when clicking on the nm_applet, I can see the available networks, but if I use the Network manager and click on the Networks drop-down menu, then it doesn't work...
Thank You for the wicd hint, it really looks more intelligent :D I'll give a go later today.

If you check this page: [http://www.devicescape.com/docs/uwp/package_guide/pkg_broadcom-wl-drv.php]("http://www.devicescape.com/docs/uwp/package_guide/pkg_broadcom-wl-drv.php")
You can see that the monitor mode is mentioned near the bottom while setting the client.
> The Broadcom driver adds a new network interface, prism0, for the monitor mode. This interface must be used (instead of eth#) when configuring tcpdump or Ethereal.

---

### Post by Ayuthia on 2008-10-22
> **_Q_ said:**
> Hey Sam,

thanks for your reply :)

Sorry if I wrote it a bit fuzzy - when clicking on the nm_applet, I can see the available networks, but if I use the Network manager and click on the Networks drop-down menu, then it doesn't work...
Thank You for the wicd hint, it really looks more intelligent :D I'll give a go later today.

If you check this page: [http://www.devicescape.com/docs/uwp/package_guide/pkg_broadcom-wl-drv.php]("http://www.devicescape.com/docs/uwp/package_guide/pkg_broadcom-wl-drv.php")
You can see that the monitor mode is mentioned near the bottom while setting the client.
This looks like a different driver because the link that you provided seems to cover the 4306 mini-PCI card and the BCM471x system-on-a-chip (SoC) radios.

---

### Post by _Q_ on 2008-10-22
> **Ayuthia said:**
> This looks like a different driver because the link that you provided seems to cover the 4306 mini-PCI card and the BCM471x system-on-a-chip (SoC) radios.Indeed it is, sorry for incorrect information.

But... a quote from the b43 driver page:
> WORKING:
    * Station mode
    * Mesh networking mode
    * Access Point mode (not quite yet, blocked by proper support in mac80211 and hostapd)
    * Ad-Hoc (IBSS) mode
    * **Monitor** and Promisc mode.
    * "Monitor while operating" and multiple monitor interfaces.
    * In-Hardware traffic de/encryption (relieves your CPU).
    * LEDs to signal card state and traffic.
    * In-Hardware MAC address filter.
    * **Packet injection** (with radiotap; no FCS injection currently though hardware supports it - a radiotap flag is being discussed for this)
I haven't tryed the b43 driver since everyone says the wl is better (better signal interpretation)..

---

### Post by Ayuthia on 2008-10-22
> **_Q_ said:**
> Indeed it is, sorry for incorrect information.

But... a quote from the b43 driver page:

I haven't tryed the b43 driver since everyone says the wl is better (better signal interpretation)..

The b43 driver is just about as good as the wl driver in 2.6.27 (Intrepid's kernel).  However, the wireless a still is not available for the 4312.

---

### Post by _Q_ on 2008-10-22
> **Ayuthia said:**
> The b43 driver is just about as good as the wl driver in 2.6.27 (Intrepid's kernel).  However, the wireless a still is not available for the 4312.So, if I understod right, you're saying that it's a kernel fault, not the drivers? Couldn't the driver be applyed if one re-compiled the kernel manually?

Also, is it confirmed that the wl driver doesn't support Monitor mode, or should I (try to) ask the Broadcom? :roll:

---

### Post by Ayuthia on 2008-10-22
> **_Q_ said:**
> So, if I understod right, you're saying that it's a kernel fault, not the drivers? Couldn't the driver be applyed if one re-compiled the kernel manually?No.  The driver is included in the kernel.  So there were updates made to the b43 driver between 2.6.24 to 2.6.27 that has made the b43 driver operate better.

> Also, is it confirmed that the wl driver doesn't support Monitor mode, or should I (try to) ask the Broadcom? :roll:Good luck!  I think I sent them a message once about something with the driver and they told me that they do not deal with the end user.  They told me that I need to go the supplier of the product for support.

---

### Post by lovethepirk on 2008-10-22
I do not know much about this but I have messed with Broadcom **** for a long time in linux.

Does this forum topic around post #13 help you at all?
[http://forums.fedoraforum.org/showthread.php?t=201366](http://forums.fedoraforum.org/showthread.php?t=201366)

It deals with the kernel a bit...

---

### Post by _Q_ on 2008-10-23
> **Ayuthia]No. The driver is included in the kernel. So there were updates made to the b43 driver between 2.6.24 to 2.6.27 that has made the b43 driver operate better.[/QUOTE]Ohhh, ok. :) I'll do a manual compiling of the 2.6.27 then and post the results here...
[QUOTE=Ayuthia]Good luck! I think I sent them a message once about something with the driver and they told me that they do not deal with the end user. They told me that I need to go the supplier of the product for support.[/QUOTE]:roll: :lol: I'll try my luck and also post the results. Thank You for the hint  said:**
> Does this forum topic around post #13 help you at all?Thank You for the information, but guys in that topic are dealing with a manual installation of the STA driver, which comes automatically in ubuntu (sweet, isn't it? :))

---

### Post by _Q_ on 2008-10-23
> **_Q_ said:**
> :roll: :lol: I'll try my luck and also post the results. Thank You for the hint ;)[QUOTE=Broadcom]Broadcom offers support for Ethernet NIC products and does not provide end-user support for other networking products at this time. Please contact your product's manufacturer for support related issues.[/QUOTE]So I've contacted HP's live support who kindly pointed me to their support forums & their phone live support (which has some distant call numbers, which I don't intend to call).
So much about finding out more about STA driver...

I'll try the kernel re-compiling with b43 driver next.

---

### Post by Ayuthia on 2008-10-23
> **_Q_ said:**
> So I've contacted HP's live support who kindly pointed me to their support forums & their phone live support (which has some distant call numbers, which I don't intend to call).
So much about finding out more about STA driver...

I'll try the kernel re-compiling with b43 driver next.

You could always try the Intrepid release candidate CD also.  That way you don't have an extra kernel sitting around.  Of course, it is more fun building things!

---

### Post by _Q_ on 2008-10-23
> **Ayuthia said:**
> You could always try the Intrepid release candidate CD also.  That way you don't have an extra kernel sitting around.  Of course, it is more fun building things!I took your advice and tryed the Intrepid Live CD. By looking at the System -> Administration -> Hardware Drivers, it seems it's using the wl (STA) driver by default. There is no problem with setting the mode to Monitor, but the whole networking in Intrepid seems to disabled :/
I can't detect any wireless networks and by issuing lshw -C network, it's obvious that both Ethernet & Wireless are marked as "DISABLED"...

Any suggestions how to try this out, before recompiling the kernel for Hardy?

btw. There are wmaster0 & wlan0 interfaces in Intrepid and in Hardy there was only eth1, although it is supposedly the same (STA) driver??

---

### Post by Ayuthia on 2008-10-23
> **_Q_ said:**
> I took your advice and tryed the Intrepid Live CD. By looking at the System -> Administration -> Hardware Drivers, it seems it's using the wl (STA) driver by default. There is no problem with setting the mode to Monitor, but the whole networking in Intrepid seems to disabled :/
I can't detect any wireless networks and by issuing lshw -C network, it's obvious that both Ethernet & Wireless are marked as "DISABLED"...

Any suggestions how to try this out, before recompiling the kernel for Hardy?

btw. There are wmaster0 & wlan0 interfaces in Intrepid and in Hardy there was only eth1, although it is supposedly the same (STA) driver??

It looks like it is still trying to use the b43 driver.  You can try the wl module by doing the following:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo ifconfig wlan0
```
I am not for sure if it will be eth1 or wlan0.  The STA driver should only have eth1 or wlan0 but no wmaster0.  In Arch, the 2.6.27 kernel has this driver using wlan0 instead of eth1.

---

### Post by _Q_ on 2008-10-23
After the changes you suggested, wireless interface is called eth0 :roll:
Wireless stations are now listable via iwlist tool.
After trying to set the mode to Monitor, it gives an unusual message
```
**sudo iwconfig eth0 mode Monitor**
Error for wireless request "Set Mode" (8B06) :
     SET failed on device eth0 ; Invalid argument.
```

---

### Post by Ayuthia on 2008-10-23
> **_Q_ said:**
> After the changes you suggested, wireless interface is called eth0 :roll:
Wireless stations are now listable via iwlist tool.
After trying to set the mode to Monitor, it gives an unusual message
```
**sudo iwconfig eth0 mode Monitor**
Error for wireless request "Set Mode" (8B06) :
     SET failed on device eth0 ; Invalid argument.
```

I forgot that your wired card has not been enabled yet so it set you to eth0.

It looks like you are now using the wl driver!  No Monitor.  Sorry.  Well, you can now enable the b43 module though since you have a connection.  That will bring you the Monitor ability if I recall correctly, but will not give you wireless a.

---

### Post by _Q_ on 2008-10-23
> **Ayuthia said:**
> Well, you can now enable the b43 module though since you have a connection.  That will bring you the Monitor ability if I recall correctly, but will not give you wireless a.I tryed the following:
```
[B]sudo modprobe -r wl
sudo modprobe b43
sudo iwconfig wlan0 mode Monitor[/B]
```
Which all worked, but then if i want to use airodump, for an example...
```
**sudo airodump-ng wlan0**
ioctl(SIOCSIFFLAGS) failed : No such file or directory
```

If I go mode back to Managed mode and want to use iwlist...
```
**sudo iwlist wlan0 scan**
wlan0     Interface doesn't support scanning : Network is down
```

---

### Post by Ayuthia on 2008-10-23
> **_Q_ said:**
> I tryed the following:
```
[B]sudo modprobe -r wl
sudo modprobe b43
sudo iwconfig wlan0 mode Monitor[/B]
```
Which all worked, but then if i want to use airodump, for an example...
```
**sudo airodump-ng wlan0**
ioctl(SIOCSIFFLAGS) failed : No such file or directory
```

If I go mode back to Managed mode and want to use iwlist...
```
**sudo iwlist wlan0 scan**
wlan0     Interface doesn't support scanning : Network is down
```
I am guessing that you have not grabbed the firmware.  You can do it through System->Administration->Hardware Drivers or just install b43-fwcutter.  You can then reload the b43 and ssb modules.

---

### Post by _Q_ on 2008-10-23
> **Ayuthia said:**
> I am guessing that you have not grabbed the firmware.  You can do it through System->Administration->Hardware Drivers or just install b43-fwcutter.  You can then reload the b43 and ssb modules.You're right. Please excuse my lack of knowledge in this matter, since I haven't delt with b43 driver (yet).
It's working now, with b43 firmware. I haven't loaded the ssb module though (and it's working), so could you please explain what it is used for?

I'm planning to switch to the b43 driver completly. If I'm using the latest firmware, should it be as good as the wl (STA) driver? (I haven't been able to test this, so if someone has, please report the results)

---

### Post by Ayuthia on 2008-10-23
> **_Q_ said:**
> You're right. Please excuse my lack of knowledge in this matter, since I haven't delt with b43 driver (yet).
It's working now, with b43 firmware. I haven't loaded the ssb module though (and it's working), so could you please explain what it is used for?

I'm planning to switch to the b43 driver completly. If I'm using the latest firmware, should it be as good as the wl (STA) driver? (I haven't been able to test this, so if someone has, please report the results)

Actually, I am glad that you are keeping up pretty well.  Unfortunately, I don't have have your card, but  I have a 4311 rev 01 and the speeds of this driver match with the ndiswrapper and wl modules.  

The ssb module is the Sonic Silicon Backplane which is something that is found inside the Broadcom cards.  It is needed by the b43 module and the b43 module will load it automatically because it needs it.  You just have to remove the ssb module manually.

You will most likely need to blacklist the wl module so that it will not load up next time:
```
echo blacklist wl | sudo tee -a /etc/modprobe.d/blacklist
```

Hope that helps!

---

### Post by carltonh on 2008-11-08
Just an update, using bcm4312 rev 1, and Ubuntu 8.10 updated through Nov. 8th, 2008, still DOES NOT work using all methods listed on this forum possibly excepting wicd or ndiswrapper, which I haven't tried.  8.04 DOES work however, although I'm pretty sure that if you use the 8.04.1 live CD, wireless will not work either due to an error at the time, but if you update it through a wired connection, wireless will work again on 8.04.

So the wl (STA) driver works on 8.04, not 8.10.  Someone please let me know if they get this particular wireless card working, no one has yet posted success on any thread I've seen for 8.10.  Note that rev 1 is different than rev 2, and also very different from bcm4311, although IIRC, 8.04 considered this wireless card to be a bcm4310.

I don't have a ndiswrapper compatible driver because my laptop (Dell Inspiron 1525) came with Vista.  If Ubuntu 8.10 isn't fixed soon, I'll have to reinstall 8.04 or go to a non-Ubuntu distro, because now I'm having to use Vista (yuck) 99% of my laptop time.

> ch2@ch2-laptop:~$ sudo lsmod|grep -e b4 -e ssb -e wl -e ieee80211
wl                   1085520  0 
ieee80211_crypt_tkip    18048  0 
ieee80211_crypt        14596  2 wl,ieee80211_crypt_tkip
ch2@ch2-laptop:~$ sudo modprobe --show-depends wl
insmod /lib/modules/2.6.27-7-generic/kernel/net/ieee80211/ieee80211_crypt.ko 
insmod /lib/modules/2.6.27-7-generic/volatile/wl.ko 
ch2@ch2-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:cd:92:b5
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.2.5 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:e1:89:ad:04
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 02:7b:59:a3:69:16
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
ch2@ch2-laptop:~$ uname -a
Linux ch2-laptop 2.6.27-7-generic #1 SMP Thu Oct 30 04:12:22 UTC 2008 x86_64 GNU/Linux
ch2@ch2-laptop:~$ lspci -knnmd 14e4:*
0b:00.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4312 802.11b/g [4315]" -r01 "Dell [1028]" "Device [000b]"
ch2@ch2-laptop:~$ 

---

### Post by carltonh on 2008-11-08
I forgot to clarify, that 8.10 will show the available networks through NetworkManager, but it will fail to connect to them.

---

### Post by Sam Lars on 2008-11-08
carltonh, I have a 1525 also, and wl was working well in 8.04, and is working great in 8.10

lspci -knnmd 14e4:*
0b:00.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4312 802.11b/g [4315]" -r01 "Dell [1028]" "Device [000b]"

You say it will fail to connect... are these networks encrypted?  If so, with WPA or WEP?  Could you get the syslog output from when you try to connect to a network?

---

### Post by smalldog on 2008-11-11
> **carltonh said:**
> I forgot to clarify, that 8.10 will show the available networks through NetworkManager, but it will fail to connect to them.

If the NetworkManager can show all available wireless network that means your wireless driver is working correctly under receiving mode. 
Therefore, your problem might caused by authentication. Try not enable encryption to the wireless connection. I am running 8.10 with wl(STA) driver. However, it seems only working under WPA encryption only. Good luck

---

### Post by stevovukovic on 2008-11-18
Maybe this is solution:

deactivate proprietary driver, return blacklist into original form (with b43xx blacklisted)
restart Ubuntu
open Synaptic
install b43-fwcutter (to install proper firmware), you will need to provide Ubuntu install disk
enable finding fw
wait task to complete
restart Ubuntu

eth1 interface will disappear
new wlan0, mon0 and other interfaces will appear
use mon0 for “mode Monitor” purposes

---

