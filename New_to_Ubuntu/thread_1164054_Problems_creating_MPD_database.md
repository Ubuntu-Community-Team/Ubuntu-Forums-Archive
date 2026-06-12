---
title: "Problems creating MPD database"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by paal on 2009-05-19
I've installed MPD and the config files looks ok, but when I try to create the database with
```
sudo mpd --create-db
```
it gives me the error
```
ffmpeg: failed to open /var/lib/mpd/Music/01 Sultans Of Swing.mp3
```
and so on for every mp3-file in my configured Music directory.

What to do?

---

### Post by cariboo on 2009-05-19
Linux see filenames with spaces as seperate files, In your pasted output:

> 01 Sultans Of Swing

would be see as:
[list]
[*]01
[*]Sultans
[*]Of
[*]Swing
[/list]

To remove spaces from file names I use a script that looks like this:

```
#!
/bin/sh
#Remove spaces from  mp3 file names
for i in *.mp3; do mv "$i" `echo $i | tr ' ' '_'`; done 
```

I save it as no_space.

I usually put scripts I create in /usr/local/bin, that way they are accessable form anywhere

```
sudo mv no_space /usr/local/bin/no_space
```

To use it you have to make it executeable:

```
sudo chmod +x no_space
```

Then just go to the directory your mp3's are and run the script:

```
no_space *
```

---

### Post by Mornedhel on 2009-05-19
I run MPD as well. Filenames with spaces have never been a problem for me.

(cariboo907: I just do rename 's/ /_/g' *.mp3)

What user does MPD run as (specified by the config file) ? I seem to remember that MPD drops all the privileges it was started as if given a user in its configuration. So sudo wouldn't have any effect. Make sure the user specified in the configuration file has access to your music library.

---

### Post by paal on 2009-05-20
> **Mornedhel said:**
> What user does MPD run as (specified by the config file) ? I seem to remember that MPD drops all the privileges it was started as if given a user in its configuration. So sudo wouldn't have any effect. Make sure the user specified in the configuration file has access to your music library.

MPD was running as user mpd. I removed that line from the config file and now it adds the songs to the db. I can't seem to find the songs in the db with GMPC though, but that might just be me doing something silly :) I'll look a bit more.

---

### Post by lunar cranium on 2009-07-04
i ran into a similar issue.  all but maybe 3 albums loaded for me.  so i checked the permissions on those albums' tracks, and they didn't look right.  so i chmod 755 *.* in their directories and mpd added them all on the next mpd --create-db.  thanks for the idea, guys!  now i'm :guitar:!

---

