---
title: "A couple font issues"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by Vunutus on 2009-04-22
I'm attempting to install a custom font for a MUD (basically a text MMORPG if you don't know what a MUD is). The MUD in question publishes two fonts, one as a .fon bitmap font, the other is a .ttf truetype font.

Both fonts are very similar (custom line drawing characters among other shapes), but the bitmap font is preferred for several reasons. After some research, I found out that .fon files are Windows specific, but there is a way to convert them. Every link I found about converting them, however, appears to be dead.

My second problem is actually a problem with the TTF font, although I suspect it will apply to the bitmap font if I get it working. I set up my custom gnome terminal profile to make the background black, set up the environment, and set the font. It correctly sets the font to the MUD's font, however, none of the special characters seem to work (which is the main point of having it). Any time the MUD outputs a line drawing character or other non-standard symbol, I see a small diamond with a "?" inside it.

I think the root of this problem lies with gnome-term's apparent inability to display nonstandard characters. The way the MUD font works is that it sets characters which are rarely used in standard English speech (accents, umlauts, foreign currency, etc) to be pictures of things (players, trees, walls, what have you). In this way, it can send those nonstandard characters and they will be converted to said pictures if the client is using the right font. Now, if I set the gnome terminal's font back to the default terminal font and tell the MUD to send those accents/umlauts/whatever, they display as a similar diamond with a "?". This leads me to believe that the problem is gnome terminal not handling those nonstandard characters. How can I fix this?

---

### Post by Vunutus on 2009-04-22
Bump.

---

### Post by Vunutus on 2009-04-23
> **Vunutus said:**
> Bump.

Seconded

---

### Post by Vunutus on 2009-04-24
> **Vunutus said:**
> Seconded

Thirded.

---

### Post by Vunutus on 2009-04-25
Bump again

---

### Post by Volt9000 on 2009-04-25
No idea if this will work, but it's something to try.
Did you try copying the .ttf file to /usr/share/fonts/truetype?

---

### Post by hw-tph on 2009-04-25
> **Vunutus said:**
> After some research, I found out that .fon files are Windows specific, but there is a way to convert them. Every link I found about converting them, however, appears to be dead.
You could try using [FontForge](http://fontforge.sourceforge.net/) to convert the bitmap font to a bitmap font type that is usable in Linux. I have done similar things with FontForge but it's several years ago now and at least back then FontForge wasn't the most straightforward program to use.

The second problem sounds like it could be related to the locale you're using. You could try setting the LC_CTYPE (character classification) environment variable to something else than the default - most likely you're using en_US.UTF-8, but try changing it to an ISO-8859 locale, along these lines: **LC_TYPE="sv_SE.ISO-8859-1" /usr/local/bin/myprogram** where myprogram is the MUD program you want to use.

Or even use some other terminal emulator like rxvt-unicode that you can play around with without messing up your "regular" Gnome Terminal settings.

Just a couple of ideas... Good luck.

---

