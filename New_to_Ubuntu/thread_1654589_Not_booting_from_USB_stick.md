---
title: "Not booting from USB stick"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by chrismax2 on 2010-12-28
[COLOR=black][FONT=Verdana]Hi,[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]I'm having a problem booting Ubuntu from my PC by my new USB stick. I know it has been installed and working correctly because it works on another computer.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I have tried flashing the BIOS to most up to date version and the PC does see the USB stick on the boot options. However it totally ignores it and loads Windows instead. Is there anything else I can do? The Motherboard is a phoenix which is only about 4 or 5 years old.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I'm assuming the motherboard just won't let me boot the USB device but I wanted to check to make sure there was nothing something else I could try first before I give up.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Thanks and Regards[/FONT][/COLOR]
 
[FONT=Verdana][COLOR=black]Chris[/COLOR][/FONT]

---

### Post by davidmohammed on 2010-12-28
in the bios can you specify the boot order?  Is USB at the top of this list and also enabled?

---

### Post by amjjawad on 2010-12-28
> **chrismax2 said:**
> [COLOR=black][FONT=Verdana]Hi,[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]I'm having a problem booting Ubuntu from my PC by my new USB stick. I know it has been installed and working correctly because it works on another computer.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I have tried flashing the BIOS to most up to date version and the PC does see the USB stick on the boot options. However it totally ignores it and loads Windows instead. Is there anything else I can do? [COLOR=Red]**The Motherboard is a phoenix which is only about 4 or 5 years old.**[/COLOR][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I'm assuming the motherboard just won't let me boot the USB device but I wanted to check to make sure there was nothing something else I could try first before I give up.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Thanks and Regards[/FONT][/COLOR]
 
[FONT=Verdana][COLOR=black]Chris[/COLOR][/FONT]

[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7191[/IMG]


1) Plug your USB in
2) Reboot your machine
3) Enter BIOS
4) Make sure your USB-Drive has the first priority to boot from.

---

### Post by chrismax2 on 2010-12-28
Hi thanks for the quick replys.
 
The problem is there is no USB choice unless I go into external devices boot options where I see it there.  I have read earlier your supose to see the USB device as a hard drive but I only see it as an external device.  So I have my external devices as the first boot option but no luck.

---

### Post by amjjawad on 2010-12-28
> **chrismax2 said:**
> Hi thanks for the quick replys.
 
The problem is there is no USB choice unless I go into external devices boot options where I see it there.  I have read earlier your supose to see the USB device as a hard drive but I only see it as an external device.  So I have my external devices as the first boot option but no luck.

Does the same USB-Drive work on your other machine?

---

### Post by chrismax2 on 2010-12-28
Yeah Ubuntu loads from the same USB stick on the other PC.  So I know it has to be my motherboard/BIOS rather then the USB stick.  It's a shame cause I think it would of been easier to sort out if it was the USB stick or I isntalled ubuntu incorrectly.
 
Would you say my motherboard just can't see it then?

---

### Post by davidmohammed on 2010-12-28
are both PC hard-drives the same type i.e. IDE or SATA?  Maybe you can swap the hard-drive and install on the PC that boots from the USB stick.

---

### Post by chrismax2 on 2010-12-28
The other one is not my pc otherwise I would use it.

---

### Post by amjjawad on 2010-12-28
> **chrismax2 said:**
> Yeah Ubuntu loads from the same USB stick on the other PC.  So I know it has to be my motherboard/BIOS rather then the USB stick.  It's a shame cause I think it would of been easier to sort out if it was the USB stick or I isntalled ubuntu incorrectly.
 
Would you say my motherboard just can't see it then?

I guess your MB is in the same age of my MB. I don't think so. I might be something else.

---

### Post by amjjawad on 2010-12-28
> **chrismax2 said:**
> The other one is not my pc otherwise I would use it.

I guess you can use a LiveCD, right?

---

### Post by chrismax2 on 2010-12-28
Well it did not pick it up the other day but my DVD player needed a clean as other stuff did not work, I will try it again, if it works I will just partition the hard drive and use it that way.  Will let you know.

---

### Post by s1baker on 2010-12-28
Just a thought. Can you completely disconnect your HD and then try to boot with only your USB stick?

---

### Post by amjjawad on 2010-12-28
> **chrismax2 said:**
> Well it did not pick it up the other day but my DVD player needed a clean as other stuff did not work, I will try it again, if it works I will just partition the hard drive and use it that way.  Will let you know.

Ok, try to clean it and try to create another LiveUSB using another USB-Drive.

---

### Post by amjjawad on 2010-12-29
> **s1baker said:**
> Just a thought. Can you completely disconnect your HD and then try to boot with only your USB stick?

Good idea. I have done that once :)

---

### Post by ppv on 2010-12-29
Could you list out the options that you see in the boot devices list....with the USB drive already plugged in.

---

### Post by amjjawad on 2010-12-29
To the OP,

Have you seen this thread:[http://ubuntuforums.org/showthread.php?t=1654004](http://ubuntuforums.org/showthread.php?t=1654004) ?

I know your machine is different but I guess that guys got the same issue.

Just in case your BIOS doesn't support booting from USB or you got some other problems, try this:
[http://blog.brothersoft.com/2008/12/09/boot-computer-from-usb-or-cdrom-even-if-bios-not-supported-using-plop/](http://blog.brothersoft.com/2008/12/09/boot-computer-from-usb-or-cdrom-even-if-bios-not-supported-using-plop/)

---

