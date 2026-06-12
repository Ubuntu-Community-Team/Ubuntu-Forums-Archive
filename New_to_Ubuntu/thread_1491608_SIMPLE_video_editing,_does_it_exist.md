---
title: "SIMPLE video editing, does it exist?"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by El Lance-O on 2010-05-23
All I'm trying to accomplish is connect videos of different formats (.flv, .avi, .mp4) into one file, and do some simple editing to cut out a couple seconds of each video, and add transitions (SIMPLE fade-in/fade-out) for those cuts so it looks smooth. I'm trying to put this together for a presentation.

I have tried Avidemux, LiVES, Open Movie Editor, Openshot, Pitivi AND Kino, and none of these programs seem to be able to do this. The only one that came close was LiVES, but it was such a hassle (a 10 minute process) just to add a simple fade-out transition to a portion of the video.

Does anyone know how I can achieve this quickly and easily?

---

### Post by NightwishFan on 2010-05-23
I tried doing this (except the fades) with ffmpeg on the command line. I could not figure it out but it should be possible.

---

### Post by El Lance-O on 2010-05-25
I'm pretty sure it's possible, but I do not want to have to go to the command-line to do something this simple, that is ridiculous.

Any ideas?

---

### Post by NightwishFan on 2010-05-25
However FFMPEG can mux the streams without reencoding them, which preserves quality, as long as they are the same type of file.

Try Kdenlive, it reminded me of Sony Vegas.

---

### Post by SRST Technologies on 2010-05-25
The answer to your problem is simple: put some money into your computer to upgrade.  Ten minutes to do a fade effect on a video is going to be ten minutes in almost any program you are downloading because most of what you have talked about so far is just a GUI frontend to ffmpeg.

You're using really old and cheap hardware to video edit.  Don't get mad at the software for your hardware's shortcomings.

---

### Post by Arla on 2010-05-25
What problems are you having? I found Kino pretty decent (put together some video of my son singing in it) although video editing in general I find is one area that's fairly lacking in Ubuntu vs Windows.

Openshot seemed to have transitions, but seemed to be horrid on performance (actually trying to edit sucked).

---

### Post by brandon_h on 2010-06-07
I've found that OpenShot works quite well for simple quick editing like that.

---

### Post by derekeverett on 2010-06-07
I agree that I have had good luck with openshot. As long as you have ffmpeg installed it will produce nice files.

I have found **_[[COLOR="Red"]this[/COLOR]]("http://www.openshotusers.com/help/en/ar01s23.html")_** page very valuable for exporting options

---

### Post by rajeev1204 on 2010-06-07
I recommend KINO also , it has the eaiest UI for doing all that you require .And it works quite fine .

Only thing i dislike about it is that it converts all file formats into dv format and eats up HDD space.Not sure why it does that.

I would suggest OP have a little patience and also video editing does take time and resources.

Good luck .

Try these steps :

Import the clips  one by one ,
select each and click split scene at top toolbar to cut clips into pieces.
Select the sliced pieces and go to FX and add the effects.

Then copy paste those into a new window and export in desired format .




rajeev

---

### Post by Zill on 2010-06-07
+1 for Kino.  I used it recently (for the first time!) to make a short DVD with fade/in and fade/out of both sound and video.

It took a bit of fiddling around with test files before I figured out how it worked but the end result was worth it. :-)

Play around with the FX options, read the help and have a look at the net for how-tos.

---

