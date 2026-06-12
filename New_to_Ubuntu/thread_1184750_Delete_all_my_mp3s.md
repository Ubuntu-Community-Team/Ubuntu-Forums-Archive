---
title: "Delete all my mp3s?"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by Jimleko211 on 2009-06-11
I recently converted all of my mp3s into .ogg, using the mp32ogg script.  Unfortunately, that left a lot of mp3s behind that I want to get rid of.  I know I can either use the terminal to do rm *.mp3 if I manually go into each directory, or I can delete them graphically, but is there a script out there that can just go into all my subdirectories of my Music folder and just delete all the mp3s?

---

### Post by TeoBigusGeekus on 2009-06-11
Why don't you go to Places->Search for files
and do a search for *.mp3 in all your partitions.
Just delete the found files.

---

### Post by hessiess on 2009-06-11
Don't, Converting between lossy formats destroys the quality of the audio. Move them into a separate file tree.

If you must delete them, you can cd into the root of your music folder and run

```

rm -R *.mp3

```

(recrsivly delete all files ending in ``.mp3'')

---

### Post by Jimleko211 on 2009-06-11
> **TeoBigusGeekus said:**
> Why don't you go to Places->Search for files
and do a search for *.mp3 in all your partitions.
Just delete the found files.
Thanks so much, that worked perfectly.

---

### Post by Jimleko211 on 2009-06-11
> **hessiess said:**
> Don't, Converting between lossy formats destroys the quality of the audio. Move them into a separate file tree.

If you must delete them, you can cd into the root of your music folder and run

```

rm -R *.mp3

```(recrsivly delete all files ending in ``.mp3'')

It sounds just fine to me.  Thanks for the terminal script, though ^^

---

### Post by unutbu on 2009-06-11
Is the loss in quality noticable? If you are satisfied with the quality of the oggs, then this command would delete the mp3s.

```
find ~/Music/ -name "*.mp3" -delete
```

PS. "rm -R *.mp3" does not work if the mp3's are in subdirectories because the bash expands *.mp3 in the top-level directory only.

---

### Post by jimv on 2009-06-11
Curious, why would one want to convert from mp3 to ogg?

---

### Post by eentonig on 2009-06-11
Maybe because ogg is free, while mp3 is proprietary?

Personnally, I keep using mp3 because it's practical if I need to share something with a friend.

---

### Post by unutbu on 2009-06-11
Maybe because mp3 has licensing issues?
[http://en.wikipedia.org/wiki/MP3#Licensing_and_patent_issues](http://en.wikipedia.org/wiki/MP3#Licensing_and_patent_issues)
while ogg is a free, open standard:
[http://en.wikipedia.org/wiki/Ogg](http://en.wikipedia.org/wiki/Ogg)

---

### Post by Mornedhel on 2009-06-11
I have found oggs to be lighter than mp3s with the same audio quality.

Note for the OP : you should have used mp32ogg with the --delete option.

---

### Post by donkyhotay on 2009-06-11
I use .ogg over .mp3 because the filesize is smaller, no licensing restrictions, and I can't hear the difference.

---

### Post by andrew.46 on 2009-06-11
Hi Jimleko211

> **Jimleko211 said:**
> I recently converted all of my mp3s into .ogg, using the mp32ogg script. 

I see that your question has been answered which leaves me to make a comment only :-). Since those external hard drives are getting so big in capacity and so small in physical footprint I think more and more it makes sense to rip music from cd and transcode to *flac* onto a big external drive and keep for archival purposes. That way subsequent transcoding to any other format is a small matter and there will be no quibbles about loss of quality. Although as unutbu has mentioned the loss of quality is often more than a little difficult to hear!

All the best,

Andrew

---

### Post by dioltas on 2009-06-11
Good point andrew. flac is too big for me at the moment though, If I ever get a monster hard drive then it would be definitely worthwhile. As foor the mp3 ogg thing, it's mp3 for me because of the portability issue, and my walkman doesn't support ogg.

---

### Post by andrew.46 on 2009-06-11
Hi dioltas,

> **dioltas said:**
> As for the mp3 ogg thing, it's mp3 for me because of the portability issue, and my walkman doesn't support ogg.

Fair enough :-). I will admit that I was keen enough when hunting for a player that I searched one out that has *native* ogg playback, in my case an iRiver x20. They are out there but of course mp3 playback is still the norm.

Andrew

---

### Post by nothingspecial on 2009-06-12
> **andrew.46 said:**
> Hi Jimleko211



I see that your question has been answered which leaves me to make a comment only :-). Since those external hard drives are getting so big in capacity and so small in physical footprint I think more and more it makes sense to rip music from cd and transcode to *flac* onto a big external drive and keep for archival purposes. That way subsequent transcoding to any other format is a small matter and there will be no quibbles about loss of quality. Although as unutbu has mentioned the loss of quality is often more than a little difficult to hear!

All the best,

Andrew

If that`s what you do (same as me) you might be interested in this.

[http://mp3fs.sourceforge.net/](http://mp3fs.sourceforge.net/)

It saves having 2 copies of every song taking up diskspace.

---

