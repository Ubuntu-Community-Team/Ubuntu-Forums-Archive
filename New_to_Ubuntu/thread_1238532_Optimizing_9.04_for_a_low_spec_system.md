---
title: "Optimizing 9.04 for a low spec system"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by raicho on 2009-08-12
Hi everyone, first time Ubuntu-user here!

I'm a poor, poor man at the moment, so I'm currently trialling Ubuntu on the only system I have available to me - an old, beat up 2Ghz laptop with 256mb RAM and a 30gb HD.

I love it so far, it's as simple and effective as I'd hoped it would be and I want to stick with it - but it is taxing what little resources my system has.

Can anyone recommend any features/processes/etc that I can disable or remove in order to make my Ubuntu run a little quicker?

Many thanks!

---

### Post by M. Fawzy on 2009-08-12
I think you may want to try Xubuntu ! it would be nice for you ! :D
visit their visit
[www.xubutu.org](www.xubutu.org)

---

### Post by Hospadar on 2009-08-12
If you want a really screaming installation, and you're up to a little challenge, you might want to install ubuntu server and build your own desktop environment with something like fluxbox.

Take a look in the community docs in my sig, they have a nice page on fluxbox.

Xubuntu would be great for a machine like that though.

---

### Post by QIII on 2009-08-12
+1 for Xubuntu, if you want to stick with 'buntu distributions.

I ran Xubuntu for a long time on a very old laptop with worse specs than that.

But don't feel like you have to use Ubuntu if something else will work better.  I prefer Ubuntu to all the other distros I have tried, but that's just me.

Your post will probably get all sorts of suggestions for other distros.  It would be worth your time to try several of them out and see what you like.

---

### Post by raicho on 2009-08-12
I've tried quite a few other distro's in the past (I've been an on/off linux user for a while now) but Ubuntu just screams at me "don't go!" more than any other distro I've tried!

Thanks for the pointers, I'm downloading the xubuntu iso now!

---

### Post by LowSky on 2009-08-12
your low amount of RAM is really your only issue. 512MB of RAM and the system would be much smoother. you could maybe score some off ebay for under $20, but you will need to know what type before making a purchase

---

### Post by nikhilbhardwaj on 2009-08-12
i think you should get rid of gnome
and try lxde instead

or better still just run openbox with fbpanel or perl panel

there are a lot of good guides here at ubuntu forums that can help you


if you want to try some other os and not ubuntu
then i'll recommend pc linux os lxde 2009.4

and if you want something thats lighter still
then there are always puppy linux and dsl

---

### Post by ajgreeny on 2009-08-12
> **nikhilbhardwaj said:**
> i think you should get rid of gnome
and try lxde instead

or better still just run openbox with fbpanel or perl panel

there are a lot of good guides here at ubuntu forums that can help you


if you want to try some other os and not ubuntu
then i'll recommend pc linux os lxde 2009.4

and if you want something thats lighter still
then there are always puppy linux and dsl
+1
I tried the ubuntu minimal install CD [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) recently just for fun and added the lxde desktop.  If you install xubuntu and just add the lxde packages it will be easier than the minimal install way, and I think you will find that it just flies.  lxde, though not to everyone's taste is incredibly fast (and pretty) so worth looking at.  It is in the repos as well so very easy to try.
```
sudo apt-get install lxde
```

---

### Post by XubuRoxMySox on 2009-08-12
+1 for LXDE. It's so very lightweight that it is often "accused," so to speak, of not being a real desktop environment at all. It's much lighter than even Xfce (Xubuntu).

I experimented with PCLXDE, but found that my scanner and printer wouldn't work even after loading all the drivers and cups and whatnot. It's gorgeous, but a little buggy. Nevertheless I predict that future versions of PCLXDE will be awesome.

They're actually working on an LXDE 'buntu release which may be available around the time Karmic Koala is released. 

The quickest and easiest way is as suggested above:

```
sudo apt-get install LXDE
```

Then log out, and under the Options menu at login, select LXDE as your Session.

I find it super-simple, and much faster than any other desktop environment I've tried yet. I like it so much I'm a fanboy and made it my forum signature!

Besides being super lightweight and simple, it has a "familiar-looking" desktop with clickable icons that any newbie could navigate easily. The other kids don't even know it's Linux!

-Robin

---

### Post by LewRockwell on 2009-08-12
> **raicho said:**
> Hi everyone, first time Ubuntu-user here!

I'm a poor, poor man at the moment, so I'm currently trialling Ubuntu on the only system I have available to me - an old, beat up 2Ghz laptop with 256mb RAM and a 30gb HD.

I love it so far, it's as simple and effective as I'd hoped it would be and I want to stick with it - but it is taxing what little resources my system has.

Can anyone recommend any features/processes/etc that I can disable or remove in order to make my Ubuntu run a little quicker?

Many thanks!

max the ram in that machine and go to town!

.

---

### Post by Lukios on 2009-09-24
If you want to stay with Ubuntu I suggest downloading the mini.iso and then installing LXDE. I'm currently a computer tech on the side and you wouldn't believe how many people want me to turn their crusty old computers into into a blazing piece of machinery. Lately I have found that LXDE works the best on slow systems (as low as PII) In fact I just put together a system that has 800mhz proc and 384mb ram with LXDE, gnome-panel, and AWN and its really fast.

If you don't deriving from Ubuntu then you can try puppy linux (I prefer the teenpup version) Antix or Elive (which is debian based). The only one out of the 3 that I really don't like is Elive. It has some issues with permissions and installing different packages, there are work arounds, but its just a pain.

---

### Post by kerry_s on 2009-09-25
1 thing to learn on the forums is to check the date of the last post, otherwise your just bringing up a dead thread.

ps: i run gnome on 450mhz 256mb of ram, if you do the performance tips & replace the heavier programs it runs just fine.
[http://library.gnome.org/admin/system-admin-guide/stable/performance-0.html.en](http://library.gnome.org/admin/system-admin-guide/stable/performance-0.html.en)

memory usually lower than that, but i been browsing all day with out closing the browser.

---

### Post by renkinjutsu on 2009-09-25
> **kerry_s said:**
> 1 thing to learn on the forums is to check the date of the last post, otherwise your just bringing up a dead thread.

ps: i run gnome on 450mhz 256mb of ram, if you do the performance tips & replace the heavier programs it runs just fine.
[http://library.gnome.org/admin/system-admin-guide/stable/performance-0.html.en](http://library.gnome.org/admin/system-admin-guide/stable/performance-0.html.en)

memory usually lower than that, but i been browsing all day with out closing the browser.

gnome-system-monitor = bad :(

what's the cpu usage displayed by something more lightweight, like top?

---

### Post by Lukios on 2009-09-25
agreed

---

### Post by kerry_s on 2009-09-25
> **renkinjutsu said:**
> gnome-system-monitor = bad :(

what's the cpu usage displayed by something more lightweight, like top?

:lolflag: you already know it would be lighter. 
anyways i already swapped it out for htop.

here's from a fresh boot.

---

### Post by fluxlizard on 2009-09-25
If you up your ram (cheap these days) ubuntu will be much much more nimble.

If you aren't attached to ubuntu-
I'm running pclinuxos gnome edition on an old 700 mhz 256mb ram laptop and it runs just fine. It would probably be screaming fast on your machine...

---

### Post by kerry_s on 2009-09-25
> If you up your ram (cheap these days) ubuntu will be much much more nimble.

not always possiable with older systems, for example 256mb is the max on mine. also older ram can cost a lot as well as being hard to find.

---

### Post by fluxlizard on 2009-09-25
oops- nvm didn't notice it was a laptop we were talking about here. Ram might be expensive, but a 2ghz cpu- shouldn't be impossible.

---

