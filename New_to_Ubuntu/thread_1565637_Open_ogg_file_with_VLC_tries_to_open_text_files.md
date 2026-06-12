---
title: "Open ogg file with VLC tries to open text files"
date: 2010-09-01
forum: New to Ubuntu
---

### Post by Paddy Landau on 2010-09-01
I am hitting a bizarre error, and I'd like some help please.

From Nautilus (or from my Desktop), if I open an ogg file with VLC, it tries to open certain other text files.

Specifically, I find that if there is another text file in the same directory containing the ogg file's name, VLC tries to open it.

An example to explain:

[LIST]
[*]In a directory, I have a file [FONT=Courier New]aq.ogg[/FONT].
[*]I double-click (or use right-click) to open the file with VLC.
[*]VLC correctly opens [FONT=Courier New]aq.ogg[/FONT], but...
[*]VLC also tries to open the files [FONT=Courier New]asyo uaqs req.txt[/FONT], [FONT=Courier New]youaqeep.txt[/FONT] and [FONT=Courier New]youaqop.txt[/FONT]. Notice that these files all contain [FONT=Courier New]aq[/FONT] in their names, which is the name of the ogg file.
[*]VLC gives the error messages as shown in the screenshot attached.
[/LIST]
VLC ignores any files that don't have the extension .txt, and any files that don't have the ogg file name within it. (I've experimented with different names and they all do the same thing.)

Is this a bug I must report? Do you get the same results?

---

### Post by alphacrucis2 on 2010-09-01
> **Paddy Landau said:**
> I am hitting a bizarre error, and I'd like some help please.

From Nautilus (or from my Desktop), if I open an ogg file with VLC, it tries to open certain other text files.

Specifically, I find that if there is another text file in the same directory containing the ogg file's name, VLC tries to open it.

An example to explain:

[LIST]
[*]In a directory, I have a file [FONT=Courier New]aq.ogg[/FONT].
[*]I double-click (or use right-click) to open the file with VLC.
[*]VLC correctly opens [FONT=Courier New]aq.ogg[/FONT], but...
[*]VLC also tries to open the files [FONT=Courier New]asyo uaqs req.txt[/FONT], [FONT=Courier New]youaqeep.txt[/FONT] and [FONT=Courier New]youaqop.txt[/FONT]. Notice that these files all contain [FONT=Courier New]aq[/FONT] in their names, which is the name of the ogg file.
[*]VLC gives the error messages as shown in the screenshot attached.
[/LIST]
VLC ignores any files that don't have the extension .txt, and any files that don't have the ogg file name within it. (I've experimented with different names and they all do the same thing.)

Is this a bug I must report? Do you get the same results?

I have seen something similar with VLC and mpg files. I recall I edited a movie clip using Kino  and it created an index file with the same name as the mpg file. When opening the mpg using VLC it did play the file but came up with an odd error message to do with presence of the index file of the same name up to the idx suffix. I have no idea why vlc does that. Just rename or move the text file I suppose.

---

### Post by alphacrucis2 on 2010-09-01
Something to do with subtitle files?

[URL="http://forum.videolan.org/viewtopic.php?f=12&t=48730"]http://forum.videolan.org/viewtopic.php?f=12&t=48730
[/URL]

---

### Post by Paddy Landau on 2010-09-01
> **alphacrucis2 said:**
> Something to do with subtitle files?
It looks interesting, but I don't think so in this case.

I filmed the original video myself, and created the ogg file myself using PiTiVi. At no stage did I do anything to do with subtitles.

---

### Post by mc4man on 2010-09-01
Possibly it's an issue with the version of vlc you're using, if it's 1.0.X then if so, (a bug), it likely won't be fixed.
The 1.0.X series is EOL

Maybe try tools - Preferences - click show 'All' - Video, click on SubTitles/OSD and if enabled then disable 'Autodetect subtitle files'
(probably won't help but worth a try

---

### Post by Paddy Landau on 2010-09-01
> **mc4man said:**
> Possibly it's an issue with the version of vlc you're using, if it's 1.0.X then if so, (a bug), it likely won't be fixed.
I'm using the standard repository version, 1.0.6.

How do I get the later version?

> **mc4man said:**
> Maybe try tools - Preferences - click show 'All' - Video, click on SubTitles/OSD and if enabled then disable 'Autodetect subtitle files'
Ha! That works! Well done! =D>

I [posted in the VLC forum]("http://forum.videolan.org/viewtopic.php?f=13&t=82063"), so I'll add your workaround there.

---

### Post by Paddy Landau on 2010-09-01
> **Paddy Landau said:**
> How do I get the later version?
I found the solution of [how to install the latest version of VLC]("http://www.ubuntugeek.com/install-vlc-1-1-2-in-ubuntu-10-049-10.html").

But the new version also has this problem, so I still need to turn off the subtitles.

I'll mark this thread as solved, even though it isn't quite, because it's a VLC bug rather than an Ubuntu one.

---

### Post by andrew.46 on 2010-09-01
Many of the vlc PPAs are struggling with FFmpeg library issues so just be a little careful. Some interesting reading here:

c-korn ppa dead where to get 1.1.x now?
[http://forum.videolan.org/viewtopic.php?f=13&t=81146&start=15](http://forum.videolan.org/viewtopic.php?f=13&t=81146&start=15)

Any chance you could post one of the problem files somewhere? I suspect that the repository version of vlc is not built against libkate, although I am not 100% sure, and this might be at least part of the problem...

Andrew

---

### Post by Paddy Landau on 2010-09-02
> **andrew.46 said:**
> Many of the vlc PPAs are struggling with FFmpeg library issues so just be a little careful...
Thanks for the link. I'll watch out in case something stops working. So far, however, everything seems to be fine after the upgrade.

> **andrew.46 said:**
> Any chance you could post one of the problem files somewhere?
Oh, I tried with three different ogg files; two that I had created and one that was from the Internet. They all gave the same problem. If a text file contained the file name of the ogg file, the problem happened.

I'm curious whether you can duplicate the problem.

Based on the previous posts, it seems that VLC looks for any file [FONT=Courier New]*name*.txt[/FONT] where [FONT=Courier New]name[/FONT] is the name of the ogg file.

> **andrew.46 said:**
> I suspect that the repository version of vlc is not built against libkate
I'm not entirely sure what that means, but if you tell me how to check, I'll check it.

---

### Post by andrew.46 on 2010-09-02
Hi Paddy,

> **Paddy Landau said:**
> Oh, I tried with three different ogg files; two that I had created and one that was from the Internet. They all gave the same problem. If a text file contained the file name of the ogg file, the problem happened.

I'm curious whether you can duplicate the problem.

I created an ogg container holding video and audio and sat it next to variously labelled text files and could not reproduce the problem you have encountered. Mind you I am using a newer version of vlc. Do you have the link to the Internet ogg?

> 
[QUOTE=andrew.46]I suspect that the repository version of vlc is not built against libkate
I'm not entirely sure what that means, but if you tell me how to check, I'll check it.[/QUOTE]

It was a possibly idle speculation, libkate can read text and images embedded *within* an ogg container. You can test your own copy as follows:

```

andrew@skamandros~$ **[COLOR="Red"]cvlc -l | grep kate[/COLOR]**
VLC media player 1.2.0-git Twoflower (revision 87200ff)
  kate                   Kate overlay decoder

```

Oddly enough MPlayer does not seem to support Kate streams on my system, only vlc... But this is moving away from your rather odd problem :).

Andrew

---

### Post by Paddy Landau on 2010-09-02
> **andrew.46 said:**
> cvlc -l | grep kate
```
VLC media player 1.1.2 The Luggage (revision exported)
  kate                   Kate overlay decoder
```> **andrew.46 said:**
> I am using a newer version of vlc.
I had upgraded to 1.1.2 as per the instructions.

> **andrew.46 said:**
> Do you have the link to the Internet ogg?
Not any more, but I quickly made a new ogg, named sand.ogg, and the text file that I made was eggsandtoast.txt (which contains 'sand'). I've attached them in an archive.

Something that I discovered: If the text file is empty, VLC will ignore it. To duplicate this, you'd need a non-empty text file.

I use 64-bit. I wonder if that makes a difference?

> **andrew.46 said:**
> Oddly enough MPlayer does not seem to support Kate streams...
MPlayer almost never works for me since installing 10.04. That's why I use VLC.

---

### Post by andrew.46 on 2010-09-02
Hi Paddy,

> **Paddy Landau said:**
> Not any more, but I quickly made a new ogg, named sand.ogg, and the text file that I made was eggsandtoast.txt (which contains 'sand'). I've attached them in an archive.

Something that I discovered: If the text file is empty, VLC will ignore it. To duplicate this, you'd need a non-empty text file.

Well knock me down with a feather, I get the same error, looks like as you mentioned the text file has to have something in it. When I tested earlier I used an empty text file. The error in more detail:

```

[0x8095dcc] main input debug: creating demux: access='file' demux='subtitle' location='/home/andrew/Desktop/eggsandtoast.txt' file='/home/andrew/Desktop/eggsandtoast.txt'
[0x81c7ccc] main demux debug: looking for demux module: 3 candidates
[0x81c7ccc] vobsub demux debug: this doesn't seem to be a vobsub file
[0x81c7ccc] main demux error: option sub-original-fps does not exist
[0x81c7ccc] subtitle demux debug: Movie fps: -1.000000
[B][COLOR="Red"][0x81c7ccc] subtitle demux debug: autodetecting subtitle format
[0x81c7ccc] subtitle demux warning: failed to recognize subtitle type[/COLOR][/B]
[0x81c7ccc] main demux debug: no demux module matching "subtitle" could be loaded
[0x81c7ccc] main demux debug: TIMER module_need() : 0.272 ms - Total 0.272 ms / 1 intvls (Avg 0.272 ms)
[0x8095dcc] main input error: no suitable demux module for `file/subtitle:///home/andrew/Desktop/eggsandtoast.txt'
[0x8095dcc] main input error: VLC can't recognize the input's format
[0x8095dcc] main input error: The format of 'file:///home/andrew/Desktop/eggsandtoast.txt' cannot be detected. Have a look at the log for details.

```

Mind you, I am testing this with vlc-git so this should in fact be a fixable error, at least in git...

Andrew

---

### Post by Paddy Landau on 2010-09-02
> **andrew.46 said:**
> Well knock me down with a feather, I get the same error
So I now I know it's not just my computer.

> **andrew.46 said:**
> ... I am testing this with vlc-git so this should in fact be a fixable error, at least in git...
I'll take your word for it, as I have no clue what 'git' means (here in the UK it means a stupid or contemptible person :lol: ).

I suppose I should raise a bug report for VLC, as I've had no response to [my post in the VLC forum]("http://forum.videolan.org/viewtopic.php?f=13&t=82063").

---

### Post by Paddy Landau on 2010-09-02
I've raised a bug report on the VLC tracker.
[https://trac.videolan.org/vlc/ticket/4132](https://trac.videolan.org/vlc/ticket/4132)

---

### Post by andrew.46 on 2010-09-02
Hi Paddy,

> **Paddy Landau said:**
> I'll take your word for it, as I have no clue what 'git' means (here in the UK it means a stupid or contemptible person :lol: ).

As it does in Australia :). We are all victims here of Linus Torvald's sense of humour in naming the revision control software [he created]("http://en.wikipedia.org/wiki/Git_%28software%29"). vlc-git refers to the development version of vlc which is held in a git repository. I shall watch your bug report with great interest.

Andrew

---

### Post by JimOCR on 2010-11-14
To quote Maxwell Smart:  "Would you believe", ran into this combination bug and serious design flaw under that other OS (W2k if you care to know) trying to open an .mp3 file (since when do MP3s typically have subtitles?)  

The instructions to cure it are correct, would only add that that they need to be followed most carefully as the location of the parameter to fix is quite obscure, again was dealing with an audio file not a video.

File this under Ubuntu Linux even fixes problems on that other OP system.

Though to be fair the culprit is in VLC not the OS.

---

