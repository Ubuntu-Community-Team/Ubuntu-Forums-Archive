---
title: "Brand New to Ubuntu-wireless connection"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by Alexhousek on 2009-09-20
I'm sorry if this is a newbie question, but I'm brand new to Ubuntu.  I am very Windows savvy, but don't know much about Ubuntu.

I just installed Ubuntu.  My biggest issue is that I cannot connect via my wireless card to my DSL router.  I've tried several tutorials and sites, but I am still having difficulty connecting to my network or the internet.  

I've tried lshw and I see my wireless nic card listed.  I added a connection under network tools and it tries to connect.  I entered my SSID and WEP key and it acts like it wants to connects but never does.

Can you point me to a link in the forums or a url that will assist me with connecting to the internet?  Once I've got that done, I feel like I can start enjoying Ubuntu and learning much more about it.

Thank you.

---

### Post by AMDBuntu on 2009-09-21
Usually it's very easy to connect to a wireless network with Ubuntu. From the desktop, in the upper right corner there's an network icon you click on. If your wifi card is working, it should show you a list of all available wifi networks in the area. If you see your network, you should be able to connect after selecting it and entering the WEP key. If it doesn't connect, try going to system>administration>hardware drivers and see if Ubuntu is offering you another driver alternative.

In my case, I have a wifi card that looks great until you connect and then it's a no go. Under hardware drivers, Ubuntu, offers me the mad wifi driver. Which works great...

Hope it's as simple as this... Good luck...

Eventually, when you get on-line go to the menu system>administration>software sources to the third party tab and check the partner's box. This will allow you to get non-free (proprietary) software. When you go back to "hardware drivers" it will search for the right driver - to include your video card.

---

### Post by chicoharv on 2009-09-21
You may have to go to admin,synaptic packages and install ndiswrapper and if you have a built in broadcom card you need to install b43fwcutter. Install the associated packages with ndiswrapper also

---

### Post by AMDBuntu on 2009-09-21
If there's no Linux driver available:

[http://en.wikipedia.org/wiki/NDISwrapper](http://en.wikipedia.org/wiki/NDISwrapper)

---

### Post by HereInOz on 2009-09-21
If your wireless adaptor uses a Broadcom chip, you are going to have some fumbling about to do, for the simple reason that Broadcom has not, to my knowledge, released Linux drivers for their range of chips.

If the wireless adaptor is changeable, like in a desktop machine, and it has a Broadcom chip, then consider swapping it for something which has an Atheros or Ralink chipset.  These are recognised immediately by Ubuntu, because these manufacturers have made their driver requirements known to the Linux community, and drivers have been written for them.

Hope this helps.

---

### Post by Alexhousek on 2009-09-22
I am using a Qwest 2701HG-D DSL modem and my computer has a D-Link wireless NIC card (DWL-520+) in it.

I found these 2 pages in relation to my wireless NIC:

[http://sourceforge.net/apps/mediawik...ink_DWL-520%2B](http://sourceforge.net/apps/mediawik...ink_DWL-520%2B)

[http://www.houseofcraig.net/acx100_howto.php](http://www.houseofcraig.net/acx100_howto.php)

I am having a hard time figuring out what to do from here? Any suggestions?

(Sorry to be such a pest.....) 

It sounds like I might need Ndiswrapper as mentioned above?

---

### Post by anewguy on 2009-09-22
Looks like it may be a Atheros chipset, but to be sure please do the following and post the output back here:

open a terminal window (applications/accessories/terminal)

type:

lspci <press enter>

copy/paste what shows there to a reply here.

type;

lsusb <press enter>

copy/paste what shows there to the same reply here.


With that information we can hopefully identify the chipset and therefore help try to locate a driver, then give you instructions.


EDIT:  <Added 9/22/09 5:32pm central time>  It looks like these adapters can also have a TI chipset.  A scan on the net shows different versions of a driver for this same device.  Please post the output as per above and we can go from there.  It may very well be that ndiswrapper is needed.  If you already have a Windows driver for the device, then we can use ndiswrapper to get you going.  Post back what you can and what you'd like to try and we can go from there.

dave 
Dave :)

---

