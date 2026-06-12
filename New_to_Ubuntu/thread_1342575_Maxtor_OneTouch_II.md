---
title: "Maxtor OneTouch II"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by rih29 on 2009-11-30
Yeah, so I was an idiot and I tried installing Ubuntu on a Maxtor OneTouch II xHD, and I guess it deleted some core files in the HD or something, and my computer won't recognize the HD what-so-ever. I can't figure out how to get it to recognize it; I'm trying in XP just because its easier, but its not recognizing it in Ubuntu either (from the LiveCD).

Anyone have experience with xHDs that can help?

---

### Post by jbrown96 on 2009-12-01
In the ubuntu liveCD with the Maxtor drive connected, could you post the output of ```
sudo fdisk -l
```

---

### Post by rih29 on 2009-12-01
Sorry for the late reply.

Anyway, I put that in, and it didn't show my xHD, like expected. It only showed the stats for my internal HD. Like I said, I did some **** to this xHD that deleted some sort of core files in it, and now just simply won't be recognized by anything. I want to get it to be recognized because I plan on putting all my files onto it from my XP OS, and then I'm going to split my internal HD into partitions; one for Ubuntu and one for XP, then I can access all my files from that xHD.

---

### Post by rih29 on 2009-12-01
Update: So I think the problem actually lies in my USB drive, which is what conveniently the Maxtor HD plugs in through...

I noticed when I went to plug in my iPod, that it wasn't doing anything. I then tried a simple flash drive; that wasn't recognized either.

This is strange to me because it happened RIGHT after I installed Ubuntu onto the drive, and then my USB drives didn't work at all. What would cause this?

Also, I need help fixing this now :P I went into the Device Manager, and I tried everything I could find; I tried reinstalling the drivers, I tried going to the Power Management settings in the USB Ports and unchecking the "turn off" box. I don't know what to do, but I really kind of need this to be fixed!

---

### Post by wilee-nilee on 2009-12-01
I don't know if this will help but a quick Google search brought me here.
[http://support.microsoft.com/kb/310575](http://support.microsoft.com/kb/310575)

It is pretty unlikely that a Linux install would have anything to do with a USB port problem, so you might check on the net and windows XP forums for information as well.

You might let us know which AV program or programs you have in XP in case this may be the issue.

---

### Post by rih29 on 2009-12-01
> **wilee-nilee said:**
> I don't know if this will help but a quick Google search brought me here.
[http://support.microsoft.com/kb/310575](http://support.microsoft.com/kb/310575)

It is pretty unlikely that a Linux install would have anything to do with a USB port problem, so you might check on the net and windows XP forums for information as well.

You might let us know which AV program or programs you have in XP in case this may be the issue.
Thanks for the reply. I tried that link before, but thanks anyway.

I'm running AVG Free.

---

### Post by wilee-nilee on 2009-12-01
> **rih29 said:**
> Thanks for the reply. I tried that link before, but thanks anyway.

I'm running AVG Free.

Here are two that are very good and recommend by a friend who cleans MS systems for a living if you want download the free versions and update them before running. Personally I feel that any single AV program will not cover all your bases, and these 1st two run independently and the 2nd of the 2 can be made to not run at startup by installing ccleaner and using the startup disable function.
[http://www.malwarebytes.org/](http://www.malwarebytes.org/)
[http://www.superantispyware.com/download.html](http://www.superantispyware.com/download.html)
[http://www.ccleaner.com/](http://www.ccleaner.com/)
Here is the latest MS version.
[http://www.microsoft.com/Security_Essentials/](http://www.microsoft.com/Security_Essentials/)
Here is another very good one.
[http://download.cnet.com/Spybot-Search-amp-Destroy/3000-8022_4-10122137.html](http://download.cnet.com/Spybot-Search-amp-Destroy/3000-8022_4-10122137.html)

These are all free. Are you using XP in a administrative or limited account generally?

Also it is only a assumption that the problem may be associated with any infection and possible damage from one, to any on board
programs. But the people who write these infective scripts are good at writing them to disable processes that will discover them and make it possible to remove them.

---

### Post by rih29 on 2009-12-02
Alright, thanks! But the weird thing is, it doesn't recognize USB when I run the LiveCD for Ubuntu either.

---

### Post by wilee-nilee on 2009-12-02
> **rih29 said:**
> Alright, thanks! But the weird thing is, it doesn't recognize USB when I run the LiveCD for Ubuntu either.

Hmm, quite the conundrum I am not by any means a computer expert, but if it was me being a serial reinstaller when the fix outweighs the ease of a fix before taking it to a computer tech I just reinstall. This may not be an option for you though, I have everything off my computers so I have the install discs for W7 and Karmic just sitting there waiting to be run. And I have the W7 and MS word keys saved in case a reinstall is needed.

I wonder if you have some sort of hardware failure that just happened to coincide with the maxtor issue.

So if you boot with the Ubuntu Live Cd and go to system-administration-gparted or partition manager with the maxtor or any usb device plugged in and check the drop down in the top right corner if any thing besides the HD shows up.

---

### Post by rih29 on 2009-12-02
SOLVED.

Who would've guessed - I had apparently turned off external USB usage in the BIOS. I am a ******* idiot.

---

### Post by wilee-nilee on 2009-12-02
> **rih29 said:**
> SOLVED.

Who would've guessed - I had apparently turned off external USB usage in the BIOS. I am a ******* idiot.

Good job figuring it out! ;)

---

