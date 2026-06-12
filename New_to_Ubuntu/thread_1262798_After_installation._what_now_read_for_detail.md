---
title: "After installation. what now? read for detail"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by Zlash on 2009-09-10
I got the, honestly, wierd annoying netbook linux interface. i just want the regular ubuntu gnome interface. how to?

Thanks in advance :)

---

### Post by ukripper on 2009-09-10
> **Zlash said:**
> I got the, honestly, wierd annoying netbook linux interface. i just want the regular ubuntu gnome interface. how to?

Thanks in advance :)

What model is your netbook  and which linux distro are you using?

---

### Post by NCLI on 2009-09-10
I assume you got UNR working. Just go to Preferences, Switch Desktop Mode ;)
[IMG]http://mugginix.com/articles/2009/May/02/Standard-Desktop-For-Netbook-Remix/images/Select%20Switch%20Desktop%20Mode.jpg[/IMG]

By the way, you might want to indicate what version of Ubuntu you're using by adding it to your profile.

---

### Post by henkeC on 2009-09-10
In a Terminal run: 

```
sudo apt-get remove go-home-applet human-netbook-theme maximus netbook-launcher window-picker-applet
```

then run:

```
sudo apt-get install ubuntu-desktop
```

Restart, Done! :)

---

### Post by NCLI on 2009-09-10
> **henkeC said:**
> In a Terminal run: 

```
sudo apt-get remove go-home-applet human-netbook-theme maximus netbook-launcher window-picker-applet
```then run:

```
sudo apt-get install ubuntu-desktop
```Restart, Done! :)
If he has UNR, he already has ubuntu-desktop installed, though you're correct that removing the packages you mention will save him a little space.

---

### Post by Zlash on 2009-09-10
> **henkeC said:**
> In a Terminal run: 

```
sudo apt-get remove go-home-applet human-netbook-theme maximus netbook-launcher window-picker-applet
```then run:

```
sudo apt-get install ubuntu-desktop
```Restart, Done! :)

After doing what you guys told me to, my desktop did indeed go back to gnome but apparently compizz is completly turned off now, aswell as my custom icons are gone.

No in theory i didnt get Netbook version of ubuntu to work, i thought i could take a shortcut so i installed ubuntu-netbook-remix via terminal.

not sure if this is enough tho, want the bedt result tbh

---

### Post by NCLI on 2009-09-10
No, that's not enough, you need to install it from the img to get the drivers ;)

---

### Post by Zlash on 2009-09-10
> **NCLI said:**
> No, that's not enough, you need to install it from the img to get the drivers ;)

Darnit! *races hand in anger*

oh well. guess il have a clean system again!  *laughs*

---

### Post by nothingspecial on 2009-09-10
All you had to do was 

```
sudo apt-get remove --purge ubuntu-netbook-remix
```

Since you are installing the netbook remix fully you are going to want to turn off the interface.

Once it`s installed just go in your menu system > preferences > start up applications and uncheck netbook-launcher and maximus.

---

