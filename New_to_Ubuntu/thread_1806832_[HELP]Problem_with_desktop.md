---
title: "[HELP]Problem with desktop"
date: 2011-07-18
forum: New to Ubuntu
---

### Post by Bakica on 2011-07-18
I've installed Ubuntu a week ago, and it ran good. Today, I installed compiz advanced desktop effects, and it lagged alot. Since then when I try to use Ubuntu I can't do anything, the only thing I see is my desktop ( with one file on it, as it was before). I can't use anything, because there isn't anything to use. 

Help needed :)

EDIT : I removed compiz with Synaptic.

---

### Post by amjjawad on 2011-07-18
> **Bakica said:**
> I've installed Ubuntu a week ago, and it ran good. Today, I installed compiz advanced desktop effects, and it lagged alot. Since then when I try to use Ubuntu I can't do anything, the only thing I see is my desktop ( with one file on it, as it was before). I can't use anything, because there isn't anything to use. 

Help needed :)

EDIT : I removed compiz with Synaptic.

Hello and Welcome,

Please mention which release of Ubuntu are you using?

After you removed compiz, is the problem fixed or not yet?

---

### Post by Bakica on 2011-07-18
I'm using Ubuntu 11.04.

The problem is still here, but I'm able to use Ubuntu when I go in recovery mode with low graphics. I still don't get what could  be a problem.

---

### Post by amjjawad on 2011-07-18
> **Bakica said:**
> I'm using Ubuntu 11.04.

The problem is still here, but I'm able to use Ubuntu when I go in recovery mode with low graphics. I still don't get what could  be a problem.

If you want to remove it, run this command from Terminal:

```
sudo apt-get purge <packagename>

```

---

### Post by Bakica on 2011-07-18
What's the name of package ? compiz ? 

And I'm just guessing that problem lies in it, i just read few threads about similar problems.

---

### Post by amjjawad on 2011-07-18
> **Bakica said:**
> What's the name of package ? compiz ? 

And I'm just guessing that problem lies in it, i just read few threads about similar problems.

Hmm, not sure.
Type compiz and then press TAB. It will list the available options.

If you are in doubt, better do it from Synaptic.

System > Administration > Synaptic

---

### Post by Bakica on 2011-07-18
I did it. But nothing changes. I can go in every mode ( safe mode, classic, recovery, console) except the normal one - Ubuntu

---

### Post by amjjawad on 2011-07-18
> **Bakica said:**
> I did it. But nothing changes. I can go in every mode ( safe mode, classic, recovery, console) except the normal one - Ubuntu

Ok, what exactly do you have or get whenever you login to Unity Session?
A screenshot will be a good idea too!

---

### Post by Bakica on 2011-07-18
I'll post screenshot when I come home :) 

Well, the only thing I see is desktop with one pdf file ( Python book, which I put there ) and that's all. I can't switch workspace, can't open anything ( I can't see anything, no taskbar, nothing). I tried to change the resolution with visual terminal, didn't work, tried couple of things ( restarded, repaired etc.) and still isn't working. But the thing is, when I press F3 ( or F4 or F2 not sure ) the Ubuntu Help Manager comes out, and I'm able to go on internet ( File -> Search for Online Help, and then mozila pops out. that's strange) and I can use it normally. I deleted all compiz ( as far as I know ). I'm currently working on safe-mod, which is running normally - but..:)

Thanks for help !

---

### Post by MG&amp;TL on 2011-07-18
I might be totally wrong- linux newbie too...but as I understand it, compiz is a 'window decorator' which means if you removed the entirety of it rather than just the settings manager, it will most probably kill something. I.e. no window border. Although I suppose it might have caused the problems you're having too. The problem with synaptic  is that you can all too easily remove something vital :D

---

### Post by amjjawad on 2011-07-18
> **Bakica said:**
> I'll post screenshot when I come home :) 

Well, the only thing I see is desktop with one pdf file ( Python book, which I put there ) and that's all. I can't switch workspace, can't open anything ( I can't see anything, no taskbar, nothing). I tried to change the resolution with visual terminal, didn't work, tried couple of things ( restarded, repaired etc.) and still isn't working. But the thing is, when I press F3 ( or F4 or F2 not sure ) the Ubuntu Help Manager comes out, and I'm able to go on internet ( File -> Search for Online Help, and then mozila pops out. that's strange) and I can use it normally. I deleted all compiz ( as far as I know ). I'm currently working on safe-mod, which is running normally - but..:)

Thanks for help !

Ok, I think you need to restore Unity which I have no idea how to do that but I'll do some search here: [http://www.googlubuntu.com/](http://www.googlubuntu.com/)
and will be back to you, hopefully soon :)

I'm replying 10 threads at the same time so it might take some time :)

---

### Post by amjjawad on 2011-07-18
> **MG&TL said:**
> The problem with synaptic  is that you can all too easily remove something vital :D

Even with command line you can do that :)
That's exactly why you need to know what are you doing and some say that Linux expect you do know what you're doing :)

---

### Post by Bakica on 2011-07-18
lol ups :p 

I'm pretty sure that I removed everything I installed today. So, if it worked for me before, it should work now, right ?

---

### Post by MG&amp;TL on 2011-07-18
Ah, but with the command line, you HAVE to know what 'something vital' is called. Or install something weird.

Whereas with synaptic, it's a GUI and you just point, click.

Anyway...if you haven't got anything important, or you can fit what IS important onto a separate hard drive/flash drive/computer, do a reinstall. Usually easiest. I've been using Ubuntu maybe 2 1/2 months now and I've reinstalled 9 times.

---

### Post by amjjawad on 2011-07-18
Perhaps this will help?

[http://ubuntuforums.org/showthread.php?t=1726770](http://ubuntuforums.org/showthread.php?t=1726770)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+restore+unity&as_qdr=all&sa=Google+Search&lang=en#1108](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+restore+unity&as_qdr=all&sa=Google+Search&lang=en#1108)

I'm doing many things at the same time so I'm really sorry for not being specific :)

---

### Post by Bakica on 2011-07-18
thanks it works, i just did this :

sudo apt-get install unity

unity --reset 

and works like charm

---

### Post by amjjawad on 2011-07-18
> **Bakica said:**
> thanks it works, i just did this :

sudo apt-get install unity

unity --reset 

and works like charm

Good to know that :)

Well done!


From Threads Tools, please mark this thread as SOLVED ;)

---

### Post by Blasphemist on 2011-07-18
A little more information. Unity is a compiz plugin in natty. So you can't remove compiz and expect things to work. Compiz does more than host unity too. A different package, compiz congig settings manager, ccsm, isn't installed by default but many do install it to tweak things. I wouldn't remove ccsm either.

These two commands will reset compiz to it's defaults including unity.
```
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
sudo reboot
```

When you have that nearly blank screen, you can press these keys to access a terminal. <Ctrl><Alt><F1>

---

### Post by wildmanne39 on 2011-07-18
Hi, I am glad you got it fixed here is a guide that you can use to set up effects and the cube with pictures for every step.
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

The lag can usually be fixed by doing what this link says to do.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)

---

