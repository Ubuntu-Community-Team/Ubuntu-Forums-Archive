---
title: "Can't connect to wirless networks"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by tonamijesus on 2007-10-20
Hello.

I'm having issues connecting to wireless networks. Linux lists all the available networks but refuses to connect to any of them. When I tested out 7.10 on the Live CD the internet worked perfectly, but now that it is installed 7.10 refuses to connect.

I've tried reinstalling the drivers, but when I get to the point of installing ndisgtk, Linux can't find the package.

Any help would be appreciated.

---

### Post by pieisgood4589 on 2007-10-20
This is what happened to me for a while...
I first tried re-installing the system, but that failed... 

What wireless card is it?
When you click connect, does it ask for a password? Does it ask for another password for the device to be enabled? Check that, then post. :guitar:

---

### Post by geetlord on 2007-10-20
I am having the same exact problem, I missed seeing your post before creating one of my own though (sorry about that)

---

### Post by geetlord on 2007-10-20
I just managed to get my connection to work here is what did it for me:

I told the network connection tool to connect directly to my network and somehow this worked, however i didn't get an ip from it.

next i typed:
sudo dhclient wlan0

this setup my connection and got me an ip...now my internet connection seems to be working correctly, i hope that helps some

---

### Post by tonamijesus on 2007-10-20
When I try and access my network I am prompted for the network key, as usual. However, when I enter it, Linux fails to connect. Sometimes it will ask me for the password again but it will fail just the same.

I tried setting the connection up manually, both with a static IP and DHCP, neither of which worked. I already know my IP address and the subnet mask, but this doesn't help if I can't even establish a connection with the router.

It's extremely odd that Linux can identify every network within range but cannot connect to any of them.

---

### Post by tonamijesus on 2007-10-20
Also: I am using a Linksys Wireless USB device. My computer doesn't have an integrated card.

---

### Post by tdmoore on 2007-10-22
I am in the same boat.

New to Linux and loaded 7.10 after testing most apps (EXCEPT wireless...I regret that now).

Have Linksys WUSB54G and it appears that it should work.  Have loaded NDISWrapper (not too sure what this really does) and have gone to help menu only to find that I should load ndisgtk...which I cannot find anywhere.  Even search comes up blank.

I have the .inf file as I have the original CD and can copy to the desktop or try off the CD if needed.

Instructions to load driver AFTER loading ndisgtk look relatively easy for an absolute newbie like me...however loading ndisgtk has me baffled.

Can someone else assist all of us on this thread?:confused:

---

### Post by geetlord on 2007-10-22
an update on my fix: it seems that while manually connecting seems to work, it has to be done each time the computer is restarted, it would be really helpful to find a way for this to happen automaticaly

---

### Post by MariusSilverwolf on 2007-10-22
Cross-posted from here: [http://ubuntuforums.org/showthread.php?t=586017](http://ubuntuforums.org/showthread.php?t=586017)


"First and foremost, Wieman1 and Zoinks, you guys wrote up some awesome tutorials for getting the Ralink drivers to work. You guys rock.

That fact nothwithstanding, here's what I've learned from following both Tutorials to the letter:

The LinksSys WUSB54Gv4 USB Wireless Network Adapter does NOT want to work in Gutsy with the AMD64 flavor. At all.

In Fiesty, the Serial Monkey rt2x00 Legacy drivers picked up the card, and as long as I dropped down to WEP instead of using WPA I could connect no problem. After the upgrade to Gutsy, I was caught in the endless loop of my Wireless network being detected, being prompted by Network Manager for the encryption password, sitting for 30 to 60 seconds, and repeating.

First, I ran through Wieman1's tutorial. Like a few others, when I Blacklist the rt2500usb driver in /etc/modprobe.d/blacklist, I see NO Wireless Network Adapters in Network Tools. I suspect this is because NDISWrapper is 32-bit, and I need to recompile it for AMD64 architecture. I tried following the NDISWrapper on AMD64 Tutorial, but there's no Debian folder within the latest package, and none of the files I need to alter to recompile exist anywhere on my system.

So, having to give up on NDISWrapper, I happened upon Zoinks tutorial and my hope was renewed. For a time. BUT, the only driver package from Serial Monkey that will bind to the card is the rt2x00 legacy version of rt2500usb. rt2500, rt2570, and rt73 all fail, no matter how many times I remove previous modules or how many alterations I make to aliases and interfaces.

So, until the rt2x00 legacy driver package can be fixed to actually let me connect to my wireless network -- which I've tried with WPA, WEP, and open without any luck -- I'm dead in the water. I may just pick up a reel of CAT5 and run a line under the house to connect from the router to the PC via hardline. For the drop on each end and the run in between I should only need about 100 feet of cable and 60 feet of pvc conduit.

Just thought I'd share my war story. If anybody else has found a way to get that confounded piece of hardware to actually connect to a wireless network and get past the router, I'd love to hear it. I'd rather not crawl around under a house in Florida when it's still 90 degrees with 70% humidity outside during the day."


After getting some sleep and doing some thinking, I believe I have a cheaper solution, at least for my desktop.  The Linksys WGA54G  Wireless Game Adapter is little more than a wireless bridge, and from what I can find, Version 2.0 supports WPA.  If I can run from my onboard NIC to the WGA54G and configure that to talk to my Wireless Network, I should be up no problem.

Something to think about . . .

---

### Post by GSF1200S on 2007-10-23
Im having the same problem, and ive tried damn near everything. Even ran Mepis, and while the card worked out of the box, it still wont connect to the network through the network manager.

Back on Ubuntu 7.10 after installing ndiswrapper and the windows driver, my card works with a 54Mbps connection, although I still cant connect through Gnome network manager (or KDE's network manager). However, if you do:

```
sudo iwconfig ath0 essid networkname
sudo iwconfig ath0 key wep123key
sudo dhclient ath0
```

where ath0 is your wireless device, it will establish an IP address and will work awesome. It just sucks you have to type these three commands every time you want to connect, especially if you have a laptop you travel with. You can use the gnome manager to see what networks are in range, or you can do:

```
iwlist scanning
```

to get a command line print out of what networks are available. Let me know if this helps, or if anyone knows how to get gnome network manager working with these (mostly) broadcom cards...

---

### Post by k3lt01 on 2007-10-24
Just tried this and it didn't work on my machine. tried both ath0 and wlan0 still no network. It even told me that there was no device yet if I do iwlist my device is listed as working. This is frustrating as it is not consistent.

---

### Post by xipher-cdb on 2007-10-24
Hello.

I have the same problem, my card can search wireless networks but can't conect to them. At home I use WPA (my own key) and in a friend house he has a 128 bits key WEP, when I write the key, the network manager can't conect and ask me the key again.

My card is a PCMCIA Gemtek WL-818F, rebranded by Telefonica (they gift me the card), it has the PrismGT chipset.

How can I make the network manager to work? Are there other software for wireless?

Thanks and sorry for my english.

---

### Post by Dmart on 2007-10-24
I have this same problem, BUT I have been able to connect to my schools network because the connection is not encrypted, then when I come home and try to connect to my linksys wrt150n router with wpa2 encryption, it doesnt work. I even tried setting it to wep and wpa but none of this work and ended up pissing off my roomates, also those commands did not work for me either

i have a broadcom g/b/n/ router, built in on my hp dv6000

edit: i even did a re-install in hope, but my hope has been crushed

---

