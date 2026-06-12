---
title: "problems with terminal"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by speedygonzalas on 2009-02-21
iv been trying to get windows to launch on my ubuntu desktop and downloaded everything, now when i tried to install vmware player it worked the first time but it failed when it tried to make a new kernel because i forgot to install kernel hearder. now that i have whenever i go onto the terminal and enter:
 cd vmware-player-distrib
it replies with 'bash: cd: vmware-player-distrib: No such file or directory'
now this doesn't make sense to me because the commands are based on my desktop (atleast it seems to say it is) and the uncompressed pkg is on my desktop, any help?

---

### Post by yeats on 2009-02-21
Where are you in the directory tree when you run the command?  Try this:

```
cd
cd Desktop
ls
```

You should see your file in the list.  If you weren't in your Desktop directory, that was the problem.  The default directory in the terminal is your /home/[*your username*] directory.  Make sense?

---

### Post by speedygonzalas on 2009-02-21
yeah it does, i just got confused cuz my command line is preceded by 
Jeff@stuff-desktop:~$  
so i assumed it was already at my desktop, but when i put that command it showed

new file~
virtualbox-2.1_2.1.4-42893_Ubuntu_intrepid_i386.deb
VMware-player-2.0.5-109488.i386.tar.gz
VMware-Player-2.5.1-126130.i386.bundle
vmware-player-distrib
Jeff@stuff-desktop:~/Desktop$

i guess that solved it, i didn't know that u had to do all that stuff at once, thanks alot!

---

### Post by speedygonzalas on 2009-02-21
one quick question though, when i put cd desktop alone y didn't it go to desktop?

---

### Post by yeats on 2009-02-21
> one quick question though, when i put cd desktop alone y didn't it go to desktop?

It depends on where you are in the directory tree :-).

```
cd
```

by itself puts you back into your home directory, which is where your Desktop directory lives.  Alternately you can do 

```
cd ~/Desktop
```

The ~/ means your home directory.

Oh - and the reason "cd desktop" won't work is that capitalization matters in Linux.  It has to be cd _D_esktop.

---

### Post by speedygonzalas on 2009-02-21
wow, well thats definately good to know, thanks alot once again

---

