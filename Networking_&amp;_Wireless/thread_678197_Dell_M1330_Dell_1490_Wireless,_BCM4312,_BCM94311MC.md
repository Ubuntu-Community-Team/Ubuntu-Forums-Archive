---
title: "Dell M1330: Dell 1490 Wireless, BCM4312, BCM94311MCAG"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by AndrewZorn on 2008-01-25
I can't get this wireless working to any extent.

Ubuntu 7.10  64bit

My invoice says **Dell 1490 Wireless.**
LSPCI says **BCM4312**
Bottom of laptop says **BCM94311MCAG**

Everyone else says that this computer is so easy to install Ubuntu on.  I installed it on an Acer under a month ago and everything but the wireless just worked, and the wireless only took me one try.

I've tried several tutorials and I probably have many different drivers installed that are doing nothing.  The problem is I still don't know WHICH WIRELESS CARD I EVEN HAVE.

Also, this one is doing the same as the Acer: when I click on the network-manager icon and do "Connect to other wireless network..." it just shuts down.  The icon goes away, and I have to restart to get it back.

Very frustrated right now.

EDIT got it!  Not sure exactly how, but after following THIS: [http://ubuntuforums.org/showpost.php?p=2661104&postcount=5](http://ubuntuforums.org/showpost.php?p=2661104&postcount=5)
[quote=farbird] Re: Helpfull Hints for a tx1000 (tx1120)
to get your wifi broadcom working, try this

sudo apt-get install bcm43xx*

sudo gedit /etc/iftab

change the interface name of the wifi interface to "wlan0"
it may be eth0 or eth1 initially [ check to ensure which is the wifi one ]

sudo gedit /etc/network/interfaces
remove all lines which make references to the old "ethx" that has been replaced above to "wlan0"

now in console, do this

sudo rmmod bcm43xx
sudo modprobe bcm43xx

this should get it working...
if the rmmod doesnt work, just reboot the laptop....

if still cannot work... post reply here[/quote]
it didn't work.  Then I last-hope removed 'bcm43xx' from the blacklist thing (was it ever supposed to be there?  I DON'T KNOW...)... nothing.  Rebooted: worked!

---

