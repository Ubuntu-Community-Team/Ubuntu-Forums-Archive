---
title: "Cannot connect 2 internet @ all, using ethernet card"
date: 2005-12-01
forum: Networking &amp; Wireless
---

### Post by Dov on 2005-12-01
G'day all
I'm a fresh and shiny newy to Linux just a couple of days ago, so this is pretty frustrating for me. I've been using an SMC EZ 1211? network card for a while with windows, but when I switched to Ubuntu, it detected the card, installed it and then failed to successfully run it. I am using dhcp? to configure connection. It couldn't even access the internet during setup. Have tried using pppeoconf in terminal, but it times out.
Pretty frustrating as you seem to need internet to do pretty much everything in setting up the system the way you want it.

Thanks in advance, 
Dov

---

### Post by akiro.yamamoto on 2005-12-01
This may seem a silly question...
But have you tried to configure your network with the GUI utility?
Click 
System >> Administration >> Networking
When the dialog comes up...
Highlight your network connection (probably eth0?) and 
Click configure...
I'm no expert but that should be your starting point....
Also post any errors you recieve.... as well as any steps you've tried so everyone can have a better idea of what's going on.
Regards

---

### Post by akiro.yamamoto on 2005-12-01
BTW:
Your ethernet card was detected and installed correctly righ?
You didn't need to use any additional drivers or use the ndiswrapper driver utility to get it to work?

---

### Post by Dov on 2005-12-01
When I checked the card in the system thing it showed up withe the right name and all

---

### Post by Dov on 2005-12-01
Is there a configuration guide for newies anywhere? Cos I can't figure that thing out. Never seen an example of manual config for me to understand it all. Been through there, but just left it to dhcp to do the work.

---

### Post by akiro.yamamoto on 2005-12-01
I was doing a little seaching around and it seems that your card may be supported by the realtek driver for the RTL8139 card :
[http://www.realtek.com.tw/downloads/dlac97-2.aspx?lineid=5&famid=12&series=8&Software=True](http://www.realtek.com.tw/downloads/dlac97-2.aspx?lineid=5&famid=12&series=8&Software=True)
This is from some info I googled as well as from a reference I found on HP's site..
It's possible that although the card was recognised your system simply does not have the drivers for the card.... and therefore pppoecon cannot talk to your card to configure it???
I hope this helps you...

---

### Post by akiro.yamamoto on 2005-12-01
This is the HP reference I found:
[http://www.linux.com/howtos/HP-HOWTO/hp-hardware.shtml](http://www.linux.com/howtos/HP-HOWTO/hp-hardware.shtml)
It lists your card as being supported by the realtek driver....

---

### Post by Dov on 2005-12-01
I had some troubles with drivers at first with Windows as well. Hope that this will work. Should I use the one labelled 'packet driver' or the one labelled 'kernel 2.4+ (Redhat 7 etc)'?

---

### Post by Dov on 2005-12-07
Yep. Have found info to point to this driver. Just wondering, if it's not too silly a question...

How do I install the driver, and is 'packet driver' the one to use?? Does Ubuntu have a Driver Wizard? If not, why not? Surely an end-user such as myself is not expected to know where everything is supposed to go file-wise? AQll the driver installation guides I have found are for specfic drivers and I do not know if the same process will suit mine. Also, how do I delete the old driver?

---

