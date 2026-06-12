---
title: "BIOS problem"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by digar4o on 2011-07-20
I followed Amjjawad's guide on how to to installl Ubuntu to a USB drive. After, I changed the hard disk boot priority in BIOS to USB HDD first and then CD-ROM. I did this because otherwise it will not boot into Ubuntu. However, when shut down my computer, unplug the hard drive and start the computer again it will boot into Windows and I have to change the HDD boot priority again. Can I stop it from resetting?

P.S: I won't be able to reply until 6pm GMT.

---

### Post by MyR on 2011-07-20
Unfortunately not all computers have the same BIOS interface, so it all depends on whether the particular BIOS you have will support the setting change.  Usually there is the option to exit and save changes; if you've already done this then there may be no way for you to make the USB the default boot device.

---

### Post by realzippy on 2011-07-20
If the cmos battery is old/empty,this behaviour can occur;
BIOS resets to default.

---

### Post by amjjawad on 2011-07-20
> **digar4o said:**
> I followed Amjjawad's guide on how to to installl Ubuntu to a USB drive. After, I changed the hard disk boot priority in BIOS to USB HDD first and then CD-ROM. I did this because otherwise it will not boot into Ubuntu. **However, when shut down my computer, unplug the hard drive and start the computer again it will boot into Windows and I have to change the HDD boot priority again**. Can I stop it from resetting?

P.S: I won't be able to reply until 6pm GMT.

Hello and Welcome :)

You should have posted on my thread so I got a notification ;)

Never mind.

There is absolutely nothing wrong.
As long as the External/USB Drive is NOT connected, BIOS will NOT detect it.
The whole point/idea is: You keep it connected/plugged in AS LONG AS you want to boot into Ubuntu, plug the USB Drive and set BIOS to boot from USB first then your internal HDD.
Don't unplug it. GRUB menu will give you both options to login either to Windows or Linux.

Let me know if you need anything and next time, please either to post on my thread or PM me ;)

---

