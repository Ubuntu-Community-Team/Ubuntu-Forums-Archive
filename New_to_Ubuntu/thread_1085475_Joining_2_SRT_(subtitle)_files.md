---
title: "Joining 2 SRT (subtitle) files"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-03-03
I have part 1 and part 2 of a movie and I plan on joining them using avidemux. However, I'm not sure how to join the two SRT files that accompany the movie. Any thoughts?

---

### Post by handy on 2009-03-03
I just had a look inside an .srt file with a text editor, & it looks like you should be able to join them quite easily.  The only potential sticking point will be how cleanly you join the two video files as you could throw out the lip-sync on the second half.

Here is some of an .srt so you can see what I mean:

[I]
2

00:05:43,543 --> 00:05:44,441

Weapon.



3

00:09:54,927 --> 00:09:56,007

It's time,

Freya.



4

00:09:56,228 --> 00:09:57,923

I told you before, Father



5

00:09:58,064 --> 00:10:00,157

the answer is no!



6

00:10:00,299 --> 00:10:02,961

Wulfric will be a good man!



7

00:10:03,102 --> 00:10:05,832

With you by his side

maybe a good king![/I]

---

### Post by abhiroopb on 2009-03-03
Thanks but the problem is this throws the time out of sync. Basically, the subtitles for the second video file starts at 0:00. They should actually be about 1 hour into the movie.

---

### Post by MrWES on 2009-03-03
> **abhiroopb said:**
> I have part 1 and part 2 of a movie and I plan on joining them using avidemux. However, I'm not sure how to join the two SRT files that accompany the movie. Any thoughts?


Try snagging a new sub file for your movie at subscene:

[http://subscene.com/]("http://subscene.com/")

---

### Post by handy on 2009-03-07
> **MrWES said:**
> Try snagging a new sub file for your movie at subscene:

[http://subscene.com/]("http://subscene.com/")

Amazing.

Everything is out there, you just have to know where. :D

---

### Post by viniciusfs on 2009-04-21
You can use Subtitles [1], it's a command line tool.

[1] [http://karasik.eu.org/software/](http://karasik.eu.org/software/)

---

### Post by serfcx on 2009-04-21
I have used this on-line service before with success
[http://submerge.delarue-berlin.de/]("http://submerge.delarue-berlin.de/")

---

