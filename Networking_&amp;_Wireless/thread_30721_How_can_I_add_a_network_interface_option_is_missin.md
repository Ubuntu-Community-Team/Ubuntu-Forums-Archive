---
title: "How can I add a network interface? option is missing."
date: 2005-04-29
forum: Networking &amp; Wireless
---

### Post by joeLB on 2005-04-29
I installed Ubuntu on my desktop computer, thus gnome is my desktop for 
the time being.  I have a pci wireless card I'm trying to install. 
There's no linux driver available, so I did what was reccommended and 
installed ndiswrapper.  Now I have to add my wireless card as a network 
interface.  However, when I go to system > admin > network and I'm 
presented with my network interfaces (ethernet and modem), there's no 
way for me to add a network interface, even though online instructions 
said their would be and the documentation on my computer for this app 
(network-admin I believe) has a picture that shows an "Add" button. 
When I did the install, I chose not to set up the network since I didn't 
have a connection at the time, is this why it's like this?  Does any one 
have any ideas how I can add my card as a network interface? thank you.

Gnome is version 2.10

---

### Post by asimon623 on 2005-04-29
As soon as you install the drivers for your card it will show.  Ndiswrapper only allows you to install the drivers...it is not a driver in itself.  what is the model of your card?

---

### Post by joeLB on 2005-04-30
The drivers are installed.  I'm using a motorola wireless pci adaptor, it's actually manufactured by broadcom.  Really, I think the gnome network interfaces frontend seems to be the problem, the "add" and "delete" buttons aren't even there, and my network interfaces that are there cannot be activated or deactivated.

---

### Post by Rob2687 on 2005-04-30
[QUOTE=joeLB]The drivers are installed.  I'm using a motorola wireless pci adaptor, it's actually manufactured by broadcom.  Really, I think the gnome network interfaces frontend seems to be the problem, the "add" and "delete" buttons aren't even there, and my network interfaces that are there cannot be activated or deactivated.[/QUOTE]
 maybe try:

ifup wlan0

---

### Post by joeLB on 2005-04-30
[QUOTE=Rob2687]maybe try:

ifup wlan0[/QUOTE]

ignoring unknown interface wlan0=wlan0

however, iwconfig wlan0 gives me some stats about my card.

---

### Post by the_real_bubba on 2005-06-08
[QUOTE=asimon623]As soon as you install the drivers for your card it will show.  Ndiswrapper only allows you to install the drivers...it is not a driver in itself.  what is the model of your card?[/QUOTE]

UGH!  So I have to deduce what packages to install by hand, then once I've installed it, I can go and click on the GUI thing...   That's kind of silly.  

I went to go install the ndiswrapper, and synaptic tells me I have to install the kernel module too, but I can't find anything named "kernel-ndiswrapper" so I have no idea what I'm supposed to install.  That's nothing compared to the problem I forsee in finding the correct driver.

What would be great is a GUI that _helps_ install...

---

### Post by az on 2005-06-08
[http://test.wiki.ubuntu.com/forum/hardware/ndiswrapper](http://test.wiki.ubuntu.com/forum/hardware/ndiswrapper)

The kernel module is already installed.  You just have to load it.  See the link.

---

