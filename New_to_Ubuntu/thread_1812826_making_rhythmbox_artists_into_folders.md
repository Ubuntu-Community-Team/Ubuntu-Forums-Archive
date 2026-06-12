---
title: "making rhythmbox artists into folders"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by djyoung4 on 2011-07-26
So I am trying to organize all of my music into folders with the artist and then the album and then the song in the respective album.  The problem is that I am manually going through and creating folders for all the artists and it is taking quite a bit of time.  I was wondering if there was a way to automate the process and save some time for myself.  Any help is greatly appreciated.

---

### Post by CatKiller on 2011-07-26
EasyTag's Scanner function can do this based on the tags of the files.

---

### Post by djyoung4 on 2011-07-26
> **CatKiller said:**
> EasyTag's Scanner function can do this based on the tags of the files.
Well if I am just changing the artists info in rhythmbox does that tag the file?

---

### Post by CatKiller on 2011-07-26
> **djyoung4 said:**
> Well if I am just changing the artists info in rhythmbox does that tag the file?
I don't know (I don't use Rhythmbox). In a sane world it would, and I know Amarok updates the tags when you change the info. 

EasyTag will show you the tags as well as let you edit them and do things based on them, so you don't need to run the scanner before you know it will work.

---

### Post by djyoung4 on 2011-07-28
Ok so i figured out how to change the filename to the title using puddletag but I would like to be able to automate the process of creating folders of all the artists names.  I have over 1000 artists and it would be extremely time consuming.  Any help is greatly appreciated

---

### Post by CatKiller on 2011-07-29
:confused:

EasyTag is automated. You set the scanner going and it does it.

---

### Post by djyoung4 on 2011-07-29
I tried that and got no success.  Is there a good tutorial somewhere that you know of

---

### Post by CatKiller on 2011-07-29
No, but the documentation is [here]("http://easytag.sourceforge.net/EasyTAG_Documentation.html#ch_1_3_2"). There are new options since the last time I did it, to fill in tags based on CDDB entries, and I haven't seen how reliable or otherwise that is.

Basically, you select the files you want to rename, select Scanner -> Rename File(s) and Directory... from the menu, choose the pattern that you want to use to rename the files to and hit the green "scan selected files" button.

Based on your description, you might want something like ```
%a/%b/%a - %n
``` You can see which variable does what by hitting the Show Legend button, and there's more information in the documentation. It'll show you a rendition of what the pattern looks like applied to the first file you've selected before you start.

It's not brilliantly discoverable, but it is the best tool for the job I've found so far.

---

### Post by djyoung4 on 2011-07-29
ok thanks catkiller.  I think I have it figured out

---

### Post by CatKiller on 2011-07-29
No worries. Don't forget to mark the thread as Solved to help the people that come after us.

---

