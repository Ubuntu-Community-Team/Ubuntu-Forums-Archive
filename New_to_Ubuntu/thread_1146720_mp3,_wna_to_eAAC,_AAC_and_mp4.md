---
title: "mp3, wna to eAAC, AAC and mp4?"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by aimpau on 2009-05-02
Hi!

I would like to know how to convert mp3 and wma to eAAC, AAC and mp4 audio. If you have excellent settings recommendation because I need good quality w/ less file size, pls include them. Also, in a matter of minutes, i will be doing a clean install in one of my high end PC so pls include necessary programs that I need to install. Thanks!

PS
The eAAC is used by the Nokia Music manager.

---

### Post by zvacet on 2009-05-03
I don´t know about eAAC but for other format you can use [pacpl.]("http://pacpl.sourceforge.net/")If you want to use CLI [here]("http://ubuntuforums.org/showthread.php?t=712064") is tutorial.

---

### Post by jmp on 2009-05-03
Hi, I use K3b with the nero codec, follow this instructions:

[http://wiki.hydrogenaudio.org/index.php?title=K3b_and_Nero_AAC_Guide](http://wiki.hydrogenaudio.org/index.php?title=K3b_and_Nero_AAC_Guide)

For eAAC encoding replace the command explained there with:
cd /your pathway to codecs/
./neroAacEnc -br 48 -hev2 -if "$1" -of "$2"
./neroAacTag "$2" -meta:title="$3" -meta:artist="$4" -meta:comment="$5" -meta:track="$6" -meta:album="$7" -meta:year="$8"

I have n82 and it work great!!
Cheers

---

