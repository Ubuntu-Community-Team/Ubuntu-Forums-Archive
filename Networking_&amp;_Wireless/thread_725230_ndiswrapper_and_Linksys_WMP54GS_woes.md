---
title: "ndiswrapper and Linksys WMP54GS woes"
date: 2008-03-15
forum: Networking &amp; Wireless
---

### Post by unknown03 on 2008-03-15
Hey everyone,
I've been reading alot of posts regarding the installation and use of wireless cards.. I installed Ubuntu 7.10 AMD64 and followed a couple tutorials that I found on these forums and got my internet up and running..
But then, since I got it working by accident, I decided to reformat and install fresh so I know what to do in the future, and failed miserably.
I have the Linksys WMP54GS with speed booster installed in my Gigabyte M57SLI-S4 motherboard that has an nVidia Ethernet controller (MCP55) -- (which I wont be using as my access point is upstairs)..

My problem is when I install ndiswrapper (and ndisgtk). Everything appears to be going fine and I install the WMP54GS.inf and that is present as well.. 

so I go on to blacklist the old bcm43xx

type in 'iwconfig' and have:
lo
no wireless extensions

eth0
no wireless extensions

eth1
(a buttload of stuff concerning my wireless card)

so I go through all the steps in the tutorials that refer to my wireless as wlan0 which I dont have anything associated with..

type in:
sudo ifconfig eth0 down

echo ndiswrapper into /etc/modules

sudo depmod -a
sudo modprobe ndiswrapper

check out /var/log/messages and there I find an error (which wasnt there the first time I got it working, and there wasnt anything to be said IF there WAS an error in the tutorials)

it says:
loadndisdriver: load driver(358): couldnt load driver wmp54gs

I suspect this is my only problem... oh and /etc/modprobe.d/ndiswrapper says something along the lines of alias wlan0 ndiswrapper ..should I replace wlan0 with eth1? and after I try installing everything I, somehow, disable any recollection of eth1....WTH!?

Thanks for Reading

My specs:
Motherboard: Gigabyte M57SLI-S4            OS: Ubuntu 7.10 AMD64
Processor: Windsor 5200+                        Video: 2xnVidia Geforce 8600 GT
RAM: 4GB Dual Channel
HDD: 1xSata 320gb 1xIDE 320gb

---

### Post by unknown03 on 2008-03-18
UPDATE:

Well I'm still not sure exactly how my devices were wiped from memory, but I am able to get it working now, with the help of [THIS]("http://ubuntuforums.org/showthread.php?p=4540744&posted=1#post4540744")

I didnt actually need to install the WinXP driver with ndiswrapper..just needed to load up the bcm43xx-fwcutter.deb and the source file to enable the Restricted driver

---

### Post by Sam Lars on 2008-03-20
Cool, I have one too, and I was using bcm43xx (the Restricted driver) a lot.
A while ago it liked to drop the connection about every day or two.  Then all of a sudden it worked great for a few months.  Just now it started dropping the connection again.  It seems that light traffic is fine, but when attempting to move a large file it has issues, and my network was fine, but as soon as I started to move files, the network stopped working.
Anyway, I moved back to ndiswrapper today... just thought I'd share in case you run into any of those problems.

---

### Post by unknown03 on 2008-03-24
thanks for the info, I was never really able to get ndiswrapper to really work on my system tho..I did ONCE by accident. But now every time i tried to put the ndiswrapper into the kernel, it erases all memory of me even having a wireless card

---

### Post by Sam Lars on 2008-03-24
Yeah, I ended up with ndiswrapper freezing my system whenever I did much over the network, so for the moment I'm tied to ethernet until I can get b43 working it Beta or figure out why bcm43xx is so iffy sometimes (or get ndiswrapper working, which it refuses to do...)
And that guide you link to doesn't make sense... you should only need ndiswrapper OR bcm43xx, not both... and it seems like it's using bcm43xx.

---

### Post by unknown03 on 2008-03-26
Yeah, the "installation" of the ndiswrapper drivers arent necessary and dont do anything when you enable the restricted driver.. As far as getting the ndiswrapper drivers to work I have no idea, as ive just experienced great failure (or progression):)

---

