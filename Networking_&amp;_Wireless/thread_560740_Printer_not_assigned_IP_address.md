---
title: "Printer not assigned IP address"
date: 2007-09-26
forum: Networking &amp; Wireless
---

### Post by josesanders on 2007-09-26
I am trying to set up an old HP laserjet printer as a network printer.  I plugged the network cable directly into my Netgear router, and the light on the router goes on, but for some reason, the router doesn't seem to be assigning it an ip address.  I've never tried setting up a printer in this way, and I don't know for sure that the network card on the printer works, but I know the printer itself works when connected to a PC directly.  Does anyone have any ideas?

Thanks

---

### Post by helgman on 2007-09-27
Maybe the printer has a default static IP-address?

Maybe your router don't have any more IP-addresses to lease?

Maybe [HP](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=bpj02326) can give you some hints?

If not try Google and search for something like "hp laserjet default ip".

If none of the above works then make a new post with the full printer name etc so that someone can help you research the specific printer.

Regards,
Helgman

---

### Post by Old *ix Geek on 2007-09-27
> **josesanders said:**
> I am trying to set up an old HP laserjet printer as a network printer.This should be pretty straightforward.
>   I plugged the network cable directly into my Netgear router
...
I know the printer itself works when connected to a PC directly.Then why not do this by connecting it to a computer that's on the network?
> Does anyone have any ideas?See above ^ .  :)

I've never set up a network printer by connecting it to a router and using its IP address.  This is how I always do it:

. connect the printer to one of the networked computers
. on that computer, make the printer shareable over the network
. on the other computers, 'add a printer' and choose 'network printer'
. depending on how your network is set up, you'll have to choose the appropriate method of connecting; on mine, I use Samba (even when no windoze boxes are present, because it's easy and reliable)
. then just step through the 'add a printer' wizard's pages

In the wizard, you should see the networked printer, but if you don't you can manually fill in the info (such as workgroup name, printer name, etc.).  Once you get to the page with all the printer brands and models listed, you can either locate your HP's model and set it up to use its drivers, etc., or you may be able to use the 'raw printer' choice.  That's what I did with my new HP F4100, and it works like a charm from every PC that prints to it.

---

### Post by josesanders on 2007-09-27
Thank you for the suggestions.  The printer is an HP Laserjet 4 Plus.  The first thing that I tried was connecting it to a computer on the network and sharing it using Samba, but I need to be able to share it with my girlfriend's laptop running Windows, and I was never able to get it to work.

I think that the answer is probably in what was suggested by helgman, but I tried, and was unable to get it to accept an IP address, either from the router which is acting as a DHCP server, or by manually entering one that I know is not taken.

Maybe I'll have more luck going back to trying to share it with Samba?

Thanks

---

### Post by Old *ix Geek on 2007-09-27
> The first thing that I tried was connecting it to a computer on the network and sharing it using Samba, but I need to be able to share it with my girlfriend's laptop running Windows, and I was never able to get it to work.Hmmmm...this should work.  :confused:  Do you recall what you tried and what happened as a result?  Keep in mind that Samba exists in order to provide connectivity with windoze machines, so your girlfriend's laptop should be able to access the printer.
> Maybe I'll have more luck going back to trying to share it with Samba?That's what I would try, but like I said this is how I always do it and really can't speak to any other methods.  But, really, for me it's always been extremely straightforward.  I've even had some bizarre instances of smoothly and quickly getting Linux boxes printing on printers attached to windoze boxes, while the windoze boxes THEMSELVES couldn't print to their own printers. :shock:

If you can recall what you tried, and what resulted, I'm sure there'll be help coming your way.  Maybe you just left out a step, such as creating a Samba username and password, that can be easily fixed.

---

