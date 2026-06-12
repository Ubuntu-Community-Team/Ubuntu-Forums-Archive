---
title: "Ubuntu Not Recognizing 3Com EtherLink III card"
date: 2006-08-26
forum: Networking &amp; Wireless
---

### Post by bydoing on 2006-08-26
I am new to Linux and know nothing. I installed Ubuntu 6.06 on my old Compaq Armada E500 a few days ago with no problems at all...and I luv it. My laptop works faster and better than it ever did under WIN98SE. I found that it came with everything I need. Hoorayyy! I so want to get away from Microsoft.

I put Ubuntu on my desktop but my ethernet card did not even show up on Network Settings under Connections. This computer was given to my with no documentation and I didn't know what kind of ethernet card it was. I opened the box and physically took the card out to see if I could find anything written on it to identify it. No luck. So I took off Ubuntu and re-installed WIN98SE.

Then I was able to find out that My Ethernet card is a 3com EtherLink III ISA [3C509bTPO]. On the webpage for Hardware support Components Wired Network cards...

   [https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards) 

...it says this card is not auto-detected. But under comments it says "add 3c509 to /etc/modules, and edit /etc/network/interfaces."

I have no idea what that means nor how to do it.

I would like to put Ubuntu back on my desktop, again, and try to fix this ethernet non-recognition problem. Can someone help me with this?

Please understand that I have no experience with Linux and will likely need a step-by-step walk-through. 

I don't know if the following info is needed but I include it as it seems to be asked for in similar questions about internet connection problems.

bydoing@bydoing-desktop:~$ sudo mii-tool eth0
SIOCGMIIPHY on 'eth0' failed: No such device

bydoing@bydoing-desktop:~$ ifconfig eth0
eth0: error fetching interface information: Device not found

bydoing@bydoing-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


Thanks in advance for any help. :confused:

---

### Post by bydoing on 2006-08-26
Well, I found a cuple of other threads regarding this subject that I could not find earlier. [can't see fer lookin]

I will give the solution a try, and then post my results.:roll:

---

### Post by tiver on 2007-05-15
look here
[http://ubuntuforums.org/showthread.php?t=363766&highlight=3c509](http://ubuntuforums.org/showthread.php?t=363766&highlight=3c509)

but I didn't manage to get it work either :(

---

