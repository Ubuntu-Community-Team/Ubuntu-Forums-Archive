---
title: "Wireless issue"
date: 2007-12-21
forum: Networking &amp; Wireless
---

### Post by sdmike on 2007-12-21
I'm running fiesty fawn and I'm using an external usb linksys wusb54g V4 card.

I tried these to articles and it still won't work:

[http://ubuntuforums.org/showthread.php?t=516649&highlight=linksys+wusb54g](http://ubuntuforums.org/showthread.php?t=516649&highlight=linksys+wusb54g)

[http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)

ndiswrapper says that the driver installed.

So what am I doing wrong here?

---

### Post by The Tronyx on 2007-12-21
Can you elaborate as to what doesn't work?  Any error messages, what is the rest of your system hardware, are you doing the 64 bit feisty?

ALso, you might need to direct ndiswrapper to the usb location

Using the command 'sudo lsusb' that will give you the location.  Assuming you made it to sudo ndiswrapper -i drivername.inf you may need to try this
> 
sudo ndiswrapper -a XXXX:YYYY drivername

Substituting XXXX:YYYY with the info you got as to the usb location of your wireless device.

---

### Post by sdmike on 2007-12-21
the adapter isn't lighting up.

in the network manager it doesn't show a wireless unit.

when I put in ifconfig wlan0 doesn't come up.

That's about it.

It's not working lol.

---

### Post by The Tronyx on 2007-12-21
> **sdmike said:**
> the adapter isn't lighting up.

in the network manager it doesn't show a wireless unit.

when I put in ifconfig wlan0 doesn't come up.

That's about it.

It's not working lol.

what is the output of iwconfig?

Did you sudo modprobe ndiswrapper?

Did you sudo ifup wlan0?

---

### Post by sdmike on 2007-12-21
> **2point0 said:**
> Can you elaborate as to what doesn't work?  Any error messages, what is the rest of your system hardware, are you doing the 64 bit feisty?

ALso, you might need to direct ndiswrapper to the usb location

Using the command 'sudo lsusb' that will give you the location.  Assuming you made it to sudo ndiswrapper -i drivername.inf you may need to try this

Substituting XXXX:YYYY with the info you got as to the usb location of your wireless device.

When I put in 'sudo lsusb' only my mouse showed.

I'll try another usb port then.

---

### Post by sdmike on 2007-12-21
OMG it was a bad usb port!!!!

oh well thank you for the nifty command though.

---

### Post by The Tronyx on 2007-12-21
> **sdmike said:**
> OMG it was a bad usb port!!!!

oh well thank you for the nifty command though.

Mark this thread as solved please and you are very welcome.:)

---

