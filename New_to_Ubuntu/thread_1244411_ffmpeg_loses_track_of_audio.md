---
title: "ffmpeg loses track of audio"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-08-19
I have a simple wmv video clip 13 minutes long.

I wish to cut a short piece out of it starting at 5:02 for 2:10s.

I used the following command.
```
ffmpeg -ss 0:5:02 -t 0:2:10 -i original.wmv cut.wmv
```ffmpeg correctly saved the video extract. Unfortunately, it cut the *beginning* of the audio, instead of the matching audio.

What have I done wrong?

(I tried using avidemux, kino, kdenlive and cinerella, but they either didn't work or were too complicated for me.)

---

### Post by AliTabuger7 on 2009-08-19
I am not familiar with ffmpeg commands.

May I suggest PiTiVi? [http://www.getdeb.net/app/PiTiVi](http://www.getdeb.net/app/PiTiVi)

Sorry if that's not helpful.

---

### Post by credobyte on 2009-08-19
Try:
```
ffmpeg -i original.wmv -ss 00:05:02 -t 00:02:10 output.wmv
```

---

### Post by Paddy Landau on 2009-08-19
@credobyte:
Wow, what a difference the order makes!

It's a lot better now.

Unfortunately, when the clip starts, the sound is still running behind, but only about 4 seconds instead of the full 5:02.

It's as if I'd used -ss 0:5:02 for the video but -ss 0:4:58 (or thereabouts) for the audio.

Do you know what I can do to get the sound in sync? So close, yet so far!

---

### Post by Paddy Landau on 2009-08-19
> **AliTabuger7 said:**
> May I suggest PiTiVi? [http://www.getdeb.net/app/PiTiVi](http://www.getdeb.net/app/PiTiVi)
Sadly, PiTiVi doesn't support wmv files.

---

### Post by FakeOutdoorsman on 2009-08-20
FFmpeg lets you copy the audio and video and avoid re-encoding.  Almost like a copy and paste.  Try this:
```
ffmpeg -i original.wmv -ss 00:05:02 -t 00:02:10 -acodec copy -vcodec copy output.wmv
```
or
```
ffmpeg -ss 00:05:02 -t 00:02:10 -i original.wmv -acodec copy -vcodec copy output.wmv
```
The first command will decode the input file and then seek to *-ss*.  The second command will seek to *-ss* and then decode the input.  Or something like that.  I usually use the second command because it is generally faster on very large files.

---

### Post by Paddy Landau on 2009-08-21
@FakeOutdoorsman, thanks for the clarification.

Well, I had some really curious results, which I don't understand. Note that the original clip has a length of 0:13:06.

```
ffmpeg -ss 00:05:02 -t 00:02:10 -i original.wmv -acodec copy -vcodec copy output.wmv
```
[LIST]
[*]Right-click > Properties > Audio/Video > Duration: 0 seconds
[*]Totem didn't know how long the clip would be.
[*]The clip started from the *beginning*, so -ss had no effect for that.
[*]The clip ran for 5:02, so it treated -ss as the duration.
[/LIST]

```
ffmpeg -i original.wmv -ss 00:05:02 -t 00:02:10 -acodec copy -vcodec copy output.wmv
ffmpeg -t 00:02:10 -i original.wmv -ss 00:05:02 -acodec copy -vcodec copy output.wmv
```These both did the same thing as each other:

[LIST]
[*]Right-click > Properties > Audio/Video > Duration: 13 minutes 6 seconds.
[*]Totem thought it would be 13:06, too, but it was shorter.
[*]The clip started from 5:02, so -ss worked.
[*]The clip ran all the way to the end, ignoring -t.
[/LIST]
 ```
ffmpeg -ss 00:02:10 -i original.wmv -ss 00:05:02 -acodec copy -vcodec copy output.wmv
```Bizarrely, as follows.

[LIST]
[*]Right-click > Properties > Audio/Video > Duration: 10 minutes 56 seconds.
[*]Totem thought it would be 10:56, too, but it was shorter.
[*]The clip started from 5:02, so -ss worked.
[*]The clip ran all the way to the end.
[/LIST]
I've tried various other combinations, but I can't seem to limit the output to 2:10.

Any ideas?

---

