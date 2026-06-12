---
title: "WPC11 V4 Wireless Network not being detected.  Absolute Newbie"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by Dangit on 2007-06-28
Please help.  You probably get this question all the time, however, I do believe that I read that my wireless card would work straightaway but the wireless network is not even detected.  I know that it is working because I have a windows pc in the other room that is happily computing away.  Please, whatever help you can offer.

I did have to install with an alternate cd.  The other kept freezing on me.

---

### Post by Antonio44 on 2007-06-28
I don't know if I can help you but everyone who can is going to need to know the model of your card and some computer specs so post them please. 



A.

---

### Post by Antonio44 on 2007-06-28
Yes and there the card name would be in the title of the post. (Yes I know that was a good move on my part) lol. You may have to try something called ndiswrapper. What you need to do is go to google and type in the model of your card and ndiswrapper. Hopefully someone has written instructions that will guide you through this. I had the same problem with my cards. Don't worry eventually you will work through it, it just takes time and effort.



A.

---

### Post by kevdog on 2007-06-28
Follow along in this thread:

[http://ubuntuforums.org/showthread.php?t=486564](http://ubuntuforums.org/showthread.php?t=486564)

We are going through the same steps to hopefully make this card work!

---

### Post by Dangit on 2007-06-30
I finally got the flipping driver installed with ndiswrapper.  Really, I think my distribution is flawed or something.  My wireless interface doesn't look like some of the other screen shots that I've seen.  Anyway, take a look at this.  I should be seeing some bars, I think.  No matter what I do, I can't get the darn thing to connect still!  It is connected to a windows box in the other room.

I will also go to the referenced thread.

---

### Post by kevdog on 2007-06-30
Please post
lshw -C network

This hopefully will tell us what driver your card is using.  I have a feeling although you configured for ndiswrapper, that card is using a different driver.

---

### Post by Dangit on 2007-06-30
Thanks for all your help, by the way.

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 83
       serial: 00:e0:b8:55:cf:0e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI firmware=N/A ip=192.168.1.101 latency=66 maxlatency=56 mingnt=8 multicast=yes
       resources: iomemory:e0200000-e0200fff ioport:3000-303f irq:11
  *-network
       description: Wireless interface
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@03:00.0
       logical name: wlan0
       version: 20
       serial: 00:0f:66:3b:be:b4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 mingnt=32 multicast=yes wireless=802.11b
       resources: ioport:3400-34ff iomemory:28000000-280001ff irq:11

---

### Post by killdragon on 2007-06-30
Hi, the easy way is to go here and try this. It is what I did and it works.


     [http://ubuntuforums.org/showthread.php?t=481422&highlight=killdragon#post2940228](http://ubuntuforums.org/showthread.php?t=481422&highlight=killdragon#post2940228)

---

### Post by kevdog on 2007-06-30
Getting beginners to look at things I ask them to post is a stuggle.

Look at the output of your wireless card....It tells you the driver it is trying to use:

configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 mingnt=32 multicast=yes wireless=802.11b

rt8180.

Notice ndiswrapper is not listed since the card is assigned to another driver.  Not this is a bad thing, but you could screw around with ndiswrapper for 10 years and nothing would happen.

Two options at this time are to attempt to use rtl8180 driver, or remove 8180 and then reassign the card to the ndiswrapper driver.

Lets try rtl8180 first.  
Please post output of
iwlist scan
Copy and paste the files:
/etc/network/interfaces
/etc/iftab

How are you trying to connect to your network?? Network Manager applet or something else?

---

### Post by kevdog on 2007-06-30
Could you also post the following file:

/etc/modprobe.d/blacklist

I think there is something here we need to change also!

---

### Post by Dangit on 2007-07-01
Thanks again, Kevdog.
[B]
iwlist scan[/B]
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:BF:AE:9E:13
                    ESSID:"ratz"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:206  Signal level:0  Noise level:28
                    Extra: Last beacon: 1101ms ago
          Cell 02 - Address: 00:0F:B3:2F:10:CE
                    ESSID:"WRCWLan"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54 
                    Quality:207  Signal level:0  Noise level:91
                    Extra: Last beacon: 1719ms ago
          Cell 03 - Address: 00:0F:B3:B0:F3:6F
                    ESSID:"gp&KP"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:9
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54 
                    Quality:209  Signal level:0  Noise level:94
                    Extra: Last beacon: 1104ms ago
          Cell 04 - Address: 00:0F:B3:A3:4B:C2
                    ESSID:"ACTIONTEC"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:9
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54 
                    Quality:221  Signal level:0  Noise level:97
                    Extra: Last beacon: 1121ms ago

**etc/network/interfaces**
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

**etc/iftab**
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:e0:b8:55:cf:0e arp 1

---

### Post by Dangit on 2007-07-01
I try to configure through System/Administration/Network then see through the computer icons at the top right.  I tried to get the packages of Wi-Fi radar and Wireless Assistant to help me through this and while I think it may get me one step further in the process I still am not connecting.

---

### Post by Dangit on 2007-07-01
:D  I did comment out the last two lines.
[B]
blacklist file:[/B]

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
# blacklist r818x
# blacklist r8187

---

### Post by kevdog on 2007-07-01
Edit the /etc/network/interfaces file:

gksu gedit /etc/network/interfaces

Add the following:
auto wlan0
iface wlan0 inet dhcp

Save the file and exit

Now reboot.
What I want you to do is when you manually connect to your network using network manager icon, is to specify the name of your router, but when you type the name, add a 'x' (no quotes) onto the end of the name.  So if your essid of your router is ratz, type ratzx

I see from your network scan there are 4 routers in your area.  Which one is yours???

---

### Post by Dangit on 2007-07-01
Good choice.  I am ratz.

---

### Post by Dangit on 2007-07-01
Restarted.  Wireless still not working.  I don't believe I have anything called "network manager"  I have System/Administration/Network... just sayin...  Below is a screenshot of the wireless networks that I can try to connect to.

**iftab now looks like:**

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
auto wlan0
iface wlan0 inet dhcp

---

### Post by kevdog on 2007-07-01
OK lets try a few things -- things from this point on are trial and error unfortunately.

Delete the wlan0 settings from the interfaces file (or simply put a # sign in front of the lines to comment them out!)

You are using the network manager applet to configure your devices!!
Delete both the ratz and ratzx interfaces.

Type
sudo /etc/init.d/networking restart 

Turn off any WEP or WPA or Mac filtering on the router (for now)
Repost the iwlist scan, but only the part that deals with the ratz router (i dont care about the other ones)

Manually reconfigure with ratzx again.

Reboot if something doesnt work at first

Post back

---

### Post by kevdog on 2007-07-01
One last thing, can you repost the 

lshw -C network 

again.  I want to double check something!

---

### Post by Dangit on 2007-07-01
**lshw -C network **
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 83
       serial: 00:e0:b8:55:cf:0e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI firmware=N/A ip=192.168.1.101 latency=66 maxlatency=56 mingnt=8 multicast=yes
       resources: iomemory:e0200000-e0200fff ioport:3000-303f irq:11
  *-network
       description: Wireless interface
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@03:00.0
       logical name: wlan0
       version: 20
       serial: 00:0f:66:3b:be:b4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 mingnt=32 multicast=yes wireless=802.11b
       resources: ioport:3400-34ff iomemory:28000000-280001ff irq:11

---

### Post by kevdog on 2007-07-01
Sorry try the things I posted 3 posts back!

---

### Post by Dangit on 2007-07-01
Kevdog,

Where would I delete ratz and ratzx from?  I manually configured ratzx but it is not showing up.  When I go into network and look at the networks (see the snapshot) there is no list of configured networks.  This may be part of the problem.

---

### Post by kevdog on 2007-07-01
Try the following 

System->Adminstration->Network

Highlight wireless connection and hit Properties

Uncheck "Enable Roaming Mode"
Can you type in ratzx for the essid and then click OK

What happens??

---

### Post by jackherer on 2007-08-28
I have ThinkPad 600E with Linksys WPC11 ver.4 and Xubuntu7.04. Tried to use Xubuntus oen driver butt did not work for me. 

Now I installed Ndiswrapper as told before. "ndiswrapper -v"  gives: 

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 586

when I try to install xp driver which o got from Linksys or Realtek webside error message for      " sudo ndiswrapper -i NET8180.inf"  is

installing net8180 ...
couldn't open NET8180.inf: No such file or directory at /usr/sbin/ndiswrapper line 217. 

"ndiswrapper -l" gives :

lsrtnds : invalid driver!
net8180 : invalid driver!
 
so what shoul *I do next cause nothing seems to work out

---

