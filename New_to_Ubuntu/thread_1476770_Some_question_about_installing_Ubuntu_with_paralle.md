---
title: "Some question about installing Ubuntu with parallels desktop"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by Dsoslglece on 2010-05-08
Hi,
I'm on iMac Intel Snow Leopard, and have just intalled on it, using parallels desktop (to be able to keep all systems running together, and including win XP) the last version of Ubuntu (10.04).

I must say first that I very much like the look and finish of it, and also the fact that it looks light and swift, and sofar, rather straight forward and simple.

There are however one or two things that I didn't find how to do yet and if someone could just tell me how, it certainly would save me quite a lot of time of searching.

First, I tried to change the language to French, I certainly wouldn't mind fot it to stay in English, but some friends of mines may find it a bit hard, if by chance using my computer, and anyway, and for my own sake, I really would like to change the keyboard from qwerty to azerty, since even if I know about the differences, it takes quite a bit of speed off in typing, so as keeping my attention on the changes.

The second problem is installing parallels tools (to allow me quickly to use the mouse from one system to another, and share applications). 
It says in the parallels help that one has to use terminal as root, well, there is anyway not much differences between Mac and Linux terminals, being both unixes, and I used it some time on Mac to compile apps and so on.

So, to use it as root one has to enter <su> and then enter PW, but when it asks me to enter PW, no character of it seems to register or get copied on the place where it should.
So, I thought that maybe since I'm the only user (and obviously also the admin) and since I was already logged, that part was just void.
so, I continued with installing the tools. One has first to do it from the CD disc image, so, and since the image appeared on desktop, I entered simply <cd /cdrom> that transported me there, but then, when trying to run the install according to the prl Help, by doing <./install>, it returns :
bash: ./install: No such file or directory
So I try few other wordings of the command, and since I think that it should be a file in there called: install.sh, I also tried with <./install.sh run>, but it didn't work either, and returned the same answer.
So, if someone could give me a clue about those hangups, I'd be very gratefull.

Thanks in advance

---

### Post by 3rdalbum on 2010-05-08
I thought Mac OS X used 'sudo', not 'su'?

In any case, Ubuntu uses sudo.

What you'll have to do is open the terminal, navigate the terminal to the directory that contains the file you want to run, and then type:

```
sudo ./install.sh
```

Don't know how to navigate a terminal? Then just type 'sudo', press the space bar, and then drag the install.sh file into the terminal:

```
sudo <drag file in here>
```

---

### Post by Dsoslglece on 2010-05-08
Thanks 3rdalbum,

I just tried now with this, and it went fine first with sudo, I had to give my PW and continued with the new command: <sudo ./install.sh> but got then the answer: 
<sudo: ./install.sh: command not found>

So, since that in prl desktop help they mention only this command <./install> I also tried it, but with sudo:
<sudo: ./install>, but it gave the same answer.

---

### Post by Dsoslglece on 2010-05-08
Hi,
I just tried a bit further, and even if it didn't succeed, it may give sumore clues.
In Ubuntu, I went for the disc image "Parallels Tools", and opened it to see exactly what it had in the stomac. and I located the file "install-tools.sh", so, I tried to open with terminal (from the cd) but it came back saying the permission was denied.
So, I did it again, but with a sudo command… same thing.

So, and since there is also in there, an installer (an exec file), I tried the same with it, from the CD, and with the command sudo after what, and after a space, I slided the installer on terminal (to be sure of its proper access). It asked for PW of course, and then started to work normally, but, after a while, it came back saying that it was impossible since permission was denied...

Apparently, this permission is for the script that runs probably also in terminal anyways.
Is there somewhere an acces to change the permissions (on Mac, it is : click right/read infos/Share & permissions, and then after a PW, one chooses what is needed)… I did find something similar here, but with the exception that this Install-Tools.sh is under read only, and, when I tried to allow read and write, the permission was denied... but since it has the permission to be executed as an app... this seems however to be enough !

---

### Post by 3rdalbum on 2010-05-08
You might need help from someone who's more familiar with Parallels and its guest additions disc.

---

### Post by Dsoslglece on 2010-05-10
Well, it seems though that it doesn't come from parallels, but from the OS, or rather, of my yet ignorant way to handle it... what's more, I had also the same problem trying to install Tor-Vidalia… since one has to do some changes in files, prior to downloading it (etc/apt/sources.list), I mean adding a DL address... and it gets stack just the same as when wanting to load the parallels tools from a disc imag.

But even, I read quite a lot about all sorts of things in this manual (BTW very excellently conceived), and I saw what to do to open a terminal session as root (<sudo su>), and tried to do the whole things again with this (as root) but same results. 

And as for the install of Tor, when getting to apt and wanting to add an url to the sources.list, when double-clicking it, and after having given my PW, I got a new window called "apps sources", and a choice of menus :
Ubuntu apps, others, etc so I choosed others, and was presented a new place to add an url, but when that was done, the place to validate it was grey (and dead).
So, I investigated, and looked for permissions, and it says that it was a root file, and not mine (!).

So, I even tried to log as root, but the windows I obtained doing it don't seem to correspond to the ones according to the manual, so it didn't work either…

I really got the feeling that it is only in all cases a question of permission denied (in fact, it says so): 
As a last experiment, I managed to open a session as root only in terminal, but I didn't find yet the way to add this url from terminal, even when I open the file into terminal, nothing can be added to it, and when using <nano> I got a blank page.

---

