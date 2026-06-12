---
title: "Monkey audio conversion"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by BurnChao on 2009-01-28
I've googled a lot over this, but all the info I find is out of date.

I have a ton of .apes with .cues. I want to split them into tracks, and convert them to another format (mp3 or flac, whatever I can get advice for). (I don't care the order. Convert then split, or split then convert.)

Everything I can find out about Monkey Audio deals with Gutsy or older versions of Ubuntu. And from what I've found out, Intrepid (I'm using Intrepid) has native support for Monkey Audio, which messes up all the tutorials I've found.

How can I convert and split apes?

---

### Post by Magnes on 2009-01-28
[http://aidanjm.wordpress.com/2007/02/15/split-lossless-audio-ape-flac-wv-wav-by-cue-file/](http://aidanjm.wordpress.com/2007/02/15/split-lossless-audio-ape-flac-wv-wav-by-cue-file/) - I always use this guide. This line does it:

cuebreakpoints sample.cue | shnsplit -o flac sample.ape

You will loose the tags though (the part about restoring tags from cue doesn't work for me).

---

### Post by BurnChao on 2009-01-28
Yeah, I found that guide, but it's written 2 years ago, and is out-of-date, using non-free mac, when Intrepid (according to Launchpad) has native support of Monkey Audio. So I get errors.

(I don't really mind losing the tags. the apes have little tagging anyways, and I go through and re-tag everything to be just how I like it. EasyTag *is* easy.)

---

### Post by BurnChao on 2009-01-28
bump

---

### Post by zvacet on 2009-01-29
You can try [this #5.]("http://ubuntuforums.org/showthread.php?t=323639&highlight=audio+convert")

---

### Post by BurnChao on 2009-01-30
Thanks zvacet, I'll try that for the conversion (for future reference, it's the Perl Audio Converter, found [here]("http://pacpl.sourceforge.net/")). That looks like it help solve one half of the problem. Now I just need a cue splitter.

---

