---
title: "Dlink DIR-655 w/sharepoint Printer Sharing"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by gspat on 2008-11-05
Hi!

I have a Dlink DIR-655 router and was trying to set it up so my printer is connected to the router and shared to my home network.

The problem seems to be that it needs some sort of specialized device driver to be utilized. (NET USB)

Has anyone tried/been successful in getting the printer to be shared by this router?

---

### Post by pedro_orange on 2008-11-05
Might be an idea to mention the printer.

Check out the Ubuntu community documentation. it's great.
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by gspat on 2008-11-06
Well, the printer is an HP 5150, this is connected to the DLink DIR-655 router... I don't believe the printer name is important (yet!), since I can't even see it across the network.

When I go into the router setup, I find this:

```
Use this section to configure your USB port. There are several configurations to choose from: Network USB, 3G USB Adapter and WCN Configuration.

Note : If using the Network USB option, users will need to install the Network USB Utility into their computers to share the USB device through the router.
```

Searching around the net, I found that the router is using something called "NET USB" to share out the printer... 

Is there an equivalent linux utility for this? The D-Link site is not very helpful.

I'll try to use the utility under wine to see if it will work, but I would rather have a linux only solution even if it does.

---

### Post by gspat on 2008-11-06
Surprise, surprise, surprise...

The utility will not even install under wine...

Sigh...

---

### Post by pedro_orange on 2008-11-13
[https://wiki.kubuntu.org/HardwareSupportComponentsPrintersHp](https://wiki.kubuntu.org/HardwareSupportComponentsPrintersHp)

Says the HP 5150 works out of the box.

How are you setting this up? Just plug the printer into the router. Go onto the router management and give it a static IP address. Then just add a network printer to that IP address in Ubuntu. Easy.

Using an Ethernet cable is your simplest option, and they cost like a fiver.

---

### Post by gspat on 2008-11-18
I've tried and tried, but to no avail..

There is no printer setup section in the router!

guess i'll just continue to use the printer from one of my file-servers.

---

### Post by qaissi on 2009-01-07
Interesting how the main point has been missed here.  

The problem is not setting up the printer the problem is getting Ubuntu to realize that there is a USB port in the router to which various USB devices can be attached.

In a windows environment using the Shareport software available on the DLink web site the USB port is available.  From there you can attach a printer or any mass storage device using USB so that it is available to one computer at a time to any computer connected to the router.

So the point is not getting a particular printer installed.  The point is to get Ubuntu to see that the port exists.

Wish I knew the answer - I am looking into that one now.

---

### Post by kalleb on 2009-01-12
I have the same issue but with D-link router Dir-855. If there is a way to enable that USB port in Linux I would be the first one to do it! Any news?

---

### Post by jawinterton on 2009-01-24
> **gspat said:**
> Hi!

I have a Dlink DIR-655 router and was trying to set it up so my printer is connected to the router and shared to my home network.

The problem seems to be that it needs some sort of specialized device driver to be utilized. (NET USB)

Has anyone tried/been successful in getting the printer to be shared by this router?

I think you mean Shareport not Sharepoint.  I've done a bit of hunting around myself for any solutions to share the printer or an external over the router but haven't found anything yet.

---

### Post by kalleb on 2009-01-24
I was thinking of hooking up an external hd and share it on my network, but then I realized it is an 1.0 USB port which won't give me much speed so I stopped bothering. Also I would be amazed if D-Link would ever work something out for Linux.

---

### Post by marksken on 2009-06-30
Any luck to get sharing working under ubuntu

---

### Post by jack24 on 2009-07-23
I've been trying to get a Dir-628 USB port working through a Ubuntu computer with no luck.  It's frustrating that D-Link will put out a version for Macs, but not Linux.  I'm sure there are as many Linux users as Mac users.  I sent them an email asking why they don't support Linux and if they knew of any way to make it work.  Hope it sends a signal that we're out here.

If I get any info, I'll post it here.

---

### Post by shadowjack1 on 2009-07-24
I've been running a home network based off of a D-link DIR 655 router for some time now. Curtrently a mixed network, 3 D-link 4 port switches,1 M$ Vista desktop, 1 M$ XP tablet/docked, 2 Ubuntu Jaunty desktops, 1 Ubuntu Jaunty laptop, 1 eeeBuntu netbook and a Windows Home server. The network is spread thru the house and extends out to a detached workshop. Instead of trying to come up with a method of getting the sharepoint printer sharing configured to attach the printer (Brother HL1440) to the USB port on the router I purchased an inexpensive USB print server. The network was ALL Windows at the beginning, been weaning myself off the M$ addiction for a while now. When I started converting machines over to Ubuntu I was amazed at how much simpler it was to configure the network printer on the Ubuntu boxes. The D-link router assigns an IP address to the print server, on the router setup page I had it 'lock' the IP address for the print server, and just enter the IP in the network printer config on the Ubuntu boxes. Works like a champ.

---

### Post by gamez on 2012-06-14
You may want to try [http://ubuntuforums.org/showthread.php?t=2002840]("http://ubuntuforums.org/showthread.php?t=2002840").

g.

---

