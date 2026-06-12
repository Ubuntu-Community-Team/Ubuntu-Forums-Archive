---
title: "FFMPEG comand line for batch processing to ipod with subs"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by powel212 on 2009-04-13
Hi

Is there a command line for batch processing avi files to ipod format while hard coding the subtitles at the same time?

*I have full season of the simpsons I want to watch on a flight to Hawaii with my wife. I need to hard encode the Chinese subtitles for my wife as her English is pretty weak. It's a long flight so we're going to watch several episodes and I was hoping i could just automate a batch process for the whole season. I have all the avi files and srt files in the same folder.*

I'd use Avidemux as it does a nice job of hardcoding subs but I don't know how to batch with Avidemux.

Any insight is appreciated

Thanks

Powel

---

### Post by lovinglinux on 2009-04-13
> **powel212 said:**
> I'd use Avidemux as it does a nice job of hardcoding subs but I don't know how to batch with Avidemux.

You can use Avidemux "Jobs" to encode a series of movies.  

Select the video, configure the settings, then click "File >>> Add to joblist". Do this for each video, then click "File >>> Show Joblist" and hit "Run all jobs".

---

### Post by powel212 on 2009-04-13
Sweet. Thanks for that. I tried finding a post about how to batch in Avidimux but to no avail. Thanks. Tried it, works. Tight.

Would still love to know a command line equivalent for FFMPG if anyone knows.

Thanks again

Powel

---

### Post by lovinglinux on 2009-04-13
> **powel212 said:**
> Sweet. Thanks for that. I tried finding a post about how to batch in Avidimux but to no avail. Thanks. Tried it, works. Tight.

Would still love to know a command line equivalent for FFMPG if anyone knows.

Thanks again

Powel

I'm trying to help someone else with a command for ffmpeg to encode subtitles [here](http://ubuntuforums.org/showthread.php?t=1124340), but it isn't working.

There are [several threads](http://www.google.com/search?q=ffmpeg+batch+site%3Aubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0) about batch converting with ffmpeg. I don't know if they work tho.

---

