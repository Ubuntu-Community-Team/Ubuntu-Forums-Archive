---
title: "ATRAC playback with Amarok or Rhythmbox?"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by julio_cortez on 2010-05-19
I bought a Sony Walkman NW-E005 more or less 3 years ago.
I know I should've avoided a Sony player but I was looking for something that would let me play my home-made house CDs without gaps between songs, with a good quality and with the chance to skip from a song to another (and the only format I could find that provided all of these features was ATRAC).

So now I'm wondering: I have lots of house CDs which I had to extract in *.mp3 format to listen to with Amarok in Linux, while I have them in ATRAC format to listen to with Sonic Stage when I'm in windows.

I don't need to be able to manage the player under Kubuntu (like described [here]("http://ubuntuforums.org/showthread.php?t=652298")) or to import new files, I only need to playback my already imported ATRAC library which is composed by more or less a  hundred of CDs.

So the question is: can Amarok or Rhythmbox (the latter also looks like having native gapless playback support) play ATRAC files?
Or is there another player capable of playing such files, possibly with 100% gapless playback (which is the real reason I went for an ATRAC player)?

---

### Post by Chronon on 2010-05-19
I was going to suggest a Rockbox simulator, but Rockbox does ATRAC3, not ATRAC.

---

### Post by julio_cortez on 2010-05-19
Thank you. I'll try and see what happens.

On a different note, even a player that has cue sheet support would do the trick (as I have ripped many CDs in both ATRAC to use with my Walkman when I'm out and with SonicStage when I'm in Windows and mp3 to use with Amarok when I'm in Linux).
I wouldn't mind writing the cue sheets for those mp3 files (even if it's a long and boring task if done by hand) to be able to skip from a track to another in Amarok or in any other player supporting cue sheets.

---

### Post by 3rdalbum on 2010-05-19
FFMPEG supports ATRAC3, so you could conceivably use the 'ffplay' command to play them. Assuming they are ATRAC3 anyway. There's gotta be a media player out there that uses FFMPEG to play audio files... surely?

Interesting to note: If your player is three years old, then it's probably the last to support ATRAC at all. 30 months ago I bought my first Walkman MP3 player, which did not support ATRAC at all, and none have since. In fact it came with a utility for converting your ATRAC music to MP3 format.

---

### Post by julio_cortez on 2010-05-19
Thank you. I'll also have a look at the ffmpeg codecs.
Hopefully there's a  player around which can use them. I think Exaile does, for example.
Now, it's just down to testing what works and what doesn't.

> **3rdalbum said:**
> If your player is three years old, then it's probably the last to support ATRAC at all.
Fortunately it looks so.
I was looking specifically for an ATRAC player (because of the gapless playback) and indeed that was the only one supporting ATRAC files.
Probably, actually, the last one.
In the bad luck (of course it's a Sony, it's kind of unsupported in Linux and even in Windows Sonic Stage isn't that solid) I guess I've been lucky :P

---

### Post by 3rdalbum on 2010-05-19
> **julio_cortez said:**
> Thank you. I'll also have a look at the ffmpeg codecs.
Hopefully there's a  player around which can use them. I think Exaile does, for example.
Now, it's just down to testing what works and what doesn't.


Fortunately it looks so.
I was looking specifically for an ATRAC player (because of the gapless playback) and indeed that was the only one supporting ATRAC files.
Probably, actually, the last one.
In the bad luck (of course it's a Sony, it's kind of unsupported in Linux and even in Windows Sonic Stage isn't that solid) I guess I've been lucky :P

Funnily enough (or maybe not), the Walkmans that came out after yours, and all ever since, work using simple drag 'n' drop on any operating system; I never used the earlier Walkmans but I heard that Sonic Stage was a travesty of computer code :-)

---

### Post by julio_cortez on 2010-05-19
> **3rdalbum said:**
> I never used the earlier Walkmans but I heard that Sonic Stage was a travesty of computer code :-)
Yes, indeed it has its flaws.

Not that I hadn't been warned, though: a friend of mine bought the same model of Walkman a couple of months before me, and she was already complaining about Sonic Stage when I got mine.

But, as I told before, I'm a house (and also trance, on a different extent) music enthusiast so I was looking for a player that supported "real" gapless playback, and Walkmen seemed the only ones supporting it (because of ATRAC).

I was also ready to face Sonic Stage in order to have gapless playback, and I must say that it's been the right choice in the end..
Now I only have to find a way to have gapless playback in Kubuntu, I think it'll be my homework in the next days :P

---

