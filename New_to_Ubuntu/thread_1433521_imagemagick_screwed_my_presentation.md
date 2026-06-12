---
title: "imagemagick screwed my presentation"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by nosyguy on 2010-03-19
I have been using ubuntu 2006. Today I made a presentation and was delayed for quite a long time (consequently delay the very tight schedule where several speakers were each given exactly 12 minutes for presentation and Q&A) as ubuntu-gnome could not detect the projector. To make things worse, someone offered his laptop and the pdf file on my usb drive could not open up, giving error msg that sort of said that the file was corrupted.

I used imagemagick to convert png slides into pdf and then used pdftk to merge them into a single pdf file. If I now use acrobat professional to convert and merge, the resulting file is fine. So the problem lies in the "convert" which outputs a format that reads fine on ubuntu, but can't even opens up in fedora (and of course windows).

Anyway, it's over already and I just want to let other users be aware that such issue may occur, and that it is still good to test certain things on other platforms instead of putting too much trust in open source software.

Anyway, I am a big fan of free software and will continue to use it. But it's disappointing that I have to boot up my windows (which I rarely do so) as programs such as this professional acrobat doesn't work well in wine, or open source alternative doesn't output format that conforms to format that is in widespread use.

---

### Post by Dayofswords on 2010-03-19
> **nosyguy said:**
> I have been using ubuntu 2006. 

ignoring your issue, but what is ubuntu 2006?
ubuntu does not use full year for versions, it would have to be 6.06(normally X.04, but it was late) or 6.10

both are old and the 6.10 is unsupported

---

### Post by nosyguy on 2010-03-19
I mean since 2006, but dropped the word "since" by mistake. It's 8.04 on my current office and home computers now

---

### Post by philinux on 2010-03-19
> **nosyguy said:**
> I mean since 2006, but dropped the word "since" by mistake. It's 8.04 on my current office and home computers now

Why not use open office presentation?

---

### Post by anaconda on 2010-03-19
A real horror story.

Why were you unable to connect a projector to your laptop?

I ususally use either the 
System>Preferences>Screen resolution
or (if nvidia display card)
nvidia-settings

to ennable external displays or projectors.(so that I have the 2 displays side-by-side) And it works wery well.

On the other hand I dont think the Fn-keys work (to enable external monitor) Maybe they work, but havn't tried yet. 

Do you think the problem is with imagemagic, or in pdftk? I have also made pdf:s with imagemagic (from .jpg:s), and they have worked very well. But I only used imagemagic. 
Where/why did you need the pdftk?  I usually just copy all the jpg:s to one folder, and then convert them to a single pdf with one command.
if I remember correctly:
convert *.jpg filename.pdf

---

