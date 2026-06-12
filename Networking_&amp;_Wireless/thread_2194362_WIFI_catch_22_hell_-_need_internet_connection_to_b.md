---
title: "WIFI catch 22 hell - need internet connection to build wifi drivers"
date: 2013-12-18
forum: Networking &amp; Wireless
---

### Post by cazub on 2013-12-18
I am now on my third usb wifi dongle and about 70 bucks in. I've tried every distro of ubuntu and kubuntu since 12.04 and i cannot get a working wifi connection. None of these are compatible out of the box 
WNDA3100v2
ASUS N-13
DLINK DWL-131

wnda:
requires ndiswrapper, cannot get this package w/o an internet connection. Hard to get a package over the internet when your only link is through the dongle with no driver!
Using a second computer and a usb stick i got  GCC (for some reason not loaded by default) and built ndiswrapper , then built my driver , modprobed it etc. Did it work? Absolutely not. I had to tangle with Network-Manager since init.d/networking restart is depricated. Great, except it doesn't work. No combination of commands would restart networking. I ended up adding my own wlan0 entry and using ifup wlan0. I got a wopping 5 seconds of internet connection out of this. 

ASUS N-13: 
I decided to do a little research and find "The best compatible linux wifi dongle". A great little product, Plugged it in............. came up , looking good.............. can't ever connect outside localhost. Still this was better than the WNDA3100v2 so i decided to try 13.04 , no luck, then rolled back further to 12.04 lts, no luck at all. Reading up the best way to get it working is to download the driver from the site (again hard to do with no internet connection) and use Make and GCC to build the driver (great, but neither package is installed by default and again, i can't get them without an internet connection).

DLINK DWL - 131:
Researching some more i find a site saying that the DWL 131 is compatible with linux and runs 'out of the box'. Well it doesn't. 13.10 see's it as an optical drive. So instead of being able to connect to the net i can load it as a k3b project???? So looking at the forums .......... hey great, i can download the driver from the manufacturer , untar the tarball , use Make and GCC to build the file (sounding like a broken record but both of those packages require an internet connection which i don't have becaues i don't have the drivers to connect my dongle to the net).

So can anyone help? I would like to plug in a wifi dongle and go with 12.04-13.10. Any help would be greatly appreciated. This has been a very disapointing couple of days and i'm about to leave ubuntu because of it.

---

### Post by squakie on 2013-12-18
IF you REALLY want ndiswrapper (common and utils) and the gui front end ndisgtk, look on the installation media under /pool/main/n.  Please be aware, however, that any guides that suggest using ndiswrapper, compiling the driver, etc., are probably outdated and most likely shouldn't be used.

So, to really help you,  we really need to know what chipsets are involved before we can help so please do the following:

- plug in only 1 adapter and post the output back of:

lsusb | grep Wireless

repeat the above for the next 2 adapters, being sure only 1 is plugged in at a time.

Copy the output to some removable media so you can take it to a PC with net access (unless of course you can hard-wire temporarily to your router) and post those outputs back here.

and BTW - I have found that Tenda USB W322U v2 adapters do work right out of the box.  I have several I'm using and have used them in the past as well on other systems running Linux.  I get mine at Micro Center for just uner $13.

---

### Post by mörgæs on 2013-12-18
> **cazub said:**
> Hard to get a package over the internet when your only link is through the dongle with no driver!

Regardless of which {dongle,operative system} you use you should begin with getting a stable and fully updated system using wired internet access before trying the dongle.

---

### Post by Bucky Ball on 2013-12-18
Without sounding totally trite ...

What in heck is stopping you from getting an ethernet cable and plugging it into your router? You say you're $70 in from going and buying dongles! Is there something preventing you from plugging in a cable as, by now, you must have walked past dozens???

Incidentally, brand names can be confusing. What you want to know is what wireless chip is inside. That is all that matters. Anything with Realtek is fairly fine.

Ndiswrapper: Avoid at all costs. 
No ethernet connection = Ubuntu/wireless catch22? Correct. Always has been that way. Nothing to do with Ubuntu. Many third-party drivers can't legally be included in the ISO. You need to install the OS and then 'agree' to third-party ToS.

---

### Post by chili555 on 2013-12-18
> WNDA3100v2I'd rather have my toe chewed off by a sewer rat than have one of those to work on. Have you read any of the hundreds of forum posts, many unsuccessful, about this device? They make your catch 22 problem seem easy. 

If you'd care to troubleshoot either of the others, I'm in.

---

### Post by cazub on 2013-12-19
The WNDA dongle is a leftover from when this was a windows only machine, didn't go out and buy it , so i guess my total is only 50 bucks. None the less without manufacturer linux support i'm left looking up compatability tables online that don't seem to be accurate. DWL131 rev A works, DWL131 rev b forget it. I'm buying from amazon, they don't even list that kind of info.
Also the PC is buried and nowhere near the router. That's why i want a WIRELESS connection. Without the driver support from the manufacturer linux is the only OS that needs a network connection to make a network connection. The only OS where i have to move the hardware to the router in order to get a network connection. Nobody see's an issue here? Ubuntu was founded as the "it just works" distro but the same networking issues are coming up that i was dealing with 8 years ago (fixed with ndiswrapper).

Ok, taking a breather............. right,  i've gota get this working so i'll go get you guys some lsusb data and maybe this can help other people too.

---

### Post by mörgæs on 2013-12-19
> **cazub said:**
> Ubuntu was founded as the "it just works" distro ...

For obvious reasons it can't "just work" without hardware vendors's support. If the they do not provide the source code (or only a semi-good binary code) there's nothing Ubuntu can do about it. 

If you want to discuss this further please open a thread in Ubuntu and Linux Chat.

---

### Post by cazub on 2013-12-19
Ok, got some data and yes morgaes i understand that. 
I wasn't able to get any data from the DWL131 directly, had to crack open the winXP driver .inf , but here goes.

//ASUS N-13
Bus 001 Device 002: ID 0b05:17ab ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter (rev. B1) [Realtek RTL8192CU]

//DWL131 (useless)
Bus 001 Device 003: ID 2001:330d D-Link Corp. 
//read up on the packaging --> DWL 131 B1, firmware 2.0 , chipset?
//From the XP driver .inf that came on disk ---> RTL8192cu   , can't tell if thats just a driver name or a chipset though.

//WNDA3100v2 
Bus 001 Device 005: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]

---

### Post by chili555 on 2013-12-19
> Without the driver support from the manufacturer linux is the only OS that needs a network connection to make a network connection. The only OS where i have to move the hardware to the router in order to get a network connection. Nobody see's an issue here? Ubuntu was founded as the "it just works" distro but the same networking issues are coming up that i was dealing with 8 years ago (fixed with ndiswrapper).I'm not at all sure that's the fault of the OS. First, newer devices with newer features are introduced almost weekly. 802.11B&G aren't good enough any more; we demand 802.11N. Pretty soon now, N won't be satisfactory and we'll all demand AC!

Next, the Linux market just isn't big enough to demand that manufacturers always provide a driver CD with drivers compatible with every kernel from 2.6.oldoldold all the way to 3.15.newnewnew. We are an irritating little flea on the back of Realtek's neck.

Finally, almost all Ubuntuans walk in to the store and buy based on price, then bring it home and demand that it work out of the box or else Linux is retarded. There is about a thread a week here and on askubuntu.com about compatible devices. I got burned and learned my lesson years ago. You haven't lived until you've tried to coax a first generation home powerline network adapter to life in Linux Mandrake 8! A real character-builder!

The driver rtl8192cu exists in Ubuntu 13.10. My first suggestion is 13.10 and this:> 0b05:17ab ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter

---

### Post by squakie on 2013-12-19
> **chili555 said:**
> ....  You haven't lived until you've tried to coax a first generation home powerline network adapter to life in Linux Mandrake 8! A real character-builder!....
Tried that same thing in a different version of Linux (Slackware).  Such a "fun" experience!

---

### Post by squakie on 2013-12-19
OP:  you are not alone.  Many, MANY peopel come here complaining that something works in Windows but not in Linux, so it must be Linuxs' fault.  Hummmm, even on that preloaded ready-made system running Windows there are such things as drivers that are installed.  Ever check the disk that comes with most wireless adapters?  Yep - Windows drivers.  Such devices don't just magically work in Windows either.  Most people just don't see that because they buy a ready-to-go PC with Windows and all the drivers preinstalled.

---

### Post by Bucky Ball on 2013-12-19
> **cazub said:**
> 
Also the PC is buried and nowhere near the router. That's why i want a WIRELESS connection. Without the driver support from the manufacturer linux is the only OS that needs a network connection to make a network connection. The only OS where i have to move the hardware to the router in order to get a network connection. Nobody see's an issue here? Ubuntu was founded as the "it just works" distro but the same networking issues are coming up that i was dealing with 8 years ago (fixed with ndiswrapper).

Totally off target. You should be emailing manufacturers rather than pointing arrows at Ubuntu. Nothing to do with them.

Anyway, one trip to the router with the hardware to set up the wireless and that's it (ever thought of moving the router for a half hour?), but you are in good hands with chilli so good luck. ;)

---

### Post by cazub on 2013-12-19
> **chili555 said:**
> You haven't lived until you've tried to coax a first generation home powerline network adapter to life in Linux Mandrake 8! A real character-builder!:
boy that does sound awful. So i'm really only in wifi purgatory. None the less if the driver exists in 13.10 whats going on? How can i check the driver that's being used now?

---

### Post by Bucky Ball on 2013-12-20
```
sudo lshw -C network

```
... will tell you everything you want to know. Down the bottom of that readout you'll find the driver currently being used, among other things.

---

### Post by squakie on 2013-12-22
> **cazub said:**
> .... The only OS where i have to move the hardware to the router in order to get a network connection. Nobody see's an issue here? Ubuntu was founded as the "it just works" distro but the same networking issues are coming up that i was dealing with 8 years ago (fixed with ndiswrapper).


So not true......install Windows from scratch and you'll find you need a driver before the wireless will ever work there as well.  If the manufacturer provided one on a disk you are lucky - otherwise you would need the network to get the drivers there as well.  It's not magic in Windows, and it's not magic in Ubuntu (or any other OS) - you have to have a driver.  Comparing things now to 8 years ago and using ndiswrapper is frankly a little ignorant (that's unknowing, by the way, not an insult or attack) of the current state of Ubuntu.  There are literally thousands of old posts left out on the net from a time when using ndiswrapper and/or compiling the driver was needed, but those posts are way outdated and should never be just followed now.  This messes up a lot of people who come to Ubuntu and try so hard to get things working - when in fact what they are reading and trying are useless now.  Those things are nothing but a source of frustration.

Chili555 is a fantastic resource on all of this - extremely knowledgable and experienced.  I would follow what he says - so if he asks for information I would do my best to just provide it.  I anyone can this woring for you it is him (at least, I alwasys assumed it was a "he" ;).  

You have learned a big lesson at your own expense - there is no need to spend that much cash trying to find something that will work and being frustrated.  Others can tell you theirs, I have already mentioned mine - at $12.99 - that DOES work out of the box.  My adapters have been the same make/model for a number of years and a number of releases of Ubuntu for just that reason.

---

