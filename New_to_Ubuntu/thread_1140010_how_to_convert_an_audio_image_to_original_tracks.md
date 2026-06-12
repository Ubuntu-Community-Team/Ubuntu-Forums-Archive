---
title: "how to convert an audio image to original tracks?"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by camaron1 on 2009-04-27
Does anyone how or what program there is to easily convert an audio image file into the separate tracks, by using the cue file or any other way?
Any help would be welcome

---

### Post by sydbat on 2009-04-27
Not sure what you mean. What is the file extension called of this "audio image"? Is it .wav or .mp3 or .flac?

---

### Post by camaron1 on 2009-04-27
The file extension is mainly .flac, but could be .ape or anything.
Sorry I should have explain it better. Many people when ripping a cd instead of keeping the original tracks they just make it into one single track for the whole cd. My question is if there is an easy way to revert to the original track separation

---

### Post by kostkon on 2009-04-27
> **camaron1 said:**
> The file extension is mainly .flac, but could be .ape or anything.
Sorry I should have explain it better. Many people when ripping a cd instead of keeping the original tracks they just make it into one single track for the whole cd. My question is if there is an easy way to revert to the original track separation
For mp3 files you could use [*Mp3splt*]("http://mp3splt.sourceforge.net/"). If you have a cue file it will even do it automatically for you.

For Flac files, you could, for example, check [this blog post]("http://aidanjm.wordpress.com/2007/02/15/split-lossless-audio-ape-flac-wv-wav-by-cue-file/"), although it requires that you have a cue file.

Hope that helps.

---

### Post by logos34 on 2009-04-27
yep, you need the .cue file for that.

Either that or chop it up manually with an app like audacity

---

### Post by camaron1 on 2009-04-27
> **kostkon said:**
> For mp3 files you could use [*Mp3splt*]("http://mp3splt.sourceforge.net/"). If you have a cue file it will even do it automatically for you.

For Flac files, you could, for example, check [this blog post]("http://aidanjm.wordpress.com/2007/02/15/split-lossless-audio-ape-flac-wv-wav-by-cue-file/"), although it requires that you have a cue file.

Hope that helps.

That is probably was i was looking for, thanks for the link, i'll haver a look at it later on.

---

### Post by logos34 on 2009-04-27
I'm familiar with aidenjm stuffs page--used shtools quite a bit last summer to convert ape album images.  As you can see, even shntools requires a cue sheet (or toc file)

I just remembered [this page]("http://www.regeert.nl/cuesheet/")--never had to use it but hopefully you can find your cd cue sheet and plug it into mp3splt, k3b, shtools or whatnot

---

### Post by jamesisin on 2009-11-19
I simplified aidenjm's version.  Two lines of code:

[http://www.soundunreason.com/InkWell/?p=980](http://www.soundunreason.com/InkWell/?p=980)

I am currently working on an APE version and will publish that shortly.

---

