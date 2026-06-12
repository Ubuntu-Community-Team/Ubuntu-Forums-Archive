---
title: "Bitrate for music on my phone"
date: 2011-07-30
forum: New to Ubuntu
---

### Post by ricardisimo on 2011-07-30
I've been synching music to my phone using rhythmbox (not too fond of Banshee for whatever reason), and I'm finding that the files that wind up on the phone are of a wildly varying quality - anywhere from 400+ kbps all the way down to the 64-ish range. What gives. Most of the source files are flac, but obviously, we're talking about a phone playing through little headphone nubs, so I don't want to waste all that space.

How do I get all of the audio files on my phone to be in the 128 kbps range? Thanks.

P.S. - I don't think it matters, but the phone is a Sony Ericsson Xperia.

---

### Post by cariboo on 2011-07-31
I'd suggest converting the files to mp3, as you said, there isn't much advantage to using flac with earbuds.

Check the various scripts located [here]("http://www.linuxtutorialblog.com/post/solution-converting-flac-to-mp3")

---

### Post by Redblade20XX on 2011-07-31
Audacity comes to mind but I'm not sure for batch conversions.

---

### Post by ricardisimo on 2011-07-31
Well, I wound up converting all of them to low bitrate mp3s with soundconverter, into a special folder that I could later delete. It works, but it's a *lot* of work.

Rhythmbox does on-the-fly conversion of all of my audio files no matter what format the original file (except 24-bit flac, but that's a completely different problem) for the purposes of synching portable media players. I guess my question had to do with editing the default configuration of whatever plugin in rhythmbox (or gnome) determines how it does this. Does anyone know how to do this?

---

