---
title: "noob with SD problems"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by linkmaster64 on 2009-02-25
I just got my Mirco SD card the a few days ago, it has been working up till today. my problem is that it is locked and i cant unlock it in any user. it says that i dont have the right permissions. what do i do?

---

### Post by llamabr on 2009-02-25
What did you change between the time that it did work, and the time that it didn't?  Do any installs?  Change any config files, even ones you consider inconsequential?

How are you mounting the sd card?  post your /etc/fstab

---

### Post by linkmaster64 on 2009-02-25
i put the card into a phone, tryied a couple things like sudos (dontremeber which ones) installed unrar and i think thats about it. i'm mounting it through usb i was also thinking of reformating it.

---

### Post by The-IRS on 2009-02-25
I have had a similar problem with my install of 8.10. If I let my usb sit for too long with no action, it converts to a read only system. probably a security measure against snoopers. my remedy was to pull it out and plug it back in.

---

### Post by linkmaster64 on 2009-02-25
tried that also

---

### Post by The-IRS on 2009-02-25
hmmmm. I'm not sure what the command is, but have you run the terminal as root to try and change the permissions? (Don't tell anyone but i'm a noob too)

---

### Post by mc4man on 2009-02-25
Just to get out of the way - did you inadvertently lock the card? (most sd cards have a little slide on the side

---

### Post by linkmaster64 on 2009-02-25
> **mc4man said:**
> Just to get out of the way - did you inadvertently lock the card? (most sd cards have a little slide on the side

no i did not inadvertently lock the card. micros dont have a slide

---

### Post by adult swim on 2009-02-26
EDIT:  woops i didnt see where you were connecting it through usb.  connect the card to your computer, then open a terminal and run ```
sudo fdisk -l
``` that -l is a lower case L
then copy and paste what it returns here

---

### Post by linkmaster64 on 2009-02-26
it says nothing

---

### Post by tarps87 on 2009-02-26
> **adult swim said:**
> EDIT:  woops i didnt see where you were connecting it through usb.  connect the card to your computer, then open a terminal and run ```
sudo fdisk -l
``` that -l is a lower case L
then copy and paste what it returns here

> **linkmaster64 said:**
> it says nothing

:confused:

Are you running from a hard drive/have a hard drive in the machine?
If you do
```
sudo fdisk -l
```
should list at least that
```
fdisk -l
```
Should list external devices

Are you sure there is not output from the command?

Can you post the output of ```
ls -l /media/*usb_card_device*/
```

---

### Post by scratman on 2009-02-26
This workaround should help you.

Go to Applications>Accessories>terminal and type ```
sudo nautilus
``` and enter your root password.
If you then navigate to the SD card, you should be able to add/delete/move files as per normal.  Sounds like you have not locked the device physically, so you may have amended the permissions on the card.  Not sure how to do this to be honest, and I don't want to guide you incorrectly.   You may need to use chmod or chown to deal with this, but _PLEASE do not_ do this until you are certain what you are doing!

---

### Post by linkmaster64 on 2009-02-26
i talk to a friend at school and he said he had the same problem and he fixed it for me. im not sure what he did though but it works now

---

