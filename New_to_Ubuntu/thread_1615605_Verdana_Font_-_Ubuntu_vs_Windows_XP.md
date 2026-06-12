---
title: "Verdana Font - Ubuntu vs Windows XP"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by Mr.Bean on 2010-11-07
Hello, I recently installed the Verdana font into Ubuntu 10.10 from my Windows XP partition so web sites that use the font look normal to me.
However whilst Firefox now appears to be using the correct Verdana font, certain text on pages looks really rough and jagged. Especially bold text (see pic).
Font smoothing is disabled on both Ubuntu 10.10 and Windows XP (ClearType), and the same text from the same web page is not at all jagged on my Windows XP install.
Is Windows XP doing something different from Ubuntu to make fonts less jagged without font smoothing enabled?

Thanks for any replies.

Screenshot:
[[IMG]http://img641.imageshack.us/img641/9223/verdanaubuntu.th.png[/IMG]]("http://img641.imageshack.us/i/verdanaubuntu.png/")

---

### Post by Daniel0108 on 2010-11-07
Hi!
Go to System->Preferences->Appearance.
Click on Fonts tab.
Now select: Subpixel smoothing (LCDs).
Close the appearance window.
Now the font should appear okay :)
Yours,
Daniel

---

### Post by Mr.Bean on 2010-11-07
Hello, thanks for the quick reply.

Whilst the "*Subpixel smoothing (LCDs)*" option certainly helps with getting rid of the jagged edges it makes my fonts too smooth like ClearType enabled in Windows, which I assume is the desired result.

I think I actually turned off this option when I first installed Ubuntu as I prefer the text to look sharp rather than smooth.

The thing I don't understand is how is Windows XP able to make fonts such as Verdana more readable (in my opinion) than Ubuntu when font smoothing is disabled?

---

### Post by Daniel0108 on 2010-11-07
> **Mr.Bean said:**
> Hello, thanks for the quick reply.

Whilst the "*Subpixel smoothing (LCDs)*" option certainly helps with getting rid of the jagged edges it makes my fonts too smooth like ClearType enabled in Windows, which I assume is the desired result.

I think I actually turned off this option when I first installed Ubuntu as I prefer the text to look sharp rather than smooth.

The thing I don't understand is how is Windows XP able to make fonts such as Verdana more readable (in my opinion) than Ubuntu when font smoothing is disabled?
What about taking "Best Contrast" instead of Subpixel smoothing?
PS: When you click on "Details" you can change more of the font-type :)
Yours,
Daniel

---

### Post by mcduck on 2010-11-07
Also try setting the correct DPI for your display/resolution in the advanced font settings. Without a correct DPI setting there's no chance your fonts would ever render correctly. :)

If you don't know your display's DPI value, here's a nice calculator: [http://members.ping.de/~sven/dpi.html]("http://members.ping.de/~sven/dpi.html")

---

### Post by srs5694 on 2010-11-07
There are a lot of possible issues and causes. Others have addressed some, but I'll add some more observations and suggestions:


[list]
[*]I notice that the sizes of individual characters in your Ubuntu display vary, particularly for bold text. For instance, the "r" in "Forum" extends well above the surrounding "o" or "u" characters. Even within a character, this can be a problem, as in the "m". This type of problem can be caused by insufficient hinting in the fonts or by insufficient use of hinting information by the font renderer. Unfortunately, I've not been following Linux font rendering (done with Freetype and Xft) all that closely lately, so I can't offer specific suggestions to deal with this -- but see below.
[*]The last I did hear, Xft (which is now the predominant font rendering tool in Linux) was configured by files in /etc/fonts. The main configuration file is fonts.conf, but you should create a local.conf file to hold any tweaks you want to make. The GUI tools might adjust this file, or might do so in some other way. In any event, try Googling relevant filenames to track down documentation on how to tweak your font rendering using these configuration files.
[*]Fonts undergo revisions. It's conceivable that a different version of Verdana will look better on your system than the one you've copied from your XP installation. That said, I'm not familiar with the revision history of Verdana specifically.
[*]As a more extreme variant to the previous point, you could try using an entirely different font, such as Helvetica or Bitstream Vera Sans. The resulting page won't look identical, but it might look better than the same page rendered with Verdana, at least in Linux.
[*]You could try turning on font smoothing. Even if you don't like the effect in Windows, it's conceivable you'd prefer it in Linux, or at least you might prefer it to the unevenness you're seeing with font smoothing disabled in Linux.
[*]Font size can make a big difference. Even a small change might improve your display dramatically -- say, changing from 11 point to 11.2 point. This sort of change can just happen to hit a "sweet spot" in the interactions between algorithms, font scaling, etc.
[*]Font format (TrueType, PostScript, etc.) can make a big difference. AFAIK, Verdana is only available in TrueType format, but you might want to double-check this. There are also programs, such as [FontForge,](http://fontforge.sourceforge.net/) that will convert between formats. Typically, the converted font will look worse than the original, but there's a slim chance that this specific font at your specific sizes, etc., will look better. Since most of your problems are with the bold font, you should start with converting the bold version of the font.
[*]Speaking of which, are you sure you've actually installed the bold version of the font? For TrueType fonts, each font variant (regular, bold, italic, and bold-italic, typically) is in a separate file. If the relevant file is missing, the font renderer will try to fake it by using another version, but this faking is likely to be poor compared to using the correct file to begin with.
[*]This isn't directly applicable, but I have [a very old Web page](http://nessus.rodsbooks.com/wpfonts/wpfonts-screen.html) on fonts in WordPerfect for Linux. I mention this only because it's got some demonstrations of the sorts of tweaks that are possible -- changing the size and source of the font file, for instance.
[*]On a much broader explanatory note, each character of a font is defined by a series of lines and curves. When text is displayed on the screen, the computer computes where the lines go relative to the on-screen pixels, but the lines are likely to cut through pixels. The computer has to figure out which pixels should be dark and which should be light in the face of this ambiguity. High-quality fonts typically include "hints" that help the computer make this judgment, particularly for small font sizes; but the hints themselves and the hinting algorithms that apply the hints are both imperfect and can interact in unexpected ways for specific font sizes.
[*]As an elaboration of the previous point, the specific code used by Windows vs. Linux (Freetype and Xft) is of course different. IIRC, the Freetype developers basically had to guess and reverse engineer much of their implementation, so of course how they handle some things, particularly regarding hinting, is different from what Microsoft did. (Apple's implementation is also different from either Microsoft's or Linux's/Freetype's/Xft's.)
[/list]


I hope this helps.

---

### Post by Mr.Bean on 2010-11-07
Wow thanks for the informative reply *srs5694*, and thanks also *mcduck* & *Daniel0108*.
[QUOTE=srs5694]...are you sure you've actually installed the bold version of the font? For TrueType fonts, each font variant (regular, bold, italic, and bold-italic, typically) is in a separate file...[/QUOTE]

This solved my problem! Thank you very much, I didn't realise there were separate font files for each font variant and assumed that verdana.tff included bold, italic etc.

In case anyone else wants to install the verdana font manually from a Windows install, the required files, which now seem pretty obvious, are: verdana.tff, verdanab.tff, verdanai.tff, verdanaz.tff

---

