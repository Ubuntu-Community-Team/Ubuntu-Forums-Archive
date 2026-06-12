---
title: "I'm booting into Command line, and I REALLY need help!"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by greenelf on 2011-06-27
Ok, so 11.04 was working great for me, until I got adventurous with it. I installed two things, Compiz Manager, and SLIM login manager. I'm pretty sure that Slim is causing the problem. How do I remove it?

---

### Post by sanderd17 on 2011-06-27
Let's first see what SLIM removed when you installed it. Check out the installation log:

```

cat /var/log/dpkg.log

```

And report what it says (maybe take a picture of it).

---

### Post by greenelf on 2011-06-27
> **sanderd17 said:**
> Let's first see what SLIM removed when you installed it. Check out the installation log:

```

cat /var/log/dpkg.log

```

And report what it says (maybe take a picture of it).

I don't know how to copy things in the command line interface, but here's a pic:
[IMG]http://i.min.us/ibDs4w.JPG[/IMG]

---

### Post by sanderd17 on 2011-06-27
Hmm, it says slim isn't installed.

try
```

sudo apt-get update
sudo apt-get install gdm

```

If you want to get your GUI without installing a login manager, you can also run
```

startx

```

---

### Post by josephmills on 2011-06-27
did you try ```
sudo /ect/init.d/gdm restart
```od ```
startx
```

---

### Post by greenelf on 2011-06-27
> **sanderd17 said:**
> Hmm, it says slim isn't installed.

try
```

sudo apt-get update
sudo apt-get install gdm

```

If you want to get your GUI without installing a login manager, you can also run
```

startx

```

I didn't see that last part about startx, so I'll do that now.
Here's what the 
```

sudo apt-get update
sudo apt-get install gdm

```
Gave me:
[IMG]http://i.min.us/ib9ags.JPG[/IMG]
EDIT: Just realized, I wrote it wrong. Let me try again

--
Ok, here's what I got:
[IMG]http://i.min.us/ib98yq.JPG[/IMG]

---

### Post by greenelf on 2011-06-27
> **josephmills said:**
> did you try ```
sudo /ect/init.d/gdm restart
```od ```
startx
```

I'll try the first one now.
Also, when I do startx, I get to my desktop, except there's no unity, no desktop icons, no taskbar. Just my wallpaper. I'm able to right click, and create a launcher, but I can't find Terminal (shortcuts don't work).

---

### Post by sanderd17 on 2011-06-27
the terminal is called gnome-terminal, so if you make a launcher with that, you can use it, and the file manager is called nautilus.

---

### Post by greenelf on 2011-06-27
> **sanderd17 said:**
> the terminal is called gnome-terminal, so if you make a launcher with that, you can use it, and the file manager is called nautilus.


Ok, so what I did was make a terminal launcher, then I did unity --reset.
This brought everything back (laucher bar, icons, etc).
But my next problem is that it constantly asks me for my login key or something?
What is that?

---

### Post by sanderd17 on 2011-06-27
It's the password of your password manager. Normally it's unlocked by your login manager (it uses the same password), but since you don't have one ...

---

### Post by greenelf on 2011-06-27
> **sanderd17 said:**
> It's the password of your password manager. Normally it's unlocked by your login manager (it uses the same password), but since you don't have one ...
I think my password worked (I must have typed it wrong).
Thank you for all your help!

---

### Post by josephmills on 2011-06-27
ok so if gdm is opening then that is a good this try to restart unity  I think I say think it is in the /ect/init.d/unity restart 
but I could be wrong I will test it on 11.10 hang on brb

---

### Post by josephmills on 2011-06-27
ok I think that it is under /usr/bin/unity restart at least in 11.10 it is but then again that is 11/10 not 11.04 you could try the command locate unity or which unity to show where it is or you couls also try the command restartx hope that this helps

---

### Post by sisco311 on 2011-06-27
> **greenelf said:**
> I'm pretty sure that Slim is causing the problem. How do I remove it?

You can select the default display manager by running:
```
sudo dpkg-reconfigure -fgnome gdm
```

---

### Post by josephmills on 2011-06-27
> **sisco311 said:**
> You can select the default display manager by running:
```
sudo dpkg-reconfigure -fgnome gdm
```

could you explain this command for us please. Just tryin  to learn thanks you so much. I am just confused about the dpkg this is a debian package manager right? what is the difference between that and apt or aptitude ?  so I see dpkg(package,manager+reconfig ) -fgnome What is the f infront of gnome for and I know that gdm is gnome desktop manager right ? thanks for your time

---

### Post by sanderd17 on 2011-06-28
> **josephmills said:**
> could you explain this command for us please. Just tryin  to learn thanks you so much. I am just confused about the dpkg this is a debian package manager right? what is the difference between that and apt or aptitude ?  so I see dpkg(package,manager+reconfig ) -fgnome What is the f infront of gnome for and I know that gdm is gnome desktop manager right ? thanks for your time

dpkg is the backend of apt-get, aptitude or similar programs. dpkg does the installing (extracting and copying) while the apt-variants do the downloading and see if the dependencies are good.

I don't know what the -fgnome argument is though.

---

