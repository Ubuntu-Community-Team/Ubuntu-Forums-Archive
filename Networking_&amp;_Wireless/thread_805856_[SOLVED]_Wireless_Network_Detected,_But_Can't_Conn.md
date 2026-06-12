---
title: "[SOLVED] Wireless Network Detected, But Can't Connect"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by seagullplayer77 on 2008-05-24
Network Manager is finding the wireless network just fine--SSID, signal strength reading, channel, the whole nine yards--but whenever I try connecting to it, Network Manager tries for about a minute and then gives up. I'm not quite sure what the problem is exactly. When I try connecting to my wireless network, the message reads "Wireless network connection to 'Rudyfi' (0%)," except I'm sitting right next to the router and Network Manager shows that I'm getting a 100% signal. I tried connecting the other night, but then it would stall for the minute and give me a message along the lines of "Trying to get the network key."

I'm not sure how much of this will help, but I got my wireless card up and running (it DID work just fine a few weeks ago) using this tutorial:

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

Here's the output of an iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Rudyfi"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

The router is a D-Link, but I don't really think that should make any difference. It's secured with WPA, but I've got wpasupplicant installed, so I don't think that would be an issue either. Then again, if I knew what the issue was, I wouldn't be posting this.

Anyway, if anyone out there is in a helpful mood, I'd really appreciate it. After all, it's kinda pointless to have a laptop and not be able to connect to wireless networks with it. I'm not a Linux master, but I'm not completely new to it either. I follow instructions and tutorials quite well, and I'd appreciate the help. Thanks!

---

### Post by mapes12 on 2008-05-24
This post may help:

[http://ubuntuforums.org/showthread.php?t=794815](http://ubuntuforums.org/showthread.php?t=794815)

:guitar:

---

### Post by seagullplayer77 on 2008-05-24
Hmm...I tried installing Wicd yesterday, and it did just about as well as Network Manager did. Kept trying to connect, but it never actually did. I'll give it another shot and sees what happens, though. It is Linux, after all, and things like this have a strange tendency to change overnight :-).

---

### Post by seagullplayer77 on 2008-05-24
Unfortunately, no joy with Wicd. It picked up the wireless signal just like Network Manager did, but it wouldn't connect to it. It tried to get an IP address from the router for about a few minutes, and then it just gave up. Any other ideas?

---

### Post by IceCap on 2008-05-24
I'm having the exact same problem.  I'm using a TrendNet USB wireless adapter with Mythbuntu (see my post below).  My output looks exactly the same as yours.  I'll be watching your progress (sorry for semi-hijacking your thread).

  IC

---

### Post by Jackie999 on 2008-05-24
I'm having same problem with my AWUS036H Alfa USB antenna (chipset rt8187) 
Ubuntu is said to support this..but I can't get it to show in iwconfig ..the only way I get it to show up is with ndiswrapper.  But same thing..I see networks all over..but won't connect..times out.
I also have a Belkin usb (rt2870) that only runs with ndiswrapper..and it works just fine.

---

### Post by seagullplayer77 on 2008-05-24
Hmm...good to know I'm not the only one having a problem. I suppose I probably should've mentioned this earlier, but I'm running Ubuntu Studio 8.04 AMD64 (on an 64-bit machine, of course). I've done some looking, and I haven't come up with anything useful yet. All of the suggestions/solutions I've come across for similar problems don't ever produce any results. I tried reinstalling the driver with ndiswrapper, but that didn't do anything either.

Anyone in a helpful mood :-)?

---

### Post by sirzepp on 2008-05-25
Man I wish I could help.  My desktop (AMD64) wireless worked OK, but I'm back to a wired connection for speed(just seems more responsive).  I've also switched the desktop back to 32 bit Ubuntu.  I'm tired of dealing with the minor issues (flash, etc.) on 64bit.  My laptop has forced me to use WICD...which is working FINE...but I really wish net-manager would work perfectly for me.

---

### Post by pgroover on 2008-05-25
I had the same problems and eventually solved it by reinstalling network-manager and kwallet-manager and then manually starting nm-applet using Alt-F2.  That tied the keyring to the encryption key and I've been running fine ever since.  With the exception of the reinstallations, I had tried all of that before and don't understand why I had no luck until then...

Good luck.

---

### Post by nzadLithium on 2008-05-25
try this:
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

This way you'll not be using any network setup program so if anything goes wrong you'll know where it did and can post back whats causing problems :)

---

### Post by mapes12 on 2008-05-25
My advice............abandon any wireless adapter that needs a windows driver via ndiswrapper to work. It just doesn't do it long term. Get yourself a native supported card. Plug it in and it just works. no configuring, no command line stuff.

Here's a good starting point:

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

I got the Comatrend RT2500 PCMCIA and all my troubles are over.

:guitar:

---

### Post by pgroover on 2008-05-25
> **nzadLithium said:**
> try this:
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

This way you'll not be using any network setup program so if anything goes wrong you'll know where it did and can post back whats causing problems :)

I definitely agree with running everything from the command line.  I have scripts to set up my wireless connection for different locations that I may be at and encryption is included with them.  I'm not sure what the problem is/was, but even the scripts failed to connect when encryption was a factor.

---

### Post by seagullplayer77 on 2008-05-25
Thanks a million, nzadLithium! The tutorial at your link got my wireless up and running :-). As a matter of fact, I'm using it right now. It was an odd feeling to be able to go to a Website and get there without the LAN cable plugged in.

I'm glad I finally got some wireless up and running, but is there any easier way than punching in a bunch of commands into a terminal? Pgroover mentioned something about scripts...maybe I could use those. I suppose I could just keep the list of commands stored somewhere and use 'em everytime I need to get wireless up and running, but it'd rock if there was a faster, easier way.

In any case, thanks a bunch to everyone who helped out.

P.S. Pgroover, would you mind sending those scripts you use my way? I'd appreciate it a lot!

---

### Post by pgroover on 2008-05-25
> **seagullplayer77 said:**
> 
P.S. Pgroover, would you mind sending those scripts you use my way? I'd appreciate it a lot!

Sure thing, basically you do exactly what you said:
Save the commands in a file, make it executable, and then run it when needed.  As time goes on, you can extend them to provide extra functionality as needed.

Just create a text file and put the following in it replacing the portions in capital letters with your networks specific info.  Then make the file executable (chmod +x filename) and run it from the command line.  Of course, if your wireless interface is something other than ath0, change that accordingly as well.

```

#!/bin/sh

sudo ifdown ath0
sudo iwconfig ath0 essid YOUR_NETWORKSID key YOUR_ENCRYPTION_KEY ap YOUR_ACCESS_POINT
sudo ifup ath0
sudo dhclient ath0

```

Good luck.

---

### Post by seagullplayer77 on 2008-05-26
Thanks for the help, pgroover. I just ran the script you gave me, and I'm using my newly (sort of) acquired wireless connection right now. It took the better part of my Memorial Day weekend to finally get this stupid thing solved, but I'm happy that it's finally out of the way.

I really don't want to bother you any more, but how would you do different scripts for different locations? Would you just write a new one for a new location, or is there a way to add a location or fuctionality into the existing one? For example: I've got the script set to work with my grandparents' wireless right now, so how would I get it to work with my home wireless? Just change the ESSID and the password? How would I get it to work with an open network with no security? Just curious...

You've helped me quite a bit already, but if you're in the mood to guide me through a little more of this, I'd be a very happy man :-).

---

### Post by nzadLithium on 2008-05-26
basically to set up multiple scripts for different network connections:

stick this in a file
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES" (key HEX_KEY)
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>

replace interface with your interface
type essid in
if you have WEP security add the hex key bit. If you dont then dont include it.

save script. make executable. 
Open script (edit) then make any changes for second network. Save under different name. Then you can just run either script depending on which network your connecting to.

If your wanting to set up wireless network but your not sure of essid then you can find out available networks by doing this: iwlist scan.
If you can do all this you can remove network manager completely (like I did. :) I got annoyed with it for being there but not doing working.

---

### Post by pgroover on 2008-05-26
To keep it really simple, you can do exactly as you said using the same format for different scripts.  To set one up without encryption just leave off the key portion and you should be fine.

A more complicated version would scan the available networks, locate ones it "knows" and then set up for the preferred one.  I have one like that somewhere, but I'll have to find it, if I can.  I wrote it quite awhile back and then stopped using it when the number of networks I connected to wasn't worth the hassle.

Don't worry about it, like nzadlithium, I don't mind at all.

---

### Post by seagullplayer77 on 2008-05-26
OK guys, I thought I had this fixed, but apparently not :-(. I ran pgroover's script last night and it connected me to my wireless network without a hitch. I tried running it again this morning, though, and it gave me grief. It kept trying to get an IP, except it never got one. I tried running the script that nzadLithium gave me in a terminal window, and this is what it put out:

There is already a pid file /var/run/dhclient.pid with pid 12621
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1f:3a:5d:d6:d9
Sending on   LPF/wlan0/00:1f:3a:5d:d6:d9
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.0.1 port 67
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1f:3a:5d:d6:d9
Sending on   LPF/wlan0/00:1f:3a:5d:d6:d9
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I'm guessing the line that starts with "error" has something to do with the fact that it isn't working, but I'm not sure what the error refers to. I wonder if the reason the script worked last night was because I tried connecting through the terminal a number of times (unsuccessfully, I might add) before I tried running the script...Any ideas?

---

### Post by seagullplayer77 on 2008-05-26
Here's a quick update for anyone that's interested:

I tried modifying /etc/network/interfaces as per [http://ubuntuforums.org/showpost.php?p=4829624&postcount=345](http://ubuntuforums.org/showpost.php?p=4829624&postcount=345), and now the file looks like this:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eht0

auto wlan0
iface wlan0 inet dhcp
pre-up /sbin/ifconfig hw ether 00:1f:3a:5d:d6:d9
wpa-psk blah, blah, blah
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid caljnet

The "blah, blah, blah" of course is my WPA password in hex, but other than that, that's what my /etc/network/interfaces file looks like. Could there be an issue with something in there? Currently, I'm working off my wired connection (which works perfectly fine--always has), and my wireless connection still refuses to connect. I've gotten it to work on three separate occasions, but the odd thing is that a solution never works more than once. I've used Network Manager once, the terminal once, and a script (ran from a terminal window) once, and all were successful in giving me wireless connectivity exactly once--no more, no less.

I'm lovin' my new 64 bit Ubuntu, but it would seriously suck if I'll have to boot into Vista (yuck!) every time I want to use a wireless connection :-). Any help?

---

### Post by seagullplayer77 on 2008-05-26
Well, for whatever reason, I finally got my wireless working (and it worked after a restart, too--that's a first!). I'm not sure exactly how I did it, but I ran:

sudo ifconfig wlan0 down
sudo ifconfig wlan0 hw ether "MAC_ADDRESS"

Then I installed Wicd, and although it's never worked for me in the past, it worked today. Weird...For anyone else having a similar problem, my /etc/network/interfaces file contains the following:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eht0

And System > Administration > Network lists all of my interfaces as NOT connected (although the wireless most certainly is connected).

In any case, a big thank you to everyone who helped me out. Wouldn't be able to use Linux without all of the wonderful people here at Ubuntu Forums!

---

### Post by thinking2loud on 2008-05-26
Seagullplayer:

   Can I trouble you to reboot 10x in a row?  Are you sure your success isn't due to luck?  My current problem is that I have WPA security and a nice fat signal, and you have to repeatedly try to connect.  However, it connects to an unsecured signal--every time, first time.  Once connected, the signal never gets dropped.

---

### Post by nzadLithium on 2008-05-27
I'm pretty sure reason my script didnt work was because I thought u were using wep. Obviously this is not the case. 

thinking2load follow this
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

make sure you follow the bit about WPA not WEP.

---

