---
title: "Amarok question"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by cptrohn on 2009-04-24
Hey all.. Happy Jaunty release day!

I have a amarok specific question.. I'm using Amarok 2 in Jaunty, and I have a question about my music collection... It seems when I was still a windoze user and I backed up all of my music to an external HD that about half of the collection got seperated from the album art/what CD it was/and the artist somehow... so about half of them are just listed as single files instead of being a part of a whole CD.... SOOOOO my question is, if I just move those single files into amarok will it sort them out in my collection or do I need to go through the about 150 different CD, (and I don't know how many seperate song files.) and put them into folders based on artist, CD name and album art manually..... Boy that sounds like an awful lot of work if I have to....

It seems that the CD's I ripped just using WMP are fine, but anything I ripped using the Zune software is spread out all over hells creation.

Could I defrag the external HD somewhere and kind of get the files back in order somehow?  (and windows is gone completely, so would I need a linux defrag app to do this?)

Boy this is just a mess, it will take me a month to get everything in order:(

---

### Post by kanikilu on 2009-04-24
I don't know about amarok specifically, but as long as the files are tagged right, I would think there has to be software out there (if amarok can't do it) that can organize them into a folder structure.

What format are these files in? I'm guessing not MP3?

Oh, and as far as I know, there isn't a way to defrag Windows partitions from Linux, so if you don't have Windows anymore, you might want to think about eventually moving data off that temporarily and formatting it with ext3 or 4.

---

### Post by cptrohn on 2009-04-24
> **kanikilu said:**
> I don't know about amarok specifically, but as long as the files are tagged right, I would think there has to be software out there (if amarok can't do it) that can organize them into a folder structure.

What format are these files in? I'm guessing not MP3?

Oh, and as far as I know, there isn't a way to defrag Windows partitions from Linux, so if you don't have Windows anymore, you might want to think about eventually moving data off that temporarily and formatting it with ext3 or 4.

Yeah they are not MP3 or Flac or Ogg, they are wma's I want to covert them over to another format( wish there was an app that would convert all the  files in a one shot bulk deal but I haven't found one yet), but finding time to do that right now is hard for me....  I asked the same question at amarok's forum, so when I get an answer I'll post back here in case anybody else might be having the same problem.

---

### Post by kanikilu on 2009-04-24
> **cptrohn said:**
> I want to covert them over to another format( wish there was an app that would convert all the  files in a one shot bulk deal but I haven't found one yet)
Have you tried SoundConverter in the repos (universe)? ```
sudo apt-get install soundconverter
```

---

### Post by cptrohn on 2009-04-24
> **kanikilu said:**
> Have you tried SoundConverter in the repos (universe)? ```
sudo apt-get install soundconverter
```

No I haven't tried that!  Thanks I will take a look at it.

---

### Post by sanguinoso on 2009-09-10
I know this is an old thread but in case anyone looks:

amarok has a way to organize your music collection. Right click on your collection and select organize files. You can choose how you want the music files to be organized on the hard drive. You can also do a custom scheme. Also, you can change the location of your collection with Settings -> Configure Amarok... Then select the Collection option.

This was done with Amarok 2.1

---

