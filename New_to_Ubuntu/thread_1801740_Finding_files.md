---
title: "Finding files"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by cheeseits on 2011-07-11
It seems that firefox caches files something like here: 

/home/<username>/.mozilla/firefox/<some-garbage-chars>.default/Cache
.

How would I search these directories for videos, like from youtube that are cached somewhere in there?  I.e., like to find all mp4 files or all <insert-file-format> files.

I'm not aware of any features of the 'find' command that allow me to interrogate the properties of files.  Anyone know how to do this?  Oh, and the file names do not have convenient extensions they're all named some 8 digit hex code like 9F94Fd01 or BB999d01. 
i.e. the files are not called thisisafile.jpg or hiimapngfile.png et cetera.

Thanks

---

### Post by wildmanne39 on 2011-07-11
> **cheeseits said:**
> It seems that firefox caches files something like here: 

/home/<username>/.mozilla/firefox/<some-garbage-chars>.default/Cache
.

How would I search these directories for videos, like from youtube that are cached somewhere in there?  I.e., like to find all mp4 files or all <insert-file-format> files.

I'm not aware of any features of the 'find' command that allow me to interrogate the properties of files.  Anyone know how to do this?  Oh, and the file names do not have convenient extensions they're all named some 8 digit hex code like 9F94Fd01 or BB999d01. 
i.e. the files are not called thisisafile.jpg or hiimapngfile.png et cetera.

ThanksHi, as far as youtube videos my understanding is that it is not allowed so the feature has been removed from the flash player that allowed that in previous ubuntu versions. Also I believe it is against forum policy to talk about those particular files.

---

### Post by cheeseits on 2011-07-11
What do you mean 'not allowed'?  Not allowed by whom?  How does that work anyway, it plays on my computer so how do they disable it?  By 'those particular files' you mean the Cache folder?  And if so again, what is the reason?  

Thanks

---

### Post by jtarin on 2011-07-11
Open Nautilus file manager and it will be opened in /home/<username> directory. Now the combination of keys Ctrl + h will allow you to view hidden files. These are the files with a "." in front of them. You can also go to Nautilus menu and select "View" and then "hidden files".Once these are viewable locate the .mozilla directory then inside will be the firefox directory then your profile folder (garbage-char). then the default directory and Cache directory inside that. There is no easy way to find these unless you use something like [Flash Got]("https://addons.mozilla.org/en-US/firefox/addon/flashgot/") and it's becoming more difficult to download these files as some of the host sites disallow.

---

### Post by cheeseits on 2011-07-11
Fine, but I don't want to find these files in the file manager since their are ~1000 files here.  
example:

[PHP]
ls -R 1>files.txt
wc -l 0<files.txt
[/PHP]

gives about 3000
and there's about 3 lines per file.

Ok, so how would I play any flash files (in the cache folder previously referred to), they seem to give an error when I try to play them (as implied in previous posts here). 


HERE'S WHAT I WAS INITIALLY TRYING TO ASK:
---When I right click on a file and click on properties (ie alt-enter) a flash file will say:
     Type:      Shackwave Flash file (application/x-shockwave-flash)
Is that information available from the shell or not, and how would someone go to find an answer if their is one?

Thanks

---

### Post by cheeseits on 2011-07-11
Ok, actually there is 715,

```

find . -type f 1>files.txt
wc -l 0<files.txt

```but the point still remains, I want to interrogate the files from shell.  Anyone know how?

---

### Post by jtarin on 2011-07-11
Those type of files used to be cached in the /tmp directory, but only while the web page was still open.....once closed they would disappear.Anything outside my /home directory I could play as root with Totem movie player. Once I moved the file and renamed it I could play it with VLC also. If you can find a way to search for these I would like to know also.BTW...these files stopped being cached in my /tmp directory and could only be downloaded with FlashGot to any folder I designated. Not all of these movies, music can be linked to download. It is something inherent in the web page that prevents it.

---

### Post by nothingspecial on 2011-07-11
```
f="$(ls -l  /proc/$(pgrep -f flashplayer)/fd | grep deleted)" && f="${f##*:+([0-9]) }" && f="${f%% -*}" && echo /proc/$(pgrep -f flashplayer)/fd/"$f"
```

That will tell you which file it is, but it is against youtubes terms and conditions to copy it to your hard drive. [-X

---

