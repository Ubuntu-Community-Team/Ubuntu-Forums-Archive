---
title: "Mount to USB Drive"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by The_Pirate_King on 2009-12-13
I do not have a working hard drive right now.  So, is there any way to automatically mount all my files and settings to my 2 GB USB drive?

---

### Post by Temposs on 2009-12-13
If your hard drive doesn't work(as in, it has physically broken), then you may not be able to read the data from it no matter what.

But, in case you can read from it, use a LiveCD or LiveUSB of Ubuntu to boot your machine, and then your hard drives should show up. You can do all of your transferring from there.

And next time, use a backup program like Deja Dup: [https://launchpad.net/deja-dup](https://launchpad.net/deja-dup)

---

### Post by The_Pirate_King on 2009-12-13
No, I don't care about the files on the hard disc.  
What I am asking is, can I use a USB like a hard disc?

---

### Post by Temposs on 2009-12-13
Yes, you can :-)

Just remember to set your USB drive as the first drive to boot, if you install Ubuntu on it.

---

### Post by The_Pirate_King on 2009-12-14
I tried that, and since it's only 2 GB, there is not enough space for it.

---

### Post by Temposs on 2009-12-14
The best you would be able to do is boot the LiveCD from your USB drive, then. You only need around 700mb for that.

---

### Post by The_Pirate_King on 2009-12-14
Yes, but it won't boot more than once that way... and what I'm really trying to accomplish is to have all my files/settings saved from session to session...

---

### Post by Temposs on 2009-12-14
If you make the Live USB with the Ubuntu USB Startup Creator, it's possible to reserve the unused space for files/settings. It's the setting that says "Stored in reserve extra space". So, you'd just pop that all the way to the highest setting, and then it will save settings and such for you.

But really, you're not going to get very far that way. You need to have a proper install if you want to do anything significant with your computer.

---

### Post by jpt266 on 2009-12-14
I think if you go to;
[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/)

Create a Ubuntu 9.10 Live USB Persistent Flash Drive from the running Live CD: 

Try check it out;

---

### Post by The_Pirate_King on 2009-12-14
Thanks, that looks promising.  Hopefully that will work.

---

### Post by longtom on 2009-12-14
All this is possible.  However - on a 2GB USB drive I'd rather use something lighter than Ubuntu all together.

Maybe you want to cast your eye to [Puppy Linux](http://www.puppylinux.org/).  I have it several versions on several USB sticks, one only 512mb.  It works very well, has a brilliant hardware detection and you can add more programs if you feel the need to do so.  Really amazing for such a small distro.

Whatever you decide - Good Luck!

---

### Post by The_Pirate_King on 2009-12-14
When I try to boot from the Ubuntu Live USB, I get the message "Boot error"
That's all it says.  I created it using Ubuntu's 'Startup Disk Creator'... I don't know why it is doing this now.  It is set to boot from USB memory. 
Any help would be appreciated.

---

### Post by longtom on 2009-12-14
> **The_Pirate_King said:**
> When I try to boot from the Ubuntu Live USB, I get the message "Boot error"
That's all it says.  I created it using Ubuntu's 'Startup Disk Creator'... I don't know why it is doing this now.  It is set to boot from USB memory. 
Any help would be appreciated.

USB Memory?  Could you tell us the exact term your bios uses to describe where it is booting from?

---

### Post by The_Pirate_King on 2009-12-14
That's the term... "USB Memory".

---

### Post by longtom on 2009-12-14
> **The_Pirate_King said:**
> That's the term... "USB Memory".

I guess every bios is different.  Mine says USB HDD, if I remember correctly.

I have also found that on different computers procedures to start from USB differ.  On this one I actually have to go one menu further as it originally appears in order to have another menu to select my start-up order, another just works in a separate start-up menu etc.

You could also try to press F12 on star-up and select your boot device from the appearing menu.

Good Luck

---

### Post by The_Pirate_King on 2009-12-14
Yeah, I've read some wikis and apparently every bios has a different name for USB.  Pretty annoying. 

And yeah, F12 is what i'm doing now... plus it's set to boot from USB first.

---

### Post by CaptainMark on 2009-12-14
On some mobos you have to set boot priority to HDD then theres a HDD priority option somehwere else where you can choose USB HDD. this isnt very common but some are set up to work this way

---

### Post by The_Pirate_King on 2009-12-14
My bios has a "USB Memory" option so I don't think this applies.

---

