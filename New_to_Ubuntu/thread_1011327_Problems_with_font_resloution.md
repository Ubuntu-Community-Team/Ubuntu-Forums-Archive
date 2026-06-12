---
title: "Problems with font resloution"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by Drjim on 2008-12-14
I've recently started using Ubunto along with my windows system and enjoying it a lot.

One problem I have though is that things are hard to read on ubunto, especially on websites. The letters look blurred, indistinct margins with the background color bleeding in. This makes things stressful to read, especially with small type.

Is there a way to fix this or is it just a weakness of Ubunto or Linux?

Jim

---

### Post by gettinoriginal on 2008-12-14
Sure, System > Preferences > Appearance > Font  Set it for Subpixel smoothing Full hinting then go to details and set Smoothing as Subpixel and Hinting as Full.  Of course these can be set to your liking, so if those settings don't give you the results you want, try others until you find the right ones for you.  :p

---

### Post by dwasifar on 2008-12-14
> **Drjim said:**
> One problem I have though is that things are hard to read on ubunto, especially on websites. The letters look blurred, indistinct margins with the background color bleeding in. This makes things stressful to read, especially with small type.

+1 on gettinoriginal's advice about font smoothing.  You may notice that it takes a while for those changes to show up in Firefox.  If you see the fonts improve everywhere but Firefox, close and restart Firefox, or restart the computer.

Also: I've noticed that if you have installed the msttcorefonts package, or something that includes it, Firefox will often use those fonts because so many websites specify them.  You can find out if msttcorefonts is installed by opening any application that allows you to select a font; if Arial is there, msttcorefonts is installed.  The MS fonts often don't look as good in Firefox as some other fonts may.  

If this is your situation. you might want to go into Firefox settings (Edit > Preferences > Content >Fonts & Colors >Advanced), select fonts in the Bitstream Vera family, and uncheck the box to let websites choose their own fonts.  

Or you can just uninstall msttcorefonts.  I usually get rid of that if anything else installs it, and I never miss it.

---

### Post by Drjim on 2009-01-16
> **gettinoriginal said:**
> Sure, System > Preferences > Appearance > Font  Set it for Subpixel smoothing Full hinting then go to details and set Smoothing as Subpixel and Hinting as Full.  Of course these can be set to your liking, so if those settings don't give you the results you want, try others until you find the right ones for you.  :p

Thanks, that worked although I needed to set hinting for slight rather than full for my system.

Jim

---

