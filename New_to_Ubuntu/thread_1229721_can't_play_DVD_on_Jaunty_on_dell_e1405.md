---
title: "can't play DVD on Jaunty on dell e1405"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by shneader on 2009-08-02
I have a Del E1405 running Jaunty. I just started using Linux a few weeks ago. I wanted to try some of the DVD ripping software (i.e., AcidRip). It can't seem to read the DVD that I have in my drive. Then, I simply tried playing the DVD with VLC or Mplayer, and it doesn't work. When I use VLC and go "Media > Open Disc > have DVD checked, and click "play", VLC just shuts down. When I try MPlayer, Media > Play #n, it says "An error occurred: Your GStreamer installation is missing a plug-in." I tried this with 2 different DVD's, and I get the same result

1. If someone can suggest the plugin I should get from Synaptic, that would be great.
2. Is there any kind of "driver" or something that I need for my E1405 so that it can read these disks? I wouldn't think so, because these DVD's work when I boot in windows. But, who knows.

Thanks.

---

### Post by ubudog on 2009-08-02
Check this out:[https://help.ubuntu.com/community/RestrictedFormats:](https://help.ubuntu.com/community/RestrictedFormats:))

---

### Post by ubudog on 2009-08-02
It worked for me:)

---

### Post by Dark Aspect on 2009-08-02
You need [libdvdcss2]("http://packages.medibuntu.org/jaunty/libdvdcss2.html") to play DVDs on Linux, also it wouldn't hurt to install Ubuntu restricted codecs. 

> sudo apt-get install ubuntu-restricted-extras

After that you should be able to play DVDs via VLC and mplayer.

---

### Post by Dark Aspect on 2009-08-02
> **ubudog said:**
> Check this out:[https://help.ubuntu.com/community/RestrictedFormats:](https://help.ubuntu.com/community/RestrictedFormats:))

That link is broken,

[[IMG]http://img217.imageshack.us/img217/7268/screenshotssb.th.png[/IMG]](http://img217.imageshack.us/img217/7268/screenshotssb.png)

---

### Post by ubudog on 2009-08-02
> **Dark Aspect said:**
> That link is broken,

[[IMG]http://img217.imageshack.us/img217/7268/screenshotssb.th.png[/IMG]](http://img217.imageshack.us/img217/7268/screenshotssb.png)

Yes it is.  Sorry about that.:)

---

### Post by Dark Aspect on 2009-08-02
> **ubudog said:**
> Yes it is.  Sorry about that.:)

I believe the semi colon caused the issue, there appears to be a page about RestrictedFormats [here]("https://help.ubuntu.com/community/RestrictedFormats"). None the less its almost easier to write sudo apt-get install ubuntu-restricted-extras.

---

### Post by ubudog on 2009-08-02
True

---

### Post by shneader on 2009-08-03
Thanks. I read the Restricted Formats page. I also had to do this:
sudo /usr/share/doc/libdvdread4/install-css.sh

Also, since I had never played a DVD via Ubuntu before, I installed regionset. Interestingly, it was already set to region 1, which is what I wanted.

Lastly, although not specified, I did not restart my computer after installation, and none of these changes worked. I tried restarting my computer, and then it worked.

Thanks.

---

### Post by ubudog on 2009-08-03
> **shneader said:**
> Thanks. I read the Restricted Formats page. I also had to do this:
sudo /usr/share/doc/libdvdread4/install-css.sh

Also, since I had never played a DVD via Ubuntu before, I installed regionset. Interestingly, it was already set to region 1, which is what I wanted.

Lastly, although not specified, I did not restart my computer after installation, and none of these changes worked. I tried restarting my computer, and then it worked.

Thanks.

Any time:)

---

### Post by Chasalin on 2009-08-03
Wow that was hard to find... I spent weeks searching for a way to play any dvd on my laptop. Today I found an old post about 7.04 telling me about `/usr/share/doc/libdvdread3/install-css.sh`, I updated it to libdvdread4, et voila...
Only with that information I was able to find this thread...

Why is there no easy-to-find option to enable this?
Yes I know it can be abused... so can anything... I abuse my mind every day ;)

---

