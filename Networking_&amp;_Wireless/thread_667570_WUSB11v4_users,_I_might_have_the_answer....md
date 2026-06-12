---
title: "WUSB11v4 users, I might have the answer..."
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by SZF2001 on 2008-01-14
I've got the Linksys WUSB11v4 card, and I've FINALLY got it working with Linux after, what, two or three years of the occasional screwing around? Anyway, here's the down low.

Years back, I had this card running fine on Breezy with ndiswrapper. I performed an update, and it never worked since. Since then I had switched back to Windows and occasionally installed different variants of Linux (Redhat, Suse, Debian, etc) but they all seemed to fail in the same pattern:

I install the latest ndiswrapper. I install the correct .inf file to associate the card with. I modprobe it. That should be everything, right? Well, every time the card just seemed to only send a signal! The computer could see the networks around it, but it would be DAMNED if it could connect, either with a Static IP or using DHCP. Forever I just kept trying and trying, hopefully thinking I'd find a magic OS that would use this card, even though the ndiswrapper website said it was supported...

But last night, I tried a crazy idea. It seemed to stick.

Make sure you've installed your card with ndiswrapper using the WUSB11v4.inf file, of course. Ther are various guides dealing with this and I'm not going into to much detail about it.

First, install "Wifi-radar", either through the terminal (sudo aptitude install wifi-radar) or with the Synaptic Package Manager (search "wifi-radar"), or however else you feel on installing program.

Now, go to System -> Preferences -> Sessions. Make sure the box next to "Network Manager" is off. This now means the Network Manager WILL NOT start with each session you bring up, either after logging out or rebooting. You may notice the icon in your system tray now - the two computers, and you can click on it to get to your Network settings and such.

I prefer to reboot at this point, just to make sure all if* and NetworkManager apps are down.

Log in. Notice that the two computers are gone from your system tray? That means you did it right.

Now, go through to Applications -> Internet -> Wifi-radar. Pick your hotspot and see if it works out!

Please note - Wifi-radar can be kind of picky with your information. Make sure you are putting in the correct key (you don't need to put any dashes or periods next to the number - an example of how to type in the keycode: aabbccddoo , if the keycode were a 16bit HEX code (or WEP)) and other information - using "auto" seems to work out, but if you don't get an IP when using the "open" option try the "restricted" option. It shouldn't be to hard.

Anyway, I'd hope people are willing to test out my theory on getting this damn card to work - it seems that with updates to kernels and packages, somehow Network Manager managed to screw over this card.

---

### Post by SZF2001 on 2008-03-03
It's so weird how this method worked one time.

I'm going to do a fresh install. If the above didn't work, I'll give my little howto on how I installed ndiswrapper.

Grab the latest from their site. Untar it.

Before using the "make" commands, install a package called build-essential. Now do a 'cd' with the terminal to where you untarred the file and run (with sudo) make uninstall, make, and make install.

I'm pretty sure that's how I got it to work that one time. ONE TIME. I did a fresh install and tried Ubuntu's deb packages... No luck at all.

---

