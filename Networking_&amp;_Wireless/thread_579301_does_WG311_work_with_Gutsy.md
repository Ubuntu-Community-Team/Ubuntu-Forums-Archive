---
title: "does WG311 work with Gutsy?"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by mikeliketrike on 2007-10-18
I previously had Feisty installed and because of my Linux newbness and lack of patience after 2 months of trying, wasn't able to get my  WG311 v2 wireless PCI card to work.  I decided then that I was going to wait for 7.10 to come out and see what I might be able to accomplish.  I've been lurking and [searching]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear") for a couple weeks and haven't really found anything too promising for my situation.  

Does it work out of the box yet?  What will I have to do to make it work?  I really want to stop using $MS (again), but a stable, WAP-ed, wireless connection is a deal breaker for me.

---

### Post by marc_hav on 2007-10-18
Yes it does.

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear)

---

### Post by mikeliketrike on 2007-10-18
I know about that page, in fact, I linked to it in my original post.  The entry for WG311 v2 (PCI) said it worked in Breezy, but I couldn't get it to work with Feisty a couple months ago.  So I'm seeing if anyone's had any experiences with Gutsy or Feisty to get it working.  If so, how they did it.

---

### Post by LeJediGris on 2007-10-18
Yes it works : Gutsy+WG311v2 (ACX 111)

But : ndiswrapper +  wicd !!, don't forget to blacklist the acx native driver.

---

### Post by mikeliketrike on 2007-10-18
> **LeJediGris said:**
> But : ndiswrapper +  wicd !!, don't forget to blacklist the acx native driver.


What's that mean?

---

### Post by LeJediGris on 2007-10-19
You have to follow the ndiswrapper install of your XP drivers for the WG311v2... first locate the drivers (XP for me) on the installation CD,
After that ==> copying the driver  on your Ubuntu desk.
And ..
 **ndiswrapper -i wg311v2.inf  **# install the driver, don't forget to copy ALL of the files included on the CD's XP folder, for example don't forget the .sys !!
**ndiswrapper -m **# links for module
**modprobe ndiswrapper**

 blacklist of native driver : **gedit /etc/modprobe.d/blacklist **and add a line with **blacklist acx**

To be sure the 
**ndiswrapper -l** # command gives you the result as : Driver wg311v2.inf installed, hardware XXX:XXXX present

So the first phase is now finished, the second one is around wicd. Wicd replace network-manager and is (for me) more useful.

1) Removing n-m

[B]killall nm-applet
apt-get remove network-manager-gnome[/B]

2) Obtaining wicd :

See [http://wicd.sourceforge.net]("http://wicd.sourceforge.net")

Download the packet,

install the packet with **dpkg -i**

The packet will install an application named "wicd" (what a surprise !!) on the applications==>internet menu on your desktop (i'm not sure cause i use a french version :) )

and after you have a nice interface to install wireless networks with wep, wpa and so one !!

For me it takes 5 minutes to work !! Config is Asus A7N8X-X with Sempron 2800+, 1,5 Go DDR, Maxtor 80G for Ubuntu, WG311v2 (not v3 !!)

Hope this help :popcorn:

---

