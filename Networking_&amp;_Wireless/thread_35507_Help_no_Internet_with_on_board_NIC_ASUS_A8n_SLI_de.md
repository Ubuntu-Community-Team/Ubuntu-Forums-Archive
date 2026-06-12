---
title: "Help no Internet with on board NIC ASUS A8n SLI deluxe"
date: 2005-05-19
forum: Networking &amp; Wireless
---

### Post by paTt3rN R3CoGnItIon on 2005-05-19
I'm the proud owner of an ASUS A8N SLI Deluxe mobo. I see that several people on this board have reported that everything works in 5.04 except for maybe nvidia or soundblaster 24 bit.

But when I booted the live distro of 5.04 for AMD64 I couldn't connect to the Internet via my router/switch. So my question is whether anyone can offer tips/guidance on getting Ubuntu to recognise the proprietary ethernet NIC in this mobo?

If not I may have to just pop in a standard, generic PCI NIC card (this is what I have previously had to resort to with other LINUX distros on other mobos with integrated ethernet/NICs.) But if possible I'd like to avoid wasting the onboard ethernet/NIC and unnecessarily taking up a PCI slot.

Thanks for any help anyone can provide!

P.S. I do plan to install the HDD based version but I wanted to sort this issue out with the Live version first in case it's easier to set things up correctly during the initial install.

---

### Post by deception on 2005-05-19
Take a look around System > Administration > Networking, and see if the card is activated, or even showing.

---

### Post by paTt3rN R3CoGnItIon on 2005-05-25
I figured out the problem. But I wanted to follow up in order to thank you for replying to my post and also in case another newb such as myself does a search for the same issue and finds the following useful:

I had to go to the "network settings" dialog then "Interface Properties", tick the box that says "This device is configured" then select DHCP configuration and click on "Activate". My DSL now works like a charm :-)

The only remaining issue is that I can't set my screen resolution to 1280 x 1024 (i.e. above 1024 x 780 or whatever it is) so the fonts look giant on my 19 inch LCD. (The drop down menu in the screen settings dialog is limited to three choices (1024 x 780, 800 x 600 and 600 x 400 or something ridiculously small which I can't remember). The area where you can type in values manually doesn't seem to have any effect on the display :-?

I have a feeling, however, that this may be issue specific to the live version of Ubuntu and that the HDD install will allow me to have high screen resolutions.

I'm optimistic because unlike some people who have posted elsewhere on this board I had Ubuntu immediately recognise my on-board sound (my ASUS A8n SLI Deluxe has on board sound which is kind of new - Marvell Yukon or something).

---

