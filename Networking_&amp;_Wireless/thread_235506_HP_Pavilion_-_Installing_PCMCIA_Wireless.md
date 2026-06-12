---
title: "HP Pavilion - Installing PCMCIA Wireless"
date: 2006-08-13
forum: Networking &amp; Wireless
---

### Post by ubun00b on 2006-08-13
I preface this post with "i am a n00b to ubuntu."

After spending about 2 weeks trying to get my built in broadcom 4303 wireless working, using both the nidiswrapper and fwcutter routes, i couldnt get it working.  So i broke down and bought a Netgear WG511v2 pcmcia card.  Don't laugh, but i plugged it in expecting it to just take off and do it's thing after some configuration in network manager.  But to my disappointment, when i plugged it in, nothing happened.  No blinky lights, nothing.  

My real question is, where the heck to i start troubleshooting this thing?  I've searched in the forums to get ideas on what to do, but nothing ive found so far gets my foot in the door.  Any help would be greatly appreciated.  Thank you!

---

### Post by oldcity on 2006-08-13
Take a look at:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

HTH
oldcity

---

### Post by weekend warrior on 2006-08-13
Or simply take it back and get something that **will** "just take off" after you plug it in. It's *not* a silly expectation at all.

See >> [this thread]("http://ubuntuforums.org/showthread.php?t=234143") or simply click on my signature.


HTH

---

### Post by roachk71 on 2006-11-03
I wonder: is this a "Made in China" card?

If you're willing to "get your hands a little dirty", I can offer quite a bit of help...

But I should warn you that it will take a few hours. After that, you might not be able to use WPA, but it works fine with either WEP key length.

I happen to own a WG511v2 "Made in China" card. This one uses the Marvell Technology Libertas chipset, which isn't supported by the version 1.1 NDISwrapper included with the distro, and there are no open source drivers, either.

I had to use the same procedure to make it work in both Dapper and Edgy.

UPDATE: Since a couple of days ago, I've been forced to switch back to Dapper. Edgy had an unexpected (and catastrophic) crash, so I had to reinstall. The system is back up entirely now (wireless included).

A word of caution: If you're gonna do something sensitive like this, don't trust JFS or XFS as your main file system... :p

Please consult the attached (compressed) PDF file regarding installation; this detailed guide should get your card up and running. If you're on a Windows machine, download and install 7-Zip from the web first.

---

### Post by roachk71 on 2006-11-06
New Update:

I just found an easier method which appears to work equally well. You'll still need the latest NDISwrapper source, but that only takes a few minutes to build, as opposed to a few hours for both that and the kernel.

First, open Synaptic, and install the latest kernel and headers for server equipment. You also need build-essential.

Now reboot. Make sure the server kernel is booted by using the Escape key before the timer expires. Then, unpack the NDISwrapper source, open a terminal and cd to its directory, issuing these commands as root:

```
make uninstall    (do this one twice)
make
make install
```Now, insert the CD which came with the card, and cd to /media/cdrom/Driver/Windows\ 2000. Issue the following command:
```
 ndiswrapper -i WG511v2.INF
```Then edit /etc/modules, and add this line to the end:
```
ndiswrapper
```Save the file, and close it. Reboot once again.

All you should have to do after this is configure the wlan0 device in the Network Configuration dialogs (Sorry, but only WEP can be used, no WPA).

I can't believe it was actually this easy--I was used to compiling a custom kernel for this!!! In fact, I'm using the card with the server kernel as I write this reply. :-k

By the way:

You will have to remove the old kernel before you reboot. Open Synaptic again, and mark the old linux-image for removal. Now apply the changes. Now the new kernel will be the first boot item, and will boot on every startup.

---

