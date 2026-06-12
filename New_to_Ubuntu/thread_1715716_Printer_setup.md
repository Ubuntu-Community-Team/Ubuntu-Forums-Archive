---
title: "Printer setup"
date: 2011-03-27
forum: New to Ubuntu
---

### Post by PZJM on 2011-03-27
Hey folks, I just bought a canon pixma mg5220 all in one printer.  I was luckily enough to find the drivers for this printer thanks to this forum.  However, I'm not sure about my setup.  I bought a wireless printer because I would like to be able to print from my laptop.  However, our main computer is a desktop also running Ubuntu 10.10.  I have a Comcast cable modem and a NetGear Wireless Router.  The desktop computer is connected to the router via an ethernet cable.  I originally set up the printer/scanner using a usb connection but I'm not sure if this will allow me to connect to the printer via my laptop.

I guess what I'm confused on is the whole wireless thing.  If I configure the printer as wireless then how can I get my desktop to connect to it?  Would I have to somehow configure this in the router?  My desktop computer does not have a wireless adapter but is directly plugged into my wireless router.

My ideal configuration would be to have the printer accessible both from my desktop computer and my laptop (via wireless).

Any help would be greatly appreciated.

---

### Post by walt.smith1960 on 2011-03-27
I'm doing what you want to do. I'm using HP & Brother and am not familiar with Canon.  I have one printer which supports wired but not wireless networking plugged into one of the 4 ports on the wireless router.  Another Brother printer is connected via wireless networking.  My setup works quite well but like I said I can't help with Canon software or setup.  The easiest is to simply go to System -> Adminstration -> Printing.  If you've installed the printer software, right click the printer icon, click on "properties" and see what the device URI and Make and Model say.  Both fields have change buttons.  I'd click either change button and see what options are offered.  If you don't like what you see there are cancel buttons.

If you haven't installed the printer software, you could do System -> Adminstration -> Printing then click on the "add" button.  Click on "network printer" then "find network printer".  Wait a minute or two and see what shows up.

---

### Post by gordintoronto on 2011-03-27
If you have the printer set up as wireless, the desktop won't be able to use it. I think you have it plugged into the Desktop, by USB cable? In that case, the desktop must "share" the printer, and the desktop must be turned on any time any computer wants to print.

The other option is to connect it to the router by Ethernet cable. Then anyone can use it any time. You might find that the printer needs to be set up to have a static IP address, and the printer manual should help you with this.

---

### Post by walt.smith1960 on 2011-03-27
> **gordintoronto said:**
> If you have the printer set up as wireless, the desktop won't be able to use it. I think you have it plugged into the Desktop, by USB cable? In that case, the desktop must "share" the printer, and the desktop must be turned on any time any computer wants to print.

The other option is to connect it to the router by Ethernet cable. Then anyone can use it any time. You might find that the printer needs to be set up to have a static IP address, and the printer manual should help you with this.

As long as the network enabled printer is "seen" by the the router it should work, whether the network connection between the various devices is wired or wireless AFAIK. Having any USB connections would complicate needlessly, wouldn't it?  I have my MFDs  with static I.P.s because of the configuration I'm using.  Any PC can talk to the router, the router can talk to the printers.  I do recall someone-not me-had to disable bidirectional support in order for the printer to work.  I don't recall any details of that situation, just that the person had to disable bidirectional support.

---

### Post by PZJM on 2011-03-27
Thanks for the advice.  I thought I would not be able to access the printer unless it was plugged it to my desktop.  However, I now have to make it accessible for my wireless laptop.

I will try your advice "gordintoronto" and thanks for the advice "walt.smith1960".  Looks like I will need to uninstall the driver and then reinstall it after I connected the printer to the router.

So, it sounds like I need to connect the printer to my wireless router?  I'm not sure if my printer contains an ethernet port?

Thanks for all the advice...

---

### Post by gordintoronto on 2011-03-28
Actually, Walt was right about using it with wireless. I had a brain cramp.

---

