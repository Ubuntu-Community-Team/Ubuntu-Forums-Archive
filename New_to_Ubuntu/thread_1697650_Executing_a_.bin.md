---
title: "Executing a .bin"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by Phaine on 2011-03-01
First off I want to say I am a complete newbie to Linux. I am working on my network+ exam and decided it was time I started to attempt learning Linux.

I've installed Ubuntu server on my laptop and after a little tinkering managed to get a teamspeak server running on it.

ATM Im currently trying to install a counterstriker server and tinker with it.

I am attempting to follow the guide post on these forums here
[http://ubuntuforums.org/showthread.php?t=76483](http://ubuntuforums.org/showthread.php?t=76483)

My issue is with "executing" the .bin file

Im using putty to connect to my linux server (as I cant seem to figure out how to effectively use screen yet so I can run TS3 and still have server access on the laptop)

I've downloaded [FONT=monospace]hldsupdatetool.bin and created the directory. However when I tried to chmod it didnt work.

I found out the directory was under root root and using this thread [http://ubuntuforums.org/showpost.php?p=10356025&postcount=5](http://ubuntuforums.org/showpost.php?p=10356025&postcount=5) changed ownership to my user (still dont know why the admin account for linux is different from root to begin with)

The directory and everything in it is now under my user name however, whenever I try ./hldsupdatetool.bin I get 
bash: ./hldsupdatetool.bin: No such file or directory

Im a little lost here. If I understand right .bin is similar to a zip file of sorts and is needing to be extracted, but Im assuming I may not have that package installed...

I'd love some help here as Im so beyond green its not even funny and the searching I've tried to do on this keeps leading me to topics that are way more complicated than what Im trying to do.

Appreciate your patience.

[/FONT]

---

### Post by Phaine on 2011-03-01
Solved for those trying to do this here's the fix, it seems to be specific to halflife

[http://ubuntuforums.org/showpost.php?p=2879354&postcount=11](http://ubuntuforums.org/showpost.php?p=2879354&postcount=11)

Sorry to drudge up a new thread but I found this thread looking for  answers and this post gave me an idea that solved this problem for me.  I'd just like it answered for the next person who's looking for answers  (or more likely: me if I set up another server and forget my own  solution.) From what I understand the Ubuntu Server & Desktop AMD64  do not come with the package lib32gcc1, which in most cases is not  needed, but for installing the half life & source dedicated servers  it is. So:

sudo apt-get install lib32gcc1

---

