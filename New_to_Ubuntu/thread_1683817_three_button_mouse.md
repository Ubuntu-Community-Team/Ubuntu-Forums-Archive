---
title: "three button mouse"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by aschweig on 2011-02-08
I have a Microsoft Wireless keyboard/mouse combo with Ubuntu 10.10, I think it's a "Wireless Laser Mouse 6000".  I have it connected to my laptop.

The keyboard and mouse work well.  However,  the scroll-where middle click is hard to use.  I was wondering if there was a way to additionally emulate the 3rd button behavior?

I saw that "Pointing Devices" (or gpointing) has an option like this, however, when I install Pointing Devices, I only see my trackpad listed.  

Can I simply modify xorg.conf and set "Emulate3Buttons" to "yes"?  

"xinput list" shows the following:

[FONT="Courier New"][SIZE="2"]&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Microsft Microsoft Wireless Desktop Receiver 3.1	id=11	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; USB Camera                              	id=9	[slave  keyboard (3)]
    &#8627; Microsft Microsoft Wireless Desktop Receiver 3.1	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
[/SIZE][/FONT]

---

