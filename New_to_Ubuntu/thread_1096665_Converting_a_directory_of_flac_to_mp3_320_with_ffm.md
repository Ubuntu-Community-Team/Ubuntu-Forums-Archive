---
title: "Converting a directory of flac to mp3 320 with ffmpeg"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by methodmarvel on 2009-03-15
I'm looking to convert a directory of flac files to mp3 320kbps lame using ffmpeg from the command line *without* deleting/overwriting the original flac files

This doesn't seem to work
```
$ ffmpeg -i *.flac -ab 320k -ac 2 *.mp3
```
Maybe it's the wildcard *? I want the mp3s to be named the same as the flacs

If I'm specific for one file:
```
$ ffmpeg -i 1.flac -ab 320k -ac 2 *.mp3
```
I get a file called *.mp3 @ 320kbps stereo but with no ID tags (which are on the .flac)

I'd use sound-converter but it doesn't make 256 VRB when I select it - it makes them ~156

---

### Post by logos34 on 2009-03-15
Here's a Python script I use that should work:


> #!/usr/bin/env python

import os
import os.path
import sys

LAME_QUALITY = CBR 320

def escape_quotes(path):
	return path.replace('"', r'\"')


# Gets the tag of a flac file
def get_flac_tag(flac_file, tag):
	flac_file = os.path.abspath(flac_file)

	# Make sure the path exists and that the file exists
	if not os.path.exists(flac_file) or not os.path.isfile(flac_file):
		return ''

	flac_file = escape_quotes(flac_file)

	f = os.popen('metaflac --show-tag=%s "%s"' % (tag.upper(), flac_file))
	meta_out = f.read()
	f.close()

	try:
		return meta_out[meta_out.find('=') + 1:].strip()
	except:
		return ''


def encode_mp3(flac_file):
	mp3_file, ext = os.path.splitext(flac_file)
	wave_file = escape_quotes(mp3_file + '.wav')
	mp3_file = escape_quotes(mp3_file + '.mp3')
	flac_file = flac_file

	# Converts to wave
	os.system('flac -d -f "%s"' % escape_quotes(flac_file))

	year = get_flac_tag(flac_file, 'DATE')
	if year: year = year[:5]
	title = escape_quotes(get_flac_tag(flac_file, 'TITLE'))
	artist = escape_quotes(get_flac_tag(flac_file, 'ARTIST'))
	album = escape_quotes(get_flac_tag(flac_file, 'ALBUM'))
	track_number = int('0' + get_flac_tag(flac_file, 'TRACKNUMBER'))
	# Missing out GENRE because genre is stored a index in mp3 but as a string in flac

	command = 'lame **[COLOR="Red"]-b 320[/COLOR]** -V %d --tt "%s" --ta "%s" --tl "%s" --ty %s --tn %d "%s" "%s"' \
	% (LAME_QUALITY, title, artist, album, year, track_number, wave_file, mp3_file)

	# Converts wave to mp3 then deletes wave
	os.system(command)
	os.system('rm "%s"' % wave_file)


def main(argv):
	for i in argv:
		flac_file = i

		if not os.path.exists(flac_file) or not os.path.isfile(flac_file):
			print '%s is not found.' % (flac_file)
			sys.exit(1)

		encode_mp3(flac_file)


if __name__ == '__main__':
	if len(sys.argv) < 2:
		print 'usage: %s <flacfile(s)>' % (sys.argv[0])
		sys.exit(1)
		
	main(sys.argv[1:])

Just name it something like 'flac2mp3.sh', make it executable

> sudo chmod +x flac2mp3.sh

and stick it in your $HOME.  Invoke it with

> [COLOR="Blue"]**./**[/COLOR]flac2mp3.sh

---

### Post by nothingspecial on 2009-03-15
Before you do that you might want to have a look at [this]("http://mp3fs.sourceforge.net/").

Its a great space saver. It mounts your flac collection as a directory of mp3s with all tags intact. But they don`t physically exist until you open/copy/play them . Then the script transfers them on the fly and puts a real mp3 where you want it without creating anything in the original directory.

If you see what I mean.........

.....I`m not explaining this very well  :redface:

---

### Post by methodmarvel on 2009-03-15
> **logos34 said:**
> Here's a Python script I use that should work:




Just name it something like 'flac2mp3.sh', make it executable



and stick it in your $HOME.  Invoke it with


I've tried your script and got the error

```
user@computer:~/flac$ ./flac2mp3.sh
  File "./flac2mp3.sh", line 7
    LAME_QUALITY = CBR 320
                         ^
SyntaxError: invalid syntax
```

---

### Post by logos34 on 2009-03-15
> **methodmarvel said:**
> I've tried your script and got the error

```
user@computer:~/flac$ ./flac2mp3.sh
  File "./flac2mp3.sh", line 7
    LAME_QUALITY = CBR 320
                         ^
SyntaxError: invalid syntax
```

oops, sorry, I changed it from "2" (I had it set for vbr 2), but apparently it has to be an integer.  So use 

> LAME_QUALITY = 2

The "-b 320' part in red is what counts and should give you cbr 320 (just checked it)

---

### Post by mc4man on 2009-03-15
While you can simply use ffmpeg directly like this it's better to decompress first to .wav and then use lame

```
for f in *.flac; do ffmpeg -i "$f" -acodec libmp3lame -ab 320k  "${f%.flac}.mp3"; done
```

If you want to transfer the flac tags then a script like this works fine ( you can insert any lame parameters you wish

[PHP]#!/bin/bash
for f in *.flac
do
OUTF=`echo "$f" | sed s/\.flac$/.mp3/g`

ARTIST=`metaflac "$f" --show-tag=ARTIST | sed s/.*=//g`
TITLE=`metaflac "$f" --show-tag=TITLE | sed s/.*=//g`
ALBUM=`metaflac "$f" --show-tag=ALBUM | sed s/.*=//g`
GENRE=`metaflac "$f" --show-tag=GENRE | sed s/.*=//g`
TRACKNUMBER=`metaflac "$f" --show-tag=TRACKNUMBER | sed s/.*=//g`
DATE=`metaflac "$f" --show-tag=DATE | sed s/.*=//g`

flac -c -d "$f" | lame --replaygain-accurate -q 0 --vbr-new -V 3 - "$OUTF"
id3 -t "$TITLE" -T "${TRACKNUMBER:-0}" -a "$ARTIST" -A "$ALBUM" -y "$DATE" -g "${GENRE:-12}" "$OUTF"
done
mkdir temp
mv *.mp3 ./temp[/PHP]

Without tags then this can be a script or seperate commands
[PHP]#!/bin/bash
mkdir temp
flac -d *.flac
for f in *.wav; do lame --vbr-new  "$f" ./temp/"${f%.wav}.mp3"; done
rm *.wav[/PHP]

Adjusted for 320k

[PHP]#!/bin/bash
mkdir temp
flac -d *.flac
for f in *.wav; do lame -b 320k "$f" ./temp/"${f%.wav}.mp3"; done
rm *.wav[/PHP]

In all 3 you can use any valid lame parameters you wish - see lame --longhelp (*must have lame installed *

---

### Post by johncc330 on 2011-06-14
Thanks mc4man...

I only had to change id3 to id3v2 in my machine... The original id3 code seemed unattended. id3v2 is command-line compatible.

John

---

### Post by W29 on 2011-11-21
> **nothingspecial said:**
> Before you do that you might want to have a look at [this]("http://mp3fs.sourceforge.net/").

Its a great space saver. It mounts your flac collection as a directory of mp3s with all tags intact. But they don`t physically exist until you open/copy/play them . Then the script transfers them on the fly and puts a real mp3 where you want it without creating anything in the original directory.

If you see what I mean.........

.....I`m not explaining this very well  :redface:

Thank you! Thank you! Thank you! This is too awesome!!!
You just made my day. \\:D/

---

### Post by ldiamond on 2012-02-02
Come on people!!! These shouldn't be the answers. Let's keep it simple would you?

[http://lewisdiamond.blogspot.com/2012/01/converting-flac-to-mp3.html](http://lewisdiamond.blogspot.com/2012/01/converting-flac-to-mp3.html)

---

### Post by uRock on 2012-02-02
Rebirth flame extinguished.

Thread Closed

---

