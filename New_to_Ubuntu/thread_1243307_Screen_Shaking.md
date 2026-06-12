---
title: "Screen Shaking"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by daniell59 on 2009-08-18
On occasion when I boot into Ubuntu 9.04 the desktop is "shaking"
At that point I shut the power off. When I re-boot it usually works without a problem. Any ideas about what is going on?

Thanks

---

### Post by Grenage on 2009-08-18
That sounds like a hardware issue to me, video card or something generating interference and on the way out.

---

### Post by daniell59 on 2009-08-18
> **Grenage said:**
> That sounds like a hardware issue to me, video card or something generating interference and on the way out.

It does not happen in Vista.

---

### Post by wojox on 2009-08-18
What video card and driver do you have installed.

---

### Post by Grenage on 2009-08-18
Then we can most likely rule out hardware.  Please give us all the information you can, including gfx card and drivers.

---

### Post by daniell59 on 2009-08-18
> **Grenage said:**
> Then we can most likely rule out hardware.  Please give us all the information you can, including gfx card and drivers.

I will get back to you on the hardware. I forgot what video card I installed.

---

### Post by daniell59 on 2009-08-18
> **daniell59 said:**
> I will get back to you on the hardware. I forgot what video card I installed.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814121259](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121259)

---

### Post by Grenage on 2009-08-18
Gravy, what driver are you using?

---

### Post by daniell59 on 2009-08-18
> **Grenage said:**
> Gravy, what driver are you using?

For Ubuntu, I did not install any driver. For Vista, the drive that came with the card.

---

### Post by Grenage on 2009-08-18
Look under System/Administration/Hardware drivers.

Do you have a "3D-accelerated proprietary graphics driver for ATI cards"? Is it enabled?

---

### Post by daniell59 on 2009-08-18
> **Grenage said:**
> Look under System/Administration/Hardware drivers.

Do you have a "3D-accelerated proprietary graphics driver for ATI cards"? Is it enabled?

I hope that this can clear it up.
Thanks

---

### Post by Grenage on 2009-08-18
OK! Activate it :)

---

### Post by daniell59 on 2009-08-18
> **Grenage said:**
> OK! Activate it :)

Thanks, I activated it.
Is it necessary for me to set the resolution. If so, how do I do it?

---

### Post by Grenage on 2009-08-18
Under Applications/Accessories you should now have an option for "ATI Catalyst Control Centre", you can change your res in there if you need to.

---

### Post by Sidewinder1 on 2009-08-18
The exact same thing happens to me from time to time. The "shaking" is most noticeable in the corners of your screen?
For me, simple fix; your graphics card/driver may be different. Go into: System---->Preferences---->Screen Resolution and change the amount of Hz in the Refresh Rate. When this problem occurs on my system, something changes it to 50 Hz, and screen shakes, all I do is switch back to 58 Hz. Problem solved. Keep in mind your optimal setting for Hz may be different.
HTH
Side

An interesting note: even with the correct 58 Hz setting, my GRUB screen still shakes. I could probably modify the Hz in BIOS but it ain't worth the effort.

---

### Post by daniell59 on 2009-08-18
> **Grenage said:**
> Under Applications/Accessories you should now have an option for "ATI Catalyst Control Centre", you can change your res in there if you need to.

The computer was off for several hours. I re-booted Ubuntu and all I got on the screen was some colors. I powered down, I tried it again and it worked perfectly. Any insight will be appreciated.

---

### Post by Grenage on 2009-08-19
Hi again daniell59,

Odd indeed, at what point did the colours kick in? Is it still happening?

Grem.

---

### Post by daniell59 on 2009-08-19
> **Grenage said:**
> Hi again daniell59,

Odd indeed, at what point did the colours kick in? Is it still happening?

Grem.

It happened when I first booted up in the morning. I cut the power, rebooted, and everything was fine.
Sometimes I the panels don't load, and I have to put them back.

---

### Post by stalkier on 2009-08-19
I know my screen shakes from time to time. I simply hit the auto-detect button on my lcd.

---

### Post by Grenage on 2009-08-20
> It happened when I first booted up in the morning. I cut the power, rebooted, and everything was fine.
Sometimes I the panels don't load, and I have to put them back

I am afraid I am pretty much out of ideas; ATI released some new drivers yesterday which might be worth a shot.  Other than that, I've got nothing.

---

