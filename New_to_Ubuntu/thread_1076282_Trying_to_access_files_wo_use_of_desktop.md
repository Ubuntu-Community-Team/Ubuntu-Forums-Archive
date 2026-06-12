---
title: "Trying to access files w/o use of desktop"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by Gelateria Punk on 2009-02-21
In trying to set up my audio driver (alsa), I foolishly followed the advice of some official-looking documents here on the forums.  I was following along without reading ahead first; and at one point I was told to essentially erase alsa, then reinstall it.  I guess this might be proper procedure under some circumstances, but I was running on Gnome.  AFTER the instructions list these two erase/reinstall commands, comes a warning that some Gnome users have experienced the destruction of "GDM" in so doing.  Then it gives a command IF this happens.  My screen went dark, and I was redirected to a terminal-like environment with no access to the desktop.  I have tried running from a live CD, but for some reason the computer won't boot to my CD drive.
All I want to do is retrieve some files (I know what directories they are in).  Is there a command I could type that would copy a directory's files onto a CD within this terminal-like environment?
When attempting the code for fixing gdm:
sudo apt-get install gdm ubuntu-desktop
I am given a message saying that there are "broken packages".
I plan to just reinstall a fresh version, (probably Intrepid) after I get these files off of my computer.

---

### Post by HunkirDowne on 2009-02-21
I've never done this.  But I did a quick search of the forum: "burn data cd terminal" and found this one as the most promising link.  I'll leave the rest up to you as I have zero experience burning from the terminal (command line, CLI, whatever ;-).

[http://ubuntuforums.org/showthread.php?t=1072620&referrerid=313805]("http://ubuntuforums.org/showthread.php?t=1072620&referrerid=313805")

HTH,
</HD>

---

### Post by Bendihossan on 2009-02-21
Have you tried changing your BIOS settings so that your machine will boot to CD on start up? Usually just before bootup there'll be instructions such as "Press F12 to enter Boot setup" or something like that. Pressing the delete key is another common keypress used to enter the BIOS menu.

---

### Post by yeats on 2009-02-21
> In trying to set up my audio driver (alsa), I foolishly followed the advice of some official-looking documents here on the forums.

I know you know this now, but you should have a basic handle on what's going on with these sorts of instructions before you just copy/paste into a terminal.  It's not that the instructions are bad - it's that things sometimes go wrong. :-)

> I have tried running from a live CD, but for some reason the computer won't boot to my CD drive.

Was your computer able to boot from CD before?  Sounds like you need to change your BIOS settings.  If you need help doing this, just post back and someone can help you.

> All I want to do is retrieve some files (I know what directories they are in). Is there a command I could type that would copy a directory's files onto a CD within this terminal-like environment?

Oh yes :-).  Many Linux users *live* in the terminal and IMHO at least *some* familiarity with it is required to (happily) use Linux.  There's not much hope that you can learn all this on the fly, but if you ever used MS-DOS in the pre-Windows days, this is a very similar (but better) environment.  

My recommendation, based on your apparent skill level would be to mess with the BIOS until you can boot to a live CD, but we can talk you through some command line stuff if that's the only option. :-)

---

### Post by Gelateria Punk on 2009-02-21
Well, I was able to boot to  CD before, and I've tried pressing 'delete' during boot-up.  Then it gives me options where I would like to boot from, so I arrow key to "DVD", press enter, but it can't find "resume image", so it boots back into the terminal (shell, or whatever).  Also, I didn't mean to insult anyone, I meant that I foolishly copied and pasted codes, should have said it that way.

---

### Post by yeats on 2009-02-21
> **Gelateria Punk said:**
> Well, I was able to boot to  CD before, and I've tried pressing 'delete' during boot-up.  Then it gives me options where I would like to boot from, so I arrow key to "DVD", press enter, but it can't find "resume image", so it boots back into the terminal (shell, or whatever).

If you're getting a "can't find resume image" message on boot, that means you're not booting from the CD - that's from your hard drive.  Are you able to run CDs/DVDs using this drive normally?

> Also, I didn't mean to insult anyone, I meant that I foolishly copied and pasted codes, should have said it that way.

I didn't take you that way :-).  It's easy to get frustrated about this sort of thing if you don't have a good grasp on the basics.

---

### Post by Gelateria Punk on 2009-02-21
Yes, this drive was working perfectly.  I moved the 'boot from dvd' option in BIOS to the top, but still: nada.

---

