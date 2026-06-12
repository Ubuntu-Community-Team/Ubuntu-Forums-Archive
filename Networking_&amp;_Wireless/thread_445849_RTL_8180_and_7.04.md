---
title: "RTL 8180 and 7.04"
date: 2007-05-16
forum: Networking &amp; Wireless
---

### Post by Riotron on 2007-05-16
Hi all

I am new to ubuntu, trying to make this card work. I have a Toshiba P10 laptop and the card is PCMCIA

I have used "sudo modprobe -v r818x" to install the modules, the card is found in the device manager, I get the wireless option to configure in the Network manager, but I do not get a connection. Am I missing something?

One thing about the network is that it is an unprotected, so no WEP key is needed. Do I need to configure that?

many thanks in advance, I would be really grateful if someone could help out

---

### Post by the_dark_light on 2007-05-19
This is a frequent problem.  Having an 8180 based card (Linksys WPC11 v4) I can sympathise.

Rather than use the bundled driver (which was disabled because of kernel issues) I opted for Ndiswrapper.

Search for Ndiswrapper on synaptic (there should be 2 packages that you need, I can't remember offhand + I'm on a windows box at the moment, so I can't check)

Download the 818? (you're using the 818x chipset, but I don't know the exact chipset you're trying to use) driver (should be on realteks website)

caveat emptor - there are a versions for various MS operating systems, as far as I'm aware the windows 2000 driver should work

in the archive you download, look for the .INF file.  Run:

ndiswrapper -i some_file.INF

check with:

ndiswrapper -l

which which should report the drive

Next you need to tell ndiswrapper to write the configuration file for modprobe, I think it's:

ndiswrapper -w

but you should check the help file first (ndiswrapper -h , sorry if I'm being patronising)

then you just need to modprobe ndiswrapper.


Be warned, I can't guarentee success.  My hardware is picked up and I can access it through network manager, but it refuses point blank to connect to my network.  It might be an issue on my machine, or I've frakked something up somewhere.

Good luck

---

### Post by konik134 on 2007-05-21
check this may help  its help me   
 [http://ubuntuforums.org/showthread.php?t=442609&highlight=linksys+wpc11+v.4](http://ubuntuforums.org/showthread.php?t=442609&highlight=linksys+wpc11+v.4)

---

