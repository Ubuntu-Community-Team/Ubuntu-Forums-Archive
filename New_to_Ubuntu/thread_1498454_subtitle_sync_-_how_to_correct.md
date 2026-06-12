---
title: "subtitle sync - how to correct?"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by paker on 2010-05-31
I need to delay subtitle for about 2-and-1/2 minutes. video is mkv, subtitle is smi.
vlc has some sync capability but not as much as 2-and-1/2 minutes.
What program can I use?
Thanks.

---

### Post by nhasian on 2010-05-31
you can use [avidemux]("apt:avidemux")

```
sudo apt-get install avidemux
```

---

### Post by paker on 2010-05-31
Can you kindly show me which button has subtitle timing?  mkv + smi

Thanks.

---

### Post by nhasian on 2010-06-01
i was afraid you would ask me that hehe i did it once before, but i'm not a video editing guy so i don't remember the steps.  avidemux has a lot of bells and whistles.  I remember it was pretty simple though.  i just shifted the subtitles and resaved the file.

---

### Post by ozbolt on 2010-06-01
All you need to do is fiagure out how much is the gap betwen audio and subtitles and then use Subtitle editor. In there it is quite simple to do this.

But if your movie is 24fps and subtitles are made for 25fps then asa far as I know there is a setting for this in the program but you will need to fiagure it out by yourself.

---

### Post by 4Orbs on 2010-06-01
+1 for Subtitle Editor. It's available in Synaptic pkg mgr. Takes a little practice, it's not just a one-click fix... but it's the quickest and best method I've found. If all the subtitles are off by the same amount of time, then you just add or subtract the appropriate number of milliseconds. If the timings are off because of a difference in framerate between the movie and subtitles, then use the scale option. Sometimes it's just easier to download a new subtitle file from one of the free subtitle websites such as [THIS ONE]("http://www.opensubtitles.com/en")

---

### Post by paker on 2010-06-01
Thank you for the replies.
1) Subtitle Editor doesn't seem to recognize .smi format.
2) I pretty much checked all buttons, but couldn't locate the subtitle time delay feature.
3) VLC has time delay, but not like 5 minutes.

Thanks.

---

### Post by acrazyplayer on 2010-06-01
for avidemux you need to click on where it says for video "copy" and then you can choose some other codec to encode the video into. This must be done to use the filters which are grayed out. one filter is "subtitle" which adds subs and also adds delay. I went far over 5000ms just to check. I however am not sure if it will recognize the smi file.

---

### Post by paker on 2010-08-06
I found the solution, GOM player. GOM handles .smi, and can sync subtitle to any video frame. Unfortunately, it doesn't work in ubuntu. I'm running GOM on a Windows machine. Thanks everyone.

---

