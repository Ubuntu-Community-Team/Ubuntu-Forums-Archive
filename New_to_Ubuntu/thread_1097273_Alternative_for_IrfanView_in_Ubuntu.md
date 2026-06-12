---
title: "Alternative for IrfanView in Ubuntu"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by The Bright Side on 2009-03-15
Hi!

I've been trying to get IrfanView 4.23 to run under Wine, but to no avail. I had it running once before I re-installed, but I can't get it to run again. In any case, I'd actually like to avoid using Wine to emulate awesome Windows programs, so here's my question: do you guys know a good alternative to IrfanView?

I hear the XnView is supposed to be very good, but on that program's homepage I can only get RPM packages for x86 systems, I am using Ubuntu 8.10 64 bit though and there's no way I can get it installed. Anybody got a link for a 64 bit package of the latest XnView?

Thanks!

---

### Post by sdowney717 on 2009-03-15
how about inkscape?
[http://en.wikipedia.org/wiki/Inkscape](http://en.wikipedia.org/wiki/Inkscape)


[http://www.boekhoff.info/?pid=linux&tip=install-irfan-view-on-linux](http://www.boekhoff.info/?pid=linux&tip=install-irfan-view-on-linux)

---

### Post by NE Key on 2009-03-15
When I used windows some years ago I thought irfanview was excellent.

Does Gimp meet that need ? Or is it too complicated ?

---

### Post by Bryantos on 2009-03-15
Personally, I believe a simple understanding of GIMP beats everything Irfanview has to offer. I hardly used Irfanview when I was on Windows, but I know GIMP is more powerful. There are are plenty of online tutorials and forums out there for GIMP that will give you a very good understanding of GIMP.

[Gimp Talk]("http://www.gimptalk.com") is where I learned my basics for photo manipulation.

If you give it a try, I hope it works out for you. :D

---

### Post by ELD on 2009-03-15
Gimp may be more powerfull but for quick edits, cropping etc it's overkill.

There used to be a program that shipped in ubuntu by defualt but newer versions don't damn annoying as it was a good program.

Edit > i think it was "gthumb".

---

### Post by Slim Odds on 2009-03-15
I used IrfanView years ago on Windows, but switched to Xnview.

Xnview also has a linux version, though I have not tried it.

I think that it will work in WINE, but I haven't tried that either.....

---

### Post by chrisod on 2009-03-15
I use Picasa for quick edits, resizing, red eye, etc.

---

### Post by egalvan on 2009-03-15
> **ELD said:**
> 
There used to be a program that shipped in ubuntu by defualt but newer versions don't damn annoying as it was a good program.

Edit > i think it was "gthumb".

I'm running Hardy  8.04.2

"gthumb' shows in Synaptic.

Is this it?

[I]an image viewer and browser 
gThumb is an advanced image viewer and browser. It has many useful
features, such as filesystem browsing, slide show, image catalogs, web
album creation, camera import, image CD burning, batch file operations and
quick image editing features like transformation and color manipulation.

It's designed for GNOME 2 desktop environment and uses its platform. For
camera import feature, the gPhoto2 library is used.

Homepage: [http://gthumb.sourceforge.net/](http://gthumb.sourceforge.net/)[/I]

---

### Post by lovinglinux on 2009-03-15
Why do you need InfranView? (The question could sound stupid, but it isn't. )

- image editing 
- photo editing
- batch conversion
- image collection browsing 
- image catalog/organizer (tags, categories, EXIF, IPTC)

What types of images do you work with?

- clipart, screenshots, logos, web stuff in general
- photos

What formats do work with?

- raw
- tiff
- jpg
- gif
- bmp
- others

These are some of the possibilities that can influence the choice of application you need.

---

### Post by presence1960 on 2009-03-15
> **The Bright Side said:**
> Hi!

I've been trying to get IrfanView 4.23 to run under Wine, but to no avail. I had it running once before I re-installed, but I can't get it to run again. In any case, I'd actually like to avoid using Wine to emulate awesome Windows programs, so here's my question: do you guys know a good alternative to IrfanView?

I hear the XnView is supposed to be very good, but on that program's homepage I can only get RPM packages for x86 systems, I am using Ubuntu 8.10 64 bit though and there's no way I can get it installed. Anybody got a link for a 64 bit package of the latest XnView?

Thanks!

Give gimp a shot. At first I **_thought_** I didn't like it. But as I used it more and became more familiar with it I realized it was "the change" that was what I disliked. this is human nature, it is natural to resist change. I am not a professional photograher, but I literally have thousands of pics I took with my digital camera. Gimp is way better than Irfanview- just give yourself time to learn it.

---

### Post by lovinglinux on 2009-03-15
> **presence1960 said:**
> Give gimp a shot. At first I **_thought_** I didn't like it. But as I used it more and became more familiar with it I realized it was "the change" that was what I disliked. this is human nature, it is natural to resist change. I am not a professional photograher, but I literally have thousands of pics I took with my digital camera. Gimp is way better than Irfanview- just give yourself time to learn it.

InfranView is a completely different application. Gimp is an image editor. That's it. What I think he needs is a image browser/organizer with editing capabilities. If this is the case, then [Digikam]("http://www.digikam.org/") would be the best option in my opinion. Besides, Gimp works only with 8 bits.

Digikam is in the repositories. To install, just run the command below:

```
sudo apt-get install digikam
```

---

### Post by presence1960 on 2009-03-15
> **lovinglinux said:**
> InfranView is a completely different application. Gimp is an image editor. That's it. What I think he needs is a image browser/organizer with editing capabilities. If this is the case, then [Digikam]("http://www.digikam.org/") would be the best option in my opinion. Besides, Gimp works only with 8 bits.

Digikam is in the repositories. To install, just run the command below:

```
sudo apt-get install digikam
```

My bad if he was looking for an image browser, i took it he was looking for editing functions. But that's the strength of this forum, we get many opinions and ways of doing things that work for a variety of people. Then we can choose the one that best fills our needs.

---

### Post by The Bright Side on 2009-03-16
Hey guys, thanks for all the suggestions! In fact, getting acquainted with Gimp is very high up on my to-do list (I'm entirely new to Ubuntu itself). I also want to explore GimPhoto, which is supposed to be very good.

However, as ELD says, as an IrfanView replacement, I'm looking for a very lightweight image viewer for the quick everyday tasks. It should have basic image editing tools like red eye, color correction, quick resizing, cropping, rotating etc. - Irfan View was perfect for that, it was up in no time and quick and easy to handle.

For the more sophisticated tasks, I'll definitely get acquainted with Gimp.
I think I'll give Picasa a shot, I've been hearing it mentioned a lot.
Any other ideas are welcome!
Thanks guys :-)

---

### Post by namaku0 on 2009-03-16
gthumb for Gnome or...
gwenview for KDE.

Others: [http://www.gnomefiles.org/subcategory.php?sub_cat_id=35](http://www.gnomefiles.org/subcategory.php?sub_cat_id=35)

---

