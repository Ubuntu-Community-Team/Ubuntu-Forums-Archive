---
title: "Dvix??"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by Zombie Robot on 2010-10-15
How can I watch divx on ubuntu? I have no idea how. Im still new lol

---

### Post by marshmallow1304 on 2010-10-15
What have you tried?  You should be able to open the file in Totem (Movie Player) and it should then prompt you to install any necessary codecs.

---

### Post by Zombie Robot on 2010-10-15
I downloaded VLC, do i need extra codecs?

---

### Post by endotherm on 2010-10-15
> **Zombie Robot said:**
> I downloaded VLC, do i need extra codecs?
nope, vlc has them all built in.

you may want to look at the [ubuntu restricted extras]("https://help.ubuntu.com/community/RestrictedFormats") package (lots of codecs for totem), and the [medibuntu ]("https://help.ubuntu.com/community/Medibuntu")repositories though so you can use a differant player. see if totem ("Movie Player") works as well for you as vlc. totem often has better picture.

I personally like SMPlayer, the best. if you look around you can find tutorials on installing it.

---

### Post by cjv8888 on 2010-10-15
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by andrew.46 on 2010-10-15
Hi endotherm,

> **endotherm said:**
> nope, vlc has them all built in.

It is a minor nitpick but the 32bit vlc can actually use external codecs if it has been compiled with the *--enable-loader* option. Minot nitpick as Ubuntu repository versions universally do not use this option :).

Andrew

---

### Post by Zombie Robot on 2010-10-16
Alright so I got this far. [http://i54.tinypic.com/33kbvi0.png](http://i54.tinypic.com/33kbvi0.png) But it doesnt have sound, well at first it does but then it goes out and it doesnt have a play button or anything. What do you need to do now??


> **cjv8888 said:**
> ```
sudo apt-get install ubuntu-restricted-extras
```
 
I did this, do I need to add something else?? or get rid of VLC?

---

### Post by khelben1979 on 2010-10-16
Are you trying to watch divX video clips in your web browser?

[http://www.xvidcodec.net/](http://www.xvidcodec.net/)

---

### Post by ibizatunes on 2010-10-16
```
sudo apt-get install ubuntu-restricted-extra && sudo apt-get install vlc
```
this will install codec and then vlc to play divx on

---

### Post by Zombie Robot on 2010-10-18
> **khelben1979 said:**
> Are you trying to watch divX video clips in your web browser?

[http://www.xvidcodec.net/](http://www.xvidcodec.net/)


Yeah I am wanting to watch it in my browser.

---

### Post by migs73 on 2010-10-19
Try this
```
sudo apt-get install totem-mozilla
```

this should get you the totem plugin for firefox.

---

### Post by Zombie Robot on 2010-10-19
> **endotherm said:**
> nope, vlc has them all built in.

you may want to look at the [ubuntu restricted extras]("https://help.ubuntu.com/community/RestrictedFormats") package (lots of codecs for totem), and the [medibuntu ]("https://help.ubuntu.com/community/Medibuntu")repositories though so you can use a differant player. see if totem ("Movie Player") works as well for you as vlc. totem often has better picture.

I personally like SMPlayer, the best. if you look around you can find tutorials on installing it.

> **cjv8888 said:**
> ```
sudo apt-get install ubuntu-restricted-extras
```


I have VLC and this downloaded. When I press play nothing happens. Sometimes it says, Search for suitable plugin? Then it says No packages with the requested plugins found
The requested plugins are:

text/html decoder

Sorry Im a new to this kind of stuff. All I have ever used was windows and everything is so easy to download for it.

---

### Post by 29732 on 2010-10-19
you could try purging vlc ```
sudo apt-get purge vlc
```
and then reinstalling the restricted extras??? (and maybe reinstalling firefox)
 
 
(boy, i hope someone finds a better solution)

---

### Post by 29732 on 2010-10-19
[removed]

---

### Post by Zombie Robot on 2010-10-19
> **29732 said:**
> you could try purging vlc ```
sudo apt-get purge vlc
```and then reinstalling the restricted extras??? (and maybe reinstalling firefox)
 
 
(boy, i hope someone finds a better solution)


This worked thank you. Thanks everyone that helped me [:

---

