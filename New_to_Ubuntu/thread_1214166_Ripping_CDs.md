---
title: "Ripping CDs"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by The Grand Wazoo on 2009-07-15
I've been away from Gnome for a while, flirting with KDE, but we didn't get on very well and I've finally left her and come back.  Before I left, I'm sure I recall being able to rip CDs in 3 or 4 differing formats straight from the file browser.  Crucially this included the ability to rip an entire CD as a single file - very useful with live music.

Sadly, I can't seem to be able to do this any more (if I ever could:-k ).  Am I dreaming or am I missing something?  It's perfectly possible that it can be done by other means so if anyone can put me out of my misery I would be very grateful.

Thanks

---

### Post by Tibuda on 2009-07-15
Never seen this tool, I always used Sound Juicer. If you have used it from the file manager, perhaps you have used a [Nautilus script]("http://www.gnome-look.org/index.php?xcontentmode=188")?

---

### Post by ramnarayan on 2009-07-15
> **The Grand Wazoo said:**
>  Before I left, I'm sure I recall being able to rip CDs in 3 or 4 differing formats straight from the file browser.  Crucially this included the ability to rip an entire CD as a single file - very useful with live music.
Thanks

whats the programme called, uner KDE

am sure you can install that on Gnome as well, if not find an equivalent through synaptic

---

### Post by The Grand Wazoo on 2009-07-15
> **ramnarayan said:**
> whats the programme called, uner KDE

am sure you can install that on Gnome as well, if not find an equivalent through synaptic

Sorry, I meant I could do it in Gnome before I ventured over to the blue side.  There were many things I couldn't do adequately under Kubuntu which was why I returned.

danielrmt - If it was a Nautilus script, I must have got it from somewhere as there is no way I could have written it myself unfortunately.  I certainly didn't ever download anything like a script on that link you helpfully supplied.

---

### Post by nynoah on 2009-07-15
Not sure which program you are using before.  But the best program that I have used to rip and encode is Ripperx.

---

### Post by The Grand Wazoo on 2009-07-15
Guys

Thanks for the suggestions so far but none of those seem to do what I need them to do which is to rip and encode an entire CD as one file (unless I missed that bit when I tried them!).

Hey ho, I need to keep looking.

---

### Post by bapoumba on 2009-07-15
[https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping)

Does anything in there ring  bell?

---

### Post by SuperSonic4 on 2009-07-15
K3B does this as you may have found out while using Kubuntu.

abcde as a cli app may do the job

---

### Post by The Grand Wazoo on 2009-07-15
bapoumba - I believe you've cracked it!!!  Half way down the page is a reference to Audiocd:/ which is part of Konqueror.  I did have that installed sometime ago, before I went full on for KDE4 so I think that may be what I was thinking of.  As KDE4's ability to handle audio files is still somewhat suspect (other than KDE) I guess installing an old version of Konqueror may do the trick.

SuperSonic4 - KDE is actually pretty good.  The one thing it doesn't do (unless I can't find it or it needs a plug-in or something) is rip and encode an entire CD as one file.  I believe Audiocd:/ can do that.

Once again, many thanks for all your help.

---

### Post by andrew.46 on 2009-07-15
Hi SuperSonic,

> **SuperSonic4 said:**
> abcde as a cli app may do the job

abcde will certainly do the job. Have a look at this page:

abcde: Command Line Music CD Ripping for Linux
[http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html)

and note the use of the '-1' option briefly described there. The man page gives a few more details:

```

 -1 Encode the whole CD in a single file. The  resulting  file  uses
    the CD title for tagging. If the resulting format is a flac file
    with an embedded cuesheet, the file can be used as a source  for
    creating other formats. Use "-1 -M -o flac" for obtaining such a
    file.

```

All the best,

Andrew

---

### Post by Arup on 2009-07-15
> **nynoah said:**
> Not sure which program you are using before.  But the best program that I have used to rip and encode is Ripperx.

I second that, its the closest to Windows EAC.

---

