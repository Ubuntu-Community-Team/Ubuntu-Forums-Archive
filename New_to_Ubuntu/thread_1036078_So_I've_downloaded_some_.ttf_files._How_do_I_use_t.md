---
title: "So I've downloaded some .ttf files. How do I use these fonts in OpenOffice?"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by Obero on 2009-01-10
Please help.

---

### Post by damis648 on 2009-01-10
Open System>Preferences>Appearance and drag in the TTF files.:popcorn::popcorn:

---

### Post by SunnyRabbiera on 2009-01-10
They should work if you drop your .ttf files into the hidden fonts folder, to do this open up your home folder
then hit control+H to unhide and then drag and drop your fonts into it.
it should work

---

### Post by Kellemora on 2009-01-10
Hi Obero

You do not need to INSTALL fonts in Linux, just copy and paste them into your font's folder.

However, it's best to keep all of your fonts in the folder that was designed to keep them in!

That folder is located at /usr/share/fonts/truetype

In Linux, it's possible to accidentally have the same fonts installed in different places and each get read and used causing overlapping and blurred fonts or worse, font's that appear scratched out.

If you are running WINE, it's best to keep the fonts folder located at /home/user/.wine/Windows/Fonts completely empty.

Some folks recommend placing fonts in a hidden folder in your /home/user directory.  I strongly suggest you do not do this, for several reasons.  Fonts stored in your /home/user/.fonts directory are not available to anyone other than the user who's folder those fonts are stored in.  And this can EASILY lead to duplicate fonts on the system available to some programs regardless of where the fonts are stored.

I store some 250,000 fonts due to the nature of my work.  Scared the bejesus out of me when I moved some into a client folder and saw ones I shouldn't be seeing available in a text program.  I was new back then, well still am, so don't remember what it was I did that made them available when they shouldn't have been.  I think it was the fact I made the folder hidden is what did it.  But I don't remember for sure now.

FWIW:  It's easy to end up with duplicate font files when you are gleaning them from other places.  One source of the font may have used the file name MM8967.ttf for example, and another company may have used 1234567.ttf for the same font, and msttcorefonts may have that font in it already under BizetB.ttf
However, you CAN rename a font any name you want, it doesn't matter to the computer, it reads the font header file to find the name of the fonts you have available.  So, most of my fonts are named by the name the header gives, as well as a backup under the original name of the font stored elsewhere.  Because often a client will give me the FILE NAME the font he is using to make sure I have the same one for doing his edit work on.  It gets confusing when they say, I'm using font name MJ8967.ttf and MM8967.ttf in this document.  I would prefer he said BitstreamArrus or ArrusBT, it would save a lot of looking!

In any case, I think you caught my drift here and hopefully it will save you a few headaches later on down the road.

Keep all font's in the same folder (or folders within that folder, yes you can nest folders!).
And you can rename hard to find ones by their real name too!

TTUL
Gary

---

