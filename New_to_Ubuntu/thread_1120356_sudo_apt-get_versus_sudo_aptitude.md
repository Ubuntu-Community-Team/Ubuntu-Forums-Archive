---
title: "sudo apt-get versus sudo aptitude"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by aufan19 on 2009-04-08
Hi everyone,

I know that to install programs in Ubuntu, you would type "sudo apt-get install whatever" in the terminal, but I've also seen commands starting with "sudo aptitude" used for various things. What is the difference between these commands? Am I correct in thinking that they can both be used to install things?

Thanks!

---

### Post by _Purple_ on 2009-04-08
You can check [this](http://www.psychocats.net/ubuntu/aptitude).

---

### Post by benj1 on 2009-04-08
does apt-get actually have any advantages over aptitude, why not just create a sym link and get rid of apt-get?

---

### Post by juancarlospaco on 2009-04-09
Chuck Norris uses apt-get

---

### Post by _Purple_ on 2009-04-09
> **benj1 said:**
> does apt-get actually have any advantages over aptitude, why not just create a sym link and get rid of apt-get?

As you can see in the link given above, there is a difference in how aptitude and apt-get handle the the dependencies. The functions were different in earlier versions. In the latest versions of Ubuntu, eventually its possible to get the same result. As for replacing one by the other, that is something beyond my knowledge.

---

### Post by juancarlospaco on 2009-04-09
aptitude is a Ncurses based GUI, execute it without packets :

sudo aptitude

---

### Post by ibuclaw on 2009-04-09
Although I was a die-hard aptitude fan in the old days of Debian, apt-get is the better package manager now when it comes to handling dependencies and resolving conflicts... At least, from an "**upgrade**" point of view.
Aptitude on the other hand has always just sought to do the **least amount** of effort when it comes to resolving conflicts, so you are far less likely to break your system unless you try really hard at it.

Regards
Iain

---

### Post by jose187 on 2009-04-09
> **juancarlospaco said:**
> Chuck Norris uses apt-get

If it's good enough for him, then it's good enough for me. Thanks for letting me know.

---

### Post by ibuclaw on 2009-04-09
> **juancarlospaco said:**
> Chuck Norris uses apt-get
```
sudo apt-get install chuck
```
++

---

### Post by hyper_ch on 2009-04-09
also aptitude installs more packages (mostly the recommended one by apt-get) and I don't like - at least on servers - to have too much stuff installed.

---

### Post by mc4man on 2009-04-09
One of the minor differences is that if you have packages marked for 'auto removal' that while a simple apt-get install <package> will list them, an aptitude install <package> will go ahead and remove them as part of the package install.

Not a big deal unless you install packages with 'build-dep', starting in 8.10 all build-dep installed packages are marked as auto installed (will be added to auto remove in apt-get and removed in aptitude.

(if you plan on building and using 'build-dep' then this prevents the auto marking if you wish to keep (and or prevent a large auto remove list in apt-get
Ex. mplayer
```
sudo apt-get build-dep mplayer -o APT::Get::Build-Dep-Automatic=false
```


Aptitude can do some rarely needed actions and provide some interesting info, not sure if apt-get has the same

[http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/](http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/)
(alot goes way over my head though have found/used some interesting things

---

### Post by lisati on 2009-04-09
> **tinivole said:**
> ```
sudo apt-get install chuck
```
++

from 'man chuck' (for the curious):
>  chuck is a new audio programming language for real-time synthesis, composition, and performance, which runs on commodity operating systems.

---

### Post by benj1 on 2009-04-09
thanks guys, im just surprised that apt-get doesn't have an automatic dependency removal feature, its an obvious advantage, and obviously implementable.

ps was a bit disappointed i was expecting 
```
sudo apt-get chuck
``` 
to be more exciting 

pps 
!idea!
chuck-norris.
a plugin for apt-get to auto remove dependencys!
"chuck-norris will kung fu all your orphaned dependencies"
(feel free to insert a better description)

---

### Post by ibuclaw on 2009-04-09
> **benj1 said:**
> thanks guys, im just surprised that apt-get doesn't have an automatic dependency removal feature, its an obvious advantage, and obviously implementable.

ps was a bit disappointed i was expecting 
```
sudo apt-get chuck
``` 
to be more exciting 

pps 
!idea!
chuck-norris.
a plugin for apt-get to auto remove dependencys!
"chuck-norris will kung fu all your orphaned dependencies"
(feel free to insert a better description)

tbh, I could so write a quick perl script to do that ;)

also, maybe a 'Mr. T' extension to it that lives as an icon in your panel area, bringing up angry, pitiful notifications to "upgrade your system fool!"

---

### Post by benj1 on 2009-04-10
> **tinivole said:**
> tbh, I could so write a quick perl script to do that ;)

also, maybe a 'Mr. T' extension to it that lives as an icon in your panel area, bringing up angry, pitiful notifications to "upgrade your system fool!"

jean-claude-vandamme

anti virus?
problem isn't so much writing the anti virus, just the viruses to make it worth while ;)

mary-whitehouse
firefox anti porn plugin ?

this seems to be going off topic so ive opened up this [thread]("http://ubuntuforums.org/showthread.php?p=7048023#post7048023")

---

