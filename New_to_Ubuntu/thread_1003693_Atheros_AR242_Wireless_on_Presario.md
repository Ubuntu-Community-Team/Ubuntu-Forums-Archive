---
title: "Atheros AR242 Wireless on Presario"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by rechelon on 2008-12-06
Okay, it's been six hours of teh Google, blog and forum trawls ("just follow these utterly simple steps" --wait, how the **** do you do that with the terminal?!).  If ever I had any pretension of not being a complete failure in life, those days have passed.

Brand new Presario CQ50 violently purged of Vista and painstakingly installed Ubuntu 8.10 from miniboot (imagine my absolute horror at being told the system was fully installed here's your terminal interface, what you want a desktop GUI too???? ).

Anyway, as per the norm with Ubuntu everything works except for the Wireless Card, which I am cheerfully told has its drivers fully enabled, yay!  Except of course the drivers are probably open source ones for the 5000 series.  And no wifi.  Not that I'd really know how to access my network without a magical dancing paperclip.

I know ****.  And apparently I can't install things without either random luck or a magical .deb .  Is there anyone on Earth with a kind enough heart to walk me through in even simpler manners than the plethora of existing walkthroughs I've already shamed and debased myself reading to no avail?

God, wouldn't it be nice if there was a deb for Madwifi so I could use a GUI the whole way through.  Of course it looks like Madwifi doesn't support AR242, so maybe my abject idiocy when it comes to installing was meaningless anyway.

---

### Post by nhasian on 2008-12-06
my post here will help you setup your wireless adaptor:

[http://ubuntuforums.org/showpost.php?p=6059353&postcount=15](http://ubuntuforums.org/showpost.php?p=6059353&postcount=15)

---

### Post by rechelon on 2008-12-06
> **nhasian said:**
> my post here will help you setup your wireless adaptor:

[http://ubuntuforums.org/showpost.php?p=6059353&postcount=15](http://ubuntuforums.org/showpost.php?p=6059353&postcount=15)

didn't solve anything.  

sudo vi /etc/modprobe.d/blacklist 

doesn't pull up anything that i can edit, it just displays the file contents in the terminal.  and of course i can't edit the file in a textpad esque app because it won't grant privileges and there's no password access to sudo power.

---

### Post by rechelon on 2008-12-06
also, i hardly see why blacklisting those drivers will make others previously unfound suddenly appear.

---

### Post by rechelon on 2008-12-06
bump

---

### Post by Crafty Kisses on 2008-12-06
What are the results of this command?
```
lshw -C network
```

---

### Post by rechelon on 2008-12-06
```
~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:72:79:dd:78
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.0.2 latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 0a:81:d3:cf:e0:a8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

---

### Post by rechelon on 2008-12-06
I mean good lord, how would I even know if I managed to get the card working? 

I've used Ubuntu for four years on three common model laptops and NEVER been able to connect to wifi networks on ANY of them.  All in all I've probably wasted weeks of my life pouring through google before inevitably giving up in abject despair and incomprehension for another couple weeks, rinse repeat.  Ubuntu: Because an end user should have to memorize arcane command line procedures if they want to do something as weird as play MP3s or use a laptop as an actual ******* laptop.

I literally got a bachelors in physics in the time its taken me to get absolutely nowhere on this learning curve.

---

### Post by 2hot6ft2 on 2008-12-06
What kernel are you using? The reason I ask is that I keep getting disconnected with one on my laptop yet the older one will connect and stay connected.
Applications>System Tools>sysinfo then system in the top left will tell you.

And I didn't need to edit the madwifi list and blacklist anything.

---

### Post by nhasian on 2008-12-07
when you start vi it is in command mode.  to begin editing the document you need to press INSERT on your keyboard.  if your not familiar with vi you can use gedit instead

```
sudo gedit /etc/modprobe.d/blacklist
```

so in the end, after you've installed the intrepid backports and blacklisted those two items, did your wifi start working as it should?


> **rechelon said:**
> didn't solve anything.  

sudo vi /etc/modprobe.d/blacklist 

doesn't pull up anything that i can edit, it just displays the file contents in the terminal.  and of course i can't edit the file in a textpad esque app because it won't grant privileges and there's no password access to sudo power.

---

### Post by nothingspecial on 2008-12-07
Copy and paste these commands -

Download the latest madwifi snapshot.

```
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3875-20081105.tar.gz	

```
Unzip it

```
tar -xvf madwifi-hal-0.10.5.6-r3875-20081105.tar.gz 	
```


navigate to the extracted file


```
cd madwifi-hal-0.10.5.6-r3875-20081105
```

If you`ve not got the tools necessary for compiling get them

```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

Then compile it


```
sudo make
```

```
sudo make install
```

load the module


```
sudo modprobe ath_pci
```

make it load every time you boot


```
gksudo gedit /etc/modules
```

then copy and paste this to the bottom of that file


```
ath_pci
```

save
exit 
reboot

---

### Post by MattyGabe on 2009-02-17
I have the ABSOLUTELY same problem on a Toshiba Satellite L305 with the AR242 wireless adapter.

I'm sorry, but this is absolutely rediculous, Ubuntu is touted as being the "user friendly" Linux, and to its credit it is much friendlier to those who are unfamiliar with it, but this random "Here, type this code in!" makes far too many assumptions (such as the knowledge of vi - luckily I was able to switch over to gedit without being prompted to, but you get the idea).  I am in the exact same boat as the original thread starter.  This is rediculous.  I've tried so many different commands in terminal, and no matter what I do my Atheros Wifi controller remains UNCLAIMED and has no LOGICAL NAME, thus the correct device drivers are not in use for it.  I have people saying "install madwifi!!!" then I have people saying "Madwifi doesn't work, uninstall it by doing THIS (then I get lost), then install ndiswrapper!!"  and then I do ndiswrapper, and it "installs" a windows driver, yet it doesn't "really" install it (because obviously the device isn't communicating with me as I expect it to).  So then I have someone else saying I should blacklist ath_pci and ath_hal, and then it will magically work.  I've disabled the proprietary/restricted drivers that Ubuntu so graciously installed for me (thanks a lot Penguin, because that sure seems to help me go Wifi... NOT!)

All I want to do is have some access to Google so when I compile some REALLY simple C code and gcc spits out some errors at me, I can know what the hell I'm doing if the man pages don't answer my questions.

:(

---

### Post by MattyGabe on 2009-02-17
Here.  Here's my output of IWCONFIG:
```
matthew@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

And here's what I get when I type sudo lshw -C network:
```

matthew@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: XX.XX.XX.XX.XX.XX (removed from post)
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.41 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: XX.XX.XX.XX.XX (removed from post)
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


```

I just don't understand why I keep seeing the exact same commands that do not do what is necessary: install a driver and then have it connect to the hardware.  There is a missing layer between me (the user) and the hardware.  The OS is doing what I tell it but it obviously doesn't know what it needs to do (I don't know how to tell it what to do).  High-level, I know, but I have yet to see barely anything with modprobe to "link" the driver to the device in the kernel.

---

### Post by lkraemer on 2009-02-18
recehlon,
I also have a Compaq Presario CQ50-139NR, and I installed the Ubuntu
8.04 Alternate LiveCD.  I also posted how I did it at the following:
[http://ubuntuforums.org/showthread.php?t=988691](http://ubuntuforums.org/showthread.php?t=988691)

If you're interested I have a post on the XP drivers for the CQ50
series at: [http://ubuntuforums.org/showthread.php?t=996311](http://ubuntuforums.org/showthread.php?t=996311)
in case you're interested in Dual Booting.

First, I'd recommend that you try booting LiveCD's of what you want
to install to verify that at least the LiveCD runs fine.  If not, try 
installing the Alternate Install ISO.  (And remember to VERIFY the
MD5SUM of the ISO, Burn as DAO (Disk at Once) and at 4x or 8x.)


lkraemer

---

### Post by MattyGabe on 2009-02-18
UPDATE: I've solved it (I don't know if it's permanent or not) but somehow I was able to get the "Atheros Wireless Driver for 5xxx Series Cards" to show up in the Restricted Drivers section of Gnome.

In lshw -C network, the Wireless adapter is shown to have the logical name wmaster0, but it doesn't work with that alias when I attempt to use it in WICD (a gui-based network config tool I installed along the way).

However, in iwconfig I got information regarding a new Wireless adapter I hadn't previously seen: wlan0 (remember, wasn't listed in lshw above).  I used that alias in WICD and thus my card was able to view available WIFI networks.  I could also obtain an IP over unsecured networks, but network auth (using WEP or WPA) didn't quite work yet.  

In WICD I have about 8 options regarding supplicant drivers that will deal with wifi authentication.  Madwifi, ndiswrapper and a few others did NOT work with the WPA2 network I attempted to connect to.  WEXT, however, did.  I don't know why, all I care is that I am typing this information to you using the aforementioned setup.

I hope someone else can make sense of this and maybe put it in a more coherent sense.  If I could also ask: could someone put a A-Z guide for Satellite users together on how to do this (Install ath5k drivers, disable other drivers, then use the proper auth methods)?  I got to where I wanted to go, but it was almost by luck. Any help in this matter will (no doubt) help countless other Toshiba Satellite users (perhaps even others who use the Atheros 5k chipsets...)

---

