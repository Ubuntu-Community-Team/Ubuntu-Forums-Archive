---
title: "Got a shot to set up my first OSS network (mostly), but need some advice please."
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by w1z4rd on 2008-04-23
Hi,

I am so really really excited about this. I have my first chance to setup a network for a client where all the workstations can be linux (if this works out). 

Let me explain whats need to be done:

There is going to be a Microsoft Windows Terminal server on the network. This server will be running an accounting business application called PASTEL. PASTEL will really only run on Windows, but this is fine, because all the clients are going to remote desktop into the terminal server to use PASTEL.

The Windows server will also be running active directory.

What my boss wants to happen is the following:

All the workstations must be able to RDP into the terminal server. One or more of the ubuntu workstations are going to have printers attached to them.

These ubuntu workstations with printers need to be able to share those printers on the network so that the terminal server is able to print to those machines. 

Say for instance I am Ubuntu workstation 1, and I have a printer attached to my PC. I RDP into the MS terminal server, and then want to print what I have being doing on PASTEL out to my local printer. The terminal server must be able to see the share of my printer on the network and be able to print to it.

The same with all the other workstations.

Now my questions are... do you see any hassles with this, and is it easy to share those printers to the windows terminal server and so on?

This is a really great opportunity to get a whole company onto OSS desktops! I dont want to mess it up.

Look forward to your replies.

---

### Post by dmizer on 2008-04-23
ubuntu comes with RDP client support, "out of the box" as they say.

it's called terminal server client.  there are other possibilities, but this is one i know of, and i know how that it works well.

regarding printing.  i think your biggest hurdle will simply be finding a printer that actually works well in linux.  once you've done that, then you should have no problem sharing the printer to your windows rdp server.  take a look here for supported printers: [http://cups.org/ppd.php](http://cups.org/ppd.php) and here for how to set up each client for printer sharing: [https://help.ubuntu.com/community/PrintingCupsWebInterface?](https://help.ubuntu.com/community/PrintingCupsWebInterface?) and [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu?](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu?)

problem i see would be potential multiple logon's to the windows rdp server.  could slow the rdp machine (and/or your network) to a crawl.  you might do some serious thinking about setting up a virtual machine install of windows on a linux host.  that way, you could transport (and copy) the server to any other computer, or host it centrally.  more information here: [http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)

could also think about setting up a local im system via something like irc or jabber.  the clients could use the system to quickly aleart others in the office that they are using the rdp server.

active directory might be something of a challenge.  i've never had an occasion to work through it, so i don't know where to point you.

might also dig through some of the links in my sig for file sharing solutions too.

---

### Post by w1z4rd on 2008-04-23
> **dmizer said:**
> ubuntu comes with RDP client support, "out of the box" as they say.

it's called terminal server client.  there are other possibilities, but this is one i know of, and i know how that it works well.

regarding printing.  i think your biggest hurdle will simply be finding a printer that actually works well in linux.  once you've done that, then you should have no problem sharing the printer to your windows rdp server.  take a look here for supported printers: [http://cups.org/ppd.php](http://cups.org/ppd.php) and here for how to set up each client for printer sharing: [https://help.ubuntu.com/community/PrintingCupsWebInterface?](https://help.ubuntu.com/community/PrintingCupsWebInterface?) and [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu?](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu?)

problem i see would be potential multiple logon's to the windows rdp server.  could slow the rdp machine (and/or your network) to a crawl.  you might do some serious thinking about setting up a virtual machine install of windows on a linux host.  that way, you could transport (and copy) the server to any other computer, or host it centrally.  more information here: [http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)

could also think about setting up a local im system via something like irc or jabber.  the clients could use the system to quickly aleart others in the office that they are using the rdp server.

active directory might be something of a challenge.  i've never had an occasion to work through it, so i don't know where to point you.

might also dig through some of the links in my sig for file sharing solutions too.

Thanks.

Though I do need to find out if I am implimenting this on an existing network and its hardware (such as printers) or if I get new hardware to play with.

Really hope I can choose the printers.

Thanks again for the information, its really helpful.

(I see Ubuntu 8 comes with added AD support!... just in time)

I have being using this desktop now for a couple of years, and I really think its ready for networks like the one I just described.

So far the application I have the largest amount of issues trying to find a good solution for is Microsoft Access :(  but the giant steps linux is making as a Desktop makes being in IT fun again.

---

### Post by w1z4rd on 2008-04-23
I just found out the printer is an epson fx80... this is bad news, because I could not find it on that cups link :(

---

### Post by DrCoolSanta on 2008-04-23
I doesn't even seem like that the printer comes with drivers for this printer anyway . . . Ask your boss to rather have the printers attached to the Windows machine rather than linux, this saves you the hassle of even sharing the printer, unless they want it to be available otherwise. The only drawback I can sense is the lack of the ability to have more than one printers, though you can, you can't have them at places far from the server.

I know how clients and boss's can be even when they buy the incompatible hardware. Hope yours is not like that.

---

### Post by w1z4rd on 2008-04-23
> **DrCoolSanta said:**
> I doesn't even seem like that the printer comes with drivers for this printer anyway . . . Ask your boss to rather have the printers attached to the Windows machine rather than linux, this saves you the hassle of even sharing the printer, unless they want it to be available otherwise. The only drawback I can sense is the lack of the ability to have more than one printers, though you can, you can't have them at places far from the server.

I know how clients and boss's can be even when they buy the incompatible hardware. Hope yours is not like that.

So you think the epson fx80 will work out the box? Also, I think the idea is that each user will be able to login, and be able to a different printer depending on the whats being worked on, (ie, sales order, invoices, jouranls, statement and so on).

I think there may be a couple of other printers on the network as well. But I was told for some reason the fx80 is important.

---

### Post by dmizer on 2008-04-23
> **w1z4rd said:**
> I just found out the printer is an epson fx80... this is bad news, because I could not find it on that cups link :(

you're kidding right?  this printer: [http://www.tonh.net/museum/epsonfx80.jpg](http://www.tonh.net/museum/epsonfx80.jpg) (note the conspicuous "museum" in the url)

anyway, i can confirm from experience that this printer works fine with ubuntu.

---

### Post by w1z4rd on 2008-04-24
Thank you, hopefully will get everything right.

---

### Post by w1z4rd on 2008-04-24
Hey, got another question.. this one has more to do with RDP. With Windows RDP, you can set it to launch an application (in this case PASTEL) on the terminal server when you RDP into it.

Bascially as the person logs into the terminal server, PASTEL opens. Does ubuntu RDP have anything like this, or anything similar to this?

Thanks in advance!

---

