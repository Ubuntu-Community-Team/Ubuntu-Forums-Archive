---
title: "Does Any one Able to Record Video in Cheese Booth Webcam?"
date: 2011-03-22
forum: New to Ubuntu
---

### Post by desaivarun_104lts on 2011-03-22
Hi Friends,

I am using Acer Aspire one 532h(A0532H),with ubuntu 11.04 Natty Alpha 3 version.From the past two months, i tried ubuntu 10.04 and ubuntu 10.10

On these three versions,in the cheese booth webcaam,i can take photos,and the webcam works perfectly.But i am unable to record video in the cheese.

When i click on the strat recording button,the cheese screen goes black,and the cheese freezes,everytime i should do the force quit to close the cheese.

Please help me,from the past three ubuntu versions,i am unable to record the video in cheese booth webcam..

---

### Post by ikt on 2011-03-23
Does it have to be in cheese?

How about this?

[http://www.youtube.com/watch?v=hW-ZoKTef_I&feature=channel_video_title](http://www.youtube.com/watch?v=hW-ZoKTef_I&feature=channel_video_title)

---

### Post by ashmew2 on 2011-03-23
Is your webcam being detected ?
I mean , have you checked any other applications with it ?



Assuming it is being detected , give this a try : (Get the .deb , install it)

[http://sourceforge.net/projects/wxcam/files/wxcam/1.0.7/](http://sourceforge.net/projects/wxcam/files/wxcam/1.0.7/)

**OR**

You could just do a ```
sudo apt-get install wxcam
```

Once installed , it will show under Applications > Sound n Video > Webcam Application 

I was experiencing lag with cheese(VERY HEAVY LAG) , and wxCam seems to be far far better than cheese for recording.

---

### Post by aelmat on 2011-04-24
hi, i have the same computer and you need to use guvcview

---

### Post by pabc on 2011-04-29
wxcam fails via apt-get in 10.04 due to a dependency issue.

guvcview install does but i've yet to figure out how to record with it but it does appear to offer many more recording codecs so i'm sure there will be one that is CPU resource light enough to record acceptable video on my AAO - ZG5

edit - found the record buttons after resizing the window. by default on my small screensize on the ZG5 they are hidden

---

### Post by no2498 on 2011-04-29
pabc for wxcam try a different package 

 [http://sourceforge.net/projects/wxcam/files/wxcam/](http://sourceforge.net/projects/wxcam/files/wxcam/)

you can get it in a deb file

---

### Post by amjjawad on 2011-09-09
Hi everyone,

Is there any other application/program based these two mentioned here?

Thank you!

---

### Post by sandyd on 2011-09-09
> **amjjawad said:**
> Hi everyone,
 
Is there any other application/program based these two mentioned here?
 
Thank you!
 webcamstudio.
You can also use ffmpeg.
 
FFMPEG renders a bit better methinks.

---

### Post by amjjawad on 2011-09-09
> **sandyd said:**
> webcamstudio.
You can also use ffmpeg.
 
FFMPEG renders a bit better methinks.

Many thanks, will have a look.
Have you used these two? I'm looking for a program/application that support many File Types.

---

### Post by amjjawad on 2011-09-09
Does [http://sourceforge.net/projects/wxcam](http://sourceforge.net/projects/wxcam) even work on 64-bit?
I don't think so.

I'll give sandyd's suggestions a try and see if that will help.

---

### Post by no2498 on 2011-09-11
you can also use vlc with a web cam

---

### Post by amjjawad on 2011-09-11
> **no2498 said:**
> you can also use vlc with a web cam

Really? that's good to know.
What are the supported file types? I'm sorry, don't have a cam on this machine, that's why I'm asking.
I'm trying to help a friend who has Ubuntu and HP Laptop. He used to have an amazing program on Windows but he's not interested about Windows any more.

Thanks!

---

### Post by no2498 on 2011-09-11
i think vlc does vob file type
last time i used it my cam stopped working in all my other programs but still worked in vlc

---

### Post by amjjawad on 2011-09-11
> **no2498 said:**
> i think vlc does vob file type
last time i used it my cam stopped working in all my other programs but still worked in vlc

My friend told me that Cheese creates a very large file when he tried to record for 1 min and the file was 55MB :/

I'll let him know about VLC and hope the file size will be much less.

Thank you :)

---

