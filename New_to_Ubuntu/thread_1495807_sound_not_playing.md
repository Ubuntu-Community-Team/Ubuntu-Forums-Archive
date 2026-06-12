---
title: "sound not playing"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by oaridus on 2010-05-28
I have some video lectures in .rm (real media) format. I am able to play the files in vlc player but the audio does not work. How do I fix this? Please help

---

### Post by ubudog on 2010-05-28
Is the sound configuration set to "Analog Speakers" mode?

---

### Post by lidex on 2010-05-29
You may need some codecs. Do 'Part 1' here:
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

You'll also want this:
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by ubudog on 2010-05-29
If it is a codec issue, then you should type this into a terminal ```
sudo apt-get install ubuntu-restricted-extras
``` That should work.

---

### Post by oaridus on 2010-05-30
> **ubudog said:**
> If it is a codec issue, then you should type this into a terminal ```
sudo apt-get install ubuntu-restricted-extras
``` That should work.

Thanks Ubudog. I did what you suggested. I also did what lidex suggested. actually they are the same. But my audio still doesnot play. I used gspot software to find the codec used in the files. The audio codec is 4cc-sipr. A quick search in google showed that this is a real media network codec. But I did not find any  package containing this codec. Could you please help me out here. Thanks in advance.

---

### Post by ubudog on 2010-05-30
Did you try to play it in Totem yet?

---

### Post by oaridus on 2010-06-04
> **ubudog said:**
> Did you try to play it in Totem yet?

Ya I did, it give the following error

GStreamer encountered a general stream error.

and nothing comes up. What shall I do. Is there a player for realplayer in linux? The vlc runs the video fine but no sound. HELP

---

### Post by oaridus on 2010-06-04
I searched google for this gstreamer error

GStreamer encountered a general stream error.

And got this interesting link 

[https://bugs.launchpad.net/ubuntu/+source/gstreamer/+bug/155894](https://bugs.launchpad.net/ubuntu/+source/gstreamer/+bug/155894)

It talks about realaudio also. But I didn't quite get what to do. Can any one go through it and let me know what tricks I have to perform.

---

