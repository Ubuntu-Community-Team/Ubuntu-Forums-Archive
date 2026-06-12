---
title: "how can i edit files owned by root in ubuntu server ?"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by docesam on 2011-05-13
i have ubuntu server (11.04) and need to edit files owned by root.

1-tried logging as root but account disabled . 

2- tried sudo but then i have to use command like editor (vi) which i could not figure out how to use it despite reading guides explaining how to do it !

3-logging in using winSCP has the same problem (i have to log in as a root to use it).

4- GUI is not installed in the server version.

5- tried booting from the live CD and using the GUI editor to edit it but no luck : "i am not the owner of the file"

so basically i am locked out !! the ubuntu server is teasing me : the file is right there few centimeter away from me but i can't touch it !!

so how to do it ?

thank you for your kind advice

---

### Post by TeoBigusGeekus on 2011-05-13
> **docesam said:**
> i have ubuntu server (11.04) and need to edit files owned by root.

1-tried logging as root but account disabled . 

2- tried sudo but then i have to use command like editor (vi) which i could not figure out how to use it despite reading guides explaining how to do it !

3-logging in using winSCP has the same problem (i have to log in as a root to use it).

4- GUI is not installed in the server version.

5- tried booting from the live CD and using the GUI editor to edit it but no luck : "i am not the owner of the file"

so basically i am locked out !! the ubuntu server is teasing me : the file is right there few centimeter away from me but i can't touch it !!

so how to do it ?

thank you for your kind advice

You could use
```
gksu gedit
```
from the live cd, or, better still, learn how to use vi/vim.
[Here's]("https://wiki.archlinux.org/index.php/Vim") a link from Arch wiki and you'll find a cheat sheet attached (if you don't have one already).

---

### Post by egalvan on 2011-05-13
> **docesam said:**
> i have ubuntu server (11.04) and need to edit files owned by root.

5- tried booting from the live CD and using the GUI editor to edit it but no luck : "i am not the owner of the file"


I use 
```
gksudo gedit
```

in this situation.

But if you truly want to "own" the server, then you should practice on a cli-type editor... along with all the other cli commands...

Although you can also use a full-GUI machine to access the server..

There are LOTS of text editors for Linux, search for them...
(apt-get is your friend here)
some even work "kinda-sorta" like GUI ones.


And of course, these questions...

WHICH files do you need to change?
WHY do you need to change those files?

Tread lightly in Root's Landscape

---

### Post by audiomick on 2011-05-13
Another vote for

short term:
```
gksudo gedit
```
from the live CD to get around your current problem

and long term learning how to deal with the cli tools you need to manage the server. Or install a GUI on it...

---

### Post by oldos2er on 2011-05-13
The nano editor is probably easier for a newbie to use than vi/vim, as long as you know that ^ refers to the Ctrl key. So try ```
sudo nano /etc/foo
```

---

### Post by wildmanne39 on 2011-05-13
> **TeoBigusGeekus said:**
> You could use
```
gksu gedit
```
from the live cd, or, better still, learn how to use vi/vim.
[Here's]("https://wiki.archlinux.org/index.php/Vim") a link from Arch wiki and you'll find a cheat sheet attached (if you don't have one already).
Is gedit as good as vi?
Thanks for your help.

---

### Post by yetiman64 on 2011-05-13
> **wildmanne39 said:**
> Is gedit as good as vi?
Thanks for your help.
Some situations even on a GUI require the use of vi/vim (because of formatting issues iirc), editing the sudoers file is one example.

Gedit from a live cd is an easy/convenient method for the OP considering they are using a server (possibly with no gui). Though as oldos2er notes nano can be installed/used on a server. 

vim/vi takes quite some getting used to for a beginner, the cheat sheet provided by TeoBigusGeekus is a very handy start to learning it (still trying to come to terms with it here when needed, which is thankfully rare as I'm on a GUI environment, though I have used it to edit the sudoers file).

---

### Post by wildmanne39 on 2011-05-13
> **yetiman64 said:**
> Some situations even on a GUI require the use of vi/vim (because of formatting issues iirc), editing the sudoers file is one example.

Gedit from a live cd is an easy/convenient method for the OP considering they are using a server (possibly with no gui). Though as oldos2er notes nano can be installed/used on a server. 

vim/vi takes quite some getting used to for a beginner, the cheat sheet provided by TeoBigusGeekus is a very handy start to learning it (still trying to come to terms with it here when needed, which is thankfully rare as I'm on a GUI environment, though I have used it to edit the sudoers file).

Hi, thank you for your help, I was just curious because I use nano when i installed gentoo in virtualbox, but I have not used vi at all. I appreciate the information.:)

---

### Post by 3rdalbum on 2011-05-14
I've never bothered learning Vi/Vim. Nano is preinstalled and that's very easy to use for a command-line editor.

sudo nano *filepath*

---

### Post by docesam on 2011-05-14
thank you all.

i now have an insight of why i couldn't use the VI editor : i was trying to edit a read only file !! lolz

anyway , the nano editor is really sexy ,i like it.

thank you again folks.

---

### Post by 5149.5 on 2011-05-14
Nano is VW beetle, vim is Mercedes. I can't imagine being limited to nano. use the cheat sheet for a while and vim will be easy very quickly.

---

### Post by TeoBigusGeekus on 2011-05-14
> **5149.5 said:**
> Nano is VW beetle, vim is Mercedes. I can't imagine being limited to nano. use the cheat sheet for a while and vim will be easy very quickly.

+1
I used to make fun of vim users, I've paid some money for my mouse and I want to use it after all, but when I forced myself to use it I realised how stupid I was; now it's my default text editor.

---

