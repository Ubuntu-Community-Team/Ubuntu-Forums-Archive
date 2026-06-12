---
title: "Linux Terminal currently playing song"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by superprash2003 on 2010-08-27
Hey,
  I'm looking for linux terminal commands to output the currently playing song of a media player. Im sure a general command for all media players would be great , but i dont think something like that exists.
 For example : i've already found out that the command to view the currently playing song in rhythmbox is "rhythmbox-client --print-playing" . 

 I would like to know similar commands for players like vlc and totem . Thanks..

---

### Post by superprash2003 on 2010-08-29
really hope to get some answers :) ..

---

### Post by MrWES on 2010-08-29
well if whichever player you are using,  you could just grep for the process.

```
pa aux | grep vlc
```

that might show the current song.

Bill

---

### Post by Vaphell on 2010-08-29
you mean ps? i tried that as the OP question intrigued me
it shows the command which spawned the process but it doesn't refresh the initial file name attached. If your vlc was started with A.mp3 and now B.mp3 plays, ps shows A.mp3

---

### Post by superprash2003 on 2010-08-29
Thanks for the replies ..yea.. i too initially thought of the ps command.. but it shows only the first played file.. just as vaphell said..any other suggestions??

---

### Post by Vaphell on 2010-08-29
i tried to check the possibly currently played song by checking the access time (stat <files>) but it doesn't seem to change when you open the mp3s or jump in the playlist so not only it's hackish but also useless :)

feature request will be the best choice i think

---

### Post by aninaiian on 2010-08-29
You could try using lsof.

```
lsof -F n -c MEDIAPLAYERCOMMAND 
```
should get you all the names of all the files opened by the program MEDIAPLAYERCOMMAND.  The -F flag allows you to select only certain fields to display with n being the name field, and the -c flag limits the output to files opened by commands that start with MEDIAPLAYERCOMMAND.

From there you could pipe it to grep if all the files your playing share some sort of common pattern.  Then parse the output to only the text after the last '/', or possibly find a command that can read media file tags to get the name as the output is a bit of a mess directly from lsof.

---

### Post by Vaphell on 2010-08-29
nice
lsof -F n -c vlc | grep "^.*\.mp3$" | sed 's/^n/vlc: now playing /g'  indeed shows which file is played currently :-)

---

### Post by superprash2003 on 2010-08-30
great work aninaiian and vaphell.. thats exactly what i wanted.. although i do know of a round about way to get the title and artist of a song given its absolute pathname , is there a direct way to get it from the terminal?
 Thanks once again both of you..

---

### Post by Vaphell on 2010-08-30
```

#!/bin/sh

apps="vlc totem rhythmbox banshee mplayer gnome-mplayer"

for app in $apps
do
  pat="([^\w-]$app)"
  if ps ux | grep -P $pat | grep -vq grep; then
    echo
    echo "$app detected"
    echo -------------------------
    file=`lsof -F n -c "$app" | grep -i "^.*\.mp3$" | sed 's/^n//g'`
    if [ ! -z "$file" ]; then
      echo -n "Now playing: "
      if mp3info "$file" 2>&1 | grep -q "does not have an ID3"; then
        echo $file
        echo MP3 info missing \(ID3v2 not supported\)    
      else
        echo
        mp3info "$file"
      fi
    else
      echo Playing no MP3 files
    fi
  fi
done

```

requires mp3info
what sucks is it doesn't support id3v2 tags, if there exists some app that does, it should go in the mp3info place.

edit:
i've found id3info (libid3-3.8.3-dev package) but its default output is not so nice, so some tweaking will be required. I'll play with it just for kicks later :)

---

### Post by Vaphell on 2010-08-30
```
#!/bin/sh

apps="vlc totem rhythmbox banshee mplayer gnome-mplayer"

echo
for app in $apps
do
  pat="([^\w-]$app)"
  if ps ux | grep -P $pat | grep -vq grep; then
    echo "$app detected"
    echo -------------------------
    file=`lsof -F n -c "$app" | grep -i "^.*\.mp3$" | sed 's/^n//g'`
    if [ ! -z "$file" ]; then
      echo "Now playing: "
      title=`id3info "$file" | grep "Title" | sed 's/^===.*[:].//g'`
      perf=`id3info "$file" | grep "performer" | sed 's/^===.*[:].//g'`
      album=`id3info "$file" | grep "Album" | sed 's/^===.*[:].//g'`
      year=`id3info "$file" | grep "Year" | sed 's/^===.*[:].//g'`
      track=`id3info "$file" | grep "Track" | sed 's/^===.*[:].//g'`
      echo File: "$file"
      if [ -z "$title" ] && [ -z "$perf" ]; then
        echo No MP3 info
      else  
        echo Title: "$title"
        echo Artist: "$perf"
        echo Album: "$album"
        echo Year: "$year"
        echo Track: "$track"
      fi
    else
      echo Playing no MP3 files
    fi
    echo
  fi
done
```

tested on 3 simultaneous apps (vlc, totem and gnome-mplayer)

---

### Post by superprash2003 on 2010-08-31
brilliant..thanks vaphell

---

### Post by glitch000 on 2013-02-11
I know this thread is old but I recently encountered the same requirement. 

In addition to Vaphell's code which is great, I would add 

file=`lsof -F n -c "$app" | egrep -i "^.*\.(mp3|flac|ogg|m4a|wma|wav)$" | sed 's/^n//g'`

so that way you get all audio files not just .mp3. Also, there is an issue with rhythmbox displaying more than 1 file to lsof. For some reason it opens the currently playing file as well as the previous one, and there is really no way of knowing which one it is because it follows no constant pattern within the lsof output.

Thanks.-

---

