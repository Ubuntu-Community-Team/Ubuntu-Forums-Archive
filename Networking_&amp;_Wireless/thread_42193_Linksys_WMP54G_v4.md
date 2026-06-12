---
title: "Linksys WMP54G v4"
date: 2005-06-16
forum: Networking &amp; Wireless
---

### Post by JettCRX on 2005-06-16
I have the Linksys WMP54G v4.  The v4 part is important to note (I didn't at first) ... because apparently the earlier versions of the card used the Broadcom chipset... but this one does not.  Not realizing that, I wasted a day trying to get the Broadcom drivers to work with NDISWrapper.  It would load the driver fine, but it never detected the hardware.  Now I know why!

After walking away from it for a while, I decided to try and verify which chipset I had ... turns out it's a RaLink chipset.  Once I got the correct drivers ([ftp://ftp.a-link.com/wl54h/WL54driver2.2.6.0.zip)](ftp://ftp.a-link.com/wl54h/WL54driver2.2.6.0.zip)), it worked beautifully the first time.

To accomplish this, I downloaded version 1.2 of the source from SourceForge ([http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)) and built it using the SetupNDISWrapperHowTo instructions ([https://wiki.ubuntu.com//SetupNdiswrapperHowto](https://wiki.ubuntu.com//SetupNdiswrapperHowto)) ... I completely missed the note at the top saying compiling from source must be avoided... /shrug... it worked though, so until that page is updated with a reason, I'm not worried about it.  I used the WinXP version of the driver above.

After restarting my machine, I ran **System > Administration > Networking**.  My wireless card was listed there!  Woohoo!  Configured it using the GUI and have restarted several times since ... I've not had to make any configuration changes since the initial setup.  It just works.

FYI, there's supposedly also a native driver for the Ralink chipset that will work with this card ... I found discussion of it here: [http://www.linuxquestions.org/questions/archive/41/2004/11/1/225068](http://www.linuxquestions.org/questions/archive/41/2004/11/1/225068) ... but given that I'm new to all of this, I'm not quite ready to tackle kernel builds, etc.  All in good time, I'm sure.

Just wanted to share my experiences in case they might help anyone else.

---

### Post by bionnaki on 2005-08-30
thanks! this helped me out.

---

### Post by Dambrosio on 2005-09-01
THANKS SO MUCH!
Dan

---

### Post by JettCRX on 2005-09-01
:cool: Glad it helped!

---

