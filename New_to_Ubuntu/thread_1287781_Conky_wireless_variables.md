---
title: "Conky wireless variables"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by gigaforce1111 on 2009-10-10
Hi all,
I tried setting up Conky with the wireless variables:
wireless_link_qual_perc
wireless_link_bar
wireless_bitrate
etc...

I noticed that the variables works (shows correct output) ONLY when I run in the terminal:
```
sudo conky 
```
1. Is there any risk running Conky with these permissions?
2. Is there a way to run Conky "normally" and making the wireless variables work?

I'll be glad to hear any suggestions!

---

### Post by wojox on 2009-10-10
Look here: [http://ubuntuforums.org/archive/index.php/t-563401.html](http://ubuntuforums.org/archive/index.php/t-563401.html)

---

### Post by slakkie on 2009-10-10
You could try this PPA, it is from the guy who made all of the conky packages for Karmic. I suspect his Jaunty version is conky-all, which is now in Karmic.

[https://launchpad.net/~norsetto/+archive/ppa?field.series_filter=](https://launchpad.net/~norsetto/+archive/ppa?field.series_filter=)

---

### Post by gigaforce1111 on 2009-10-10
> **wojox said:**
> Look here: [http://ubuntuforums.org/archive/index.php/t-563401.html](http://ubuntuforums.org/archive/index.php/t-563401.html)
I saw that before and it  talks about older version of Conky. Following that didn't produce any good.

> **slakkie said:**
> You could try this PPA, it is from the guy who made all of the conky packages for Karmic. I suspect his Jaunty version is conky-all, which is now in Karmic.

[https://launchpad.net/~norsetto/+archive/ppa?field.series_filter=]("https://launchpad.net/%7Enorsetto/+archive/ppa?field.series_filter=")
I installed as instructed in the link. 
I chose the full features version.
Still the wireless variables only work if run Conky as root (sudo).

I don't know how to do that but I want to run something like "sudo conky" in my conky_start.sh file:
```
#!/bin/bash
sleep 20 && conky;
```Any idea?

---

### Post by gigaforce1111 on 2009-10-13
anyone?

---

### Post by gigaforce1111 on 2009-10-13
Hi all,
after digging more, I found this post:
[http://ubuntuforums.org/showpost.php?p=799286&postcount=2](http://ubuntuforums.org/showpost.php?p=799286&postcount=2)
I guess this is solved.

---

