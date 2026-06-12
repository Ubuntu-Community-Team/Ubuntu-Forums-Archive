---
title: "ndiswrapper driver problem - &quot;no vendor&quot;"
date: 2005-11-22
forum: Networking &amp; Wireless
---

### Post by bribera on 2005-11-22
Hello-

I'm attempting to install a Proxim Orinoco 802.11b Silver card in my laptop.

My first attempt followed this HOWTO: [http://questier.com/howto.html](http://questier.com/howto.html)
That's the exact card I have, and I've successfully followed those steps on a different laptop running Slackware.  For whatever reason, I can't get the installation to succeed under Ubuntu.

So I move to ndiswrapper:
I'm using the drivers from [http://www.agere.com/mobility/wireless_lan_drivers.html](http://www.agere.com/mobility/wireless_lan_drivers.html)
and from the proxim site.  Whenever I attempt to add the drivers under ndiswrapper, it responds "no vendor".

*sudo ndiswrapper -i <inf file>* doesn't add the driver.  Anyone have ideas?

---

### Post by az on 2005-11-23
Out of the box, your card should be detected on installation, or when you go to the networking tool.  You do not need to compile anything.  Woking linux drivers are included in Ubuntu.

When you plug your card it, does the light come on?  How old is your laptop?

Look in the log tool and post what changes in /var/log/messages when you plug your ard in for the first time.

---

### Post by bribera on 2005-11-23
[QUOTE=azz]Out of the box, your card should be detected on installation, or when you go to the networking tool.  You do not need to compile anything.  Woking linux drivers are included in Ubuntu.[/QUOTE]
Well, that's not the case.  Neither the card nor the built in ethernet were detected for me (I had to either disable apci or build the 2.6.14.2 kernel to get the ethernet to work).

[QUOTE=azz]When you plug your card it, does the light come on?  How old is your laptop?[/QUOTE]
No lights whatsoever.  It's an IBM Thinkpad A21m (see [http://thinkwiki.org/wiki/Category:A21m](http://thinkwiki.org/wiki/Category:A21m))

[QUOTE=azz]Look in the log tool and post what changes in /var/log/messages when you plug your ard in for the first time.[/QUOTE]
Let's see... I open up the System Log gui, insert the card, and ... it crashes gnome-system-log.  When I re-open, I see nothing helpful or new in the messages log.

---

### Post by Lambert on 2005-11-23
The site that you provided shows that card with two different ids

 	Model 8241-WD
 	Proxim Corporation 8420-WD,

The 8420-wd is supported by the wavelan driver which is a native driver in breezy.

  802.11b  8420-WD   
 PCMCIA  Orinoco  Wavelan  

So suggestion 

1. Run the command sudo lshw -businfo. Find the device in this short list. NOtice it's class then sudo lshw -C network. Post that output here. What I'm looking for is the line configuration: for your device to see if there is a section that says driver=XXX

Next suggestion for ndiswrapper

2. Run lspci and notice the first colum's numbers. Should be in this format 0000:00:0c.0 Then run lspci -n Find the line that matches and then notice what the PCI ID is of the device. Should be in this format. 104c:8400

Then go [here]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")

Do a search on that page for the PCI ID It may not match up to the exact model of your card but it matches up with the chipset. There will be a download link there for a driver. Download that driver and make sure you unzip both the .inf and .sys drivers into a directory and install the driver from that directory.

---

