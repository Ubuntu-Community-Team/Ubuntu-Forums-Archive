---
title: "Is there a program that can &quot;bleep&quot; out curse words in for .avi (or any other)format?"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by davidstri on 2009-03-23
I wanted to edit a movie of it's bad words by adding loud beeps, or if there isn't any program that can do that, maybe just silence. I looked, but I can't find any.

---

### Post by llamabr on 2009-03-23
I had a friend who had an uncle who bought something for his tv that did this.  That guy was a wacko.

I think he bought it at some christian bookstore.  Check there.

---

### Post by cybergalvez on 2009-03-23
> **davidstri said:**
> I wanted to edit a movie of it's bad words by adding loud beeps, or if there isn't any program that can do that, maybe just silence. I looked, but I can't find any.

Your kidding right, you want a program that will scan essentially an audio stream and find "bad words" and remove/replace them.  The best you can do is edit the audio stream your self and when you find an offensive phrase replace the segment with anything you want.

---

### Post by sailthesea on 2009-03-23
If you don't want to hear swear words make a choice in what you listen to
Censoring things yourself won't work because you will just see/hear it anyway 
 Or maybe friends wacko uncle has the answer!

---

### Post by jolx on 2009-03-23
You could use ffmpeg to extract the audio from the movie, edit the audio using audacity. Then use ffmpeg to make a copy of the movie without an audio track. Then use ffmpeg once more to combine the edited audio track with the video that has no sound.

or just stop being offended ;)

---

### Post by lovinglinux on 2009-03-23
Identifying words on an audio stream is not an easy task, even for advanced speech-to-text applications. 

Extracting the audio stream from the avi container and editing it manually is the easiest way, but time consuming.  You could at least download the video subtitles and search for the bad words using any text editor, then annotate the time of the sentences with bad words, to facilitate editing the audio. This way you don't have to listen the entire stream.

> **jolx said:**
> You could use ffmpeg to extract the audio from the movie, edit the audio using audacity. Then use ffmpeg to make a copy of the movie without an audio track. Then use ffmpeg once more to combine the edited audio track with the video that has no sound.

or just stop being offended ;)

He could avoid one of the steps above by simply converting the original into mkv, using mkvtoolnix, because this tool allows to remove audio streams and add new one in a single procedure. This is also really fast because there isn't any re-enconding, just muxing.

---

### Post by davidstri on 2009-03-23
Thank you for your help, but I think you misunderstood the question or I mis-stated the question. I just want a program where I can manually add the loud beep or silence to the bad word(s) of the .avi,or any other movie format, movie. But I guess they haven't made something like that yet.

---

### Post by davidstri on 2009-03-23
Oh, thanks lovinglinux, I'll give that a try.

---

