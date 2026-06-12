---
title: "Broadcom 4322AG in Hardy 64-bit driver solution?"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by B.C. on 2008-07-06
I recently purchased an HP dv9920us. Not wanting to be That Guy&#8482; spamming the forums with a thrice-answered question, I scoured both Google and these forums in hopes of finding a concise solution to my problem, but I have come up empty-handed for several days now.

And so, I turn to you, my friends. :)

Ndiswrapper obviously doesn't work with Vista drivers (bcmwl6), and I can't seem to find drivers for XP 64-bit (somebody please point me in the right direction if there are xp-64 drivers which are specifically for the 4322AG). HP's website lets you download some sort of executable for XP, but it's an installer, not a self-extracting zipfile like the other driver packs I've downloaded in my attempts to find a working driver.

**lspci -nn | grep Broad** shows the following:

[B]3:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
[/B]

I'm not looking for draft-N support (I'm not really a fan of hardware manufacturers putting it in their devices the first place since the standard hasn't even been officially approved yet), but I am looking to be able to connect with 802.11g using WPA if possible, WEP as a secondary option, and unencrypted wireless as a last resort.

If you are able to help me, hopefully this thread and the emo tears shed over my wireless troubles will be useful in helping others avoid the same headaches if they decide to buy a laptop with this chipset. :)

Edit: I forgot to add that if you have gotten this chipset to work with Ubuntu 32-bit, your input is valuable as well, as I've heard that the 32-bit XP drivers work fine with ndiswrapper. I just really really want to get it to work with 64-bit since my laptop has 4GB of RAM and I'd like to be able to use all of it. :)

---

### Post by B.C. on 2008-07-07
I managed to find XP 32-bit drivers (sp39243) which at least get the wireless LED to go blue.

Now I'm just having an issue connecting. I have the right driver, and I can see the wireless network, but with wicd, I can't seem to connect with WPA, WEP, or even unsecured. It gets stuck at obtaining an IP address (which a quick googling suggests is a common problem). Anyone manage to get this working with any particular wireless manager? WPA/WEP/Unsecured?

---

### Post by B.C. on 2008-07-07
Update: I'm not able to connect to even unsecured wireless with the method listed on the forums. It hangs the entire system and I can't stop the process, even with ^C. My router is a Netgear WGR614 v6 running the latest firmware.

Could it be a problem with ndiswrapper? Is it the fact that I'm running 64-bit Hardy instead of 32-bit Hardy? Does this particular chipset just not like to play nice?

---

### Post by B.C. on 2008-07-07
I installed 32-bit Hardy on my laptop just a few minutes ago, used the wired ethernet to manually compile and install the latest version of ndiswrapper (as of this writing 1.52) and use the same 32-bit XP driver previously mentioned. Network Manager is able to connect to my WPA network without incident.

I will try with Hardy 64-bit perhaps some other time and update this thread if there is any change. I suppose having only 3GB of usable RAM will have to suffice for the time being. :)

Relevant (maybe?) info:
"lshw -C network" shows

 *-network
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: **:**:**:**:**:**
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,03/21/2008, 4.170. ip=192.168.1.2 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

"ndiswrapper -l" shows

bcmwl5 : driver installed
	device (14E4:432B) present

---

### Post by crimesaucer on 2008-07-18
I have the exact same computer, with the exact same problem... except I don't even have the 32 bit xp driver.


If you find the Xp 64bit "bcmwl564.sys" and inf file, please contact me so I can get that driver from you... I'll even take the "bcmwl5.sys" from the 32 bit Xp if you could get me a copy of that one that worked for you... or a link to a downloadable self extracting file of the same driver.


Thanks,
-c.

---

### Post by ungermax on 2008-07-21
You can get the XP driver from the HP website, 
[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=15351&prodSeriesId=447687&swItem=ob-61972-1&mode=4&idx=3](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=15351&prodSeriesId=447687&swItem=ob-61972-1&mode=4&idx=3)

I got this driver to properly recognize my Wifi Card usinf ndiswrapper 1.93, I have a Broadcom 4322 chip.
iwconfig tells me the interface is up,
but I can't scan for APs and assigning one manaully doesn't work either.
 I believe this is because I am running with ACPI=off right now, until HP updates the BIOS.

Hope this helps

---

### Post by athianos on 2008-07-26
SOLVED!

I installed this little package in synaptic and I can use WEP without a problem.

Network manager even shows me an accurate signal bar!

hostapd

I found the solution here.

Thanks gstamp!

[http://ubuntuforums.org/showthread.php?t=75017](http://ubuntuforums.org/showthread.php?t=75017)

---

### Post by crimesaucer on 2008-07-31
> **ungermax said:**
> You can get the XP driver from the HP website, 
[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=15351&prodSeriesId=447687&swItem=ob-61972-1&mode=4&idx=3](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=15351&prodSeriesId=447687&swItem=ob-61972-1&mode=4&idx=3)

I got this driver to properly recognize my Wifi Card usinf ndiswrapper 1.93, I have a Broadcom 4322 chip.
iwconfig tells me the interface is up,
but I can't scan for APs and assigning one manaully doesn't work either.
 I believe this is because I am running with ACPI=off right now, until HP updates the BIOS.

Hope this helps

Thanks, I might give this a try latter, it looks like the correct 32bit driver. I was hoping for a 64bit driver (from the Xp 64bit professional OS), but this looks like a good solution if I hadn't already bought a brand new usb-wifi card that works perfectly out of the box and is aircrack-ng compatible.


With money already spent, and my wifi working perfectly with the supported rtl8187 driver, I probably won't mess around with ndiswrapper and will wait until the b43 project gets around to the pre-n bcm43xv drivers for Vista64.


I do like the fact that the driver you linked me too has pre-n support. I want to try the 802.11n if I find a wireless router using mimo to compare the difference, and now I know a way if become impatient.


Thanks again for the info, it might of saved me $60 dollars if I had seen your reply post before ordering my usb wifi device: [http://www.tuto-fr.com/en/tutorial/materiel/awus036h-alfa-network.php](http://www.tuto-fr.com/en/tutorial/materiel/awus036h-alfa-network.php)


... however, I did my homework and got myself a very nice usb-wifi card (and huge 9dBi antenna kit) that won't become obsolete once my bcm43xv 64bit pre-n becomes supported properly.

---

### Post by datrucka on 2008-08-15
Never got the ndiswrapper to work properly on 64 bit ubuntu but found that broadcom has released a linux driver which I got going in a few minutes.

Mine was the  Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by pvgorp on 2008-09-04
Dear datrucka,
I am a bit surprized by your succes...

Personally, I have also been able to compile the wl.ko, and get it modprobed after switching back from kernel .19 to .18 (for linux-restricted-modules-2.6.24-18-generic).  However, the wireless network interface does not show up...

I am on a HP Pavilion TX2550ED => lspci for the wireless card: 
```
08:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
```

The native driver is loaded:
```
 lsmod | grep wl
wl                   1062272  0 
ieee80211_crypt         7040  2 wl,ieee80211_crypt_tkip
```

However:
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.
```

Don't mind the two ethernet interfaces (non-standard for my tablet-pc, but I am using a USB Ethernet dongle since also the built-in Realtek Ethernet interface is not working yet, other story...)

On previous attempts, I was insmodding the wl.ko on restricted-modules-2.6.24-19-generic and I was already trying to use wpa_supplicant etc. but since over there I didn't get any access points I decided to really modprobe the thing (after which I discovered errors in dmesg (as discussed in [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/243930](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/243930) and two other threads...)

I was getting nervous but since you seem to have closed the circle I am very eager to know what should be the final steps to get the network interfaces right.  Once I have those, I will try out wpa_supplicant and hostapd etc. (I'll have to learn more about those in another thread I guess...)

Thanks a lot in advance,
in despair,
Pieter VG

---

### Post by datrucka on 2008-09-04
Hi,
The only other thing I did was put "blacklist bcm43xx" in /etc/modprobe.d/blacklist

I load the module from /etc/rc.local at boot the way suggested by the broadcom help(modprobe ieee80211_crypt_tkip ; insmod <path_to_module/wl.ko>). 

To get it working after sleep had to make a script(templates found at /usr/lib64/pm-utils/sleep.d) in /etc/pm/sleep.d to unload the module before sleeping(modprobe -r wl) and reload the module after sleeping(insmod <path_to_module/wl.ko>).

Hope that helps.

---

### Post by pvgorp on 2008-09-05
Thanks for your reply,
unfortunately in my case even no other Broadcom modules are active (as indicated by 'lsmod | grep bcm'...

Just to double-check: usually, a device should become visible right after the module is loaded succesfully, not?  Or should I execute other commands?

---

### Post by Ayuthia on 2008-09-05
> **pvgorp said:**
> Thanks for your reply,
unfortunately in my case even no other Broadcom modules are active (as indicated by 'lsmod | grep bcm'...

Just to double-check: usually, a device should become visible right after the module is loaded succesfully, not?  Or should I execute other commands?
This is going to be a long message so I apologize in advance.

You can try the following to see if it works:
```
sudo modprobe -r b43 ssb ndiswrapper bcm43xx ieee80211_crypt_tkip
sudo rmmod wl
sudo modprobe ieee80211_crypt_tkip
sudo insmod <location of wl.ko>
```
If it does, then you have a configuration issue in either /etc/modules or /etc/modprobe.d/blacklist.  If it does not, check dmesg and see if there are any error messages.

The modules that need to be blacklisted are the following:
b43 bcm43xx ndiswrapper ssb

The only trick is if you have to use the b44 module for your wired connection.  You can check this by doing lshw -C network.  The ssb module is used by b43 and b44 and it causes conflicts with ndiswrapper and wl modules.  So if you do have the b44 module, you will have to load b44 and ssb after wl is loaded.

If you don't want to have to use insmod all the time, you can move your wl.ko file over to /lib/modules:
```
sudo mkdir /lib/modules/`uname -r`/hybrid
sudo cp <location of wl.ko> /lib/modules/`uname -r`/hybrid
sudo depmod -a
```
Once that is done, you should be able to just do a "sudo modprobe wl" and it will load ieee80211_crypt_tkip and wl for you.  Of course, since we are compiling this module, we will have to do this (the compiling of the wl module along with copying the file over to /lib/modules) every time there is a kernel update.

Just to summarize what is being done in my code section, the first step is creating a directory out there for the wl.ko module so that it we know where it is located.  The uname -r is the kernel version that you are currently using.  The quotes are a back-quote not a single quote.  It will execute the command when you use the back-quote and substitute the result with the command.  /lib/modules is looked up based on kernel versions.  If I understand correctly, to use modprobe the module needs to be in /lib/modules.  

The second command copies the wl.ko module over to the /lib/modules directory.  I prefer to copy instead of move so that I don't lose the file by accident.

The last command rebuilds the modprobe library (I can't think of the proper terminology for this).  It will build the dependencies for the module and allow you to use modprobe for that module.

Hopefully this helps and not confuse.

---

### Post by pvgorp on 2008-09-05
> This is going to be a long message so I apologize in advance
No problem, your answer is very informative.  I see a lot of similarities with what I was already doing (/lib/modules for wl.ko etc) but I did not "rebuild" the modules tree and did not explicitly force the removal of the modules you mention (since I presumed/concluded they were not active).  I will reboot from my vista to Ubuntu right away and try out your suggestions literally.

Thanks again and sincere regards,
Pieter

---

### Post by pvgorp on 2008-09-05
Hi again,
here is an update:
 - I do get an extra network interface (eth2) when I use insmod explicitly :popcorn:... 
 - Unfortunately, similar to when I was still using kernel version .19, I still don't get any access points :mad: 
 - With version .19 I could also insmod wl.ko (no errors reported) but modprobe failed ([https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/243930](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/243930): missing symbols etc.)
 - Therefore, I am a bit suspicious about the "successful" insmod... in fact, on my current kernel (.18 ), I still got a 'tainting kernel' message... something to be ignored or not?
 - Anyhow, since the 'missing symbols' errors from kernel version .19 are not present with my older kernel version, I am tempted to stop digging further in the modprobe story, and i now just want to get the thing online for once... 

Are you using wpa_supplicant as well?  In that case, what driver are you listing?  It says wext in my case but perhaps that should be wl???

Here is my /etc/network/interfaces:
```
auto lo
iface lo inet loopback

iface eth1 inet dhcp

iface eth0 inet dhcp

iface eth2 inet dhcp
wpa-psk 8b85015e8b.... etc.... 0927e1fd1d299d
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid Wireless169Power
auto eth2

#pre-up wpa_supplicant -Bw -Dwext -ieth2 -c/etc/wpa_supplicant.conf
#post-down killall -q wpa_supplicant
#wireless-channel 7
```

As you see, I have commented out some lines in an desparate attempt but I don't find what change could make it work.  Also note that I cannot scan for access points:
```
iwlist scan
```
gives
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth2      Failed to read scan data : Invalid argument
```

Moreover,
```
root@pvgorp-tx2550ed-ubuntu:/home/pvgorp# iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

eth2      IEEE 802.11abgn  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:44 Mb/s   Tx-Power:off   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by d3vnu11 on 2010-01-21
> **B.C. said:**
> I recently purchased an HP dv9920us. Not wanting to be That Guy™ spamming the forums with a thrice-answered question, I scoured both Google and these forums in hopes of finding a concise solution to my problem, but I have come up empty-handed for several days now.

And so, I turn to you, my friends. :)

Ndiswrapper obviously doesn't work with Vista drivers (bcmwl6), and I can't seem to find drivers for XP 64-bit (somebody please point me in the right direction if there are xp-64 drivers which are specifically for the 4322AG). HP's website lets you download some sort of executable for XP, but it's an installer, not a self-extracting zipfile like the other driver packs I've downloaded in my attempts to find a working driver.

**lspci -nn | grep Broad** shows the following:

[B]3:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
[/B]

I'm not looking for draft-N support (I'm not really a fan of hardware manufacturers putting it in their devices the first place since the standard hasn't even been officially approved yet), but I am looking to be able to connect with 802.11g using WPA if possible, WEP as a secondary option, and unencrypted wireless as a last resort.

If you are able to help me, hopefully this thread and the emo tears shed over my wireless troubles will be useful in helping others avoid the same headaches if they decide to buy a laptop with this chipset. :)

Edit: I forgot to add that if you have gotten this chipset to work with Ubuntu 32-bit, your input is valuable as well, as I've heard that the 32-bit XP drivers work fine with ndiswrapper. I just really really want to get it to work with 64-bit since my laptop has 4GB of RAM and I'd like to be able to use all of it. :)

I guess HP had slight changes in hardware. I also have a dv9920US laptop but lspci I get a Broadcom BCM4328 (Rev. 3) But nothing works. I grep dmesg to see if it requests a firmware nothing. I've been at this for 3 days now. Tried the broadcom's hybrid src still nothing lsmod wl 0 use. Even tried a number of drivers with the ndiswrapper. I'm so frustrated :) Everything else works great and I always have the Alfa usb wifi but it would be nice to get the internal wifi working for connecting to my own wifi. Anyone have any ideas willing to try anything at this point. Been running some form of Linux for about 13 years. So not exactly new to it :)

---

### Post by bkratz on 2010-01-21
> **d3vnu11 said:**
> I guess HP had slight changes in hardware. I also have a dv9920US laptop but lspci I get a Broadcom BCM4328 (Rev. 3) But nothing works. I grep dmesg to see if it requests a firmware nothing. I've been at this for 3 days now. Tried the broadcom's hybrid src still nothing lsmod wl 0 use. Even tried a number of drivers with the ndiswrapper. I'm so frustrated :) Everything else works great and I always have the Alfa usb wifi but it would be nice to get the internal wifi working for connecting to my own wifi. Anyone have any ideas willing to try anything at this point. Been running some form of Linux for about 13 years. So not exactly new to it :)

Here is at least one successful attempt, maybe it will be of some use.
[http://ubuntuforums.org/showthread.php?t=1370058&highlight=BCM4328](http://ubuntuforums.org/showthread.php?t=1370058&highlight=BCM4328)

---

