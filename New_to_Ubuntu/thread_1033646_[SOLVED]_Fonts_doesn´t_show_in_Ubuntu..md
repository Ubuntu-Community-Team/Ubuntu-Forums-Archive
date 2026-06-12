---
title: "[SOLVED] Fonts doesn´t show in Ubuntu."
date: 2009-01-07
forum: New to Ubuntu
---

### Post by gronater on 2009-01-07
Hi,

Im new on Ubuntu and ubuntuforums.org. So can someone help me with my fonts. I use ubuntu 8.10 and i download it 3 days ago.I thougt the problem was KDE, but maybe not:-?
They doesnt work in Amarok and all other programs. I make a few screenshots.

[http://nl.tinypic.com/view.php?pic=35jfoyh&s=5](http://nl.tinypic.com/view.php?pic=35jfoyh&s=5)

click on the amarok pic and he will show.
Then you see left-up my problem. He doesnt show the fonts.
the same with utorrent:

[http://nl.tinypic.com/view.php?pic=szy979&s=5](http://nl.tinypic.com/view.php?pic=szy979&s=5)

this happens with everything I open and download that is not from gnome

Grtz,

PS: im dutch and my  english isn´t very good:D

---

### Post by blueridgedog on 2009-01-07
Just a suggestion, perhaps you can install the non-free true type fonts:

```
sudo apt-get install ttf-xfree86-nonfree
```

Run this in a terminal.

---

### Post by kestrel1 on 2009-01-07
This does seem to be a problem with 8.10.
I have had this with any program that is meant for KDE (Amarok, K3B) when being used in gnome.

---

### Post by kestrel1 on 2009-01-07
Unfortunatly the above font install does not work.
The only way I have found to get this working is to turn off all visual effects. I am not saying there is no fix, but I don't know what else to do.

---

### Post by gronater on 2009-01-08
> **kestrel1 said:**
> Unfortunatly the above font install does not work.
The only way I have found to get this working is to turn off all visual effects. I am not saying there is no fix, but I don't know what else to do.

Thx it works. I´ve got no visual effects any more but i can see the fonts now.

---

### Post by kestrel1 on 2009-01-08
It is a bit of a pain to be honest.
I like the visual effects, so have moved to using different programs that are compatable with gnome.
For Amarok I use Exaile & I have stuck to using Brasero instead of K3B for disc burning.
I expect it will get sorted out, but someone may know of a better way, rather than getting rid of the visual effects.

---

### Post by gronater on 2009-01-08
He´s not doing great, i got a problem with utorrent. I make a pic from it:

[http://img150.imageshack.us/img150/8086/schermafdruktorrent181eb6.png](http://img150.imageshack.us/img150/8086/schermafdruktorrent181eb6.png)

This is my problem now, hope you can solve it.

---

### Post by kestrel1 on 2009-01-08
I think if you go to system - preferences - appearance
Then go to the Fonts tab & select Subpixel Smoothing (LCD's)
I think that will do it.

---

### Post by gronater on 2009-01-08
No he´s still not working. maybe it is a problem with my resolution?

---

### Post by kestrel1 on 2009-01-08
Maybe.
Try lowering your resolution & see if that sorts it. I am surprised that changing the font to subpixel didn't work though. 
Hold on a sec, you have changed back to no visual effects. I think you want to change the fonts to Monochrome.
I hope I am right.

---

### Post by gronater on 2009-01-08
No nothing works at all. Lowering resolution doesn´t work and change to monochrome make it all much worser.

---

### Post by gronater on 2009-01-08
He is still not working. Changing my resolution doesn´t work and change fonts to monochrom doesn´t work too.

---

### Post by gronater on 2009-01-08
He is still not working. Changing my resolution doesn´t work and change fonts to monochrom does not work too.

---

### Post by gronater on 2009-01-09
No nothings works. I have lowered my resolution and I change fonts to monochrom but it did not work. Change to monochrom make it just all worser.

---

### Post by gronater on 2009-01-09
No nothing works. I have lowered my resolution and i have change my fonts to monochrom. Change it to monochrom make it all just more worser.

---

### Post by gronater on 2009-01-09
No it all doesn´t work.

---

### Post by kestrel1 on 2009-01-10
I am affraid I am out of suggestions on that one. At present 8.04 LTS works better with any of the graphics stuff, but when the drivers etc for 8.10 get sorted I am sure this will be OK.

---

