---
title: "Wireless PCMCIA - Was working fine..."
date: 2005-07-05
forum: Networking &amp; Wireless
---

### Post by Straker on 2005-07-05
Hello all.  Found so much useful stuff on this forum, I never thought I would have to post, but alas....

I have a Linksys WPC11 (version 2.5) Wireless PCMCIA card which was working fine until I removed it to use it temporarily in another laptop.  I put the card back, and now, Ubuntu (5.0.4) doesn't recogize it as my eth0 interface.

Here are some more details.

"cardctl ident" sees the pcmcia card fine and the "etc/pcmcia/config" entry has the correct manfid which matches the cardctl ident info.

My "etc/network/interfaces" shows the eth0 adapter with all the settings it was using before.  includes "auto eth0"

When the system boots up, however, only the loopback interface is found.  So the eth0 does not even show up in ANY network GUIs or CLIs.  "sudo ifconfig" only shows the loopback (lo).

Is there a setting somewhere or config file I need to modify to "bind" eth0 to my pcmcia card?  Sorry, I really dont get it.  It was working fine but shouldn't Ubuntu display the eth0 if it is in the interfaces file?

Thanks in advance for any help.

---

### Post by Straker on 2005-07-06
bump

---

### Post by bin on 2005-07-07
Hi

Out of interest, does your machine have a built in ethernet port? 

Does iwconfig give back anything?

lspci -v  does it show your card?

Have been down a similar road with a different card but atheros chipset

---

### Post by Straker on 2005-07-09
My Laptop has no built-in or other ethernet ports.

**iwconfig** gives:

lo         no wireless extensions

sit0      no wireless extensions

**lspci -v** does not show the card.

**cardctl ident** gives:

Socket 0:
   product info: "The Linksys Group Inc.", "Instant Wireless Network PC Card", "ISL37300P", "RevA"
   manfid: 0x0274, 0x1612
   function: 6 (network)

Socket 1:
   no product info available

**ifconfig** only shows the lo Loopback

my **/etc/network/interfaces** file shows the eth0 interface.

Believe me, I followed the ubuntu instructions...	

> run "cardctl ident" and add info to /etc/pcmcia/config under wireless network adapters section. Be sure to include manfid and bind to orinoco_cs. Then just reboot and run "gksudo network-admin" in console and configure eth0...works like a champ! 

...the first time and IT WORKED.  I removed the card, and used it elsewhere, put it back in, and now I cant get it to work.

](*,) 

I just ran my network-admin from the console and am getting the following error (could it be the prob?):

** (network-admin:4393): CRITICAL **: gst_xml_element_find_first: assertation 'parent != NULL' failed

Help someone please.  My next step is to buy another card!?!?!?!

---

