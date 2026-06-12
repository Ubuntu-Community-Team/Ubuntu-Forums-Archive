---
title: "Is this possible?"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by silvercliff on 2008-07-06
I have a standard wired LAN in my house, and it works fine.  Now I have a computer on the network that I use as a fileserver/TV and that is all working great.  What I want to know is, would it be possible to put a wireless pci card into that fileserver and use it as a 'wireless hub', so a bunch of wireless devices (psp, a couple of laptops... etc) could connect to my wired LAN and access the internet/files on it?

If so, how would I go about doing it?

---

### Post by lswb on 2008-07-06
It is possible but you need to do some homework first. Not all wireless devices can act as an access point or master. The OS must have a driver that is capable of using the card in this mode. And you will need to be able to configure the OS to act as a router, dhcp server, etc. For as little as wireless routers cost these days, I would take a look at using one instead, plus you don't have to have the fileserver/tv computer turned on for the rest of the network to work.

---

### Post by silvercliff on 2008-07-06
Well I already have a wireless card, and after doing a bit of reading I found out that the chipset of my card is bcm43xx, which can be tricky, because it of an issue with going into ad-hoc mode.  I also read that this problem can be worked around using nsidwrapper.  So I have got the ndiswrapper driver working.

The fileserver is ALWAYS on :) so I dont need to worry about down time.  Now its running ubuntu 8.04.

So how would I go about this?  It would be nice to have the FS controlling the wireless network with dhcp, but its not a must.

---

### Post by lswb on 2008-07-06
First off, there are several very good howtos and threads that discuss this that you can search for right on these forums, or with google for the wider web. That and man pages is how I learned what I know! I'd advise that you do some searching & reading along these lines just for a better idea of what's going on if nothing else. 

First I suggest checking the capabilities of your wireless card installed in the server. In my experience Network Manager is of little use or even a hindrance at this stage, so open a terminal and type the command:

   iwconfig

You'll see several lines of info, hopefully similar to this:

lo        no wireless extensions.

eth1      unassociated  ESSID:""  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

This is from my laptop. It tells me that interface eth1 has wireless capabilities and its current configuration.  Your interface may use a different name, substitute that where I use eth1 below. Note that you'll need to use sudo with the iwconfig command if you are changing any settings.

To see if ad-hoc mode is supported:

sudo iwconfig eth1 mode ad-hoc

If there are no error messages just type iwconfig again to verify, hopefully you will see "ad-hoc" in the output where "managed" was the first time. Then check if you can use "master" mode the same way,

sudo iwconfig eth1 mode master

and again, if there is no error message, verify by typing iwconfig. 

My laptop BTW with an Intel ipw2200 mini-pci card, supports ad-hoc, but not master mode. I get an error message like this:

Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.

Sometimes the limititation is in the card itself, sometimes it's the driver. (module)

If you were able to set the card to either master or ad-hoc, it's just a matter of working out the details. If your laptop and server are fairly recent distros they will have the avahi/mdns zero-config service running by default, and for a quick ad-hoc network you can try this command, which is using the essid mynet:

sudo iwconfig eth1 mode ad-hoc essid mynet channel 6

(The channel 6 part may not be strictly necessary but I have had better results when including it. It doesn't need to be channel 6, anything between 1 and 11 IIRC is OK)

Now click on network manager on the laptop and see if it shows mynet as an available network. (IIRC, Network Manager can connect to an ad-hoc net OK but can't create one) If so click on it and see if it connects. If avahi & mdns are running on both systems, you should get an ip address in the 169.254.x.x range, and you should also be able ping the systems by using .local as a domain name. Say for example your systems use the host names "server" and "laptop", open a terminal on the laptop and type 

ping server.local

If all went well you'll see something like
  64 bytes from server (169.254.2.99): icmp_seq=1 ttl=64 time=0.057 ms
repeated several times, just press Control-C to stop.

Note that this simple ad-hoc network is completely insecure, no WPA or WEP, and some systems, especially older ones without avahi or a similar service running, may have problems. I have an old iPaq for instance that can ping another host on such a network by ip address but not by host name. 

Good luck!

---

### Post by lswb on 2008-07-06
Damn those smileys!

Hey, I just realized you said that you're already running a wired network, so maybe you already have a dhcp server. How are you assigning address on the wired net? You should be able to use the same method for wireless.

---

### Post by silvercliff on 2008-07-06
OK sweet. I now have my laptop and FS able to ping each other. Thanks :D

My wireless card on the FS will run in Ad-Hoc mode, but not master.

Now down to buisness :)  My wired network is managed by my router/modem, not the FS so I would have to setup the DHCP server on the FS.  I assume that I can enable it for only one interface (ie the wireless card).  Also how do I link the wireless network to the wired network so that I can use internet and browse my network files from the laptop?

Also, is there a way to implement WPA on this network to protect it?

---

### Post by lswb on 2008-07-06
Okay, It's getting a little over my head here for me to provide details. I've never tried it, but I believe you can use WEP and/or WPA on an ad-hoc netowrk, provided of course the adapters and drivers support it. Look at the man pages for iwconfig. As for the dhcp part, do some searching or googling for "internet connection sharing" With the right settings on your server, you can have it forward dhcp requests to the exisiting router, (avahi won't be used in this case) I've never had occasion to set this up myself, but I've seen lots of posts from others who have successfully done it.

---

