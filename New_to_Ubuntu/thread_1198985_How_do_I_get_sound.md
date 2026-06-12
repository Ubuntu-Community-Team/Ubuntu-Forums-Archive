---
title: "How do I get sound?"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by goog64 on 2009-06-28
I installed Ubuntu 9.04 five days ago. I have no sound. I also have no sound when I boot from the Live CD. For two days I have done all the usual suggestions in the various posts I have read, with no success.
This was the most promising link:[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
but I soon ran into trouble when the author said his driver was 1.0.18, when his screen said it was 1.0.18rc3. This of course snowballed into many questions and different possible paths (all of which I followed), and 4 hours later I am no better off. I would like to stick with Ubuntu, but this is getting ridiculous, I miss my children, and they need a father.
I am using a Compaq Presario B3800.
DEVICE MANAGER says that my audio controller is Intel 82801DB-ICH4 with AD1981B Sound Card.
One of the posts mentioned adjusting audio devices in the BIOS. How do I do that, pleeaaase?? When I press F10 during startup I get a BIOS page, but there are definitely no options for anything like this.
Thanks
John

---

### Post by gn2 on 2009-06-28
Something to try is add the line:
```
options snd-hda-intel model=lenovo
```
to the file /etc/modprobe.d/alsa-base

---

### Post by goog64 on 2009-06-28
Thank you. I typed in the line you suggested, but then when I tried to save the file I got:
**"You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."**
What do I do, please?

---

### Post by gn2 on 2009-06-28
To get the permissions to save it, open the file by pressing Alt+F2 then:
```
gksudo gedit /etc/modprobe.d/*alsa-base.conf
```
gksudo = sudo for graphic applications
sudo = super-user do
gedit = Gnome default text editor application

---

### Post by DPJ93 on 2009-06-28
Edit the file via the Terminal.

Open up Terminal, then enter 
```
gksudo gedit [insert file directory here]
```

EDIT: [U]gn2, ey, you posted that while I was writing this one :P
[/U]

---

### Post by goog64 on 2009-06-28
Thanks guys. I've done it, but unfortunately no sounds at all.

---

### Post by DPJ93 on 2009-06-28
> **goog64 said:**
> Thanks guys. I've done it, but unfortunately no sounds at all.

Did you restart your computer?

---

### Post by Martje_001 on 2009-06-28
```
sudo /etc/init.d/alsa-utils restart
```
Should also work, in stead of shutting down the system.

---

### Post by goog64 on 2009-06-28
Hi,
yes I restarted, I switched users, I rebooted in a different kernel, I checked that the contents of the file had been saved correctly. Still no sound. I think it's back to Vista for me. Sorry, I can't take it anymore!

---

### Post by goog64 on 2009-06-29
This is what finally worked: (I am so happy!)

In 8.04, double click on the volume control, click on Edit/Preferences, then check External amplifier to be visible. The switches tab then appears. Uncheck External amplifier in that tab.

But I also now have the world's largest alsa-base.conf file, so that may be important too!

---

### Post by danny_galaga on 2009-06-29
DOH! just realised i had a similar problem on mine!

---

