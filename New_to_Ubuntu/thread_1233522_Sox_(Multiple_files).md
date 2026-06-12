---
title: "Sox (Multiple files)"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by Elep.Repu on 2009-08-06
Hello, I have read the man page for sox, but it is very confusing, and I believe I have tried everything.

Basically I want to convert a whole bunch of One type of file (flac) to another (mp3)
I tried 
```
sox "*.flac" ~/test/Nada/*.mp3
```and several other variations, but the man page is no help, nor is Google.
Anyone familiar with this program?
MAN page: [http://sox.sourceforge.net/sox.html](http://sox.sourceforge.net/sox.html)

Example;
```
aji@aj:~/test/Ada/Ada - Blondie$ sox -t *flac ~/test/Nada/*.mp3
sox FAIL formats: no handler for detected file type `flac'
aji@aj:~/test/Ada/Ada - Blondie$ sox "*.flac" ~/test/Nada/"*.mp3"
sox FAIL formats: can't open input file `*.flac': No such file or directory
aji@aj:~/test/Ada/Ada - Blondie$ sox -t *flac ~/test/Nada/*.mp3
sox FAIL formats: no handler for detected file type `flac'
aji@aj:~/test/Ada/Ada - Blondie$ sox *.flac ~/test/Nada/*.mp3
sox FAIL formats: no handler for detected file type `flac'
aji@aj:~/test/Ada/Ada - Blondie$ sox '*.flac' ~/test/Nada/.mp3
sox FAIL formats: can't open input file `*.flac': No such file or directory
aji@aj:~/test/Ada/Ada - Blondie$ 

```The *flac* package is installed. Apparently 
libsox-fmt-flac is obsoleted by the general base (so it should be installed..)

```
$ sudo apt-get install libsox-fmt-flac
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libsox-fmt-flac is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libsox-fmt-base
```

---

### Post by unutbu on 2009-08-06
Here are some other ways to convert flac to mp3:
[http://ubuntuforums.org/showthread.php?t=790587](http://ubuntuforums.org/showthread.php?t=790587)

---

### Post by mc4man on 2009-08-06
Here's a little script for flac2mp3 using the flac metadata to tag

```
#!/bin/bash
for f in *.flac
do
OUTF=`echo "$f" | sed s/\.flac$/.mp3/g`

ARTIST=`metaflac "$f" --show-tag=ARTIST | sed s/.*=//g`
TITLE=`metaflac "$f" --show-tag=TITLE | sed s/.*=//g`
ALBUM=`metaflac "$f" --show-tag=ALBUM | sed s/.*=//g`
GENRE=`metaflac "$f" --show-tag=GENRE | sed s/.*=//g`
TRACKNUMBER=`metaflac "$f" --show-tag=TRACKNUMBER | sed s/.*=//g`
DATE=`metaflac "$f" --show-tag=DATE | sed s/.*=//g`

flac -c -d "$f" - | lame [COLOR="Blue"]--vbr-new -V 2[/COLOR]  - "$OUTF"
id3v2 -t "$TITLE" -T "${TRACKNUMBER:-0}" -a "$ARTIST" -A "$ALBUM" -y "$DATE" -g "${GENRE:-12}" "$OUTF"
done



```

If you want to try and need help for running a script just ask.

you can add any number of ways to create a folder for the mp3's and move them, or just move them somewhere

The blue can contain any valid lame command(s) 
requires id3v2 installed for tagging

sudo apt-get install id3v2

---

### Post by Elep.Repu on 2009-08-19
> **mc4man said:**
> Here's a little script for flac2mp3 using the flac metadata to tag

```
#!/bin/bash
for f in *.flac
do
OUTF=`echo "$f" | sed s/\.flac$/.mp3/g`

ARTIST=`metaflac "$f" --show-tag=ARTIST | sed s/.*=//g`
TITLE=`metaflac "$f" --show-tag=TITLE | sed s/.*=//g`
ALBUM=`metaflac "$f" --show-tag=ALBUM | sed s/.*=//g`
GENRE=`metaflac "$f" --show-tag=GENRE | sed s/.*=//g`
TRACKNUMBER=`metaflac "$f" --show-tag=TRACKNUMBER | sed s/.*=//g`
DATE=`metaflac "$f" --show-tag=DATE | sed s/.*=//g`

flac -c -d "$f" - | lame [COLOR=Blue]--vbr-new -V 2[/COLOR]  - "$OUTF"
id3v2 -t "$TITLE" -T "${TRACKNUMBER:-0}" -a "$ARTIST" -A "$ALBUM" -y "$DATE" -g "${GENRE:-12}" "$OUTF"
done



```If you want to try and need help for running a script just ask.

you can add any number of ways to create a folder for the mp3's and move them, or just move them somewhere

The blue can contain any valid lame command(s) 
requires id3v2 installed for tagging

sudo apt-get install id3v2

Hey, I'd like to create a folder when I do it. How do I run it?

---

### Post by Elep.Repu on 2009-08-19
I just found [this]("http://www.linuxtutorialblog.com/post/solution-converting-flac-to-mp3-advanced-supports-drag-n-drop"), I'm trying to figure it out.
Anyone use it?

I don't really understand how to use the .desktop file, 
nor what he means by: 

[I]To be able to run the script directly (without explicit path) if you placed it in ~/bin, add the following line to your ~/.bashrc:
[/I] 	[INDENT] 		* 		export PATH="$PATH:~/bin" 		*
 	[/INDENT]

---

### Post by Elep.Repu on 2009-08-19
Ok, well I kind of got it working I think.
I installed* flac lame libmp3lame0*

I still don't know how the .desktop file works, or how I can right click a folder and run the command.

---

