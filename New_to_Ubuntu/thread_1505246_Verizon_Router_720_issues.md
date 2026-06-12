---
title: "Verizon Router 720 issues"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by HellBomb on 2010-06-08
I just downloaded the newest version of Ubuntu and installed it. Now I cannot get my Verizon Router USB720 to work and have no internet access on ubuntu untill I get it to work so help please!

---

### Post by pizza-is-good on 2010-06-08
I had the same problem. Read my thread [here]("http://ubuntuforums.org/showthread.php?t=1397796"). It is full of good stuff. In it is a link to [this thread]("http://ubuntuforums.org/showthread.php?p=2048477"), which helped me solve the problem.

Hope it helps.

~pizza

---

### Post by HellBomb on 2010-06-08
> **pizza-is-good said:**
> I had the same problem. Read my thread [here]("http://ubuntuforums.org/showthread.php?t=1397796"). It is full of good stuff. In it is a link to [this thread]("http://ubuntuforums.org/showthread.php?p=2048477"), which helped me solve the problem.

Hope it helps.

~pizza

i have actually tried both ways and sadly they did not work, thus the reason i am making this thread, the first one does not show what is in the box and the second shows no info in the  window that opens

---

### Post by pizza-is-good on 2010-06-08
> **HellBomb said:**
> i have actually tried both ways and sadly they did not work, thus the reason i am making this thread, the first one does not show what is in the box and the second shows no info in the  window that opens

I'm not sure what you mean by "the first one does not show what is in the box and the second shows no  info in the  window that opens". What is the first one? and what is the second one?

Just wondering, did you really read my thread that fast????

---

### Post by HellBomb on 2010-06-08
yea i saw your thread several times, what i meant by the first one is the first method. I got alot of information and non of it was what your thread said it was supposed to be. Which method should i be trying from afresh install with the newest version of ubuntu?

when i do the command in method one
```
 gksudo gedit /etc/wvdial.conf
```
it says it cant find the document

when i try method 2 and i enter 
```
sudo gedit /etc/init.d/mountdevsubfs.sh
``` comes up with a blank document

---

### Post by pizza-is-good on 2010-06-08
On the second link, the instructions that I followed were these:
> **Mach1US said:**
> 

**_[COLOR=SeaGreen] Third for Verizon USB760 users [/COLOR]_**

```

sudo gedit /etc/udev/rules.d/70-persistent-cd.rules
```find the line  that contains **[COLOR=Red] Novatel_Mass_Storage [/COLOR]** and  append the following to it: 
```
RUN+="/usr/bin/eject %k"
```save and close
```

sudo gedit  /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi
```Add this  in the USB devices section
```
<!-- Verizon USB760-->
<match key="@info.parent:usb.vendor_id" int="0x1410">
<match key="@info.parent:usb.product_id" int="0x6000">
<match key="@info.parent:usb.interface.number" int="0">
<append key="info.capabilities"  type="strlist">modem</append>
<append key="modem.command_sets"  type="strlist">IS-707-A</append>
</match>
</match>
</match> 
```Save and close

Now plug in your card and make sure it didn't mount anything (Places  -> Computer USB Drive shouldn't be mounted)
Now left click the network applet and select 'Auto mobile broadband  (CDMA) connection'
Let it connect.
If it doesn't make sure to go into VZAccessManager on a Windows machine  and activate your USB 760.

It worked fine on Karmic Koala (Ubuntu 9.10).

Did you also try the username and password thing from my thread? Maybe a combination of the two will work.

---

### Post by pizza-is-good on 2010-06-08
> **HellBomb said:**
> yea i saw your thread several times, what i meant by the first one is the first method. I got alot of information and non of it was what your thread said it was supposed to be. Which method should i be trying from afresh install with the newest version of ubuntu?

when i do the command in method one
```
 gksudo gedit /etc/wvdial.conf
```it says it cant find the document

when i try method 2 and i enter 
```
sudo gedit /etc/init.d/mountdevsubfs.sh
``` comes up with a blank document

The blank document might be what you need, because I think that it wants you to write stuff to it, correct?

Try the first one by just using sudo instead of gksudo... Not sure if that will do something, but worth a try.

---

### Post by HellBomb on 2010-06-08
again on step one i open that file and this is what it says in it.

```
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-cd-aliases-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# DVDRAM_GH22LS40 (pci-0000:00:11.0-scsi-3:0:0:0)
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.0-scsi-3:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.0-scsi-3:0:0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.0-scsi-3:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.0-scsi-3:0:0:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"


```

---

### Post by pizza-is-good on 2010-06-08
> **HellBomb said:**
> again on step one i open that file and this is what it says in it.

```
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-cd-aliases-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# DVDRAM_GH22LS40 (pci-0000:00:11.0-scsi-3:0:0:0)
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.0-scsi-3:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.0-scsi-3:0:0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.0-scsi-3:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.0-scsi-3:0:0:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"


```

That looks like the file I had to edit. Keep going...

---

### Post by HellBomb on 2010-06-08
Ok thanks for all your help, for some reason it randomly started working. I didn't enter my phone number or anything it just randomly connected and is running twice as fast as usual.

---

