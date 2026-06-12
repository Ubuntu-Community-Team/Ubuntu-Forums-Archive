---
title: "Speakers Not working. Headphones do."
date: 2009-09-22
forum: New to Ubuntu
---

### Post by jhk30 on 2009-09-22
OK so i have a laptop (HP pavilion DV2 1027ca) and sound doesn't work through the speakers (built in of course its a laptop) but It does work when I plug headphones into the (built in) headphone jack.

I need help please! thank you.

I have ubuntu 9.04 desktop edition

---

### Post by tgeer43 on 2009-09-23
> **jhk30 said:**
> OK so i have a laptop (HP pavilion DV2 1027ca) and sound doesn't work through the speakers (built in of course its a laptop) but It does work when I plug headphones into the (built in) headphone jack.

I need help please! thank you.

I have ubuntu 9.04 desktop edition
Go into System->Preferences->Volume Control and select 'Preferences'. Make sure everything has a checkmark next to it. Go back to the mixer and turn everything up.

tgeer

---

### Post by majiciannz on 2009-09-23
> **jhk30 said:**
> OK so i have a laptop (HP pavilion DV2 1027ca) and sound doesn't work through the speakers (built in of course its a laptop) but It does work when I plug headphones into the (built in) headphone jack.

I need help please! thank you.

I have ubuntu 9.04 desktop edition
I have an HP dv5 and had the same problem.

First do as is suggested in post #2 by tgeer43.
If that doesn't fix it you may have to do what I did........

Try inserting the following in /etc/modprobe.d/alsa-base.conf:

options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel


To do the above you will have to open a terminal and enter "sudo nautilus"
Note: without the ""
That will open a root browser.
Navigate to and open "alsa-base.conf" in gedit.
Copy and paste the commands at the bottom of the page.
Save and close.
Reboot.

Should work....
Hope this helps.

---

### Post by tgeer43 on 2009-09-23
Just nitpicking here but you can edit the file directly from the command line without first opening an administrative nautilus session:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```tgeer

---

### Post by majiciannz on 2009-09-23
> **tgeer43 said:**
> Just nitpicking here but you can edit the file directly from the command line without first opening an administrative nautilus session:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```tgeer
Yes, you are right of course. Cheers.
I went the graphical way, wasn't sure how much the person knew.

---

