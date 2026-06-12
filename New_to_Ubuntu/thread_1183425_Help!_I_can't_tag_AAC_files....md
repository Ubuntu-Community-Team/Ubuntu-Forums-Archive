---
title: "Help! I can't tag AAC files..."
date: 2009-06-10
forum: New to Ubuntu
---

### Post by aimpau on 2009-06-10
So here's the story...

I have a FLV audio only file. I convert to AAC using FFmpeg through

```

sudo ffmpeg -i input.flv -ab 128k output.aac

```

Don't worry, I have libfaac installed. The problem is, I can't edit or tag the AAC file using almost everything in the repos. They always say "unknown error" etc etc.. I've even used kid3-qt but to no avail. Even the built in FFmpeg tagger doesn't work. The only thing that can edit the tags is my gf's Nokia N76.

Need help pls.

---

### Post by andrew.46 on 2009-06-10
Hi aimpau,

> **aimpau said:**
> I have a FLV audio only file. I convert to AAC using FFmpeg through

```
sudo ffmpeg -i input.flv -ab 128k output.aac
```

Don't worry, I have libfaac installed. The problem is, I can't edit or tag the AAC file using almost everything in the repos. 

I had a look at the Hardy repository (you have yourself as a Hardy user) and noted the following:

```

andrew@skamandros:~$ **[COLOR="Purple"]apt-cache search easytag[/COLOR]**
easytag - viewing, editing and writing ID3 tags
easytag-aac - viewing, editing and writing ID3 tags

```

so I suspect that easytag-aac might be your best bet here:

```
sudo apt-get install easytag-aac
```

BTW you do not need to use *sudo* to run FFmpeg and in fact this might give you a few problems with playback and manipulation of your files.

All the best,

Andrew

---

### Post by aimpau on 2009-06-10
oops..sori, I'm on 9.04. gotta update profile. I also have easytag-aac...but that sudo thing made me think...

---

### Post by aimpau on 2009-06-10
**HAHAHAHAHAHA!** You are right! **clunks aimpau's head with harddrive** It's the SUDO!!!! I tried kid3-qt under gksu...and BAM! it worked! hhaha. Thanks!

---

### Post by andrew.46 on 2009-06-10
Hi aimpau,

> **aimpau said:**
> **HAHAHAHAHAHA!** You are right! **clunks aimpau's head with harddrive** It's the SUDO!!!! I tried kid3-qt under gksu...and BAM! it worked! hhaha. Thanks!

Well I must say I am glad that was so easy :-). BTW if you are a keen FFmpeg user under Jaunty don't forget to visit the FakeOutdoorsman's guide:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

and unlock a little more of FFmpeg's potential. Mind you if you are already transcoding to aac perhaps you have been there already?

Andrew

---

