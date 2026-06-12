---
title: "MegaMario install issues in 10.04"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by heartlesshero on 2010-11-11
I am trying to install MegaMario 1.6 in Lucid. I am using this post as a reference: [http://ubuntuforums.org/showthread.php?t=645800](http://ubuntuforums.org/showthread.php?t=645800). I have installed the necessary repositories and I have done everything correctly up to cd ~/Desktop/MegaMario_v1.5_w32_linux/ (except i my folder's name is MegaMario_v1.6c_full). When I run:
make PREFIX=/usr/local
or
sudo make PREFIX=/usr/local install 

I get the error: 

g++ -g -Wall -O2 -DDATADIR=\"/usr/local/share/megamario/\" -o src/bonus.o -c src/bonus.cpp
make: g++: Command not found
make: *** [src/bonus.o] Error 127

Can anyone help me identify what's wrong? If you need anymore information I will happily supply it. The Program can be located at: [http://sourceforge.net/projects/mmario/](http://sourceforge.net/projects/mmario/)
I'm sorry if this post is not in the best format. I just joined today.

---

### Post by bioterror on 2010-11-11
You've got gcc installed?
```
sudo apt-get install gcc
```

---

### Post by heartlesshero on 2010-11-11
Yes I do and it's the latest edition.

---

### Post by bioterror on 2010-11-11
> **heartlesshero said:**
> Yes I do and it's the latest edition.

```
sudo apt-get install g++
```
that should do it ;)

> 
$ sudo apt-get install g++
[sudo] password for sad157: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  g++-4.4 libstdc++6-4.4-dev
Suggested packages:
  g++-multilib g++-4.4-multilib gcc-4.4-doc libstdc++6-4.4-dbg
  libstdc++6-4.4-doc
The following NEW packages will be installed:
  g++ g++-4.4 libstdc++6-4.4-dev
0 upgraded, 3 newly installed, 0 to remove and 4 not upgraded.
Need to get 7,280kB of archives.
After this operation, 23.6MB of additional disk space will be used.



---

### Post by heartlesshero on 2010-11-11
No Dice. I already Had that installed as well.

---

### Post by bioterror on 2010-11-11
> **heartlesshero said:**
> No Dice. I already Had that installed as well.

well, what is you g++ command like? type g++<press tab><press tab>.

If you're missing just plain "g++" when we have to do it something like this:

```

sudo ln -s /usr/bin/g++-4.4 /usr/bin/g++

```

but I assume you already have a g++, so that should be un-needed command

---

### Post by heartlesshero on 2010-11-11
I did that and returned:

hyde@Miuna:~$ sudo apt-get install g++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
g++ is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
hyde@Miuna:~$ g++
g++      g++-4.4  
hyde@Miuna:~$ g++
g++      g++-4.4  
hyde@Miuna:~$ g++^C
hyde@Miuna:~$ sudo ln -s /usr/bin/g++-4.4 /usr/bin/g++
ln: creating symbolic link `/usr/bin/g++': File exists


is this correct?

---

### Post by bioterror on 2010-11-11
> **heartlesshero said:**
> I did that and returned:

hyde@Miuna:~$ sudo apt-get install g++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
g++ is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
hyde@Miuna:~$ g++
g++      g++-4.4  
hyde@Miuna:~$ g++
g++      g++-4.4  
hyde@Miuna:~$ g++^C
hyde@Miuna:~$ sudo ln -s /usr/bin/g++-4.4 /usr/bin/g++
ln: creating symbolic link `/usr/bin/g++': File exists


is this correct?

that's correct-a-mundo!.

Something wrong with the MegaMario then.

---

### Post by heartlesshero on 2010-11-11
I ran the make PREFIX=/usr/local command again and I have this returned now.


hyde@Miuna:~/Desktop/MegaMario_v1.6c_full$ make PREFIX=/usr/local
g++ -g -Wall -O2 -DDATADIR=\"/usr/local/share/megamario/\" -o src/global.o -c src/global.cpp
src/global.cpp: In function ‘void THEGAMEENDSHERE()’:
src/global.cpp:164: error: ‘PATH_MAX’ was not declared in this scope
src/global.cpp:165: error: ‘buf’ was not declared in this scope
src/global.cpp:193: warning: deprecated conversion from string constant to ‘char*’
src/SDL_gfxPrimitives_font.h: At global scope:
src/SDL_gfxPrimitives_font.h:8: warning: ‘gfxPrimitivesFontdata’ defined but not used
src/functions.h:42: warning: ‘GfxFont’ defined but not used
src/functions.h:43: warning: ‘GfxFontColor’ defined but not used
src/functions.h:45: warning: ‘gfxFontdata’ defined but not used
make: *** [src/global.o] Error 1
hyde@Miuna:~/Desktop/MegaMario_v1.6c_full$

---

### Post by heartlesshero on 2010-11-11
There is something wrong with how linux is compiling the files. I did find a work-around for anyone who wants the game.
```
sudo aptitude update
sudo aptitude install megamario 
```
then I found the .deb file in /var/cache/apt/archives for using in other linux distro's I think. I hope that Helps anyone else.

---

