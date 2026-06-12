---
title: "MP3 Burning"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by garwoon on 2008-12-13
Hi

I am a bit of a newbie to Ubuntu.

Wondered is anyone could help me, I have a CD player in the Car that will play MP3s. I am looking for a CD burner that will all me to burner my MP3 collection to MP3 CD's but will reduce the bit rate as part of the burn process so I can get move on a CD ?

I use gnome.

Thanks

---

### Post by bapoumba on 2008-12-13
Just install ubuntu-restricted-extras for codecs (in multiverse) and use sound-juicer (default on a ubuntu install).
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping)

---

### Post by garwoon on 2008-12-14
Hi

I guess probally what I am asking for a is the best app to reduce the bit rate and therefore size of MP3's.

Nigel

---

### Post by Tom--d on 2008-12-14
> **garwoon said:**
> Hi

I guess probally what I am asking for a is the best app to reduce the bit rate and therefore size of MP3's.

Nigel

Install this package:

```
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
```

This will provide MP3 encoding.

Then install sound converter from Add/Remove.

Then go to Sound Converter and then Options (or what ever it is) and change the output to MP3 and then chose your bitrate from there.

Drag your songs you want to convert in the Sound converter window and then press Convert.

*Make sure you put the output folder somewhere else (maybe on the desktop?)*

Then with those files,

Go to Places > CD/DVD creater
then drag those songs in there and burn the disk.

---

