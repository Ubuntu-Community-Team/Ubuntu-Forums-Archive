---
title: "Seeking a good PDF viewer for Gnome"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by TheEvilOne6620 on 2009-08-02
Can anyone tell me of a good pdf viewer for a Gnome desktop?? I currently have Evince installed but it has no options whatsoever and I do not like its setup either.  I typically use Foxit Reader on Windows but the Linux version is no were near as feature rich.  I was thinknig of Adobe as a last resort but it takes forever to load and is a memory hog so I really dont want to have to go that route.

Are there any good ones?  From what Ive seen on Google it does not seem like there is anything at all that can compare to Windows pdf readers.

I guess as a last resort I would be willing to install a PDF reader that is for KDE if I have to.

---

### Post by credobyte on 2009-08-02
Adobe Reader works just fine for me ( search for acroread in Add/Remove ).

---

### Post by HermanAB on 2009-08-02
Kpdf, Xpdf and of course Adobe Reader.  It is actually a good idea to install the whole lot, since they all have their strengths and weaknesses.

Xpdf is interesting, since it doesn't use the same libraries as everybody else, so it can usually read a file that no other tool can.

---

### Post by sasho_zl on 2009-08-02
Well, "Okular", the KDE pdf reader is a good one.

---

### Post by binbash on 2009-08-02
There is also Foxit PDF Reader

---

### Post by llamabr on 2009-08-02
> **TheEvilOne6620 said:**
> Can anyone tell me of a good pdf viewer for a Gnome desktop?? I currently have Evince installed but it has no options whatsoever and I do not like its setup either.  I typically use Foxit Reader on Windows but the Linux version is no were near as feature rich.  I was thinknig of Adobe as a last resort but it takes forever to load and is a memory hog so I really dont want to have to go that route.

Are there any good ones?  From what Ive seen on Google it does not seem like there is anything at all that can compare to Windows pdf readers.

I guess as a last resort I would be willing to install a PDF reader that is for KDE if I have to.

I filed a feature request to evince a few years ago asking for a flag for fullscreen.  They said it was a dumb idea, since you can start it, and then press the fullscreen button.  They rejected my request.  I guess they like reaching over for the mouse more than I do.

Since then, I've used xpdf.  It's light, fast, very feature rich, and very configurable.  If that's what you mean by 'best' i'd give it a try.

---

### Post by Revolutionary101 on 2009-08-02
I like adobe reader the most.

---

### Post by wayfarer_boy on 2009-09-09
I just found out that there's a KDE4 version of the fantastic kpdf app.  I used to use this as it was feature-rich and reasonably fast (at least evince speed), as well as highly accurate (unlike xpdf which occasionally gets its kerning a little wrong).

The new KDE4 version is called Okular and is in Ubuntu's standard jaunty repos, so can be installed with:```
sudo aptitude install okular
```

---

### Post by Excedio on 2009-09-09
I guess I just don't understand the need for a feature rich PDF viewer. Evince works as it should, it allows you to view a PDF.

What exactly is everyone else doing that I am not?

---

### Post by pythonscript on 2009-09-09
+1 on xpdf. I use that on my ubuntu systems that don't run gnome, and it's fantastic. Very few dependencies, fast start time, etc. If you're looking for something lightweight, that's your solution.

---

### Post by NightwishFan on 2009-09-09
I like Evince a lot. The only problem I have with it is that you cannot drag the mouse to scroll the page. Or if you can, I do not know how. I always drag by habit, (Old okular/kpdf user) and a new window opens with whatever picture my mouse is over. A bit annoying but evince is really fast.

Also, you can set up compiz/metacity fullscreen mode to a keyboard shortcut in the GNOME preferences for keyboard shortcuts. I like using ctrl+alt+f. Most apps actually go into "fullscreen mode" if it is available. Other ones just remove the the titlebar and border and stretch over the panels. (Like KDE Kwin fullscreen)

---

### Post by Excedio on 2009-09-09
I don't know about you all, but F11 sends my Evince into fullscreen. Simpler than a three key combination.

---

### Post by wojox on 2009-09-09
> **NightwishFan said:**
> I like Evince a lot. The only problem I have with it is that you cannot drag the mouse to scroll the page. Or if you can, I do not know how. I always drag by habit, (Old okular/kpdf user) and a new window opens with whatever picture my mouse is over. A bit annoying but evince is really fast.

Also, you can set up compiz/metacity fullscreen mode to a keyboard shortcut in the GNOME preferences for keyboard shortcuts. I like using ctrl+alt+f. Most apps actually go into "fullscreen mode" if it is available. Other ones just remove the the titlebar and border and stretch over the panels. (Like KDE Kwin fullscreen)

I just use my arrow down button in Evince. Sit back and read.

---

### Post by shae on 2009-09-09
> **Excedio said:**
> I guess I just don't understand the need for a feature rich PDF viewer. Evince works as it should, it allows you to view a PDF.

What exactly is everyone else doing that I am not?

This is exactly what I was thinking :confused:

I use Evince all the time and it just works.

---

### Post by wayfarer_boy on 2009-09-10
> **Excedio said:**
> I guess I just don't understand the need for a feature rich PDF viewer. Evince works as it should, it allows you to view a PDF.

What exactly is everyone else doing that I am not?

You're right. I'd be using evince if I didn't need the features.

I work in the creative field, so exporting from pdfs is a must, and although I can use gimp, imagemagick, or sometimes inkscape or scribus to get at the pages of a pdf, I sometimes just need a reader that can export areas of the pdf cleanly and quickly.

okular does this very well by allowing me to make a selection around the area I want to grab, image or text, and copying it to the clipboard.  This feature is missing from the other apps.  It's also a good pdf reader :)

The thing is, I came to Ubuntu from a Mac background, and I only switched fully to open source around 4 years ago.  Since then I've found very few areas where I miss features I had on my Mac - but one of those, however, is a good native pdf reader like Apple's Preview.  You could convert any page to a jpg/pdf etc., had fast load time, rendered perfectly, and was nowhere near as bloated as Adobe's appalling osx 10.4 reader app.

I often wonder how often I've had to 'just do' since turning to open source, but when I think about it a bit more, it really isn't that much at all.  I'm probably more satisfied and competent with my open system now than I could ever have been with a proprietary OS.  I only have a few 'niggles' left...

---

