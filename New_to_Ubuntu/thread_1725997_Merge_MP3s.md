---
title: "Merge MP3s"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by doppel.ganger on 2011-04-10
I want to easily merge 18 MP3s into one file. If you want to show me how to do this in the command line, the 18 MP3s are under albumname under artist under music under home. I'm not very command-line friendly! :) By the way, I run Ubuntu 10.10.

---

### Post by seawolf167 on 2011-04-10
See if [this link]("http://lyncd.com/2011/03/lossless-combine-mp3s/") helps you out

---

### Post by wolfen69 on 2011-04-10
I believe Audacity is good for this.

---

### Post by TeoBigusGeekus on 2011-04-10
```
cd ~/Music/replacewithartistname/replacewithalbumname
cat *.mp3 > nameoffinalhugesong.mp3
```

---

### Post by Enigmapond on 2011-04-10
> **wolfen69 said:**
> I believe Audacity is good for this.
Agreed as I've used it in the past for that however, that command line, in the link, worked for me as well...I just tried it. It's just a bit easier with Audacity.

Cheers!

---

### Post by doppel.ganger on 2011-04-10
cd ~/Music/Brian Regan/I Walked On The Moon
bash: cd: /home/thomas/Music/Brian: No such file or directory

i'll try audacity

---

### Post by GWBouge on 2011-04-10
Escape the spaces (put a \ before them), or put the directory in quotes.  Likewise, type the first 2 or 3 letters of the file or directory, and use the TAB key to autocomplete name, and it will do it for you.  Ex:

cd ~/Mu<press tab>Bria<press tab>I<press tab>

or

cd ~/Music/Brian\ Regan/I\ Walked\ On\ The\ Moon

or

cd "/home/thomas/Music/Brian Regan/I Walked On The Moon"

---

### Post by seawolf167 on 2011-04-10
> **doppel.ganger said:**
> cd ~/Music/Brian Regan/I Walked On The Moon
bash: cd: /home/thomas/Music/Brian: No such file or directory

i'll try audacity

It'd be

```
cd ~/Music/Brian\ Regan/I\ Walked\ On\ The\ Moon/
```

---

### Post by doppel.ganger on 2011-04-10
doppel@doppel-Dell-DE051:~$ cd ~/Music/Brian\ Regan/I\ Walked\ On\ The\ Moon/
doppel@doppel-Dell-DE051:~/Music/Brian Regan/I Walked On The Moon$ cat *.mp3 > iwalkedonthemoon.mp3
doppel@doppel-Dell-DE051:~/Music/Brian Regan/I Walked On The Moon$

Am I missing something? Audacity is WAY to advanced for me.

---

### Post by ~Plue on 2011-04-10
> **doppel.ganger said:**
> doppel@doppel-Dell-DE051:~$ cd ~/Music/Brian\ Regan/I\ Walked\ On\ The\ Moon/
doppel@doppel-Dell-DE051:~/Music/Brian Regan/I Walked On The Moon$ cat *.mp3 > iwalkedonthemoon.mp3
doppel@doppel-Dell-DE051:~/Music/Brian Regan/I Walked On The Moon$

Am I missing something? Audacity is WAY to advanced for me.
there should now be an iwalkedonthemoon.mp3 in that directory

---

### Post by ajgreeny on 2011-04-10
The trouble with using audacity is that each file will be decoded from mp3 to the raw sound then "merged", as you call it, and then encoded again, possibly resulting in a loss of sound quality.  If that is not important, audacity could be your answer, it is not really very advanced.

However have a look at mp3wrap from the repos, which will do this job for you quickly and easily without the need to decode and re-encode.  It is command line but can not be much simpler than this:-
```
mp3wrap album.mp3 file1.mp3 file2.mp3 file3.mp3 file4.mp3 
```which will produce the file **album.mp3** from all those **file1, file2, file3**, etc etc mp3 files.

I have used it a lot, together with mp3splt, and mp3gain.  Together they make up a sort of "mp3 suite" for simple splits, wraps, and volume changes of mp3 files.

---

### Post by doppel.ganger on 2011-04-10
I got it! SOLVED with the command line thing from TeoBigusGeekus and seawolf167! Thanks all of you sooo much!

---

