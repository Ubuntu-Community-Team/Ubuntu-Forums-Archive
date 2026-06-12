---
title: "De-uglifying ubuntu"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by Luke M on 2011-07-04
The standard fonts are literally giving me a headache. They make my LCD monitor look like a poorly calibrated CRT. Fuzzy. I tried disabling anti-aliasing with mixed results. Some things looked much better, others much worse. Any tips would be appreciated, especially easy things to try.

---

### Post by WinterMadness on 2011-07-04
download the microsoft fonts if you prefer those

---

### Post by mikewhatever on 2011-07-04
My tip is, provide a lot more info about the problem. Describe the hardware and the software you use, as something is obviously wrong with either of those, unless of cause it is just your personal aesthetic taste. 

PS: A friendly advice, using trollish titles is counter productive. ;)

---

### Post by deconstrained on 2011-07-04
Main Menu -> System -> Preferences -> Appearance -> "Fonts" tab

Install more font packages if you don't like the ones available by default. There are plenty out there in the repos.

---

### Post by Luke M on 2011-07-04
> **deconstrained said:**
> Main Menu -> System -> Preferences -> Appearance -> &quot;Fonts&quot; tab

Install more font packages if you don't like the ones available by default. There are plenty out there in the repos.

 Thank you. With smoothing set to "none" in preferences, the menu fonts etc. look good. However, Firefox is still using fuzzy fonts. I'm using a 23" 1920x1080 LCD. The fuzzy fonts probably look great on a high-DPI screen (like a laptop), but not one like mine.

---

### Post by antmenj on 2011-07-04
> **Luke M said:**
>  I'm using a 23" 1920x1080 LCD.

Is ubuntu running at the above resolution?

System --> Preferences --> Monitor  (on my version)

---

### Post by dFlyer on 2011-07-04
> **Luke M said:**
> The standard fonts are literally giving me a headache. They make my LCD monitor look like a poorly calibrated CRT. Fuzzy. I tried disabling anti-aliasing with mixed results. Some things looked much better, others much worse. Any tips would be appreciated, especially easy things to try.

The nice thing about Linux is the ability to modify your desktop environment and use whatever font or desktop you want. What looks good to me may not look good to you. There are a lot of fonts in the archives find what you feels good to you.

---

### Post by nzjethro on 2011-07-04
You can change Firefox fonts in Edit > Preferences > Content > Fonts & Colors.
If it is a hardware/software issue, maybe post a screenshot so we can see what you mean by "fuzzy".

---

### Post by Luke M on 2011-07-04
> **antmenj said:**
> Is ubuntu running at the above resolution?

System --> Preferences --> Monitor  (on my version)

 Yes. But that's a good analogy - "smooth" fonts are a lot like using an LCD at a non-native resolution which is close to the native resolution. It creates eye strain because you are subconsciously trying to focus on a fuzzy image. I'm not picky about fonts at all. I don't care about fonts. I just want them to not be fuzzy.

---

### Post by mikewhatever on 2011-07-04
Are you sure the correct resolution and refresh rate for your monitor are selected? A lower then 1920x1080 resolution would usually produce fuzzy fonts. Some more font settings are hidden under the 'Details...' button in the 'Fonts' tab. Perhaps some if them will resolve the problem.

---

### Post by Luke M on 2011-07-05
I figured out the main problem. It's not anti aliasing by itself, but the "sub pixel rendering" feature which is so evil. I think I can tolerate grayscale antialiasing (though I would prefer fonts that were good enough not to need it). But that sub pixel stuff is toxic.

---

### Post by Dipper on 2011-07-05
Part of the reason I use Kubuntu is because Ubuntu is so ugly.  Aesthetics are important to me, so I understand where you're coming from.  If you choose to stick with gnome, what I would suggest is going to [www.gnome-look.org](www.gnome-look.org) and choosing a desktop theme that works for you.

---

### Post by Thras0 on 2011-07-05
I love the eye-candy in KDE too. Gnome can be beautiful in its simplicity , but sure needs alot more work for it.

As for the fonts issue, I had alot of problems with Open Office in Gnome. For some strange reason , it used to mess up the UI with most of the fonts I had installed on my system. Same goes for Oracles Virtual Box. Maybe it was just me.

---

### Post by Dipper on 2011-07-05
And of course, there's the Unity issue.  Ubuntu 11.04 should have been called "Venereal Vista".  Sticking with Kubuntu avoids that.

---

### Post by nzjethro on 2011-07-05
> **Dipper said:**
> Part of the reason I use Kubuntu is because Ubuntu is so ugly.

I don't think I'd go quite so far as to call GNOME (Ubuntu) "ugly". I think what it needs (as do KDE and Xfce) is some time spent making it look how you want it to look. No DE looks exactly how you want it to look on first boot, but with some time, any DE can look good, and no DE will look "ugly".
In my opinion, when first booting Kubuntu, Xubuntu, and Ubuntu, Ubuntu (GNOME) looks best. I found that Ubuntu looked polished on first boot, while Xfce and KDE looked slightly chunky, and in need of a tidy up, but this is just my opinion. :P

---

### Post by Dipper on 2011-07-05
Personal taste, I guess.  I will say that Ubuntu (Gnome) has come a long way.  The brown/yellow/orange color scheme used before 10.04 was not only ugly, but hideous, reminiscent of the contents of an unflushed commode.  I like the more purplish look. I suppose my last complaint about gnome is that its widgets look kind of XP-ish and not very modern.

---

### Post by dFlyer on 2011-07-05
Gnome as come a long way since the early 90's when it was still beta. The current gnome is very mature and I myself can't wait for Ubuntu to release a gnome 3 desktop environment. Unity is nice but not gnome.

---

### Post by mikodo on 2011-07-05
> **dFlyer said:**
> Gnome as come a long way since the early 90's when it was still beta. The current gnome is very mature and I myself can't wait for Ubuntu to release a gnome 3 desktop environment. Unity is nice but not gnome.

+1

I am still enjoying Gnome2 in Lucid. When I go to the next LTS, in the year before Lucid is not supported by Canonical, I hope that there is an option to use Gnome3 or Unity, with the ability to toggle between the two shells; maybe like we have with Gnome2 and KDE.

For me, that would be ideal!   ;)

---

### Post by Luke M on 2011-07-06
I think part of the problem I had with sub pixel rendering could be due to rotating the monitor 90 degrees. This means that the orientation of the sub-pixels changes, and perhaps the antialias setting does not change automatically to match. Just a theory. I have no intention of subjecting myself to the option ever again.

---

### Post by jtarin on 2011-07-06
> **dFlyer said:**
> Gnome as come a long way since the early 90's when it was still beta. The current gnome is very mature and I myself can't wait for Ubuntu to release a gnome 3 desktop environment. Unity is nice but not gnome.I think you mean the early 2000's. Gnome was only started in 1997.

---

### Post by jtarin on 2011-07-06
> **Luke M said:**
> I think part of the problem I had with sub pixel rendering could be due to rotating the monitor 90 degrees. This means that the orientation of the sub-pixels changes, and perhaps the antialias setting does not change automatically to match. Just a theory. I have no intention of subjecting myself to the option ever again.
You could consider the option of rotating your body 90 degrees to compensate.:P

---

### Post by Luke M on 2011-07-09
For future reference, the general procedure for de-uglifying ubuntu:

1) Disable antialiasing (or at least switch to grayscale). However, this exposes the weakness of the free fonts, so you also need to

2) install Microsoft truetype fonts (copy from any Windows installation)

What a difference!

---

### Post by Luke M on 2011-07-10
I found there is a subtle problem with copying over Windows fonts. The regular fonts work fine, but for some reason the bold version of the fonts are not used; instead you get a synthetic bold, which can look strange or ugly depending on the size.

Do this instead:

sudo apt-get install msttcorefonts

---

### Post by JRV on 2011-07-10
The first thing I do is get rid of the purple wallpaper, and change the font from Sans to FreeSans.

---

