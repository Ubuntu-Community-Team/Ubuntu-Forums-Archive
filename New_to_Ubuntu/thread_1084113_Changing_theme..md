---
title: "Changing theme."
date: 2009-03-01
forum: New to Ubuntu
---

### Post by DannyP87 on 2009-03-01
Hi everyone, really new to Ubuntu. I'm literally a complete newbie to this having partitioned my hard drive and installed from the Live CD.

I love the concept of Linux/Ubuntu and on first impressions think it's excellent. I'm not so bad with computers as a whole and I'm a quick learner but sorry if I end up asking too many questions which may seem so easy!

I'm trying to change my theme and I've managed to download a couple including one called Moomex. It seems to be on fine but the Wallpaper that was shown with it wasn't included, is this normal?

Also, (Sorry to be a pain!) I downloaded another theme but a message appeared saying it may not display correctly due to GTK+2 being required to be installed. What is this? I've tried downloading somehting which has the file name "gtk-qt-engine-1.1.tar.bz2" but when I click on it it seems like a compressed file. I'm guessing installing a program isn't as easy as an exe file unless you do it through Add/Remove in Applications.

I understand this will take a lot of getting used to, I've downloaded the Ubuntu pocket guide which I've started to read and were I work they use Linux very similar to Ubuntu so I'm really keen to learn.

Really sorry for the essay, I'll be suprised if anyone replies ha!

Thank you

---

### Post by Bodsda on 2009-03-01
To install the gtk2 engine run this command from a terminal

```
sudo apt-get install gtk2-engines
```

or search synaptic for the package 'gtk2-engines'

Hope this helps

Bodsda

---

### Post by DannyP87 on 2009-03-01
Ok, done that and terminal confirmed it was installed. How do I access the program? Gone to applications and can't see it.

Also what exactly is GTK?

---

### Post by llamabr on 2009-03-01
> I'm guessing installing a program isn't as easy as an exe file unless you do it through Add/Remove in Applications.

I believe the opposite is true.  Installing from a tarball is not hard.  But yes, using synaptic or apt will be simpler, and keep your system consistent.

> Really sorry for the essay, I'll be suprised if anyone replies ha!

Get ready to be surprised by how supporting the linux community can be.

Anyway, let us know how it comes out.

---

### Post by DannyP87 on 2009-03-01
> **llamabr said:**
> I believe the opposite is true.  Installing from a tarball is not hard.  

True, just installed GTK with help from Bodsda and was suprides how easy that was.

> **llamabr said:**
> 
Get ready to be surprised by how supporting the linux community can be.

Anyway, let us know how it comes out.

Yeah, i was quite suprised when i logged onto the forums and saw 6 million replies to a million posts. Quite staggering to think about.

I've installed GTK but don't know where to find it or what it actually does?

---

### Post by ClaytonOT on 2009-03-01
Every theme I've downloaded has been a tarball which installation is as simple as System>Preferences>Appearance Themes tab hit the install button and select the tarball.

---

### Post by RomeReactor on 2009-03-01
Hi. Are you getting the same warning when you try to use the theme, after installing the GTK2 engines?

As for the wallpaper, it's likely it's not part of the package.

---

