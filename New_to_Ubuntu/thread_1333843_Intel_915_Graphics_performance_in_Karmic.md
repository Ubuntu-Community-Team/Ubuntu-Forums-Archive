---
title: "Intel 915 Graphics performance in Karmic?"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by emeraldgirl08 on 2009-11-21
I have 9.10 installed on my R51e and the open-source drivers for the graphics card for it are quite good :)

On my R52 I have integrated Intel graphics. 

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
```

Switching from using the R51e to the R52 Intel graphics is very noticeable. The cursor is almost flickery when it you move it across the screen. Some webpages seem very jittery and it feels like the CPU is doing the rendering. That or the graphics driver I have needs some tweaking? 

I would like to know if Intel 915 GM graphics with Karmic are decent or not?

---

### Post by Jon Monreal on 2009-11-22
Not sure if [this bug might be what you're experiencing]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/440069").

I'll look further into this.

---

### Post by emeraldgirl08 on 2009-11-22
I have Jaunty on my R52 w/intel 915gm graphics. I was @ a relatives house-sitting so I took that laptop along. I noticed that there was the graphics issue. I never really took notice b/c I have been almost exclusively been using my other laptop- the R51e which has some dedicated graphics memory. It works well with both W7 and Karmic so I'm used to the almost smooth operation from it.

When I got to my cousins house and began to use the R52 I noticed how flickery movements were. Also when I have a window open and drag it around it seems to be relying on VGA compatible solutions to render the images. I've run lspci and it shows VGA compatible something-or-other. I'm sorry I don't have my R52 handy right now. I did save the lspci txt and will post that in a couple of minutes.

What I wanted to know was would it even be worth deleting my Jaunty partition and installing Karmic? Or would tinkering with xorg and such alleviate some of the laziness of the graphics rendering?

---

### Post by emeraldgirl08 on 2009-11-30
Installed Crunchbang on the R52.

Works fine for the moment :popcorn:

---

