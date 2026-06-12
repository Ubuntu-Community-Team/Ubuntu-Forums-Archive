---
title: "MP3 quality very poor"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by DJ Mike on 2010-07-14
I installed Ubuntu on a computer that does not have access to the internet so I have to get what I need with another computer, store it on a flash drive and move it to my computer. After I finally got Ubunto to recognize and access my flash drive I came here to find out how to get it to play MP3's. A couple of posts led me to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) 

Oh, BTW [http://ubuntu.com/](http://ubuntu.com/) has no link to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) so the only way to find it is via the forum or search engines. 

So I try the package non-free-codecs_1.1_amd64.deb and that didn't work so I tried realplayer_11.0.0-0.2medibuntu0.8.04.1_i386.deb. That gave me a working MP3 player but the quality is very poor, something like an old 78. Later when I restarted to Window I found that ALL of my music players sound bad now. VLC, Winamp, Windows Media Player, Audacity's playback... When I tried to watch a video I got another nasty surprise. All formats of video are now yellow tented and blurred.

How did something I did with Ubunto screw up Windows? How can I fix this so music and video play well on both Ubunto and Windows?

---

### Post by ubunterooster on 2010-07-14
The problem seems to be with the MP3s. What bit-rate are they?

---

### Post by DJ Mike on 2010-07-14
I don't remember what the rate is but I have not changed them from what they were before I started trying Ubuntu. Before Ubuntu they sounded OK. If I play them on a portable they still sound OK. Now they sound bad on my computer even when I am not using Ubuntu. I haven't tried ripping a new MP3 or burning a CD yet so I don't know if only the playback is effected or  anything else.

---

### Post by Zeike on 2010-07-14
> **DJ Mike said:**
> How did something I did with Ubunto screw up Windows? How can I fix this so music and video play well on both Ubunto and Windows?

Since it is very unlikely something you did in Ubuntu caused issues like this in Windows, you could be experienced some kind of hardware problem that has occurred as a coincidence.

---

### Post by DJ Mike on 2010-07-14
> **Zeike said:**
> Since it is very unlikely something you did in Ubuntu caused issues like this in Windows, you could be experienced some kind of hardware problem that has occurred as a coincidence.


Could something I did with Ubuntu have changed how the sound card is used?

---

### Post by Zzl1xndd on 2010-07-14
> **DJ Mike said:**
> Could something I did with Ubuntu have changed how the sound card is used?

Unlikely, Ubuntu and Windows would be using totally separate drivers. So anything done on the Ubuntu side should not affect the Windows side. 

Likely there is some kind of hardware issues. It might just be the speakers have you tried another set? or maybe some headphones?

---

### Post by techunit on 2010-07-14
What are the system specs of your computer? I assume it ran windows XP... Ubuntu actually requires more resources than Windows XP now. So it could be that your computer isn't powerful enough to run ubuntu efficently and it is causing audio problems. Another problem could be that it isn't accessing the graphics card and is defaulting back on the Motherboard.

---

### Post by MooPi on 2010-07-14
It sounds more like an equipment failure than software issue. The only way to test is to create a new mp3 file batch and play them to see if your system plays the new files properly. My choice for terminal playing of mp3 files would be mpg123, encoded with lame. Lame does an excellent job of encoding and mpg123 will tell you the bit rate of the files being played.

---

### Post by 3rdalbum on 2010-07-14
1. Don't use Realplayer, just get the codecs for all the real Linux media players. The "gstreamer0.10-fluendo-mp3" package is the one you want.

2. If your sound is crackling, then the PCM volume is up too loud. Go to the terminal and type:

```
alsamixer
```

Scroll across with your arrow keys and find the PCM channel. Turn it down to around 90%.

---

### Post by DJ Mike on 2010-07-15
> **techunit said:**
> What are the system specs of your computer? I assume it ran windows XP... Ubuntu actually requires more resources than Windows XP now. So it could be that your computer isn't powerful enough to run ubuntu efficently and it is causing audio problems. Another problem could be that it isn't accessing the graphics card and is defaulting back on the Motherboard.

Even though my problem is sort of resolved I should know the the specs for future question so can you tell me how to find out what they are? I live in a collage community so I get computers out of the garbage when the students move out. The one I have been using for the last year has parts and programs from six computers. I got interested in Umbuntu because I had to use it to crack the password on a hard drive that I added. That gave me Windows XP and now that I have XP it complains every time I make any changes.

I hooked up the speakers to my TV and they worked fine. I don't think it could have been a sound card issue because video was degraded too. I noticed that the boot up sounds for both Ubunto and Windows were unaffected so I tried some video games and they were also unaffected. I played a wav and mp3 again and they sounded like crap. I converted a wav to an mp3, bitrate 128, not good but not THAT bad. Next I checked some video again ... flv, mp4. They were yellow and sounded bad. 

Now the strange part. I noticed a video that I hadn't viewed yet and it looked and sounded OK. I check the format - mp4. I recheck the video that was bad just 5 minutes ago and they are OK. I check the wav's and mp3s and they are now OK. I switch to Ubuntu and they wav's sound OK now. mp3s and mp4 still don't play at all but I didn't expect them to yet.

So what mysterious problem can effect both music and video on both Ubunto and Windows but not video game sounds?

---

### Post by robert shearer on 2010-07-15
To find the specs of your machine boot into Ubuntu and go..

Applications=>Accessories=>Terminal  and when the terminal opens type 

```
sudo lshw
```  and hit enter. (thats a lower case L)

after it asks for and you enter your password then you will get an output of your hardware.

Scroll through it to see things like CPU, Memory, etc.

If your mp3s and video now work ok then it definitely sounds like a hardware fault.
Probably one of the reasons it was in the trash in the first place.!

Applaud your re-purposing of older discarded hardware but be aware that accessing data from old drives has legal implications.

---

