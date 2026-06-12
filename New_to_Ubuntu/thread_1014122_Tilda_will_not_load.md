---
title: "Tilda will not load"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-12-17
I use the program Tilda. I love it, when it worked that is. For some reason it hasn't worked for the past week or so. I have tried re-installing it. I tried completely removing it and then installing it again. Nothing works though. What can I do to fix this? Anyone else have this problem?

---

### Post by Shhnap on 2008-12-17
What does it do when it doesn't work. Does it give an error message? something we can work from??

Please give us a little more description of the error and somebody may be able to help. :)

---

### Post by donkyhotay on 2008-12-17
You might try using yakuake instead. It's a KDE program but the features it has are so much better then tilda that (for me at least) it's worth installing all the necessary KDE libs required to run it even though I use gnome and it's the *only* kde program I have installed on my system.

---

### Post by slughappy1 on 2008-12-17
Until Shhnap said that I didn't even think of trying to run it in the terminal. When I pressed the button I assigned it and the ~ button it just didn't do anything. But when in the terminal:
```
jason@Barnaby:~$ tilda
Segmentation fault
jason@Barnaby:~$ 

```

Why does it get a segmentation fault all of a sudden?

I'll have to try yakuake too.

---

### Post by slughappy1 on 2008-12-22
Anything?

---

### Post by evilkastel on 2008-12-22
Segfault.
Well there is not much you can do. you can get the source and try to compile it, but is easier to try yakuake. is quite better actually- i used tilda for a while, then yakuake, then ii discovered zsh and got back to regular terminal just to enjoy zsh.

---

### Post by mlilien on 2008-12-27
I get this problem sometimes as well.  If I delete the tilda configuration directory, and reconfigure it, then it works again.  Until it for some reason, mysteriously starts segfaulting.

I've tried building from source, but when I configure it, I get the error "no lex program found".  I haven't been able to find any help with that by searching the forums or googling it, so I've just been removing the configuration file everytime this happens.

Not a great solution, but I've been too busy to devote some real time to it.

---

### Post by snova on 2008-12-27
> **mlilien said:**
> I've tried building from source, but when I configure it, I get the error **"no lex program found"**.  I haven't been able to find any help with that by searching the forums or googling it, so I've just been removing the configuration file everytime this happens.

Install the 'flex' package.

---

### Post by slughappy1 on 2008-12-28
mlilien, I would say try Yakuake. The only bad side is that it has to install all of the KDE dependencies. I really liked Tilda, but I like Yakuake more. Personally, if I install a program from the repositories I expect it to work. If it doesn't, I will try and see if there is something I can do. If not, I will go with a program that works.

---

### Post by mlilien on 2008-12-28
Thanks, Snova.  I've got Tilda installed from source now, so hopefully, that'll fix the segfaulting issue.

I've tried Yakuake in the past, but I like the simplicity of Tilda more.  No window borders or such.

---

### Post by micczu on 2009-01-03
There is also yeahconsole (in repo). 
I installed it when tilda start segfaulting. Light and simple but without any graphic configurator. 
So I created file '.Xdefaults' in my home directory and pasted there example configuration from [http://tom.azatom.info/blog/index.php/post/2007/12/30/x11-terms/yeahconsole-Quake-like-xterm](http://tom.azatom.info/blog/index.php/post/2007/12/30/x11-terms/yeahconsole-Quake-like-xterm).
(after changing .Xdefaults I needed to run 'xrdb -load ~/.Xdefaults' in console to made the changes work)

Edit:
I've just found something more friendly; 'guake' (also in repo).

---

### Post by mlilien on 2009-01-03
Maybe I'll check those out later, but I haven't had any issues with tilda since installing from source.

---

### Post by userid on 2009-08-20
start tilda as tilda -C to delete the config. worked for me

---

### Post by geoffm on 2009-10-04
before installing KDE libs for yakuake, try Guake terminal.

---

### Post by Shhnap on 2010-02-16
Um, did somebody make a bug report in launchpad for that segfault? It might be important.

---

### Post by slughappy1 on 2010-02-17
I don't think I did. Just switched to guake. Although I do have problems with it not staying on the top of the screen. It some times starts at the bottom of the screen.

---

