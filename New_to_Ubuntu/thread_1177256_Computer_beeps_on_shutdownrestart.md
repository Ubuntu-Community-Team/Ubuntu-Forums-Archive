---
title: "Computer beeps on shutdown/restart"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by mbuchoff on 2009-06-03
Although I have unchecked System->Preferences->Sound->Sounds tab->Play alerts and sound effects as well as the "Play alert sound" checkbox, my computer beeps several times when shutting down or restarting.  How can I disable this?

Thanks in advance.

---

### Post by CLomax on 2009-06-03
Try this: [http://www.detector-pro.com/2008/11/how-to-stop-pc-speaker-on-ubuntu.html](http://www.detector-pro.com/2008/11/how-to-stop-pc-speaker-on-ubuntu.html)

:KS

---

### Post by LewRockwell on 2009-06-03
some computers have a setting in BIOS that turns the beep on and off.

---

### Post by mbuchoff on 2009-06-05
> **CLomax said:**
> Try this: [http://www.detector-pro.com/2008/11/how-to-stop-pc-speaker-on-ubuntu.html](http://www.detector-pro.com/2008/11/how-to-stop-pc-speaker-on-ubuntu.html)

:KS
It worked!  Thank you for the quick (and helpful) response.

---

### Post by Tholley on 2009-06-05
I tried both ways and **did not** work for me.
the first try, going to /etc/modprobe.d, there was several blacklists, did not know which to choose.
 
second try, sudo gedit /etc/modprobe.d/blacklist gave me a blank doc, I typed in #Stop PC speaker (enter) blacklist pcspkr (enter) and clicked save on the top.
 
Did nothing... when I shut down, beep-beep. Booted back up... beep.

---

### Post by Celauran on 2009-06-05
I'd go back and check for typos. /etc/modprobe.d/blacklist should be present from the get go, and you'd just add the pcspkr line to the bottom of the file.

---

### Post by Tholley on 2009-06-05
Well on the 2nd try I mentioned above, I cut & pasted directly from the Detector-Pro website.
 
If I go into the /etc/modprobe.d folder, can u tell me which blacklist i need to add the lines to?

---

### Post by CLomax on 2009-06-05
I just had a look in */etc/modprobe.d/* and it turns out that the file might be *blacklist.conf* rather than simply *blacklist*.

**Addendum: Confirmed, I added *blacklist pcspkr* to */etc/modprobe.d/blacklist.conf*, rebooted and it works.**

---

### Post by Tholley on 2009-06-05
Ok thanks! I'll see if that was one of my choices when I get back home.

---

### Post by Celauran on 2009-06-05
> **CLomax said:**
> I just had a look in */etc/modprobe.d/* and it turns out that the file might be *blacklist.conf* rather than simply *blacklist*.

Could be that due to version difference. On 8.04 and 8.10 it's definitely just blacklist.

---

