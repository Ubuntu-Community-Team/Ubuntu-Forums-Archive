---
title: "How to uninstall Spotify?"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by missfroguk on 2009-11-18
Hi all,

I installed Spotify yesterday (on Ubuntu 9.10), couldn't hear anything alledgedly because there was a problem with my sound card, eventually managed to listen to one whole album...then the "problem with my sound card" popped up again.

I found other people on the Ubuntu forums who had the same problems and tried to follow their suggestions to remedy the problem.

First I followed the advice in this thread 
[http://ubuntuforums.org/showthread.php?t=1306011](http://ubuntuforums.org/showthread.php?t=1306011)

and did 

sudo aptitude remove wine
sudo aptitude install wine1.2

After that though, when I clicked on the spotify icon from Applications > Wine > Programs > Spotify, nothing happened

So then I followed the advice in this thread 
[http://ubuntuforums.org/showthread.php?p=8293379](http://ubuntuforums.org/showthread.php?p=8293379)
and tried to purge wine and wine1.2 (assuming there was still any life left in Wine!) by doing

sudo aptitude purge wine
sudo aptitude purge wine1.2

to get rid of Spotify within it...but it still hasn't worked.

When I do
find -name 'spotify*' -print
I still have a Spotify folder in ./.wine/drive_c/Program Files/Spotify/, in which the Spotify.exe and uninstall.exe are.

So my question is, how can I uninstall Spotify altogether (or do I just need to delete that folder?!) so that I can then reinstall Wine AND Spotify.

Also, why hasn't Wine purged itself completely?!

Thanks for your help!

In this folder, I have 2 files

---

### Post by kostkon on 2009-11-18
Just, go to your home, select *View &#8594; Show Hidden Files*, then find and delete the *.wine* folder. Or faster, in a terminal do:
```
rm -rf ~/.wine
```

---

### Post by ukripper on 2009-11-18
i guess you can use this command:
```
rm -f -R ~/.wine/drive_c/Program Files/Spotify
```

try if it works

---

### Post by ukripper on 2009-11-18
> **kostkon said:**
> Just, go to your home, select *View &#8594; Show Hidden Files*, then find and delete the *.wine* folder. Or faster, in a terminal do:
```
rm -rf ~/.wine
```

lol you beat me to it.

---

### Post by kostkon on 2009-11-18
> **ukripper said:**
> lol you beat me to it.
Yeah, he/she wants to purge wine, so it's better to delete the *.wine* folder completely.

---

### Post by ukripper on 2009-11-18
> **kostkon said:**
> Yeah, he/she wants to purge wine, so it's better to delete the *.wine* folder completely.

Yeh I guess.

---

### Post by missfroguk on 2009-11-18
Thanks to you all, it worked a treat!

---

