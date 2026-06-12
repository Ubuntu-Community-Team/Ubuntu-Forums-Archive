---
title: "one mp3 file plays choppy on my comp"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by hanzj on 2009-04-02
Hello,
I downloaded a mp3 from a website. On my ubuntu comp, it plays kinda choppy (with the default mp3 player Movie Player). By this I mean there would be a slight pause every second. When I examine the file in audacity, there are no choppiness I can see in the file.  And when I play the file in Audacity, it sounds fine. The file is MPEG 3 Audio, Layer 3 (MP3)

Other mp3 files that I have on my comp are not choppy.  

What's going on?

---

### Post by blazemore on 2009-04-02
If you bought the track, you're entitled to download it again from wherever you want.
Try another website that will enable you to download the track again.

---

### Post by mikechant on 2009-04-02
You could use this tool:
[http://mp3val.sourceforge.net/download.shtml](http://mp3val.sourceforge.net/download.shtml)
to validate the file and possibly fix it if it's dodgy.

The binaries for this tool are for windows, but the source is platfrom independant, with a Linux specific make file.

---

### Post by blazemore on 2009-04-02
Have you got everything installed to play mp3s?
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by brayden13 on 2009-04-02
Why don't you try VLC? It is opensource. To install It i think you just enter into terminal
```
sudo apt-get install vlc
```
You can install it from Synaptic Package Manager.

It is a really good media player that i suggest you use. It is very light and plays heaps of formats.

---

### Post by blazemore on 2009-04-02
I'd still recommend just downloading it again.
You said Audiacity doesn't look choppy. When you play it in audacity, does it play back choppy?

---

### Post by hanzj on 2009-04-02
blazemore,
when I play the mp3 in audacity, mp3 file does _NOT_ play back choppy. It plays back just fine.

---

### Post by blazemore on 2009-04-03
Okay so that indicates to me a problem with your music application (totem).
Try opening it in Rhythmbox, Banshee, Exaile, Songbird, Amarok, or another dedicated music application. I recommend all of the above:

Rhythmbox: Included with Ubuntu
Banshee: Attractive and easy to use
Exaile: Brilliant Dynamic Playlists
Songbird: Excellent iTunes clone
Amarok: Great KDE integration

---

### Post by hanzj on 2009-04-03
[blazemore]("http://ubuntuforums.org/member.php?u=326352"),
I tried rhythmbox and banshee, and I get the same choppiness.
And this is  after I installed 
 ubuntu-restricted-extras

---

### Post by billgoldberg on 2009-04-03
Just download it again.

Either the file is badly downloaded or it's a fluke.

I have 10.000+ mp3 files and they all play fine, with the same codecs you have.

---

### Post by hanzj on 2009-04-04
I downloaded the file again but it's still choppy. This is weird.

---

### Post by hanzj on 2009-04-04
I used audacity to convert the mp3 into ogg. now my media players play the file without any choppiness.

---

### Post by PGScooter on 2009-07-21
you should post a bug report with regard to the applications that play it back choppily.

---

