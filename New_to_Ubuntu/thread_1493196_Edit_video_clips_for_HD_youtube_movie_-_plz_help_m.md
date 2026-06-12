---
title: "Edit video clips for HD youtube movie - plz help me out"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by Norfeldt on 2010-05-25
Hello all

It's been a looong time since I tried ubuntu, but now I'm back again to give it another try.

:guitar:

Here is how far I got:
Got the latest ubuntu version - checked!
Recorded some looong video clips i high def that needs to be cut - checked!
Search the ubuntu forum for video editor programs - checked!

I have tried OpenShot, Kdenlive, kino and Cinerella (and some other prgs)

OpenShot seemed to worked best until it crashed!!!:(
The other programs seemed to have some problems with the format..  tended to be lagging when during playback or just not showing the video (only got a laptop to work on).

I believe that my problems come from the format of the video clips (too heavy). I need the video to be sharp on youtube...

:confused:
I believe that the solution would be to have a program that can convert the movie clips to some sort of format that the programs will swallow without losing too much quality..

Do you guys (and chicks) know any program that will swallow the vid clips without converting to do cutting (NEEDS TO BE STABLE)? Or do you know a easy converter program and format that I need to be working with???

(I'm not so crazy about the terminal, so if there is another way.. - it would be great)

Thank you for your time.. :KS

---

### Post by Ozymandias_117 on 2010-05-25
If you're using 10.04 it came with a program called Pitivi that may do what you want. (If not, if you're using 9.10 it's in the repos, before that you need the PPA)

Edit: What formats does youtube let you post HD content in?

---

### Post by soro2005 on 2010-05-26
I'm not sure I understand, but for easy conversion, Avidemux is your friend. You can also use it to chop up your videos, and possibly to combine several. You can resize your video and apply some filters. No transitions, though. I might be wrong. Avidemux is reasonably stable.

As a format, try to encode the video with the x264 codec (mpeg-4 avc), and there's a chance that Youtube puts it up as is, i.e. without producing more loss by recompressing your file. Your quality will depend almost entirely on the bitrate (amount of bits of information per second of video). You will have to experiment a little, but from 600 upward should yield usable qualities at common sizes.

Use AAC for audio, and mp4 as the container (Format in Avidemux). If you don't see one of the codecs, you may have to enable the Medibuntu repository to install the non-free multimedia stuff.

As for editing: Though luck. Openshot promises a lot, but I can't even get it to start currently. Pitivi seems to be the best option. Vlmc will hopefully be as good as Vlc once it is actually usable.

---

### Post by Norfeldt on 2010-05-26
> **Ozymandias_117 said:**
> If you're using 10.04 it came with a program called Pitivi that may do what you want. (If not, if you're using 9.10 it's in the repos, before that you need the PPA)

Edit: What formats does youtube let you post HD content in?

Thank you for your time. I already have tried Pitivi but it crashed..

I believe that youtube eate mp4 format which is the format that I did my recording.

---

### Post by Norfeldt on 2010-05-26
> **soro2005 said:**
> I'm not sure I understand, but for easy conversion, Avidemux is your friend. You can also use it to chop up your videos, and possibly to combine several. You can resize your video and apply some filters. No transitions, though. I might be wrong. Avidemux is reasonably stable.

As a format, try to encode the video with the x264 codec (mpeg-4 avc), and there's a chance that Youtube puts it up as is, i.e. without producing more loss by recompressing your file. Your quality will depend almost entirely on the bitrate (amount of bits of information per second of video). You will have to experiment a little, but from 600 upward should yield usable qualities at common sizes.

Use AAC for audio, and mp4 as the container (Format in Avidemux). If you don't see one of the codecs, you may have to enable the Medibuntu repository to install the non-free multimedia stuff.

As for editing: Though luck. Openshot promises a lot, but I can't even get it to start currently. Pitivi seems to be the best option. Vlmc will hopefully be as good as Vlc once it is actually usable.

Thank you for your time and reply. I will give it a try and report back.

---

### Post by sandyd on 2010-05-26
> **Norfeldt said:**
> Thank you for your time and reply. I will give it a try and report back.

you can also try kdenlive. p.s. youtube accepts mp4 files -i just uploaded a 1080p one onto youtube a week ago.

---

### Post by Norfeldt on 2010-05-26
> **carlee said:**
> you can also try kdenlive. p.s. youtube accepts mp4 files -i just uploaded a 1080p one onto youtube a week ago.

thanks Carlee, but did try KdenLive.. 

Just think I need to make the clips smaller

---

### Post by 0004tom on 2010-05-26
What format are these clips your trying to edit?

---

### Post by Norfeldt on 2010-05-26
> **0004tom said:**
> What format are these clips your trying to edit?

the format are .mp4 and the files are big...

---

### Post by Norfeldt on 2010-05-26
It didn't work... when I draged the movies in it gave me this

> H.264 detected

If the file is using B-frames as reference it can lead to a crash or stuttering.
Avidemux can use another mode which is safe but YOU WILL LOSE FRAME ACCURACY.
Do you want to use that mode?

Tried yes and no but no difference...

---

### Post by sandyd on 2010-05-26
> **Norfeldt said:**
> thanks Carlee, but did try KdenLive.. 

Just think I need to make the clips smaller

if your trying to convert them, use winff

---

### Post by Norfeldt on 2010-05-27
> **carlee said:**
> if your trying to convert them, use winff

Thank you Carlee. WinFF did the job well.

I have now been trying to work in KdenLive as you suggested with some of the converted clips.

But when I try to export them I get this
[IMG]http://dl.dropbox.com/u/3216968/Billeder/Rendering_006.png[/IMG]

and when I hover the mouse over I get a message that an audio aac codec is not supported.. I then go into the Ubuntu Software Center and get this
[IMG]http://dl.dropbox.com/u/3216968/Billeder/acc%20codec%20problem.png[/IMG]

How do I get this codec????:confused:

---

### Post by sandyd on 2010-05-27
install libfaac (or is it just faac?) and libfaad (or is it just faad) and try again.

---

### Post by sandyd on 2010-05-27
p.s. a good person to ask about editing HD video in linux (for some reason I dont have the problems your having, so I can only provide limited help) is nixiepixel. Shes a user here on ubuntuforums (she hasn't logged in recently tho), but you can contact her through nixiepixel.com, her youtube channel (username is nixiepixel), or twitter (username is also nixiepixel). She does a lot of HD youtube videos, and therefore could posibly give you some help with editing videos on linux (she gets a lot of feedback though, so she may not have time)

---

### Post by Norfeldt on 2010-05-27
> **carlee said:**
> install libfaac (or is it just faac?) and libfaad (or is it just faad) and try again.

Tried that but no luck... been trying a lot lately.. :( ...beginning to feel that ubuntu isn't that great after all.. it's just so complicated with all those codecs...:(

I know about NixiePixel by the way. She was the one showing me KdenLive on youtube.. think she did a great video :P

---

### Post by sandyd on 2010-05-27
> **Norfeldt said:**
> Tried that but no luck... been trying a lot lately.. :( ...beginning to feel that ubuntu isn't that great after all.. it's just so complicated with all those codecs...:(

I know about NixiePixel by the way. She was the one showing me KdenLive on youtube.. think she did a great video :P
hmm... my bad.
I figured out why it wasn't working. it seems that I had enabled the medibuntu repositories, and installed the fffmpeg version from **there** not from the standard ubuntu repos. which was why my encoding was curiously working. The ffmpeg libraries from the ubuntu repos do not have the correct faac codecs...
so...
```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update[FONT=Verdana]
[/FONT]sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-good gstreamer0.10-plugins-bad-multiverse ffmpeg libavcodec-extra-52 libavdevice-extra-52 libavformat-extra-52 libavutil-extra-49 libswscale-extra-0 libpostproc-extra-51 

```32bit
```

sudo apt-get install w32codecs
```64bit
```

sudo apt-get install w64codecs
```

---

### Post by Norfeldt on 2010-05-28
> **carlee said:**
> hmm... my bad.
I figured out why it wasn't working. it seems that I had enabled the medibuntu repositories, and installed the fffmpeg version from **there** not from the standard ubuntu repos. which was why my encoding was curiously working. The ffmpeg libraries from the ubuntu repos do not have the correct faac codecs...
so...
```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update[FONT=Verdana]
[/FONT]sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-good gstreamer0.10-plugins-bad-multiverse ffmpeg libavcodec-extra-52 libavdevice-extra-52 libavformat-extra-52 libavutil-extra-49 libswscale-extra-0 libpostproc-extra-51 

```32bit
```

sudo apt-get install w32codecs
```64bit
```

sudo apt-get install w64codecs
```

Once again thank you for your time. I did try some tutorials for medibuntu before your post and that was getting me confused - because it didn't work.. 
I tried your guide and it didn't work either.. Kdenlive still says that the aac format is unsupported... 

How do I see in the terminal if I have install aac correct??? 
..and more important how do I install it if it isn't there?
..or if it is install correctly, how do I get it enabled in kdenlive?

---

