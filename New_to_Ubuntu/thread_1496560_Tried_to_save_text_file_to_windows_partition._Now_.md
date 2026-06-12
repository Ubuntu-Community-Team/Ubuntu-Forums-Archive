---
title: "Tried to save text file to windows partition. Now its an application file won't open."
date: 2010-05-29
forum: New to Ubuntu
---

### Post by MathMcC on 2010-05-29
I wrote a text file in gedit then saved it to the drive on which I have windows installed, hoping I'd be able to open it there. I couldn't even see it when logged into windows. And now that I'm back in ubuntu I see the files been saved as an application! (octet stream)

Is there anyway I can open the file now? Obviously it won't let me do it the standard way.

---

### Post by acrazyplayer on 2010-05-29
have you tried renaming it with .txt at the end?

---

### Post by MathMcC on 2010-05-29
Tried that. (Though it wouldn't let me rename in windows and would only let me rename in ubuntu when I copy-pasted it to the drive ubuntu is installed on.) And its just gobbldey-gook.

Think I'll give this up as a lost cause.

But a couple of other questions while I'm here:

As you can see this is my first foray into the world of ubuntu. And I like what I see. However I'm finding it to be much less snappy. Could this be due to the fact I've installed it on an older IDE drive (as oppose to the SATA I have Win 7 on)?

Also Ubuntu installed a driver automatically for my HP 2200D printer, but so far I'm never given the option to print in duplex mode (which I can do in Windows).

---

### Post by acrazyplayer on 2010-05-29
I can not help at all with printer issues as I dont have a printer and never really used one with ubuntu lol you can do a nice little benchmark to test your drives speed in ubuntu. just go to system--administration--disk utilty, then choose your hard drive and then choose "benchmark" make sure to do the read-only benchmark. let it run and see what it says. my results were something like 40mb min, 88mb max and 70mb average. mine is a 320gb 7200rpm sata hdd.

---

### Post by anewguy on 2010-05-29
I know some printer drivers in Linux don't support duplex, but not having your printer it would be foolish for me to comment on that.

However, yes an old IDE drive could be slower than a new SATA drive.  The buffer could be smaller, the transfer rate could be slower, the rotational speed could be slower.  And yes, this can make a noticeable difference in apparent speed.

As far as your file is concerned:

I haven't ever saved directly to the Windows disk - I've always used an interim media such as a flash drive or CD/DVD.  However, you may want to try "save as" in gedit, change the file type and change the "character encoding" option and the "line ending" option (if you don't change the line ending option to Windows, your files won't have the CR/LF at the end and will just be one big set of lines with an odd character each place a CR/LF was to be).

Dave ;)

---

