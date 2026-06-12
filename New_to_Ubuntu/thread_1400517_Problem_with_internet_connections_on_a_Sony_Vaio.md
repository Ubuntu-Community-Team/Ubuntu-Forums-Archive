---
title: "Problem with internet connections on a Sony Vaio"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by googoodlmcs on 2010-02-07
Alright, so I just downloaded Ubuntu 9.10 and installed it yesterday on my Sony Vaio VGN-NR180E. If it makes any difference, the install created a dual-boot system, with stupid Vista being the other half.

The install went great, the partitioning went smoothly, and the operating system itself works great. However, the internet has been a huge hassle to try and configure.

I've tried using the wireless setup wizard that Ubuntu came with to set up with my pre-existing wireless network, which is a WPA Personal network. My Sony came with Intel Centrino and an Intel Pro/Wireless 3945abg network card, which is supposed to be supported "out-of-the-box" with Ubuntu.

I've tried both wireless and wired networks, and even though the network icon changed to a "Connected" symbol when I used the a wired network, I still get no internet. On the Vista side of things, my connection works either way. I've done all of the restarting and turning on and off of the Sony wireless LAN switch and such.. No change for Ubuntu.

I'm guessing there may need to be some correction of privileges under the Vista control panel to allow access to the other partition..? Other than that, I know of nothing besides finding some kind of additional driver to help Ubuntu figure things out..

Any help would be great. Thanks in advance.

---

### Post by 3rdalbum on 2010-02-07
Your driver is probably fine, but your router may be set up in an odd way that causes Ubuntu not to be sent the address for your DNS server. You can fix this by right-clicking on Network Manager and going to Edit Connections, clicking your network and going to Edit, and then going to the IPv4 Configuration tab. Change the "method" to "Automatic (DHCP) Addresses Only" and then put in the following under "DNS":

208.67.222.222

This is a DNS server that is free for anybody to use.

Disconnect from the wireless and then reconnect. If it's worked, then you should be able to access [www.google.com](www.google.com).

Check your router's DHCP Server configuration in its web-based interface and see if anything pops out at you as being wrong.

---

### Post by googoodlmcs on 2010-02-07
Alright, so I went to turn on my computer to change that IPv4 configuration, but was surprised to see that the laptop automatically connected itself to my network and had a working internet connection without changing any settings.

This ability to connect to the internet lasted about an hour, and then it went back to not working, without warning.

So, after it stopped working, I went ahead and changed the IPv4 settings, as you suggested, but I still didn't get any internet.

At this point, I have a possibly related issue. The wireless LAN switch on the front of the laptop itself seems to do almost nothing. When the internet was temporarily connected, the switch was in the ON position and glowed green. But now, the switch is ON and there is no glowing green light. I've tried moving the switch back and forth, as well as restarting the computer, multiple times with no change- I get no green light and no connection either way. However, when I put the switch in the OFF position, the Ubuntu wireless network wizard informs me that my wireless network device is "Not Enabled," and when it's in the ON position, it says "Device Not Ready."

I also was able to update my drivers and system when I was connected to the internet, which is slightly comforting. Still, it seems like the Ubuntu partition of my harddrive is not communicating with my actual hardware correctly..

---

### Post by googoodlmcs on 2010-02-17
Anybody have a suggestion....??

---

### Post by Iowan on 2010-02-17
What are results of (from a terminal) **ifconfig -a** and **sudo lshw -C network**?

---

### Post by Greenwidth on 2010-02-17
This post is a fix for Jaunty which seems to work (see post #8):
[http://ubuntuforums.org/showthread.php?t=1289484](http://ubuntuforums.org/showthread.php?t=1289484)

Change last line from jaunty to karmic.

---

