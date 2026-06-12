---
title: "Q on Joining-splitting mp3 with Audacity"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by paker on 2011-04-17
I am joining and splitting mp3 files with Audacity. 128 kbps files. Is Audacity is joining/splitting mp3 files without conversion/reconversion? What I mean is when Audacity imports my mp3, does it convert mp3 to wave? When it exports the joined/split files, does it convert them from wave to mp3?

---

### Post by paker on 2011-04-19
Audacity seems to convert mp3 to wave and back to mp3. Sound quality goes down noticeably. I searched this forurm and found other members with the same experience.

Is there a program that works like audacity without converting repeatedly mp3 > wave > mp3?

---

### Post by Paqman on 2011-04-19
There's a command line tool called mp3wrap which will join mp3 files without re-encoding. For a really quick and dirty solution you can use cat to join them, but that will mess up the metadata.

---

### Post by paker on 2011-04-26
I already tried cat but car cd player (mp3) gets hung up every once in a while. I will try mp3wrap. What I am really looking for is a little more advanced, an editor. The original mp3 files were poorly prepared (voice recordings). They were improperly cut to smaller pieces in the middle of lecture, and joined different lectures. If any one knows an editor like audacity without conversion/reconversion, please let me know. Thanks.

---

### Post by paker on 2011-05-04
I couldn't find an mp3 editor that works like audacity. But I can join with cat command,
cat file1.mp3 file2.mp3 file3.mp3 > joined.mp3.
And clean up the tag.

For splitting, mp3splt (without i) from [http://mp3splt.sourceforge.net/mp3splt_page/home.php](http://mp3splt.sourceforge.net/mp3splt_page/home.php)
It has a graphical user interface. If split to 2 halves, enter 3 split times, beginning, split point, end.

Thanks for suggestions.

---

