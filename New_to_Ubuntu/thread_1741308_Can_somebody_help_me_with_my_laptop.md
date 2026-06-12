---
title: "Can somebody help me with my laptop?"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by Murdererjim on 2011-04-27
I just installed ubuntu 10.10 using wubi. I started to install updates, when my laptop froze and I had to hold the power button in to turn it off. When I
turned it back on, I just had a black screen and that was it. Does anybody know how I can get everything running again without sending it to hp?

---

### Post by K_45 on 2011-04-28
Boot up a live CD and then backup all your data for a start. Then boot up normally again. What do you see?

---

### Post by Murdererjim on 2011-04-28
I can't boot anything. I get the black screen as soon as the computer turns on.

---

### Post by K_45 on 2011-04-28
Set the CD/DVD drive to boot first in the BIOS and boot the LIve CD. That should do it.

---

### Post by Murdererjim on 2011-04-28
I can't get into the bios or anything. The screen is black as soon as I hit the power button. So I can't even boot the cd or change bios settings.

---

### Post by K_45 on 2011-04-28
What brand is the laptop?

---

### Post by HermanAB on 2011-04-28
Wait, this is a WUBI install.  WUBI is a file on a Windows file system.

You should be able to reboot Windows by selecting the HDD in the BIOS boot sequence and doing a Safe Mode boot.

There are also special Repair Install CDs available for different versions of Windows that can be used to fix the Windows boot process.

---

### Post by Murdererjim on 2011-04-28
hp

---

### Post by K_45 on 2011-04-28
To access the BIOS, boot up and keep on pressing Esc until you see the BIOS. If that won't do it try F1 or F2.

---

### Post by Murdererjim on 2011-04-28
I tried that but the screen is still black. The screen doesn't come on at all.

---

### Post by DrkOn on 2011-04-28
I had the same problem a few weeks ago, when I first installed... try to increase the screen brightness, that worked for me

---

### Post by HermanAB on 2011-04-28
Howdy,

The laptop may also have a corrupted suspend image.  You can usually force a reboot without trying the suspend image, by removing the battery and cycling power before rebooting, to ensure that all suspend information is flushed from RAM.

---

### Post by gauth91 on 2011-04-28
Dude you do one thing!Reset your laptop! First you remove your ram and place it again hope this will work!It works for me.Just give a try if you want!I cannot give assurance:confused:

---

### Post by jramshu on 2011-04-28
You don't get the HP splash screen either?
Is the hard drive spinning up?
How long did you wait with a black screen?
Did you burn your recovery disks for Windows?

---

### Post by Murdererjim on 2011-04-29
> **jramshu said:**
> You don't get the HP splash screen either?
Is the hard drive spinning up?
How long did you wait with a black screen?
Did you burn your recovery disks for Windows?
 
I don't get the hp screen. I have my recovery disks, but I don't know how I can use them if I don't even get the hp splash screen. The hard drive is spinning up, and the black screen lasts from the time I turn the laptop on until I turn it off.

---

### Post by Murdererjim on 2011-05-03
Should I just send it to hp? I need my laptop back. I'm using a desktop computer with only 96 mb of ram.

---

### Post by DogMatix on 2011-05-03
Could you connect the laptop to the desktop screen just to see if it is the laptop screen that is at fault?

---

### Post by jramshu on 2011-05-03
Did you try what gauth91 suggested? 
I have had a LOT of problems with windows vista on my HP G60. That's the main reason I put Ubuntu on it. I've not run across one that wouldn't auto-boot from cd.
Have you tried hitting the "esc" repeatedly when you turn it on?
I would try everything before sending it to HP, they can get expensive fast.

---

