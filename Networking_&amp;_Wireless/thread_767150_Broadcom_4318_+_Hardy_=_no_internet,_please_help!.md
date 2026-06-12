---
title: "Broadcom 4318 + Hardy = no internet, please help!"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by SkipBlue on 2008-04-25
Ok so I just upgraded from 7.10 to 8.04 and my Broadcom 4318 wireless card is not working... help please?:confused:

---

### Post by lewelma on 2008-04-25
I can second that for the Broadcom 4306 driver! I have a Dell True Mobile 1300 card using bcm4306 (R.2), which worked fine under Gutsy. I did a clean install for Hardy, and no wireless! When shutting down, there's a complaint about some bcm-legacy driver that Hardy is attempting to use.

Suggestions? I've attempted to install the bcm43xx-fwcutter, with no success, and then attempted the ndiswrapper routine with no success. I'm going to clean install Hardy to get to an easy starting place, and then see what brilliant solution is posted here.

---

### Post by imaworrier on 2008-04-25
If you can hook up directly with the same pc ( I used ethernet) then reinstall the driver( system/administration/hardware drivers) and Hardy should be able to download the updated driver. This worked for me insofar as the wlan came on.

---

### Post by lewelma on 2008-04-25
> **imaworrier said:**
> If you can hook up directly with the same pc ( I used ethernet) then reinstall the driver( system/administration/hardware drivers) and Hardy should be able to download the updated driver. This worked for me insofar as the wlan came on.

Hardware Drivers says: "No proprietary drivers are in use on this system."

---

### Post by SkipBlue on 2008-04-25
> **imaworrier said:**
> If you can hook up directly with the same pc ( I used ethernet) then reinstall the driver( system/administration/hardware drivers) and Hardy should be able to download the updated driver. This worked for me insofar as the wlan came on.

I tried that and downloaded the driver, however the 'enabled' checkbox is not checked! I have restarted **multiple** times and it still doesn't work... :(

---

### Post by lewelma on 2008-04-25
Here's some more info:

[iwconfig]

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

[lshw -C network]

  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5702X Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:0b:db:a3:ec:4e
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pcix pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5702-v2.25 ip=192.168.1.7 latency=64 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:28:6a:aa
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

[lspci -v | less]

...

02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
        Subsystem: Dell TrueMobile 1300 WLAN Mini-PCI Card
        Flags: bus master, fast devsel, latency 32, IRQ 5
        Memory at fafee000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

---

### Post by calibre97 on 2008-04-25
I hope you aren't completely adverse to this kind of advice, but what I did is give up. I got my built-in broadcom (HP laptop) working under 7.04 (upgraded to 7.10) but all the tricks I tried for that refused to work under 8.04. So I did some searching and found that the D-Link 652 (G) is supported. Not only supported but Plug and Play. It was $43 and worth it to have it just work after plugging it in. Sometimes upon booting I have to finagle selecting my wireless network, but eventually it comes on, connects and works. There was no NDISWRAPPER or drivers to mess with. I just plugged it in and it worked. So maybe that's an option?

---

### Post by imaworrier on 2008-04-25
mine says the same but the driver is enabled and the wlan is on. sorry I was unable to help.

---

### Post by lewelma on 2008-04-25
Here's some more info:

[iwconfig]

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

[lshw -C network]

  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5702X Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:0b:db:a3:ec:4e
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pcix pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5702-v2.25 ip=192.168.1.7 latency=64 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:28:6a:aa
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

[lspci -v | less]

...

02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
        Subsystem: Dell TrueMobile 1300 WLAN Mini-PCI Card
        Flags: bus master, fast devsel, latency 32, IRQ 5
        Memory at fafee000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

---

### Post by GroupB on 2008-04-25
I have a similar problem with the Broadcom card on my Dell Latitude D600 (sorry, I just made a post about it, but it could be combined with this thread).  It worked under 7.10, but not after my upgrade to 8.04 today.  It instructed me to download the restricted driver (which I did) but still no luck.  Everytime I try to check the "Enable" box, it tells me that a restart of the machine is required, which doesn't work despite multiple attempts.  Any thoughts?

---

### Post by imaworrier on 2008-04-25
> **SkipBlue said:**
> I tried that and downloaded the driver, however the 'enabled' checkbox is not checked! I have restarted **multiple** times and it still doesn't work... :(
sorry new to the posting...I was using 7.10 before and upgraded. I did reinstall the old driver I had on cd (for 7.10) and then tried the direct connect previously mentioned. If you have driver try that, if not and you know of a way I can post it here or send it to you I do have it on cd.

---

### Post by lewelma on 2008-04-25
> **GroupB said:**
> I have a similar problem with the Broadcom card on my Dell Latitude D600 (sorry, I just made a post about it, but it could be combined with this thread).  It worked under 7.10, but not after my upgrade to 8.04 today.  It instructed me to download the restricted driver (which I did) but still no luck.  Everytime I try to check the "Enable" box, it tells me that a restart of the machine is required, which doesn't work despite multiple attempts.  Any thoughts?

Yep -- I have the old Dell Latitude D600 as well...

---

### Post by SkipBlue on 2008-04-25
> **imaworrier said:**
> sorry new to the posting...I was using 7.10 before and upgraded. I did reinstall the old driver I had on cd (for 7.10) and then tried the direct connect previously mentioned. If you have driver try that, if not and you know of a way I can post it here or send it to you I do have it on cd.

I do not have that driver... I'm guessing it's the B43xx
you could try email it to me at [email]bristol.corinthian@gmail.com[/email]
thanks!

---

### Post by GroupB on 2008-04-25
Hey,
I just found this thread which told me to uninstall 2 packages related to the Broadcom card with Synaptic Manager and then use the command line to re-install the driver. The instructions are here (the second post in the thread has the method I used):

[http://ubuntuforums.org/showthread.php?t=709259](http://ubuntuforums.org/showthread.php?t=709259)

It worked on my Dell Latitude D600!  Thanks,

---

### Post by imaworrier on 2008-04-25
> **SkipBlue said:**
> I do not have that driver... I'm guessing it's the B43xx
you could try email it to me at [email]bristol.corinthian@gmail.com[/email]
thanks!
email sent, good luck.

---

### Post by Rocket2DMn on 2008-04-25
I have had the same problem in Hardy but have not been able to fix it (tried Group B's suggestion a couple of times, a little differently each time).
I filled out a bug report earlier, so please confirm it on Launchpad if applicable.  Thanks.
[https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/222197](https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/222197)

---

### Post by cpxondo on 2008-04-25
Hello! I have a Compaq Presario with bcm4311. I installed 7.10 and the wireless card was enabled but it didn't capture any network. Today I installed 8.04, but the card was not enabled, no driver, no wireless. Any help?

---

### Post by harpazo on 2008-04-25
I just got wireless to work in 5 minutes... 

Here's the details:

HP zv6000 laptop 
AMD Athlon64
Hardy 8.04 64-bit
Broadcom 4318 (bcwml5 drivers)

I copied my Broadcom drivers (from my Windows XP partition) into a folder in Hardy. 
Next I selected "System" on the top panel ---> then "Administration" --->
then "Hardware Drivers" and Hardy took over, with BWCutter (?) and installed the driver (a screen popped up, sorry I didn't get an image and I had to check the box on the screen) 
When the driver was extracted by Hard/BWCutter the "Hardware Drivers" screen came back up and I selected "Enable", said yes to the question about using restricted drivers.

Now I have Wireless for the first time without using Linuxant's Driverloader pay software!  


Hope this helps.  

P.S. Is it legal to share Broadcom Drivers with others?  I will if it's legal...

Harpazo

---

### Post by Rocket2DMn on 2008-04-25
> **harpazo said:**
> I just got wireless to work in 5 minutes... 

Here's the details:

HP zv6000 laptop 
AMD Athlon64
Hardy 8.04 64-bit
Broadcom 4318 (bcwml5 drivers)

I copied my Broadcom drivers (from my Windows XP partition) into a folder in Hardy. 
Next I selected "System" on the top panel ---> then "Administration" --->
then "Hardware Drivers" and Hardy took over, with BWCutter (?) and installed the driver (a screen popped up, sorry I didn't get an image and I had to check the box on the screen) 
When the driver was extracted by Hard/BWCutter the "Hardware Drivers" screen came back up and I selected "Enable", said yes to the question about using restricted drivers.

Now I have Wireless for the first time without using Linuxant's Driverloader pay software!  


Hope this helps.  

P.S. Is it legal to share Broadcom Drivers with others?  I will if it's legal...

Harpazo

What folder were the drivers in on your windows partition and what folder did you put them into in Hardy?  Are you using WinXP or Vista?
I have a dual boot with Vista, so I'm willing to give this a try.  Did you have to enable ndiswrapper for this?

---

### Post by SkipBlue on 2008-04-25
Well I just got my wireless to work!!!!!!!!:guitar:

all I did was (after trying many different things in different threads)

go into synaptic (system->administration->synaptic)
and search for 'Broadcom'
then I installed all three packages that came up (b43-fwcutter [which should already be installed, but I updated it to be sure], bcm43xx-fwcutter, and bcm5700-source)
after download and installation a setup for the bcm43xx-fwcutter came up, i went through it (don't remember exactly) and now my wireless connects, infact I am posting from it RIGHT NOW!!!!!!!!

---

