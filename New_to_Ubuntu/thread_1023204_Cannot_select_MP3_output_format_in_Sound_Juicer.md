---
title: "Cannot select MP3 output format in Sound Juicer"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by JohnRory1971 on 2008-12-27
I cannot select CD Quality, MP3 output format in either Sound Juicer or Rhythmbox. I have the relevant codecs installed so what am I missing? Any ideas please?

---

### Post by Tom--d on 2008-12-27
Easy one.

Run this command:
```
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
```

---

### Post by Michael.Godawski on 2008-12-27
hi JohnRory1971,

what relevant codecs do you have installed? Is it working after you have installed the codecs Tom--d suggested?

---

### Post by Tom--d on 2008-12-27
> **Michael.Godawski said:**
> hi JohnRory1971,

what relevant codecs do you have installed? Is it working after you have installed the codecs Tom--d suggested?

It should work yes.
If you want AAC encoding as well, install this:
```

sudo apt-get install gstreamer0.10-plugins-bad-multiverse
```

---

### Post by JohnRory1971 on 2008-12-27
Tom & Michael

Thank you. I installed gstreamer0.10-plugins-ugly-multiverse and I can now select MP3 output which makes me a very happy man.

It's good to know some one out there always has the answer. I'm loving Ubuntu more by the minute. I just got 3 D desktop up and running. Revolving cube is so cool

By the  way I had installed gstreamer0.10-fluendo-plugins.Why were they not sufficient for Sound Juicer and Rhythmbox?

Thanks 
John

---

### Post by Tom--d on 2008-12-27
> **JohnRory1971 said:**
> Tom & Michael

Thank you. I installed gstreamer0.10-plugins-ugly-multiverse and I can now select MP3 output which makes me a very happy man.

It's good to know some one out there always has the answer. I'm loving Ubuntu more by the minute. I just got 3 D desktop up and running. Revolving cube is so cool

By the  way I had installed gstreamer0.10-fluendo-plugins.Why were they not sufficient for Sound Juicer and Rhythmbox?

Thanks 
John

No problem :)
To say thanks, press the [IMG]http://ubuntuforums.org/images/buttons/post_thanks.gif[/IMG] on my post :)
Too be safe, just install all the gstreamer packages. You will never be short of codecs ;)

---

### Post by Michael.Godawski on 2008-12-27
I guess because you have not paid for them :P


[LIST]
[*][http://www.fluendo.com/shop/product/complete-set-of-playback-plugins/](http://www.fluendo.com/shop/product/complete-set-of-playback-plugins/)
[/LIST]
If you have issues with restricted formats check out this page:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

