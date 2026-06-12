---
title: "How I got sound to work on Dell mini 9"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by greenleaves123 on 2009-03-13
I am just writing this for future reference and to help anyone who has the same problem as I did.

It all started when suddenly my Dell mini 9 with Ubuntu crashed. Hardy Heron would not work.

I had to reinstall and upgrade to Intrepid. I used unetbootin and a USB stick to do this.

Sound didn't work and I tried everything.

I ended up reinstalling Ubuntu once again and this time this simple fix got sound to work:

In a terminal type:
sudo gedit /etc/modprobe.d/alsa-base

At the end of alsa-base file add:
options snd-hda-intel model=dell

Then I saved the file.

Source was: [http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html](http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html)

Before I did this though, I tried playing a movie using the Totem player and got the gstreamer plugins.

Then once I got those I was able to do the restricted extras.

sudo apt-get install ubuntu-restricted-extras

After this, I did the sound fix, added that line to the alsa base file. Then adjusted the speakers volume and stuff.

Viola, sound!!!

I am so happy. I was tried going to Geek Squad to get help one this, but they don't do Linux. I figured it out on my own without spending money. Yay!

---

### Post by greenleaves123 on 2009-03-13
Oh I sound mention that I had tried that sound fix the first time, but it did not work. I must have messed things up so much that nothing worked.

Reinstalling Ubuntu helped.

Now I am just worried about my solid state drive. I wonder how long it will last with so many reinstalls?

---

