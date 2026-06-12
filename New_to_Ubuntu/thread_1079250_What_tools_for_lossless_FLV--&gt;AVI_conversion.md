---
title: "What tools for lossless FLV--&gt;AVI conversion?"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by tarahmarie on 2009-02-24
Hi, all:

It seems that most of the guides out there involve Windows tools.  Are there any apps that will achieve a lossless conversion to avi from flv?

Thanks, all!

---

### Post by jolx on 2009-02-24
maybe have look at ffmpeg

---

### Post by tarahmarie on 2009-02-24
> **jolx said:**
> maybe have look at ffmpeg

Thanks!  I went and took a look; my problem is that after looking at the FAQs, I'm still not sure which opts give me lossless encoding.  I"m fine with either AVI or MPEG-3/4; I don't really care.  One or the other of those will work fine.  My concern is that flv is temperamental; I'd just like to get this encoded as losslessly as possible.  Any suggestions for  good opts for ffmpeg commandline work?

---

### Post by Anxious Nut on 2009-02-24
I think MEncoder is your answer, it's a free command line video decoding. Download it.

```
sudo apt-get install mencoder
```

All you have to do now is to open the terminal, move to your directory, and paste the following:

```
mencoder **YourVideo.flv** -oac lavc -ovc lavc -lavcopts abitrate=160 -o Output.avi
```

---

### Post by jolx on 2009-02-24
i don't know about most of the options, but to convert stuff i usually just go:
```
ffmpeg -i ~/Desktop/Example_file.flv "~/Desktop/Example file.mpg"
```

---

### Post by tarahmarie on 2009-02-24
So ffmpeg worked--but there's no audio.  Any reason why?

PS: the conversion's a bit lossy; maybe 15%.  Am I doing something wrong?

---

### Post by HavocXphere on 2009-02-24
mpeg is usually quite "lossy" on default settings. Its that way by design...its Filesize vs benefit kind of thing.

Your best bet is to boost the output filesize, max out the settings and use something like h264.

But your going to lose something with flv->avi no matter what you do.

There are lossless video codecs...but they are obscure and supported by pretty much no software/hardware. There's a list of them on wikipedia somewhere.

---

### Post by tarahmarie on 2009-02-24
> **HavocXphere said:**
> mpeg is usually quite "lossy" on default settings. Its that way by design...its Filesize vs benefit kind of thing.

Your best bet is to boost the output filesize, max out the settings and use something like h264.

But your going to lose something with flv->avi no matter what you do.

There are lossless video codecs...but they are obscure and supported by pretty much no software/hardware. There's a list of them on wikipedia somewhere.

ok, so, given that I can live with a small loss on conversion, how would I alter this commandline to adhere to your suggestions?  (Also, to ensure that there's audio in the footage)

```
mencoder sample.flv -oac lavc -ovc lavc -lavcopts abitrate=160 -o sample.avi
```

---

### Post by andrew.46 on 2009-02-25
Hi tarahmarie,

> **tarahmarie said:**
> So ffmpeg worked--but there's no audio.  Any reason why?

PS: the conversion's a bit lossy; maybe 15%.  Am I doing something wrong?

It might help to examine one of the files before you convert it:

```
ffmpeg -i myfile.flv
```

Post the *full* information generated here, including the command, and I am sure someone can suggest a suitable commandline and a reason why the sound did not appear.

Andrew

---

