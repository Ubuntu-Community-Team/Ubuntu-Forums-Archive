---
title: "Converting mp3 to AAC/m4a"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by drunkmatador on 2009-06-10
Hey everyone.. I just purchased a Nintendo DSi and am now having some trouble putting music on it. The DSi does not support mp3 files, but rather AAC and m4a files. Maybe another extension too I'm not sure.

So now I've got to convert all my mp3 files to AAC, as my original cds and vinyl are locked in storage, far, far away. This is proving to be a much more difficult task than I imagined.

I managed to convert the files to AAC using a script that somebody posted in an earlier thread on this site. This is the script:

```
#!/bin/bash
mp3file=$1
wavfile=$(echo $mp3file | sed -e s/mp3$/wav/)
aacfile=$(echo $mp3file | sed -e s/mp3$/aac/)

mplayer -ao pcm:file="$wavfile" "$mp3file"
faac -o "$aacfile" "$wavfile"
rm "$wavfile"
```

As you can see, it uses mplayer and faac to do the conversion. This left me with AAC files that played and sounded fine (as fine as to be expected when converting from one lossy format to another).

But then I put them on the DSi, through an SD card, and the files don't show up. Out of curiosity I then changed the file extensions to .m4a, popped the card back into my DSi, and.. the songs showed up!

Only this time they won't play. Says something about an invalid format, if I remember right. I'm thinking maybe I need to convert the mp3 files straight to m4a with AAC encoding, if this is possible? I don't know much about media files or converting them, so I really have no idea.

Oh and I know this isn't a forum for Nintendo DSi questions, but in Windows/Mac it's as easy as telling itunes to convert the files and then it's done. So there's got to be something wrong with the method I'm going about this.. perhaps another program I should use? I read about the nautilus script that converts audio files but am not sure if it converts to AAC or m4a and after installing through Synaptec I can't even figure out how to work the darn thing.

Thanks!

---

### Post by CJ Master on 2009-06-10
I am also interested in this.

While the DSi reads AAC-type files, it will (ironically) not read *.aac files, and these are not the same as *.m4p.

---

### Post by drunkmatador on 2009-06-10
This really is turning out to be impossible! I downloaded a windows program called Format Factory, at the advice of somebody in another thread who was specifically talking about converting for use on a DSi, and tried running it in Wine. Seemed to be working and then the program froze.

---

### Post by aimpau on 2009-06-10
hmmmmmm....

try first to install ffmpeg in the repos. then on the command prompt:

```

sudo ffmpeg -i input.mp3 -ab 192k output.aac

```
The problem here would be AAC tagging....also I'm not sure if what I just posted is just the same thing as your script since this also uses libfaac

---

### Post by nothingspecial on 2009-06-10
Will ffmpeg not do it? something like

```
ffmpeg -i input.mp3 -acodec libfaac -ab 128k output.aac
```

Never tried this particular conversion.

---

### Post by zvacet on 2009-06-10
You can convert yo aac with [pacpl.]("http://pacpl.sourceforge.net/") How to work with it you can find [here.]("http://ubuntuforums.org/showthread.php?t=712064")

---

### Post by andrew.46 on 2009-06-10
Hi drunkmatador,

> **drunkmatador said:**
> This really is turning out to be impossible! I downloaded a windows program called Format Factory, at the advice of somebody in another thread who was specifically talking about converting for use on a DSi, and tried running it in Wine. Seemed to be working and then the program froze.

The program called 'Format Factory' was discussed in some depth [in another thread]("http://ubuntuforums.org/showthread.php?t=1133138"). It is not a program I would use myself but I leave you to make your own judgement if you have the time to read this thread.

Some have suggested FFmpeg which might not be such a bad idea. Have a look at the FakeOudoorsman's page so you can unlock the most from your copy:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

I converted mp3s quite successfully to aac using several different suffixes: .aac, .m4a, .mp4 so you could perhaps use trial and error to see which particular naming scheme your device is happy with?

All the best,

Andrew

---

### Post by drunkmatador on 2009-06-11
> **aimpau said:**
> hmmmmmm....

try first to install ffmpeg in the repos. then on the command prompt:

```

sudo ffmpeg -i input.mp3 -ab 192k output.aac

```
The problem here would be AAC tagging....also I'm not sure if what I just posted is just the same thing as your script since this also uses libfaac

"Unsupported codec for output stream #0.0"

---

### Post by drunkmatador on 2009-06-11
> **nothingspecial said:**
> Will ffmpeg not do it? something like

```
ffmpeg -i input.mp3 -acodec libfaac -ab 128k output.aac
```

Never tried this particular conversion.

"Unknown codec 'libfaac'"

---

### Post by drunkmatador on 2009-06-11
> **zvacet said:**
> You can convert yo aac with [pacpl.]("http://pacpl.sourceforge.net/") How to work with it you can find [here.]("http://ubuntuforums.org/showthread.php?t=712064")

This program worked great!

To anybody who is going to be using it, I had to make a change to the /usr/bin/pacpl file.. do a search for "ablum" and change it to say "album" instead. I found this when a conversion to m4a wouldn't work.. and in verbose mode it said it didn't understand the option "ablum".. haha.

So just convert to m4a and the DSi should read them right away.. man this thing is cool, so many effects to add to the music. Nothing I'd use most the time of course but it's fun to play with. :D

---

