---
title: "Anyone playing Frogatto? Installation problem"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by Bluenoser81 on 2011-03-09
Hi folks, I recently read about Frogatto, a sort of throwback 2d action platformer game that looks really cool (see clip at [http://www.youtube.com/watch?v=kApZR5nc8ck&feature=feedu](http://www.youtube.com/watch?v=kApZR5nc8ck&feature=feedu)). 

I installed using the .debs for 32-bit (using 10.04LTS) but when I tried to run it through the menu...nothing happens. After trying to run it through the terminal I got the following error:

```
craig@xlappy:/usr/local/games/frogatto$ ./game
./game: error while loading shared libraries: libboost_regex.so.1.42.0: cannot open shared object file: No such file or directory
```So where do I find this file? Google search turned up nothing, but maybe I didn't dig deep enough? And what do I do with it?

Thanks!

---

### Post by Wobblybob on 2011-03-13
Have you tried installing libboost_regex.so.1.42.0?

In a Terminal

sudo apt-get install libboost_regex.so.1.42.0

---

### Post by Bluenoser81 on 2011-03-13
I would try installing the file if I could find it :P

Apt-get returns nothing, any other ideas?

---

### Post by spillin_dylan on 2011-03-13
[http://www.frogatto.com/forum/index.php?topic=20.0](http://www.frogatto.com/forum/index.php?topic=20.0)

Looks awesome, can't wait to try!

---

### Post by Wobblybob on 2011-03-13
opps that should be 

sudo apt-get install libboost-iostreams1.42.0

---

### Post by Bluenoser81 on 2011-03-13
```
craig@xlappy:~$ sudo apt-get install libboost-iostreams1.42.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libboost-iostreams1.42.0

```

---

### Post by Bluenoser81 on 2011-03-13
> **spillin_dylan said:**
> [http://www.frogatto.com/forum/index.php?topic=20.0](http://www.frogatto.com/forum/index.php?topic=20.0)

Looks awesome, can't wait to try!

The 32-bit version is the one I installed (installed without a problem, but when I try to run it...nothing, and I get the libs error when I try to start it from a terminal)

If it works for you, let me know how it is! It does look awesome!

---

### Post by dstil on 2011-03-14
I had exactly the same issue and I posted a question to the Frogatto's problem:
> [http://www.frogatto.com/forum/index.php?topic=208.0](http://www.frogatto.com/forum/index.php?topic=208.0)

Their answer is that I need to
1) either install 1.42 version
2) or to compile the frogatto from source (I am a little noob to do this)

However, finding 1.42 version for Ubuntu 10.04 is not an easy task.
Can someone provide some idiot-proof instructions that I can copy-paste to a terminal? (add a PPA and then install?)
It seems that Maveric version (10.10) has the right version.

Also in Linux Mint Debian it is possible to install 1.42 through Synatpics (not the case with 10.04 ubuntu).

Any help?

---

### Post by Wobblybob on 2011-03-14
you could try donloading the maverick deb from link below and try installing it on your system

[[COLOR="Blue"]https://launchpad.net/ubuntu/maverick/i386/libboost-iostreams1.42.0/1.42.0-3ubuntu1[/COLOR]]("https://launchpad.net/ubuntu/maverick/i386/libboost-iostreams1.42.0/1.42.0-3ubuntu1")

---

### Post by racie on 2011-03-14
I found a solution [here](http://translate.google.com/translate?hl=en&sl=zh-CN&u=http://forum.ubuntu.org.cn/viewtopic.php%3Ff%3D34%26t%3D309011%26start%3D0&ei=9IF-TZfGEpTrrAGImtjCBQ&sa=X&oi=translate&ct=result&resnum=3&ved=0CC0Q7gEwAg&prev=/search%3Fq%3D./game:%2Berror%2Bwhile%2Bloading%2Bshared%2Blibraries:%2Blibboost_regex.so.1.42.0:%2Bcannot%2Bopen%2Bshared%2Bobject%2Bfile:%2BNo%2Bsuch%2Bfile%2Bor%2Bdirectory%26hl%3Den%26prmd%3Divns): 

Basically, you need to first install any hex editor from the repositories.  Then, open /usr/local/games/frogatto/game in the hex editor.  Next, search for a line of text containing:
```
libboost_regex.so.1.42.0.libboost_system.so.1.42.0.
```

And change it to:
```
libboost_regex.so.1.40.0.libboost_system.so.1.40.0.
```

Works like a charm!

---

### Post by Bluenoser81 on 2011-03-14
> **racie said:**
> I found a solution [here]("http://translate.google.com/translate?hl=en&sl=zh-CN&u=http://forum.ubuntu.org.cn/viewtopic.php%3Ff%3D34%26t%3D309011%26start%3D0&ei=9IF-TZfGEpTrrAGImtjCBQ&sa=X&oi=translate&ct=result&resnum=3&ved=0CC0Q7gEwAg&prev=/search%3Fq%3D./game:%2Berror%2Bwhile%2Bloading%2Bshared%2Blibraries:%2Blibboost_regex.so.1.42.0:%2Bcannot%2Bopen%2Bshared%2Bobject%2Bfile:%2BNo%2Bsuch%2Bfile%2Bor%2Bdirectory%26hl%3Den%26prmd%3Divns"): 

Basically, you need to first install any hex editor from the repositories.  Then, open /usr/local/games/frogatto/game in the hex editor.  Next, search for a line of text containing:
```
libboost_regex.so.1.42.0.libboost_system.so.1.42.0.
```And change it to:
```
libboost_regex.so.1.40.0.libboost_system.so.1.40.0.
```Works like a charm!

This worked! I tried this method first because I wasn't sure about installing the 10.10 maverick package, as suggested, just in case it somehow messed up other stuff on my system that needs the version i have know (probably not the case, just want to be careful since i have no idea about what those files do and what programs depend on them). 

Marking as problem solved, thanks a bunch!

---

### Post by racie on 2011-03-14
No problem!  I think someone should inform the Frogatto team about this though.  I'll have to check out the website.

I'm actually getting quite addicted to this game right now.

---

### Post by Linston on 2011-03-15
Hi All,

There is another way to turnaround, maybe less "invasive":

cd /usr/lib
sudo ln -s libboost_system.so.1.40.0 libboost_system.so.1.42.0 
sudo ln -s libboost_regex.so.1.40.0 libboost_regex.so.1.42.0 

This procedure will create a symbolic link from the current version to the files searched by the game. Easy... :)

[FONT=Trebuchet MS]Linux Counter [/FONT]#289571

---

### Post by racie on 2011-03-15
Ahh!  Great solution!  It is much simpler than the way I found on the internet.

---

### Post by ben.na on 2012-07-19
This solution have also worked for a different version, namely libboost_regex.so.2 :

cd /usr/lib
sudo ln -s libboost_system.so.1.46.1 libboost_system.so.2 
sudo ln -s libboost_regex.so.1.46.1 libboost_regex.so.2 

Thank-you!

---

### Post by overdrank on 2012-07-19
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

