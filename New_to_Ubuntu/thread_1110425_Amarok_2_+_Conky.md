---
title: "Amarok 2 + Conky"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by mjheagle8 on 2009-03-29
how can i do dbus calls to get the now playing information from amarok 2 to include in my conky script?

---

### Post by blueridgedog on 2009-03-30
I have not tried it, but this was what I was looking at when contemplating it:

[http://ubuntuforums.org/showthread.php?t=481720](http://ubuntuforums.org/showthread.php?t=481720)

---

### Post by radischem on 2009-05-03
Hey

I was looking for the same. I use it like this:

.conkyrc:

  Music ${hr 2}

	${execi 10 ~/.conky/amarok artist}
	${execi 10 ~/.conky/amarok title}
	${execi 10 ~/.conky/amarok album}
	${execi 10 ~/.conky/amarok year}
	${execi 10 ~/.conky/amarok genre}

.conky/amarok:

#!/bin/bash
# based on: amaroK info display script by eirc <eirc.eirc@gmail.com>
# amarok2 info display script by fireandfuel <fireandfuel@hotmail.de>
#
# requirements: amaroK 2 (!)

case "$1" in

# Now Playing Info
artist) qdbus org.kde.amarok /Player GetMetadata | grep artist ;;
title)  qdbus org.kde.amarok /Player GetMetadata | grep title ;;
album)  qdbus org.kde.amarok /Player GetMetadata | grep album ;;
year)   qdbus org.kde.amarok /Player GetMetadata | grep year ;;
genre)  qdbus org.kde.amarok /Player GetMetadata | grep genre ;;

esac





Hope that helped, although your post is quite old.

---

### Post by mjheagle8 on 2009-05-03
i actually learned about qdbus and wrote a similar script myself. thanks anyways though.

---

### Post by Sarai the Geek on 2009-06-08
> **radischem said:**
> Hey

I was looking for the same. I use it like this:

.conkyrc:

  Music ${hr 2}

    ${execi 10 ~/.conky/amarok artist}
    ${execi 10 ~/.conky/amarok title}
    ${execi 10 ~/.conky/amarok album}
    ${execi 10 ~/.conky/amarok year}
    ${execi 10 ~/.conky/amarok genre}

.conky/amarok:

#!/bin/bash
# based on: amaroK info display script by eirc <eirc.eirc@gmail.com>
# amarok2 info display script by fireandfuel <fireandfuel@hotmail.de>
#
# requirements: amaroK 2 (!)

case "$1" in

# Now Playing Info
artist) qdbus org.kde.amarok /Player GetMetadata | grep artist ;;
title)  qdbus org.kde.amarok /Player GetMetadata | grep title ;;
album)  qdbus org.kde.amarok /Player GetMetadata | grep album ;;
year)   qdbus org.kde.amarok /Player GetMetadata | grep year ;;
genre)  qdbus org.kde.amarok /Player GetMetadata | grep genre ;;

esac





Hope that helped, although your post is quite old.

Is there a way to make it display without the labels, i.e. "artist:" or "album:"?

---

### Post by unutbu on 2009-06-08
Sarai the Geek, does the output of the command 
```

qdbus org.kde.amarok /Player GetMetadata | grep artist
```

look like this:
```

artist: blah blah blah?
```

If so, try changing the command to 

```
qdbus org.kde.amarok /Player GetMetadata | awk '/artist:/{print substr($0,9)}' 
```

and if that works, try```
 

qdbus org.kde.amarok /Player GetMetadata | awk '/album:/{print substr($0,8)}'
```

to print the album without the "album:" part.

If it doesn't work, please post the output of 
```

qdbus org.kde.amarok /Player GetMetadata
```

when run in a terminal (and with amarok playing a song).

---

### Post by Sarai the Geek on 2009-06-08
When I replace the code with the one you provided, it doesn't print anything in conky. Here's the output of that command:

```
album: Cease to Begin
artist: Band of Horses
arturl: file:///home/sarai/.kde/share/apps/amarok/albumcovers/large/402982b936105d7ec249b59bf6822aab
audio-bitrate: 256
audio-samplerate: 44100
comment: 
genre: 
location: file:///home/sarai/Music/Band%20of%20Horses/03%20No%20One's%20Gonna%20Love%20You.m4a
mtime: 217000
rating: 0
time: 217
title: No One's Gonna Love You
tracknumber: 3
year: 2007

```

Also, this is the error message given by conky:
```
/home/sarai/Scripts/amarok: line 10: syntax error near unexpected token `org.kde.amarok'
```

---

### Post by Sarai the Geek on 2009-06-08
double post... whoops!

---

### Post by unutbu on 2009-06-08
Could you please post the contents of 
/home/sarai/Scripts/amarok
?

---

### Post by Sarai the Geek on 2009-06-08
> **unutbu said:**
> Could you please post the contents of 
/home/sarai/Scripts/amarok
?

It's the script posted by radischem earlier in the thread:

```
#!/bin/bash
# based on: amaroK info display script by eirc <eirc.eirc@gmail.com>
# amarok2 info display script by fireandfuel <fireandfuel@hotmail.de>
#
# requirements: amaroK 2 (!)

case "$1" in

# Now Playing Info
artist) qdbus org.kde.amarok /Player GetMetadata | grep artist ;;
title) qdbus org.kde.amarok /Player GetMetadata | grep title ;;
album) qdbus org.kde.amarok /Player GetMetadata | grep album ;;
year) qdbus org.kde.amarok /Player GetMetadata | grep year ;;
genre) qdbus org.kde.amarok /Player GetMetadata | grep genre ;;

esac
```When the error was given, I had changed it like you suggested so it looked like this:
```
#!/bin/bash
# based on: amaroK info display script by eirc <eirc.eirc@gmail.com>
# amarok2 info display script by fireandfuel <fireandfuel@hotmail.de>
#
# requirements: amaroK 2 (!)

case "$1" in

# Now Playing Info
qdbus org.kde.amarok /Player GetMetadata | awk '/artist/{print substr($0,9)}'
title) qdbus org.kde.amarok /Player GetMetadata | grep title ;;
album) qdbus org.kde.amarok /Player GetMetadata | grep album ;;
year) qdbus org.kde.amarok /Player GetMetadata | grep year ;;
genre) qdbus org.kde.amarok /Player GetMetadata | grep genre ;;

esac
```

It's entirely possible that I'm a little confused here, it happens more than I'd care to admit. 
```
qdbus org.kde.amarok /Player GetMetadata | awk '/artist:/{print substr($0,9)}
```
does print the correct information when entered into a terminal, but I'm not entirely sure how to get that information to be displayed in conky. I tried "exec" but it didn't seem to want to parse it. A google hunting-gathering mission is probably in order here.

---

### Post by Sarai the Geek on 2009-06-09
Ah, figured it out. I just needed to make a separate script containing only that line then use execi to display it in conky. :)

---

### Post by unutbu on 2009-06-09
Instead of making another script, you could instead 

change

```
qdbus org.kde.amarok /Player GetMetadata | awk '/artist/{print substr($0,9)}'
title) qdbus org.kde.amarok /Player GetMetadata | grep title ;;
album) qdbus org.kde.amarok /Player GetMetadata | grep album ;;
year) qdbus org.kde.amarok /Player GetMetadata | grep year ;;
genre) qdbus org.kde.amarok /Player GetMetadata | grep genre ;;

```

to
```

**artist)** qdbus org.kde.amarok /Player GetMetadata | awk '/artist/{print substr($0,9)}' **;;**
title) qdbus org.kde.amarok /Player GetMetadata | grep title ;;
album) qdbus org.kde.amarok /Player GetMetadata | awk '/album/{print substr($0,8)}' ;;
year) qdbus org.kde.amarok /Player GetMetadata | grep year ;;
genre) qdbus org.kde.amarok /Player GetMetadata | grep genre ;;

```

---

### Post by bingotailspin on 2009-06-30
Here is progress in percentage of song:

```

progress)
    curr=`qdbus org.kde.amarok /Player PositionGet`
    tot=`qdbus org.kde.amarok /Player GetMetadata | awk '/mtime:/{print substr($0,8)}'`
    if (( $tot )); then
        expr $curr \* 100  / $tot
    fi
    ;;

```

---

### Post by aijeitpipol on 2010-12-25
i tried everything in this thread and conky does not show anything :( just the empty space where the info from amarok2 should appear

this is my script in .conky

```
#!/bin/bash
# based on: amaroK info display script by eirc <eirc.eirc@gmail.com>
# amarok2 info display script by fireandfuel <fireandfuel@hotmail.de>
#
# requirements: amaroK 2 (!)

case “$1&#8243; in

# Now Playing Info
artist) qdbus org.kde.amarok /Player GetMetadata | awk '/artist/{print substr($0,9)}' ;;
title) qdbus org.kde.amarok /Player GetMetadata | grep title ;;
album) qdbus org.kde.amarok /Player GetMetadata | grep album ;;
year) qdbus org.kde.amarok /Player GetMetadata | grep year ;;
genre) qdbus org.kde.amarok /Player GetMetadata | grep genre ;;
progress)
    curr=`qdbus org.kde.amarok /Player PositionGet`
    tot=`qdbus org.kde.amarok /Player GetMetadata | awk '/mtime:/{print substr($0,8)}'`
    if (( $tot )); then
        expr $curr \* 100  / $tot
    fi
    ;;

esac
```and this is how I'm calling it in .conkyrc
```
${font Goudy Bookletter 1911:style=Bold}Musica${font} ${hr 2}
${execi 10 ~/.conky/amarok artist}
${execi 10 ~/.conky/amarok title}
${execi 10 ~/.conky/amarok album}
${execi 10 ~/.conky/amarok year}
${execi 10 ~/.conky/amarok genre}
${execi 10 ~/.conky/amarok progress}
```I'm using Amarok 2.3.0 and KDE 4.2.2 

Can u help me?

---

