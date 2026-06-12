---
title: "Ubuntu 9.04 Flash problems"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by Grujah on 2010-01-02
I cannot get flash to work properly. When I go to a YouTube video, the where video should be shows only the controls and a giant "play" button in middle. When I click it, it starts searching for MPEG-4 decoder, cannot find it, and than the video either plays REALY badly or doesn't play at all.

Other flash videos/games either play really slow or wrong. I'm running Ubuntu 9.04 on a Toshiba Satellite L500 1-EU.

---

### Post by Methuselah on 2010-01-02
It seems as if you're using swfdec or gnash.
They're prety ambitious (and your only option if you're running ps3 or something like that) but probably don't work as well as the adobe flash player right now.

Enter **about:plugins** in the firefox address bar to see what you have.
If you see **gnash** or **swfdec** you might want to remove them.

Follow the instructions for installing adobe flash here:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by Grujah on 2010-01-02
Yay, it works :D it was swfdec.

---

