---
title: "Sudden change in font style?"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by ColdVerge on 2010-09-03
Hi,

Quite randomly the text on websites such as google/youtube and others have changed.  From what I can tell the font is the same, (same application font in settings--> appearance), but it  has become narrower - more notably height than width.

Any ideas why this happened or how to fix it?

If it helps, i had recently installed the repository apps hydrogen and linux multimedia studio, and the change occurred a minute or so after opening up lmms for the first time.

Thank you

---

### Post by SoFl W on 2010-09-03
Does ctrl+0 fix it?  (When you are in Firefox)

---

### Post by ColdVerge on 2010-09-03
unfortunately, no it doesn't

---

### Post by techningeer on 2010-09-03
> **ColdVerge said:**
> Hi,

Quite randomly the text on websites such as google/youtube and others have changed.  From what I can tell the font is the same, (same application font in settings--> appearance), but it  has become narrower - more notably height than width.

Any ideas why this happened or how to fix it?

If it helps, i had recently installed the repository apps hydrogen and linux multimedia studio, and the change occurred a minute or so after opening up lmms for the first time.

Thank you
Ubuntu has been changing their fonts. If you watch what Update Manager installs, you will see some font packages.

---

### Post by garvinrick4 on 2010-09-03
In Preferences to Content to Advanced

Do you allow pages to choose their own fonts? Or is it unchecked?

---

### Post by techningeer on 2010-09-03
> **garvinrick4 said:**
> In Preferences to Content to Advanced

Do you allow pages to choose their own fonts? Or is it unchecked?

What program are you using?

---

### Post by ColdVerge on 2010-09-03
> **techningeer said:**
> Ubuntu has been changing their fonts. If you watch what Update Manager installs, you will see some font packages.

Yep, i see them now

@garvinrick

There is no Content in preferences, just:

About Me
Appearances
Assistive Technologies
Bluetooth
Default Printer
...
Startup Applications
Windows

---

### Post by jtarin on 2010-09-03
I noticed the same thing last night when I had google.mail open and was browsing and came back to the mail and the fonts wer as you descibe.....this was in Chromium, but a few hours later they went back.

---

### Post by garvinrick4 on 2010-09-03
> **ColdVerge said:**
> Yep, i see them now

@garvinrick

There is no Content in preferences, just:

About Me
Appearances
Assistive Technologies
Bluetooth
Default Printer
...
Startup Applications
Windows Sorry I was looking at Firefox. I like to use msstcorefonts they are clear type and just look better. Some do not like to use any third party but the fonts and flash and such I do. 

Package: ttf-mscorefonts-installer
State: installed
Automatically installed: no
Version: 3.2
Priority: optional
Section: multiverse/x11
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 201k
Depends: wget, cabextract, xfonts-utils, defoma, debconf (>= 0.5) | debconf-2.0
Recommends: ttf-liberation, x-ttcidfont-conf
Conflicts: msttcorefonts (< 2.6)
Replaces: msttcorefonts (< 2.6)
Provides: msttcorefonts
Description: Installer for Microsoft TrueType core fonts
 This package allows for easy installation of the Microsoft True Type Core Fonts
 for the Web including: 
 
  Andale Mono
  Arial Black
  Arial (Bold, Italic, Bold Italic)
  Comic Sans MS (Bold)
  Courier New (Bold, Italic, Bold Italic)
  Georgia (Bold, Italic, Bold Italic)
  Impact
  Times New Roman (Bold, Italic, Bold Italic)
  Trebuchet (Bold, Italic, Bold Italic)
  Verdana (Bold, Italic, Bold Italic)
  Webdings
 
 You will need an Internet connection to download these fonts if you don't
 already have them. 
 
 NOTE: the package ttf-liberation contains free variants of the Times, Arial and
 Courier fonts. It's better to use those instead unless you specifically need
 one of the other fonts from this package.

rick@rick-laptop:~$

---

### Post by ColdVerge on 2010-09-04
Thanks you all! It's back to normal

---

