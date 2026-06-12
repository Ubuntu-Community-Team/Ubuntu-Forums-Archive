---
title: "Subtitles not displaying on Totem Movie Player"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by BLiNOK on 2010-10-19
Hi again guys,
I have a problem with Totem Movie Player on Ubuntu 10.10. When I press View - Subtitles - Select Text Subtitles and load the srt file they don't display right from the start in the movie. I also noticed that when I open the subtitles with gedit they appear like this (strange symbols):

5 
00:01:36,175 --> 00:01:39,683 
Íåâúçìîæíîòî ìîæå äà ñå 
îñúùåñòâè àêî ïîâÿðâàìå â íåãî.

How can I change the encoding to cyrillic ( I know its Windows-1251 for windows but for Ubuntu I dont know how.)

EDIT: I tried to load subtitles again and this time  the movie gets very laggy and the sound dissapears .

---

### Post by BLiNOK on 2010-10-19
Sorry for offtopic, but does anyone here know how to change subtitle encoding of Totem so that cyrillic is displayed correctly ? I have created a thread but no reply so far.

---

### Post by migs73 on 2010-10-19
Seems like a resolution here;

[http://ubuntuforums.org/archive/index.php/t-82015.html](http://ubuntuforums.org/archive/index.php/t-82015.html)

Please read all the thread first. It is old so some of the info might be useless, but better than nothing.

---

### Post by BLiNOK on 2010-10-19
> **migs73 said:**
> Seems like a resolution here;

[http://ubuntuforums.org/archive/index.php/t-82015.html](http://ubuntuforums.org/archive/index.php/t-82015.html)

Please read all the thread first. It is old so some of the info might be useless, but better than nothing.

Thanks , I found some usefull info there...here is what I did :

1. Installed recode with Ubuntu software center.
2. Opened terminal and run:
recode windows-1251 <full_path_to_subtitles_file.srt>

Not the best solution but better than nothing. Thank you.Also I would like to add for others like me that might be having the same problem that if you scroll through the movie with Totem player at some intervals the subtitles may disappear. So better watch it from the start and not scroll. Also Recode works only when there are no intervals in the full path to subtitles for example you should write: ecode windows-1251 /media/LocalDiskE/Movies/Alice.In.Wonderland.DVDSCR.XVID-PrisM/Alice.In.Wonderland.DVDSCR.XVID-PrisM.srt AND NOT /media/LocalDiskE/Movies and TV episodes/Alice.In.Wonderland.DVDSCR.XVID-PrisM/Alice.In.Wonderland.DVDSCR.XVID-PrisM.srt

---

### Post by Ms_Angel_D on 2010-10-19
I moved your post here with your original thread please don't hijack threads.

---

### Post by john-raso on 2010-10-22
> **BLiNOK said:**
> Thanks , I found some usefull info there...here is what I did :

1. Installed recode with Ubuntu software center.
2. Opened terminal and run:
recode windows-1251 <full_path_to_subtitles_file.srt>


i try using recode, but .... why i still can't display my subtitle ? :(
i open my .srt file using gedit, and there is no problem with the encode symbol..(there is no strange symbol..)

note :
-i'm using ubuntu 10.10
-the .srt file name same as movie file name.
-where is the config file for totem player?? i still can't find it ..

---

### Post by paparozoumis on 2010-10-22
Why not use another player like VLC?
Any special reason you want Totem necessarily?
VLC will do the trick just fine....

---

### Post by john-raso on 2010-10-22
Thx to paparozoumis... 
i tried VLC n i think everithing is clear now...

---

### Post by paparozoumis on 2010-10-22
> **john-raso said:**
> Thx to paparozoumis... 
i tried VLC n i think everithing is clear now...

One of the best players for both Windowz and Ubuntu 
Good I could help!!!

---

