---
title: "Wierd characters displayed on help files."
date: 2008-12-14
forum: New to Ubuntu
---

### Post by Lenus on 2008-12-14
Hi,

I am using Ubuntu Heron (quite new to Ubuntu). 

I am getting weird characters displayed when viewing the help files (mostly HTML files). I searched for this bug in the web but found no help.

I am attaching an image file herewith which displays this bug. Can anyone please help me on this regard?

---

### Post by Michael.Godawski on 2008-12-14
hi, 

do you encounter this behavior only in html files or in "normal" text-files like .odt and .doc file, too?

Are you running Compiz?

---

### Post by Lenus on 2008-12-14
hi,

I encounter this only in html files. Do I need to add some plugins?

I have installed the live cd version of Ubuntu and don't think Compiz is being used by default. Correct me / lemme know how to check this :-).

---

### Post by Lenus on 2008-12-14
Any thoughts???

---

### Post by Kellemora on 2008-12-14
Hi Lenus

Have you installed any fonts on your own, other than the ones that loaded with the CD, or did you load any programs that come with fonts.

I'm asking because some of the font problems (not the one you are displaying though) occur when two of the same font is loaded in two different font seek locations on your hard drive.

In the case of what I'm seeing in your image, it appears that the desired font is substituted for a different font that is not installed.

May I suggest that you go into Synaptic Package Manager and install msttcorefonts and see if that clears up your problem.

Synaptic Package Manager is located under System in your top panel, then click on Administration and look down the list that opens up for Synaptic Package Manager and click on it.
It will take a few seconds for it to load.  Then scroll down that long listing until you find msttcorefonts and place a checkmark in front of it.  This will cause a pop-up asking if you want to check it, select yes, then select APPLY, you will then have to select APPLY again at the top of the screen for the fonts to install.

Give that a try and if that don't cure the problem, post back again.

TTUL
Gary

---

### Post by Lenus on 2008-12-15
Hi Gary,

Thnx for the great insight. 

Installing msttcorefonts didn't solve the problem. Do we have any other workarounds?

---

### Post by Kellemora on 2008-12-15
Hi Lenus

For one, you'll hear folks say to put files in a hidden folder named .fonts in your home directory.  DON'T DO IT!

Put them where they belong! TrueType fonts would go into the folder named truetype located at /usr/share/fonts/truetype

You can add folders into the truetype folder to keep font sets filed separately with no problems at all.

You do not have to INSTALL fonts, just copy n paste them into the folder you want to keep them in.

If you ever get unreadable text after loading a font, it's often because you have two of the same font loaded where it can be read from and it's appearing twice on the document offset just enough to make it blurry or weird looking.

Many of us acquire new fonts from various sources, sometimes they come in a package where all the fonts are stored under a file recognized by a number.  EG 1234567.ttf
Which as you can see is no help in identifying your fonts, or keeping them together.
You CAN rename a font without affecting how it works, because with fonts, the font name is INTERNAL to the program.
In other words, it's OK to rename 1234567.ttf to it's true name or something recognizable to you.  

Most of my fonts folders are named by the manufacturer of the font.  For example, my Arrus font set is in a folder named, ttfBitstreamArrus.  This keeps all Bitstream proprietary fonts together in my file listing.  You may prefer to keep them with the actual font name in the lead, ttfArrusBitstream so your files are in alphabetical order by the name of the font.

Here is a Scenario to be wary of!
You buy a new printer and it comes with a set of fonts gratis.
You copy those fonts to your fonts folder thinking all those fonts are different than what you have due to the NAME assigned to the font as the filename.
They may have named the filename Cooper Heavy and you already have that font under the name Cooper Black.  Since the computer sees the hidden name inside the font itself, suddenly you get blurred text on a page that used Cooper Heavy.

Just go through your fonts named Cooper with a FontViewer and read the REAL NAMES of those fonts that appear when you view fonts and you will find two with the same name appearing.
Remove one of them and everything should start working just fine again.  Keep either the Newest or the Largest more complete file.  Don't always go by the latest date though, some fonts are issued as partial and some are issued as complete.  Going by dates alone you may end up deleting a full font set for a partial one distributed by some hardware vendor.

Also, many programs come with fonts proprietary to that program, and although they work in other things and can be used for other purposes just fine, we easily forget that a particular font MUST be installed for program xyz to function properly.  So if a particular program requires a proprietary font, make a font folder with that program name on it so you remember that and don't delete or remove it.  It's just to easy to go through fonts using a font viewer and say, ugh, that's ugly, don't need it for sure.  Then Wham, one of your favorite programs stops working since it can't find it's proprietary font set.

This is just one of the many things that makes Ubuntu so GREAT and user friendly!  It's just learning all these neat features that can sometimes become a daunting and overwhelming task.
It's convenience things like this, that are IMPOSSIBLE to do in WinDOZE, why I like Ubuntu so much!

TTUL
Gary

---

### Post by Kellemora on 2008-12-15
Hi Lenus

I just noticed that you said it DIDN'T help!  I misread it, thought you said DID help.

This trick MIGHT work, but I don't know for sure.

Copy the .html file that is giving you the problem.
Paste it into Open Office Writer.
Highlight the messed up word.
Look at the top where it shows the font set used for that word.
Check to see if you have that particular font in your fonts.

Also, check to make sure it's not being SUBSTITUTED with another font that does NOT have the full character set.
or that another font is hiding in /usr/local/share/fonts

Off the top of my head I don't remember where the substitution tables are located.  Could be /etc/fonts/fonts.conf maybe.

I have a UPS truck backing up to the loading dock, so have to run!

TTUL
Gary

---

### Post by Lenus on 2008-12-16
Hi Gary, 

Appreciate your detailed way of getting on to resolve this issue !

But the simplest workaround (which i found accidentally) is unchecking the 'Use system fonts' check box in Edit->Preferences.

Does this convey you more on the problem I am facing with?

---

### Post by Lenus on 2008-12-17
Any thoughts Gary?

---

### Post by Lenus on 2008-12-19
Hope ur busy but thnx for the great response.

---

