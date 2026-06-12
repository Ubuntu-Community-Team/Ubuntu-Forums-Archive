---
title: "Video Card problem after upgrade"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by IceyBlack on 2009-04-24
Hi guys i have this VGA 00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) and it works ok in ubuntu 8.04 and 8.10 no need driver or something and now after upgrade to jaunty i cannot nebale desktop effect , how can i activate the driver?Laptop Fujitsu Siemens amilo 2727.
On system >> Administration >> Hardware Drivers appear only the wifi card.
Please help .

---

### Post by Peter09 on 2009-04-24
Look at 
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by IceyBlack on 2009-04-24
> **Peter09 said:**
> Look at 
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

I already do that Peter but same problem when i try to choose normal or 3d appearence a pop up window appear : Desktop effect could not be enabled!

---

### Post by Peter09 on 2009-04-24
Yeah, just looked at the table at the bottom of the link, your card shows no improvement. 

It may be the case that you have to wait for new drivers to be produced.

---

### Post by Dynaflow on 2009-04-24
[This]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/363821/comments/7") worked for me.  Step by step:

Open the terminal.

```
gedit compiz_enable.sh
```Put the following in the blank file, then save:
```
#!/bin/bash
SKIP_CHECKS=yes compiz
```Now, back in the terminal, type:
```
chmod +x compiz_enable.sh
```Then go to System -> Preferences -> Startup Applications.  Click Add, browse for the file you just created under Command (the file itself will be the command), and fill in an arbitrary Name and Comment, if you so desire.


Log out, log back in, and all should be well, without needing to revert to an earlier Intel driver.

---

### Post by IceyBlack on 2009-04-24
> **Peter09 said:**
> Yeah, just looked at the table at the bottom of the link, your card shows no improvement. 

It may be the case that you have to wait for new drivers to be produced.

No way , it works before in ubuntu 8.04 and 8.10 so your answer has no sense i think , i will make clean install to be sure.

---

### Post by clive littlewood on 2009-04-24
Hi

Check out the Ubuntu-Geek website they have a solution to your problem posted this morning.

Clive

---

### Post by IceyBlack on 2009-04-24
> **clive littlewood said:**
> Hi

Check out the Ubuntu-Geek website they have a solution to your problem posted this morning.

Clive

Thank you guys for the help , i will try now

---

### Post by bearozo on 2009-06-01
> **Dynaflow said:**
> [This]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/363821/comments/7") worked for me.  Step by step:

Open the terminal.

```
gedit compiz_enable.sh
```Put the following in the blank file, then save:
```
#!/bin/bash
SKIP_CHECKS=yes compiz
```Now, back in the terminal, type:
```
chmod +x compiz_enable.sh
```Then go to System -> Preferences -> Startup Applications.  Click Add, browse for the file you just created under Command (the file itself will be the command), and fill in an arbitrary Name and Comment, if you so desire.


Log out, log back in, and all should be well, without needing to revert to an earlier Intel driver.
I tried your suggestion on an old gericom p4 with intel graphics (running jaunty 9.04 previous editions did not give picture at all not this one either sometimes but most of the time :) ) when I tried your solution it seemed to work but when the screen turned black and I just had a mouse pointer, had to remove the file from recovery to get a pic again so that solution did not work for me :(

---

