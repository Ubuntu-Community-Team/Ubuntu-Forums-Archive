---
title: "Shell Script"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by jualin on 2009-11-20
I have some video files all ending in .wmv .mov .mpg. I have music files ending in .mp3 .wma. And finally I have some text files all end in the extension .txt

With the help of the forum, I wrote a script that generates subfolders, one for the music files, one for the video files, and one for the text files, and then organizes all of the files into the correct subfolders.
But I ran into a little problem :-({|=

*** I would like the script to write a log file that contains, for each file, the original file name, as well as the new file path/name it was moved to. And I would like the script to accept a command line argument, which is the folder that contains the unorganized files. This should allow the script to be located and run from anywhere in your file system, and accept any folder of unorganized files.

Example:

  organizefiles.sh mystuff/media 

where the subfolders would go inside "media"

Any ideas on how to do that?
Thank you!

---

### Post by scorp123 on 2009-11-20
Why are you not posting your script here so we can take a look? It would be easier than to reinvent the wheel and the fire ...

---

### Post by jualin on 2009-11-20
> **scorp123 said:**
> Why are you not posting your script here so we can take a look? It would be easier than to reinvent the wheel and the fire ...

here it is ```
#!/bin/bash
#the script

mkdir movies
mkdir songs
mkdir textfiles
mv *.wmv movies
mv *.mov movies
mv *.mpg movies
mv *.mp3 songs
mv *.wma songs
mv *.txt text
ls -l movies, >> log.txt
ls -l songs >> log.txt
ls -l textfiles >> log.txt
```

I would like for the log file to be something like this:

coolclip.wmv --> movies/coolclip.wmv
movie1.wmv --> movies/movie1.wmv
movie2.mpg --> movies/movie2.mpg
myvideo.mov --> movies/myvideo.mov
awesomesong.mp3 --> songs/awesomesong.mp3
jazz.mp3 --> songs/jazz.mp3
rock.mp3 --> songs/rock.mp3
song1.wma --> songs/song1.wma
song2.mp3 --> songs/song2.mp3
file1.txt --> textfiles/file1.txt
final.txt --> textfiles/final.txt
grades.txt --> textfiles/grades.txt
secretdoc.txt --> textfiles/secretdoc.txt

---

### Post by diesch on 2009-11-20
```
#!/bin/sh

RCFILE=~/.organizefilesrc

SRCDIR="$1"
LOGFILE=organizefiles.log

log(){
 msg="$1"
 echo "$msg"
 echo "$msg" >> "$LOGFILE"
}
     

for f in $SRCDIR/*; do
  ext="${f##*.}"
  dest="$(awk -F: "/^$ext:/ {print \$2}" "$RCFILE")"
  if [ -z "$dest" ]; then
     log "NOT moved $f"
  else
     mkdir -p "$dest"
     mv "$f" "$dest"
     log "Moved $f --> $dest"
  fi
done
```It needs a file *~/.organizefilesrc* that lists which extensions should moved to which folder, like

```
mp3:/home/someuser/audio/
wav:/home/someuser/audio/
avi:/home/someuser/video/
txt:/home/someuser/text

```

---

### Post by scorp123 on 2009-11-20
@diesch:  nice one :)

---

