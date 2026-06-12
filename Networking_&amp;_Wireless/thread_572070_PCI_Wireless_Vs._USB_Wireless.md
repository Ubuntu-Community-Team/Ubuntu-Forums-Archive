---
title: "PCI Wireless Vs. USB Wireless"
date: 2007-10-10
forum: Networking &amp; Wireless
---

### Post by lemonseed on 2007-10-10
I'm about to make my first  wireless network in my house to share the high-speed connection off a wireless router. The problem I face is which option I should go for to get wireless on the desktop machines. Should I go with PCI NICs or just get USB wireless devices? Right now I'm not worried about the device taking up a USB slot because I don't really have too many USB devices to begin with (just a camera and ipod). Is either one better than the other in terms of longevity, signal strength, compatibility, and price? Any opinions and suggestions are most welcome.

---

### Post by kvonb on 2007-10-10
The main thing is compatibility.

Make sure it will work before you pay any money!

Try and get the make and model number, then search the forum for it.

That should tell you whether it will work, or if you are in for mass headaches :).

---

### Post by adamos on 2007-10-10
i second that. do your homework before purchasing that. linksys usb adapters are known for linux compatibility .
but i hate wireless setups, especially the main network. i run wired network for my 5 pcs in the house. wireless is unstable. period.

---

### Post by SactoBob on 2007-10-11
IMO the best performing and most trouble free and compatible solution for a Linux (or any other OS) home network is neither PCI nor USB, but a wireless bridge.  You should at least consider this option.
[http://ubuntuforums.org/showthread.php?t=387871](http://ubuntuforums.org/showthread.php?t=387871)
Bob

---

### Post by lemonseed on 2007-10-11
Thanks Sacto. This seems like an even easier solution since the bridge costs just as much as either a PCI card or a USB device, and it can be shared.

/salute

---

### Post by kryliss on 2007-10-12
I prefer USB adapters myself. The main reason is that you can change the location of where your usb device is at. If you get bad reception with a PCI card you would have to move your whole computer, with a USB device you can put it on a USB extension cable and set it where ever you need it. And yes linksys works quite well under linux.

My 2 cents.

---

### Post by lemonseed on 2007-10-17
Update:

Following SactoBob's suggestion and doing some research, I purchased 2 LinkSys Wireless-G Broadband Routers ( Model WRT54GL it's already Linux-based and doesn't discourage third-party firmware, [http://www.newegg.com/Product/Product.aspx?Item=N82E16833124190](http://www.newegg.com/Product/Product.aspx?Item=N82E16833124190) ). First thing I did was flash them with DD-WRT v23 SP2. It actually took me longer to download the DD-WRT file than it did to flash the router. It was super easy. Then followed this guide, [http://www.dd-wrt.com/wiki/index.php/Wireless_Bridge](http://www.dd-wrt.com/wiki/index.php/Wireless_Bridge) , and set the second router as a wireless bridge in the other room for those computers.

Everything works perfectly!! Took me about an hour to get it all flashed, configured, and running. I probably could've done it faster because it was a truly painless process, but I took my time since it was my first wireless setup.

Many thanks to SactoBob for saving me much time and money for this awesome solution. Hopefully it can help anyone else out there having this same dilemna.

A very good article that sold me on this idea can be found at [http://lifehacker.com/software/router/hack-attack-turn-your-60-router-into-a-600-router-178132.php](http://lifehacker.com/software/router/hack-attack-turn-your-60-router-into-a-600-router-178132.php)

---

### Post by SactoBob on 2007-10-22
You're welcome, and thanks for the link.  Yet another way to skin the cat.  It's hard to beat a bridge for performance or the money in a home network.  I'm lazy and prefer just buying a unit that is already set up as a bridge like the Buffalo Ethernet Converter.  

The great thing is you will never have to worry about drivers, kernels, updates, new OS etc.  I think more people would be using bridges if they knew about them.  Most people seem to think, as you did, that your choice is between PCI and USB.
Bob

---

