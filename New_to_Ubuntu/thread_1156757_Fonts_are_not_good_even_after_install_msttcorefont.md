---
title: "Fonts are not good even after install msttcorefonts"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by rams123 on 2009-05-12
I've installed msttcorefonts but still fonts are little blurry..

In Windows: [http://img257.imageshack.us/img257/2397/ufwin.png](http://img257.imageshack.us/img257/2397/ufwin.png)

In Linux: [http://img212.imageshack.us/img212/3910/screenshotycc.png](http://img212.imageshack.us/img212/3910/screenshotycc.png)

What's the problem?

---

### Post by swoody on 2009-05-12
Are you looking to make your Ubuntu fonts more like your Windows fonts? It looks like it may just be 'sub-pixel smoothing' is activated in your options. Go to System>Preferences>Appearance and under the 'Fonts' tab, change the options in there from Sub-pixel smoothing to one of the other settings. I think you may see the fonts much sharper with 'Best Contrast' but this is a completely personal choice, so try them out and select the one that looks best to you :D

---

### Post by kerry_s on 2009-05-12
i don't see the problem, other than the windows 1 looks like crap.

you installed the fonts, but are you actually using it?

---

### Post by Didius Falco on 2009-05-12
Go to **System/Preferences/Appearance**, then to the **Fonts** tab. From there, you can changed the appearance using the options at the bottom, or even the fonts used by setting the font choices at the top.

The first setting you may want to adjust would be the **Rendering** section. If **Sub-Pixel Smoothing** is on, you can either switch it to a different mode or go on to the **Details** button at the bottom, which leads to more settings to adjust. 

There are a lot of options, so you should have no trouble getting it to display in your preferred way.

I hope this Helps...

Regards,

Didius

---

### Post by YldGuy on 2009-05-12
try changing the auto-hinting from fonts tab.
that should help. and as an added measure you can try enabling bytecode hinting (Straight from the book Ubuntu Kung-fu)

To activate bytecode hinting, open a terminal window and type the following:

```
$ sudo dpkg-reconfigure fontconfig-config
```

Using the cursor keys, select Native from the menu and then hit Enter.
On the next screen you’ll be asked if you want to activate subpixel
rendering. This is good for TFT screens, so make the choice (or just
select Automatic). Next you’ll be asked if you want to activate bitmap
fonts, which are non-true type fonts good for use at low point levels.
There’s no harm in using them, so select yes.
The program will quit when it’s finished. Once that’s happened, type
the following to write the changes to the system and update files:

```
$ sudo dpkg-reconfigure fontconfig
$ sudo dpkg-reconfigure defoma

```

Click System ! Quit ! Logout, and then log back in again. The difference
should be noticeable immediately. Letters will appear more rounded
and the antialiasing will appear better.
Bytecode hinting isn’t to everybody’s taste. If you don’t like it, just
repeat the steps and enable autohinting again.

---

### Post by rams123 on 2009-05-12
> **kerry_s said:**
> i don't see the problem, other than the windows 1 looks like crap.

you installed the fonts, but are you actually using it?

I've adjusted that settings but still not satisfied, windows has won in this.. :(

In windows : 
[[IMG]http://img56.imageshack.us/img56/2397/ufwin.th.png[/IMG]](http://img56.imageshack.us/my.php?image=ufwin.png)

In Linux: 

**1. **[[IMG]http://img56.imageshack.us/img56/3128/screenshot1m.th.png[/IMG]](http://img56.imageshack.us/my.php?image=screenshot1m.png)

**2. **[[IMG]http://img524.imageshack.us/img524/7787/screenshot3d.th.png[/IMG]](http://img524.imageshack.us/my.php?image=screenshot3d.png)

**3.** [[IMG]http://img134.imageshack.us/img134/5551/screenshot2dvf.th.png[/IMG]](http://img134.imageshack.us/my.php?image=screenshot2dvf.png)

Can you able to see that blurriness? If we've tasted windows fonts, we will nvr like this stupid fonts, really!

---

### Post by Celauran on 2009-05-12
I'm not sure what the problem is, really. The Linux fonts look sharp in the images; no blurriness whatsoever. They also look considerably better than the Windows fonts.

---

### Post by caravel on 2009-05-12
> **kerry_s said:**
> i don't see the problem, other than the windows 1 looks like crap.

My thoughts exactly.  The Ubuntu screenshots show better and smoother fonts.  I don't see what the problem is.

If you don't want the smoothing then turn off the sub pixel smoothing as explained above.

---

### Post by philinux on 2009-05-12
I prefer the ubuntu version. The windows version is too spidery for me. I hate using my GF's xp machine.

---

### Post by kerry_s on 2009-05-12
> **rams123 said:**
> I've adjusted that settings but still not satisfied, windows has won in this.. :(

In windows : 
[[IMG]http://img56.imageshack.us/img56/2397/ufwin.th.png[/IMG]](http://img56.imageshack.us/my.php?image=ufwin.png)

In Linux: 

**1. **[[IMG]http://img56.imageshack.us/img56/3128/screenshot1m.th.png[/IMG]](http://img56.imageshack.us/my.php?image=screenshot1m.png)

**2. **[[IMG]http://img524.imageshack.us/img524/7787/screenshot3d.th.png[/IMG]](http://img524.imageshack.us/my.php?image=screenshot3d.png)

**3.** [[IMG]http://img134.imageshack.us/img134/5551/screenshot2dvf.th.png[/IMG]](http://img134.imageshack.us/my.php?image=screenshot2dvf.png)

Can you able to see that blurriness? If we've tasted windows fonts, we will nvr like this stupid fonts, really!


to get that windows look you need to turn off antialiasing, and put hinting to full.

here's the screen shot

---

