---
title: "&quot;Listen&quot; audio player doesn't start"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by user1986 on 2009-06-03
Hi. I downloaded the latest version of this audio player (a tar.gz file downloaded from the official site of the project), and I installed it. Well, I think I did. Inside the tar.gz file there was a file called "installation". it said that for installing it, it was necessary to do: 

make clean 
make 
make install  

i did "make clean" 
everything ok 

i did "make" 
a couple of times the terminal said that i was missing some necessary things (pyGTK and intltool) i installed them from sinaptyc  

when i reached the make install it said it could not create the directory to make the installation  

i repeated the process with 
sudo make clean 
sudo make 
sudo make install  
apparently everything was ok, the icon for "listen" audio player was in the menu of audio & video in the applications menu, but when i clicked it a new window appeared in the lower bar, the one saying "starting (name of the application)" that appears for any program, but it didn't start. the little box just closed and nothing happened

 i just have a week using ubuntu (using wubi) so i don't understand most of the stuff about the terminal and all that...  

then, i went to applications menu/add-remove and i searched listen audio player, an older version appeared in the list, it wasn't checked. i checked it, so it downloaded it.  it appeared in the applications menu/audio-video (with its own icon, corresponding to the older version) but it didn't start either.  some idea of what can i do to make the latest version work?? or in the worst case, make the older version work?

I edit again:

I solved the problem. Reading the terminal again I found there were other things i was missing. got them through synaptic. Everything ok.

Thanks anyway to the ones that would have answered.

---

### Post by durand on 2009-06-04
In the future, run ```
sudo apt-get build-dep listen
``` This will get all the dependencies for building listen.

---

### Post by Hund on 2009-06-04
You could use the Listen PPA:

[https://launchpad.net/~listen-devel/+archive/ppa](https://launchpad.net/~listen-devel/+archive/ppa)


It's much more easyier. :)

---

### Post by user1986 on 2009-06-08
Thank you durand and Hund. I appreciate your help.

Durand:
Does that command works for any program to be installed?? a couple of days ago I installed a program and it had a pretty long list of dependencies to download first. It would be pretty useful if it works for any program. And does it install the dependencies only or does it install the program as well??

Hund:
I didn't know this thing of the PPA's, but I'll read about them for sure. Thank you.

Thanks to both of you.

---

### Post by cariboo on 2009-06-08
I have to ask, why are you installing programs from source? Almost everything you need is in the repositories, check Applications-->Add/Remove or System-->Administration-->Synaptic Package Manager.

---

### Post by durand on 2009-06-08
user1986 wants the latest version of listen.

build-dep works for any program in the repos that have a source package, which cs most of them.

---

### Post by user1986 on 2009-06-10
Hi again.
cariboo907:
I'm installing from source because, as durand said, I wanted the latest version (which I may add, works pretty fine and has more functions and features than the version in the repositories. And as a matter of fact, that's exactly why I looked for the latest version). However, I recognize that the repositories are very useful and simple for most cases. Thank you.

durand:
Thanks again. Your advice was very helpful. I installed another program and I used build-dep just to see it and it worked perfectly. Thank you.

---

### Post by user1986 on 2009-06-10
I might add also, that I have found very interesting (although very patience-killing too) to use the terminal.

---

### Post by durand on 2009-06-10
No problem! Now to work out how to remove all those deps when I don't need them...

---

