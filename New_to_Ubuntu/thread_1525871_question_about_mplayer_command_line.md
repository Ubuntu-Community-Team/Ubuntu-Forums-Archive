---
title: "question about mplayer command line"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by Old Jimma on 2010-07-07
Hi Ubuntu Community:

I use the following command line to record a radio program:

[PHP]mplayer "http://radioheartlandstream1.publicradio.org:80/" -ao pcm:file=/tmp/mystream.wav -vc dummy -vo null[/PHP]

I've read the man page on **mplayer**, and would be grateful if an **mplayer** expert can clue me in a little better about what all of the options in the line mean.

Also, I'd be interested in knowing whether **mplayer** can produce a **flac** file (instead of that **wav** file).

Thanks!
Phil Smith
Duluth, GA

---

### Post by RiceMonster on 2010-07-07
-ao Audio Output - specify the audio output driver, in this case, pcm, which is outputting to that wav file.

-vc Video Codec - use dummy video codec

-vo Video Output - in this case it is null, so it means do not use a video output driver.

Basically it's saying to output the audio for a file and don't output any video.

---

### Post by Old Jimma on 2010-07-07
Hi RiceMonster dude or dudette:

Thanks for your explanation.

Cut script. I couldn't resist!

Best regards,
Phil

---

### Post by andrew.46 on 2010-07-08
Hi Phil,

That is an mp3 stream so you can capture it directly as mp3:

```

mplayer -cache 2048 'http://radioheartlandstream1.publicradio.org:80/' \
        -dumpstream -dumpfile broadcast.mp3

```

Looks like the svn FFmpeg can save this stream as flac but I have not too much experience with saving streams in this way...

Andrew

---

### Post by nothingspecial on 2010-07-08
I didn`t think there was much point saving an mp3 as flac.

---

### Post by mcduck on 2010-07-08
You might also want to try Streamripper, which is a command-line tool specifically made for ripping web radio streams. It's able to do some nice stuff mplayer (and others like it) won't do, like automatically splitting songs into separate files and naming them (if the stream provides information about currently playing song).

---

