---
title: "Wireless range appears to be shorter in Ubuntu (Gutsy) than in Windows (XP Home)"
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by vdalmonte on 2008-04-09
In Ubuntu (Gutsy) my wireless connection doesn't work (at all in a certain spot I need it wo work) while with Windows (XP Home) it works (in the same spot).
I did some "empiric tests" (walking 'round the house with the laptop) and the wireless range seems shorter for me with Ubuntu than with Windows.
Does anybody have any suggestions (besides amplifying the wireless range)?

---

### Post by kle on 2008-04-11
Same problem here.

---

### Post by prshah on 2008-04-11
> **vdalmonte said:**
> 
Does anybody have any suggestions (besides amplifying the wireless range)?

> **kle said:**
> Same problem here.

Try setting the wireless cards on your laptop to max power ```
sudo iwconfig wlan0 txpower fixed
sudo iwconfig wlan0 commit
```

Replace wlan0 with the actual name of the interface in your laptop. The second command MAY give an error; that can be ignored.

---

### Post by vdalmonte on 2008-04-15
when I run the second command I get 

```
Error for wireless request "Commit changes" (8B00) :
    SET failed on device eth1 ; Operation not supported.
```

eth1 is my wireless network card

---

### Post by kevdog on 2008-04-15
What driver are you using?  Again b/c some of the drivers used in Ubuntu or linux in general are not truly native but a workaround since the manufacturer didnt release real Linux drivers, you might not a drop in performance.

---

### Post by vdalmonte on 2008-04-15
Yes! It's a Broadcom, one of those drivers which the system asks you if you want to use that hardware!

---

### Post by kevdog on 2008-04-15
I found better range with the broadcom cards with nidswrapper rather than the builtin bcm43xx kernel module driver.  I would give that a shot just to see if your range expands.

---

### Post by vdalmonte on 2008-04-16
Do I have to disable the Broadcom firmware from the Restricted drivers setting? cos I tried to do so [EDIT]after installing the Windows driver[/EDIT] and now the wireless doesn't work.

---

### Post by vdalmonte on 2008-04-16
I rebooted a couple of times and now the wireless works again but the signal range is as before

---

