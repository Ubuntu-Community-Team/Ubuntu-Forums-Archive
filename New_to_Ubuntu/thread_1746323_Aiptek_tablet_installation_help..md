---
title: "Aiptek tablet installation help."
date: 2011-05-01
forum: New to Ubuntu
---

### Post by ironic.demise on 2011-05-01
Using [https://help.ubuntu.com/community/AiptekTablet](https://help.ubuntu.com/community/AiptekTablet) I tried to install my tablet.

It's trust branded and Ubuntu marks it as an aiptek apt-2.
It has no effect at all on the mouse, it's getting power but won't move the moust, click or do anything in any program or at the desktop.

Is there something I missed? I followed the instructions exactly.

Using 10.10, copied the code in the 10.04 into the respective files and made sure I got /usr/share instead of /usr/lib.

---

### Post by Favux on 2011-05-01
Did you check if the Aiptek driver is installed in Synaptic Package Manager or the Software Center?  The package is called something like xserver-xorg-input-aiptek.

---

### Post by ironic.demise on 2011-05-02
> **Favux said:**
> Did you check if the Aiptek driver is installed in Synaptic Package Manager or the Software Center?  The package is called something like xserver-xorg-input-aiptek.

Installing now, Seems like such an easy thing to miss.
Thanks for pointing it out, it should work fine now, thanks.

Installed, rebooted, to no avail, still not getting any input.

---

### Post by Favux on 2011-05-02
The package doesn't automatically install an aiptek.conf like it should.  You installed one in the correct directory it sounds like.  What are the contents?  Also we found naming it 50-aiptek.conf seemed to work best.

---

### Post by ironic.demise on 2011-05-02
> **Favux said:**
> The package doesn't automatically install an aiptek.conf like it should.  You installed one in the correct directory it sounds like.  What are the contents?  Also we found naming it 50-aiptek.conf seemed to work best.
I'll rename it to 50 now, see if it helps.
```
/usr/share/X11/xorg.conf.d/10-aiptek.conf:
[code]Section "InputClass"
        Identifier "pen"
        MatchProduct "Aiptek|AIPTEK|aiptek"
        MatchDevicePath "/dev/input/event*"
        Driver "aiptek"
        Option "SendCoreEvents" "true"
        Option "USB" "on"
        Option "Type" "stylus"
        Option "Mode" "absolute"
        Option "zMin" "0"
        Option "zMax" "511"
EndSection
```[/code]

---

### Post by Favux on 2011-05-02
Alright.  You can also get rid of this line:
```
        Option "SendCoreEvents" "true"
```
because that's been deprecated since Xserver 1.7.

---

### Post by ironic.demise on 2011-05-02
Changed it, can't see any improvements yet
Rebooting to see if it helped.

---

### Post by ironic.demise on 2011-05-02
Getting a response now thanks for the help.

---

