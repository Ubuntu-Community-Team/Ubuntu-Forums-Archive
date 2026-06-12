---
title: "Renaming Multiple files at once in Terminal"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by 73bazinga on 2011-01-24
Hello i am very new to Ubuntu and programing in general. i am trying to rename files in terminal. I would like to rename a list of mp3 files from Track 1, track 2, ect. to LOTR_01-01, LOTR_01-02 ect. I have a program in windows that does this for me but figure i should be able to do this in terminal as well. If there are any programs that will do the same in bulk on Unbuntu 10.10 that would help as well.

---

### Post by Sleven7 on 2011-01-24
Hi bazinga,

There is a much easier way of renaming files.

Places>Home Folder

Navigate to the folder where the files you want to rename are.

Right click on the file that you want to rename.

Select rename from the menu.

If you want to learn how to do it in the terminal (CLI) 
open the terminal and enter
```
man mv
```

Hope that helps...

---

### Post by Vaphell on 2011-01-24
```
#!/bin/bash

if [ "$1" ]
then
  label="$1"
else
  echo missing parameter \(label\)
  exit 1
fi

for f in *.mp3
do
  if [ $( echo "$f" | grep -E -c '[0-9]+\.mp3$' ) == "0" ]
  then
    echo $f - skipped, track number not found
    continue
  fi
  i=${f%.mp3}
  i=${i##*[^0-9]}
  mv -v "$f" "$label"-$( printf '%02g' $i ).mp3
done
```

it takes label as a parameter, for each .mp3 file it hunts for the last sequence of digits before .mp3 and assumes this is the track number, normalizes # to 2digits and renames the file to LABEL-##.mp3. Maybe not perfect but should work in trivial cases where there are no conflicts in track numbers.

---

### Post by PunkLV on 2011-01-24
I'd suggest to try this step by step, as it may prove useful in the future.
In your case this will do the job:
```
$ rename 's/ /_/' *.mp3
```
Replaces spaces in the filenames with underscore.
```
$ **N**=1; for i in *.mp3; do **echo** mv $i TRACK_$N.mp3; N=$[N+1]; done
```
**N**: Number to begin counting from
**echo**: after executing you will see exactly what is "feeded" to terminal; useful to avoid problems. To actually rename files using **mv** remove "echo" from the line.
However I'd suggest reading this beforehead, as it may prove quite useful to you [http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal](http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal)

---

### Post by 73bazinga on 2011-01-24
Thank You PunkLV and Vaphell. These look like the type of solutions I was looking for. I will try later and repost my results.:)

---

### Post by Teh_Messiah on 2011-07-18
I'm trying to do something similar from work through ssh to rename tv series episodes.

for example
```
sudo mv The.Simpsons.S08E06.DVDRip.XviD-TOPAZ.avi TS-S08E06.avi
```
except there are 22 seasons of the simpsons and 22 episodes in some seasons.
How do I do that?

Edit:
Ok I got my head around rename
```
sudo rename 's/the.simpsons.03x/TS-S03E/' *.avi
```
but how do I remove exeverything inbetween the TS-S03E(2 numbers here) and the .avi?

I need something like
```
sudo find /home/share2/TV_Series/ -name '[NAME]-S[0-9][0-9]E[0-9][0-9][EPISODE NAME].avi -exec mv {} [NAME]-S[0-9][0-9]E[0-9][0-9].avi
```
I know that wont work but I need something that does that please?

---

### Post by Teh_Messiah on 2011-07-18
Ok
```
sudo find . -name '*S[0-9][0-9]E[0-9][0-9]*.avi'
```
actually worked :D

---

### Post by PunkLV on 2011-07-20
Now officially you are one step closer to the abyss that is RegExp.
Enjoy the fall into botomless pit of variations and limitless creativity. Quite useful though.

---

### Post by Teh_Messiah on 2011-11-13
Finally after being bugged by this for so long and finally looking up and researching regex stuff I got my head around it.

To *rename* files like:
series.name.s01e01.episode.title.avi to SN-S01E01.avi
series.name.s01e02.episode.title.avi to SN-S01E02.avi
series.name.s01e03.episode.title.avi to SN-S01E03.avi
series.name.s01e04.episode.title.mpg to SN-S01E04.mpg

I used this!
```
sudo rename -n 's/series\.name\.s(\d{2})e(\d{2}).+(\.\D{3})/SN-S$1E$2$3/' *
```
**Note: I am using -n to make only a test and see if the result is what I want**
\. is making it so it reads a . as text not regex code.
What is in between the ()'s become a string value which is reflected in order of appearance as
$1 = whats in the 1st set of ()
$2 = whats in the 2nd set of ()
$3 = whats in the 3rd set of ()
The dot or . or (period, if you wish) can be taken to match any character whatsoever!
The + sign tells Perl to 'match one or more of the preceding character'.
**Once you have received the desired output from the test run change the -n to -v so you can verbosely see what it has done.**
It is possible to use it without using -v but if you make a mistake this is your only record of how **what** was moved to the **new what**.
I used information gathered from these sites.
[[COLOR="blue"]REGEX (LINK)[/COLOR]]("http://www.anaesthetist.com/mnm/perl/Findex.htm#regex.htm")
[[COLOR="Blue"]Rename multiple files with Linux (LINK)[/COLOR]]("http://www.go2linux.org/rename-bulk-files-with-linux-console-command")

---

### Post by Cyclane on 2011-11-14
I always use sed to make formulate commands and pipe those to a shell.

for example:
```

marvink@M-MWK-Ubuntu:~/testing$ ls
series.name.s01e01.episode.title.avi  series.name.s01e03.episode.title.avi
series.name.s01e02.episode.title.avi  series.name.s01e04.episode.title.avi
marvink@M-MWK-Ubuntu:~/testing$ ls | sed 's|^\([a-Z]\)[a-Z]*\.\([a-Z]\)[a-Z]*\.\(s[0-9]\{2\}e[0-9]\{2\}\)\..*$| mv & \1\2-\3.avi|'
 mv series.name.s01e01.episode.title.avi sn-s01e01.avi
 mv series.name.s01e02.episode.title.avi sn-s01e02.avi
 mv series.name.s01e03.episode.title.avi sn-s01e03.avi
 mv series.name.s01e04.episode.title.avi sn-s01e04.avi
marvink@M-MWK-Ubuntu:~/testing$ ls | sed 's|^\([a-Z]\)[a-Z]*\.\([a-Z]\)[a-Z]*\.\(s[0-9]\{2\}e[0-9]\{2\}\)\..*$| mv & \1\2-\3.avi|' | sh
marvink@M-MWK-Ubuntu:~/testing$ ls
sn-s01e01.avi  sn-s01e02.avi  sn-s01e03.avi  sn-s01e04.avi

```

many roads lead to rome ;)

---

### Post by Teh_Messiah on 2011-11-14
No one gave me any more help or suggestions since July so I gave up and spent many hours looking for the solution.
Mine looks shorter/simpler and I haven't done anything with sed before.
But thank you for the alternative.

---

### Post by Cyclane on 2011-11-14
Yeah sometimes, you need a little luck. Though regex isn't exactly for the 'absolute beginner' the forum this thread is posted in. ;)

The regex I posted could probably be improved since I don't have a lot of experience with regex, but it works. Sometimes that's the hardest part of a regex, actually getting a match. But regex is one of those things why linux rocks, you can do countless of things using it.

---

### Post by jzl003 on 2012-08-26
> **PunkLV said:**
> I'd suggest to try this step by step, as it may prove useful in the future.
In your case this will do the job:
```
$ rename 's/ /_/' *.mp3
```
Replaces spaces in the filenames with underscore.
```
$ **N**=1; for i in *.mp3; do **echo** mv $i TRACK_$N.mp3; N=$[N+1]; done
```
**N**: Number to begin counting from
**echo**: after executing you will see exactly what is "feeded" to terminal; useful to avoid problems. To actually rename files using **mv** remove "echo" from the line.
However I'd suggest reading this beforehead, as it may prove quite useful to you [http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal](http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal)

this was really useful to me but if you want to have space just use a backward slash before it so if its pictures ```
N=1; for i in *.jpg; do echo mv $i [COLOR="Red"][SIZE="4"]pictures\ [/SIZE][SIZE="4"][/SIZE][/COLOR]$N.jpg; N=$[N+1]; done
```
this basically works for everything in the terminal for a space

---

