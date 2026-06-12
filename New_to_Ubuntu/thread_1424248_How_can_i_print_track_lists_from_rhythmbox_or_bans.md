---
title: "How can i print track lists from rhythmbox or banshee?"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by kbabeatbox on 2010-03-07
I recently made a few playlists and burned them to CD.
Is there a way of turning a playlist into a simple .txt file or equivalent, which shows only the artist name and song title.
I would very much like to be able to print off a list and put it in the CD case of the CDs I am burning. Is there a utility to do this for me and maybe make it fit in the CD cover?
Thanks in advance
xo

---

### Post by DouglasAWh on 2012-01-29
> **kbabeatbox said:**
> I recently made a few playlists and burned them to CD.
Is there a way of turning a playlist into a simple .txt file or equivalent, which shows only the artist name and song title.
I would very much like to be able to print off a list and put it in the CD case of the CDs I am burning. Is there a utility to do this for me and maybe make it fit in the CD cover?
Thanks in advance
xo

I would like to be able to do this too. However, I'd want to grab a little bit more from the ID3 tag, like what's in the license and comment field. I'd be fine running it from nautilus or command line, but going to each track and getting this info is quite tedious!

---

### Post by mcduck on 2012-01-29
That shouldn't be too complicated, if you export the playlist from banshee as .m3u file, you could then use a shell script with some CLI tool like id3info (included in the *libid3-tools* package) to read the tags from each file in the playlist and parse them to a more human-readable format.


Of course if writing such script is easier than doing it by hand depends on how long playlist you have... ;)

edit: Actually exporting to .xspf instead of .m3u might be a good idea, that would give you a much more useful XML file.

---

### Post by DouglasAWh on 2012-01-29
> **mcduck said:**
> 
Of course if writing such script is easier than doing it by hand depends on how long playlist you have... ;)

I have to do this weekly. It's a major time-suck. There's no way scripting it won't be quicker.

Below is what I have so far (it's not from banshee, but best-practices call for me to group them all in the same directory anyway, so it is quite a bit better than what I had). I don't really know sed and awk, so it will take some time to figure out how to parse the text, but at least now I don't have to click in banshee 1000 times to get the info.

```

#!/bin/bash
# It's not pretty, but I think it's better than what I've got now!

echo "This script requires mid3v2. If nothing happens, make sure it is installed. Was already installed on my system so I have no idea how it will react if you don't have it installed."
echo "As coded, the script requires being in the dir you want the output from"

#This part will rename all your files and dir and take the spaces out and replace them with underscores.
for f in *; do
     file=$(echo $f | tr ' ' _)
     [ ! -f $file ] && mv "$f" $file
done


cd .
for file in `dir -d *` ; do
mid3v2 -l "$file" >> test.txt
done


```

---

