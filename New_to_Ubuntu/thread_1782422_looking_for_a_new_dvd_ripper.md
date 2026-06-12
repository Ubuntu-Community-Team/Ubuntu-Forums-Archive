---
title: "looking for a new dvd ripper"
date: 2011-06-14
forum: New to Ubuntu
---

### Post by CaptainMark on 2011-06-14
I know this qeustions been asked a million times before here i expect but im looking for a dvd ripper that is easy to use, (im not savvy on technical details of video encoding) i have some criteria i need to fill though

ive used handbrake but find all the videos are too quiet so on my ipod i can barely hear them even at full volume if im in a noisy environment, i need one that can boost audio as far as im aware handbrake wont do this

ive also used acid dvdrip which does have a nice easy audioboost option but cannot rip to a format for ipods, i think its only .mp4 that can be played

i dont want to waste time and effort ripping then re encoding so can anyone recommend options that might do what i want in one hit

thanks 
mark

---

### Post by bodhi.zazen on 2011-06-14
There are many tools to manage multimedia , but, for full control the command line tools work best.

For a graphical interface, k3b

From the command line ffmpeg.

If you like handbrake, you should be able to adjust the volume with ffmpeg

---

### Post by nothingspecial on 2011-06-14
For a gui/cli way to get your dvds on your ipod (I do this for my kids).

Rip them to avi with dvdrip and make sure they are all saved on your desktop.

**** you can save them anywhere you like if you understand how to change this to reflect that ****

This (typed exactly) will only work if all the avi files are on your Desktop.

```
for f in ~/Desktop/*.avi; do ffmpeg -i "$f" -acodec libfaac -ab 128kb -vcodec mpeg4 -b 1200kb -mbd 2 \
-flags +4mv -trellis 2  -cmp 2 -subcmp 2 -s 320x180 -metadata title="${f%.avi}.mp4" \
"${f%.avi}.mp4"; done 
```

---

### Post by JohnAStebbins on 2011-06-14
> **CaptainMark said:**
> ive used handbrake but find all the videos are too quiet so on my ipod i can barely hear them even at full volume if im in a noisy environment, i need one that can boost audio as far as im aware handbrake wont do this


The HandBrake [nightly builds]("https://build.handbrake.fr/view/Nightlies/") now have audio gain control.

---

### Post by andrew.46 on 2011-06-15
> **bodhi.zazen said:**
> There are many tools to manage multimedia , but, for full control the command line tools work best.

This looks like an excellent opportunity for me to pimp my page that describes in perhaps excruciating detail how to rip and convert dvds using the commandline:

FFmpeg and 'Fist of Fury'
[http://www.andrews-corner.org/fist.html](http://www.andrews-corner.org/fist.html)

There is a small section on this page that demonstrates how to raise volume safely using SoX which might be especially useful to you?

---

### Post by bodhi.zazen on 2011-06-15
> **andrew.46 said:**
> This looks like an excellent opportunity for me to pimp my page that describes in perhaps excruciating detail how to rip and convert dvds using the commandline:

FFmpeg and 'Fist of Fury'
[http://www.andrews-corner.org/fist.html](http://www.andrews-corner.org/fist.html)

There is a small section on this page that demonstrates how to raise volume safely using SoX which might be especially useful to you?

Nice page.

This one has been best for me:

[http://howto-pages.org/ffmpeg/](http://howto-pages.org/ffmpeg/)

It is very detailed, but, after reading at least the top half users will understand teh basics of what they are doing at least =)

---

### Post by CaptainMark on 2011-06-15
ah i think ill pass on the command line programs just for now, not that im one those terminalphobes but im learning so many other things on the terminal just now, my head is ready to explode, its on my list of things to do, for now, ill try the handbrake daily

thanks

---

### Post by bodhi.zazen on 2011-06-15
> **CaptainMark said:**
> ah i think ill pass on the command line programs just for now, not that im one those terminalphobes but im learning so many other things on the terminal just now, my head is ready to explode, its on my list of things to do, for now, ill try the handbrake daily

thanks

I completely understand how you feel, but ...

As far as multimedia goes, when you have time, take a look at ffmpeg, it is a fantastic tool and if you spend some time with the links we gave you will will get a better (invaluable) understanding of what you are doing.

---

