---
title: "Search for an internal hard drive"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by murderous mouse on 2009-03-16
hey guys, here's the situation I'm in:

I recently bought a computer from someone online, when I got the computer it had one administrator account and a BIOS password. After contacting the selling I got no reply so I figured the easiest way would be just changing the password by swapping some files to get to the unprotected DOS prompt as a screen saver etc etc

The problem that I am facing is that the only way for me to get access to the computers files to change the files so I can change the password is to boot in another operating system (Hence Ubuntu) although because of the BIOS password I cannot simply boot up and go, instead I need to unplug the hard drive, boot from a live USB then plug the hard drive back in once the computer moves past the hard drive as a boot option.
The problem with this is that once the computer is started up and I'm at the desktop of ubuntu I'm faced with the problem that I cannot find the hard drive, probably I would assume because the computer booted up without a hard drive plugged in, or at least figured there was not hard drive before booting.

So here's my question:
Is there any way that anyone can think of that I can scan for the internal hard drive or find the hard drive while logged in on ubuntu?

If anyone has any idea then it would be a great help, I already had one friend who thought there might be a terminal(?) command that would do it, or a list of commands whatever, but he couldn't remember them...

Or if anyone has any idea of another way that I can change the password without re installing the operating system or reformatting the computer then that would be great as well :D

Thanks guys.

---

### Post by Elfy on 2009-03-16
[http://www.tech-faq.com/reset-bios-password.shtml](http://www.tech-faq.com/reset-bios-password.shtml)

---

### Post by ivanvajar on 2009-03-16
You can reset BIOS (that removes BIOS password) by removing and putting back a battery on a motherboard.

---

### Post by murderous mouse on 2009-03-16
thanks for the quick replies, I just had a look at that and it was about a password to access the computer (as in you can't get to the log on screen without that password) the password that this computer has is just one which stops your from editing any of the BIOS settings.
Does anyone know if this is essentially the same thing? I don't really want to risk stuffing something up especially if it might not work in the first place 0.0

---

### Post by Elfy on 2009-03-16
The link I gave has reset bios password - usually it is as simple as removing the battery as ivanvajar for a few minutes and then reinserting it - it clears the password. Once you have done so and the password has been removed - set the BIOS to boot cd first and you should be in a position to replace the OS

However at times you need to do other things - hence the link.

I've had to do it on more than occasion and have had no problems - in fact the battery can just need replacing eventually.

---

### Post by oldos2er on 2009-03-16
"Is there any way that anyone can think of that I can scan for the internal hard drive or find the hard drive while logged in on ubuntu?"
```
sudo fdisk -l
```

---

### Post by murderous mouse on 2009-03-16
thanks for the replys again, ill give the wiping bios pass thing a shot, but first I think ill try the sudo fdisk -l thing, it seems a bit more safe to me =D and ive had huge problems with even opening a computer in the past >.< I'm not the luckiest of people lol

---

### Post by orethrius on 2009-03-16
Assuming all you touch is the battery that stores the BIOS password, the only thing that will be removed is the BIOS password.  Passwords on Windows user accounts will remain intact.

---

### Post by cariboo on 2009-03-16
I've used something similar to [this]("http://home.eunet.no/pnordahl/ntpasswd/"), for years to reset XP passwords.

Jim

---

### Post by orethrius on 2009-03-16
> **cariboo907 said:**
> I've used something similar to [this]("http://home.eunet.no/pnordahl/ntpasswd/"), for years to reset XP passwords.

Jim

Here I am, wondering whether to post the link to certain distros, and someone else posts the right tool. :)

---

### Post by sarang on 2009-03-16
Before you clear the bios, make a note of the various settings. This is especially applicable for older computers that have many non-auto BIOS settings. Also, if it is a really secure system, resetting the BIOS can cause data loss. Rare, but there exists proprietary hardware on which this can happen.

---

### Post by murderous mouse on 2009-03-17
Thanks again for all the replies, I just reset the bios password and it worked like a charm =D so now I just need to change the admin password and everything will be fine :)

thanks for all the help

---

