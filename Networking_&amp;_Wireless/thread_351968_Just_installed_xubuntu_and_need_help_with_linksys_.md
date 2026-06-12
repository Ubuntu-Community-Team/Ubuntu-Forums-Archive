---
title: "Just installed xubuntu and need help with linksys wireless"
date: 2007-02-02
forum: Networking &amp; Wireless
---

### Post by thebigeis on 2007-02-02
I just installed Xubuntu on an old machine (Dell Inspiron 5000e notebook with 96mb of RAM, and 10GB of HD space, pentium3 processor) and I had WinME previously installed on this machine. I have a notebook adaptor (Linksys Wireless-G 2.4 Ghz 802.11g) that I used on it and it worked fine.

How do I install it on Xubuntu? (As I'm posting this, Xubuntu hasn't completely installed yet..)

---

### Post by tturrisi on 2007-02-02
what model name and version # of the linksys card?

---

### Post by thebigeis on 2007-02-02
It's model number is WPC54G version 2

Where do I go to ask about why, after I installed xubuntu from an alternate install cd, the display is all messed up, showing parts of 3 desktops at a time?

---

### Post by tturrisi on 2007-02-02
That's a good card, I have one.
It has a Texas Instruments ACX chipset and uses the ACX111 driver for linux.
Follow these instructions to install the driver and the firmware:
[http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu](http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu)

Post your other questions in the desktop environments forum.

---

### Post by thebigeis on 2007-02-02
I don't understand which part of that I'm supposed to do. Also, i don't have an internet connection on that laptop if that helps. 

And where did you say I should go about my problem?

---

### Post by tturrisi on 2007-02-02
Well you're going to need an internet connection to download and install the needed packages to build and make the drivers from the downloaded source code.  This is rather easy and a no-brainer using module-assistant.  If the laptop has ethernet then connect using a cable.  Go back and read these pages:
[http://acx100.sourceforge.net/wiki/ACX](http://acx100.sourceforge.net/wiki/ACX)
[http://acx100.sourceforge.net/wiki/Firmware](http://acx100.sourceforge.net/wiki/Firmware)
[http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu#Build_Instructions](http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu#Build_Instructions)

The other problem here:
[http://www.ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=132](http://www.ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=132)

---

### Post by thebigeis on 2007-02-02
It doesn't have an ethernet connection, and thanks, I resolved my other problem. There's no way I can do it without the internet.. cause I really can't get the internet on it without the wireless card..

---

### Post by thebigeis on 2007-02-02
Is it possible I can put these files onto a floppy and then download them from the floppy to the old computer?

---

### Post by andytof47 on 2007-02-02
TTURRiSI Just a question

I want to install Xubuntu with a Linksys wusb54g version 4 do i need to worry about this type of thing or is the card supported? out of the cd?

---

### Post by tturrisi on 2007-02-03
> **andytof47 said:**
> TTURRiSI Just a question

I want to install Xubuntu with a Linksys wusb54g version 4 do i need to worry about this type of thing or is the card supported? out of the cd?
[http://rt2x00.serialmonkey.com/wiki/index.php?title=HOWTOS](http://rt2x00.serialmonkey.com/wiki/index.php?title=HOWTOS)
[existing wusb54g threads]("http://www.ubuntuforums.org/search.php?searchid=13886318")

---

### Post by andytof47 on 2007-02-03
Cheers for the serial monkey links:)

---

