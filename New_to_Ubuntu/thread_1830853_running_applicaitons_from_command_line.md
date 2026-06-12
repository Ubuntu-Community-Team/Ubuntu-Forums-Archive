---
title: "running applicaitons from command line"
date: 2011-08-22
forum: New to Ubuntu
---

### Post by manish411 on 2011-08-22
I have a folder of .mp3 files . Now I want to open these 
files through media player from the command line itself 
without going to the folder through gui and then clicking 
on the song. How to do this??

---

### Post by TeoBigusGeekus on 2011-08-22
Supposing you use vlc
```
vlc /path-to-folder/*.mp3
```

---

### Post by Johnb0y on 2011-08-22
> **TeoBigusGeekus said:**
> Supposing you use vlc
```
vlc /path-to-folder/*.mp3
```

+1 - should work. if all are actual MP3...

p.s. dont forget: 

sudo apt-get install mplayer-nogui ubuntu-restricted-extras

---

### Post by Overcast32 on 2011-08-22
There is a MP3 player out there for the command line too - if that's what you are looking for. 

Dang, I forget the name though. 

Check this thread too: [http://ubuntuforums.org/showthread.php?t=1573685](http://ubuntuforums.org/showthread.php?t=1573685)

---

### Post by raja.genupula on 2011-08-22
> **Johnb0y said:**
> +1 - should work. if all are actual MP3...

p.s. dont forget: 

sudo apt-get install mplayer-nogui ubuntu-restricted-extras

hey 
thanks you for this , but 
my system saying its not available , what i've to do now ? 

sudo apt-get install mplayer-nogui ubuntu-restricted-extras

```
[sudo] password for assassin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mplayer-nogui is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  mplayer

E: Package 'mplayer-nogui' has no installation candidate
```

---

### Post by raja.genupula on 2011-08-22
aah good news is **mplayer** is doing the job as you mentioned ,.
i think **sudo apt-get install mplayer-nogui ubuntu-restricted-extras** no need . now i am playing through terminal it self . 

how can i control volume through terminal ?

---

### Post by Neoncamouflage on 2011-08-22
```
alsamixer
```
Should do it for you.

---

### Post by nmaster on 2011-08-22
gnome-open is also very useful.  it'll use the default application settings.  also, if you close the terminal, the application will stay open. it'll also work on things other than a mp3s.
```
gnome-open file
```

---

### Post by nmaster on 2011-08-22
> **raja.genupula said:**
> hey 
```

sudo apt-get install mplayer-nogui ubuntu-restricted-extras
[sudo] password for assassin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mplayer-nogui is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
[B]However the following packages replace it:
  mplayer
[/B]
E: Package 'mplayer-nogui' has no installation candidate
```

> **raja.genupula said:**
> aah good news is **mplayer** is doing the job as you mentioned ,.


you should really learn to read error messages that you get.  in this case, it tells you exactly what to do and there was no reason to post anything

---

### Post by nmaster on 2011-08-22
> **Neoncamouflage said:**
> ```
alsamixer
```
Should do it for you.

here's a little wrapper script i use sometimes to change the master volume and post a notification. its not much, but it'll give you the basics for using amixer to set the master volume.
```

./volume.sh up   # increase volume by 3%
./volume.sh down # decrease volume by 3%
./volume.sh mute # mute/unmute volume

```

---

### Post by jfed on 2011-08-22
There is a CLI music player called "cmus" you could look into installing.

Alternatively you can use mplayer to play things threw the command line, no gui involved. Just run a command like this.

Say I had an mp3 file on my desktop, this is how I would play it with mplayer.

```
cd /home/jfed/Desktop && mplayer song.mp3
```

---

