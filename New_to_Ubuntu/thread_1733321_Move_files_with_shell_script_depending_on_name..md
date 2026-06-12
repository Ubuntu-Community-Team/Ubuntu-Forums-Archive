---
title: "Move files with shell script depending on name."
date: 2011-04-19
forum: New to Ubuntu
---

### Post by junkyhlm on 2011-04-19
Hi, im trying to make a shell script to move files automatically.
 
The files in question are torrent-files and i want to move them to subfolders depending on their name. 
 
ex.
./folder/TVShow1.S01E01.torrent moves into ./folder/TVShow1/
./folder/TVShow2.S01E01.torrent moves into ./folder/TVShow2/
./folder/TVShow3.S01E01.torrent moves into ./folder/TVShow3/
 
etc.
 
As of now the only scripting i've done is:
 
```
 
#!/bin/sh
 
# Change directory
cd /media/store/download/000-torrents/Serier
 
# Move the torrentfiles
mv TVShow1*.torrent ./TVShow1
mv TVShow2*.torrent ./TVShow2
mv TVShow3*.torrent ./TVShow3
 
exit

```
 
Any one chan help me make this more efficient?

---

### Post by Crusty Old Fart on 2011-04-19
This should do it:
```

#!/bin/bash
set -e

# Change directory
cd /media/store/download/000-torrents/Serier

# Move the torrentfiles
for file in TVShow*.torrent; do
  mkdir -p ${file%%.*}
  mv $file ${file%%.*}
done

exit 0

```

---

### Post by junkyhlm on 2011-04-19
Okay. Thank you.
 
But what if the tvshow has different names?
 
ex.
 
./TVShow1
./LeMacabre
./Flash
./Thunder
 
etc.

---

### Post by Crusty Old Fart on 2011-04-19
> **junkyhlm said:**
> Okay. Thank you.
 
But what if the tvshow has different names?
 
ex.
 
./TVShow1
./LeMacabre
./Flash
./Thunder
 
etc.

In that case:
```

#!/bin/bash
set -e

# Change directory
cd /media/store/download/000-torrents/Serier

# Move the torrentfiles
[COLOR=Blue]**for file in *.torrent; do**[/COLOR]
  mkdir -p ${file%%.*}
  mv $file ${file%%.*}
done

exit 0

```

---

### Post by junkyhlm on 2011-04-19
Thank you, now the next problem.
 
Can i tell the script that i want to name the folder with all the words before S01E01 etc?
 
i tried with file%%.S0* but then the folders named ex. S12E12 wont be affected. Can i somehow make in name the folder "file%%.S[NUMBER]"?

---

### Post by Crusty Old Fart on 2011-04-19
> **junkyhlm said:**
> Thank you, now the next problem.
 
Can i tell the script that i want to name the folder with all the words before S01E01 etc?
 
i tried with file%%.S0* but then the folders named ex. S12E12 wont be affected. Can i somehow make in name the folder "file%%.S[NUMBER]"?

Like this?
```

#!/bin/bash
set -e

# Change directory
cd /media/store/download/000-torrents/Serier

# Move the torrentfiles
[COLOR=Black]for file in *.torrent; do[/COLOR]
[B][COLOR=Red]  foo=${file%.*}
  mkdir -p ${foo%.*}
  mv $file ${foo%.*}
[/COLOR][/B]done

exit 0
```

---

### Post by Crusty Old Fart on 2011-04-19
After fixing the code in Post #6, it will strip out the .S[NUMBER] and the .torrent extension ***only if*** they always follow the last two dots in the file names.

If that doesn't work for all your file names, it would help to have a better explanation of the format of your file names so we can design the parsing to give the result you want.

---

### Post by nothingspecial on 2011-04-19
You just need a quick lesson in parameter expansion.

Read this

[http://mywiki.wooledge.org/BashGuide/Parameters](http://mywiki.wooledge.org/BashGuide/Parameters)

Click number four - parameter expansion.

---

### Post by junkyhlm on 2011-04-19
> **Crusty Old Fart said:**
> After fixing the code in Post #6, it will strip out the .S[NUMBER] and the .torrent extension ***only if*** they always follow the last two dots in the file names.

If that doesn't work for all your file names, it would help to have a better explanation of the format of your file names so we can design the parsing to give the result you want.

Ok the file name is structured like this:
**Flash.Episode.S01E01.720p.WEB.X264-JUNKYHLM**
and i want the folder name to be either
**Flash.Episode** or **Flash Episode**

I tried the code above and the result was:
*Flash.Episode.S01E01.720p.WEB*

Edit:

And because some folders are named ex. **Flash.S01E01**... etc and some **Flash.Episode.Guide.S01E01**... etc this solution does not work

```
#!/bin/bash
set -e

cd /media/store/download/000-torrents/Serier/tmp

for file in *.torrent; do
  foo=${file%.*.*}
  mkdir -p ${foo%.*.*.*}
  cp $file ${foo%.*.*.*}
done

exit 0
```

---

### Post by DaithiF on 2011-04-19
Hi, at the risk of being impolite, are you looking for help with understanding the techniques that crusty and nothingspecial have pointed  you towards?  Or help with how to apply those techniques in your particular situation?  Or do you just want someone to give you the answer so you can get on with your day.  Seems like the last to me ... ie. I don't see much effort on your part.

In any case, seems like you need to strip off something from the end of a string, but where the first part of that string (that you want to keep) isn't always the same ... 'Flash' or 'Flash.Episode' etc.  Is there a particular piece of the string that is consistent that you can use as a marker to base your rule on?  Seems like the all have .S<number><number> as the start of the pattern you want to remove, so: 
```

f1='Flash.Episode.S01E01'
f2='Flash.S12E01'
echo ${f1%%.S[0-9][0-9]*}
echo ${f2%%.S[0-9][0-9]*}

```

---

### Post by junkyhlm on 2011-04-20
> **DaithiF said:**
> Hi, at the risk of being impolite, are you looking for help with understanding the techniques that crusty and nothingspecial have pointed you towards? Or help with how to apply those techniques in your particular situation? Or do you just want someone to give you the answer so you can get on with your day. Seems like the last to me ... ie. I don't see much effort on your part.
 
In any case, seems like you need to strip off something from the end of a string, but where the first part of that string (that you want to keep) isn't always the same ... 'Flash' or 'Flash.Episode' etc. Is there a particular piece of the string that is consistent that you can use as a marker to base your rule on? Seems like the all have .S<number><number> as the start of the pattern you want to remove, so: 
```

f1='Flash.Episode.S01E01'
f2='Flash.S12E01'
echo ${f1%%.S[0-9][0-9]*}
echo ${f2%%.S[0-9][0-9]*}

```
 
 
First of all i want to thank you for your help, then i want to excuse myself because i didn't at first understand the technics but i think i do now.

---

### Post by Crusty Old Fart on 2011-04-20
> **junkyhlm said:**
> Ok the file name is structured like this:
**Flash.Episode.S01E01.720p.WEB.X264-JUNKYHLM**
Which suggests that not all of the files to be considered for manipulation end in: **.torrent**
But, maybe they do...ya think?...just maybe?

---

