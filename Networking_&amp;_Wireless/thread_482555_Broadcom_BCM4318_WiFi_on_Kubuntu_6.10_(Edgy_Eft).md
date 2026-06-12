---
title: "Broadcom BCM4318 WiFi on Kubuntu 6.10 (Edgy Eft)"
date: 2007-06-23
forum: Networking &amp; Wireless
---

### Post by biscuits on 2007-06-23
I have been trying to get this wireless card working for some time, but have been unsuccessful so far. All the advice I found involves using a tool that downloads packages - as I don't have another card I can't download from within Ubuntu (I can download files in windows and access them from within Linux though).

I have installed the drivers using ndiswrapper-1.8, and "ndiswrapper1.8 -l" reports everything is fine.

I can't activate the device in the network manager though, and calling "sudo ifup eth0" starts an infinite "network is down" loop.

I'm a complete newbie at this so be gentle. I'm happy to provide any extra information if needed.

Once I get this thing detecting the networks, I need to figure out how to get it using WPK and the interface only seems to support WEP.

Thanks in advance.

---

### Post by scrooge_74 on 2007-06-23
Check this thread [http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174)

---

### Post by Darkhack on 2007-06-23
NetworkManager is still in development and pretty buggy at this point, so I wouldn't use it as my primary configuration tool.  It gave me a kernel panic whenever I tried to enable my wireless with it.  I have a follow up questions for you.  Are you trying to connect via a static IP or dynamic with DHCP?  Also could you please show the output of the following three commands...

sudo less /etc/network/interfaces
ifconfig
iwconfig

---

### Post by biscuits on 2007-06-23
scrooge_74, that thread is of no help because 1) I am using KDE, not Gnome, and 2) I do not have a working network card within Linux, which that thread requires.

Darkhack, here is the output from those commands:

```
oem@Boxy:~$ sudo more /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface eth0 inet dhcp



oem@Boxy:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

oem@Boxy:~$ iwconfig
lo        no wireless extensions.

eth0   IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I am trying to use DHCP. I'm not sure if the program I was using is called NetworkManager. It's just the default GUI provided with KDE.

It looks like when I did [FONT="Courier"]sudo ndiswrapper-1.8 -m[/FONT] earlier it registered the card as eth0, but I'm at a loss as to why it doesn't function.

---

### Post by kevdog on 2007-06-23
Follow along in this thread that I currently helping someone with right now -- Begin about page 3: [http://ubuntuforums.org/showthread.php?t=473379](http://ubuntuforums.org/showthread.php?t=473379).  Erky is using a different card than you, but some of the problems he(she) is having may be applicable to you!

---

### Post by Drate on 2007-06-24
This is my fix for Ubuntu Edgy... the part you'll have to fix for Kubuntu is going to be the Gnome Network Manager bit.  Alternatively you could just use WPA Supplicant manually from command line... there are many a folk that could give you the generics and specfics on how to do that... but this is what I did wtih my Linksys WMP54GS (broadcom chipset) wireless NIC in Edgy...

[http://ubuntuforums.org/showthread.php?t=381770](http://ubuntuforums.org/showthread.php?t=381770)

---

### Post by biscuits on 2007-06-24
Thanks for the help so far all.

I *thought* I had managed to get it working without the use of ndiswrapper as apparently ubuntu comes able to recognice bcm43xx cards but not to use them without adding the firmware, or something like that. Anyway I was able to download the bcm43xx-cutter tool and add the relevant files (scrooge_74, your post was more useful than I intially thought once I found out how to install packages offline ;)), only to find there are still support issues with the 4318. So it's back to ndiswrapper again, and Drate your fix looked promising, however I'm now back to square 1.

These are my problems:
If I manually edit /etc/network/interfaces to include wlan0, the system hangs on startup.

KNetworkManager detects no network interfaces, even though ndiswrapper reports the driver is up and running.

KNetworkManagers *does* work with WEP if I use the native driver instead of nsidwrapper, but I need it to work with WPA.

Here is my current state if any of this is useful, I'm guessing my /etc/network/interfaces is not correct:

```
oem@Boxy:~$ ndiswrapper-1.8 -l
Installed drivers:
bcmwl5          driver installed, hardware present
oem@Boxy:~$ more /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

#iface eth0 inet dhcp


oem@Boxy:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

oem@Boxy:~$ more /etc/modprobe.d/blacklist
[snip]
# wireless card model 4318 not supported properly yet
blacklist bcm43xx

oem@Boxy:~$ ndiswrapper-1.8 -m
modprobe config already contains alias directive

```

---

### Post by Drate on 2007-06-24
This is what my /etc/network/interfaces file looks like:

--------------

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

-------------

As far as KNetwork Manager... Like I said, you may have to resort to a manual configuration and startup of wpa_supplicant.  Gnome Network Manager handles that on it's own.  I truly DON"T know that much about KDE.  There are other ppl with the appropriate howto for WPA config, but HOPEFULLY with a properly set interfaces file KNetwork Manager will work for you.  If it does all you'll have to do is click on the KNetwork Manager icon, and click around for something like, Join New Network.... or else click on the wireless Network it lists, tell it WPA, and give it your password.

---

### Post by kevdog on 2007-06-24
Trust me Knetworkmanager works the same as gnome's network manager.  KDE isnt your problem.  Here is the instructions how to install ndiswrapper.  Obviously from what you posted it isnt installed:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

---

### Post by biscuits on 2007-06-24
I duplicated that file Drate, but it causes the system to hang for a long time during startup (I can't find a way to view a diagnostic message, it just shows me the splash screen). However once loaded the networks show up in KNetworkManager.

I'm pretty sure ndiswrapper is installed, check out the first line of the code in my previous post. Also, I can connect to my neighbour's unsecured network no problem using both [FONT="Courier New"]ifup wlan0[/FONT] and KNetworkManager. So ndiswrapper is at least working for that.

The problems are when I try to use WPA. Trying to connect to a WPA netwok in KNetworkManager causes it to give up on "configuring device". Using wpa_supplicant directly via a conf file as suggested in kevdog's link, causes it to infinitely repeat the first part of the handshake.

---

### Post by kevdog on 2007-06-24
ndiswrapper is most likely set up correctly, but if you would go through the instructions on the ndiswrapper website, you would know for sure if it was.


As far as wpa -- its very tricky with certain drivers.

ndiswrapper website list suggests you try this:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,wpa/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,wpa/)

This way is very cumbersome, however Ive found if you can get your machine to connect using this approach, then there are ways to "automate the process".  If it cant connect using this approach, then the easier more direct methods (ie Knetworkmanager) probably wont work either.

---

### Post by Drate on 2007-06-30
I can say the extra long boot-up time is normal.  That frustrated me at first too, but I can see no way around it.  Unfortunately though, in Edgy, the only problem I have run into is forgetting to blacklist the bcm43xx... that caused similar issues to what you are describing.

Try in the console "ndiswrapper -l" and see if it still lists bcm43xx as an "alternate driver"... if so... I feel fairly certain you're not getting any further until you can make it STOP trying to use bcm43xx for ANYTHING.  That's a problem I'm having in Feisty, blacklisting isn't enough apparently.

As far as the infinitely repeating the first part of the handshake... you are most likely more knowledgeable of such things than I am, but in the (probably unlikely) event you are wrong and it actually is doing what it's sposed to do, just refuses to stop doing things in general... add the "-B" near the front of the command to run it in background so you can close the console and get on with life.

---

