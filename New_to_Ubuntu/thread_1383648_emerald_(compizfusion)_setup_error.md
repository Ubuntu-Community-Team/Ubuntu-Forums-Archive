---
title: "emerald (compizfusion) setup error?"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by killazys on 2010-01-17
Hi Ubuntu, I'm having some difficulty with CompizFusion's theme manager Emerald. I'm aware of the bug where you have to run emerald --replace after selecting a theme, but that doesn't work for me. In Terminal, I ran it and I got this error:

```
(emerald:32050): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. The offending font is 'Vibrocentric 9.9990234375'

(emerald:32050): Pango-WARNING **: font_font status is: <unknown error status>

(emerald:32050): Pango-WARNING**: scaled_font status is: out of memory

(emerald:32050): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. The offending font is 'Vibrocentric 9.9990234375'

(emerald:32050): Pango-WARNING **: font_font status is: <unknown error status>

(emerald:32050): Pango-WARNING**: scaled_font status is: out of memory

(emerald:32050): Pango-WARNING**: shaping failure, expect ugly output. shape-engine='BasicEngineFC', font='Vibrocentric 9.9990234275', text='The quick brown fox jumps over the lazy dog.'
```Obviously, my error is in the Vibrocentric font downloaded from dafonts. The problem is, I ran fc-cache -fv after moving the fonts into my ~/.fonts directory, and I couldn't find them anymore. So I re-downloaded and did the same thing over again, to no avail. If I delete the fonts, it still gives me the same error output. I'm running XFCE on Linux Mint (which is basically Ubuntu, right?). Any ideas would be greatly appreciated, thanks..

EDIT: After running compiz --replace, everything works as it's supposed to except for titlebars: they all show up as a bunch of squares. I guess this is the error?

---

### Post by ankspo71 on 2010-01-17
Hi,
What titlebar font is your Emerald theme set to use? I think most of the emerald themes have an option to change the title font. I am attaching a screenshot so you can see where to change the titlebar font.

I'm not  familiar with xfce's font settings, but in gnome, you can change them in the appearence preference window of gnome. system menu > preferences > appearance . 

So make sure the emerald theme isn't looking for the font, and make sure xfce isn't looking for it too in xfce's theme preferences.

Hope this helps.
(see screenshot)

---

### Post by ankspo71 on 2010-01-17
Hi again,
Did you run the command fc-cache -fv again after deleting the unwanted font?  On a side note... I never needed that command before... so that might be one of the differences between gnome and xfce.

---

### Post by killazys on 2010-01-17
well.. yeah i ran that. i am using a different font now, but i was trying to get that font to work, actually xP

in addition, im having problems inputting asian characters. is that a new thread? or can i just ask all i want here? :D

---

