---
title: "Googe gears could not be installed (Linux_x86-gcc3)"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by al.adab on 2010-10-17
Trying to install Google Gears (Firefox 3.6.10) and I keep getting the following error message: 

[I]Incompatible Extension 
"Google Gears" could not be installed because it is not compatible with your Firefox build type (Linux_x86-gcc3). Please contact the author of this item about the problem."[/I]

what to do?

---

### Post by al.adab on 2010-10-19
bump?

---

### Post by al.adab on 2010-10-21
just tried again to install Google Gears (through Zoho Writer). I now get a new error message: 

[I]Firefox could not install the file at 

[http://dl.google.com/gears/current/gears-linux-opt.xpi](http://dl.google.com/gears/current/gears-linux-opt.xpi)

because: Not a valid install package
-207[/I]

does anyone know what's going on?

---

### Post by P4man on 2010-10-21
No idea. It installs fine here, same firefox version on ubuntu 10.10, 64 bit. 

Either way, please be aware that google gears is being fased out:
[http://gearsblog.blogspot.com/2010/02/hello-html5.html](http://gearsblog.blogspot.com/2010/02/hello-html5.html)

Not that that explains your problem

---

### Post by al.adab on 2010-10-22
So I suppose there won't be any support for Google Gears users so long as a replacement (HTML5?) has been put in place? 
Interesting you're on a 64bit - Gears says that 64bit is not supported! :) 

I'm trying to install xul-ext-gears ([http://packages.ubuntu.com/lucid/xul-ext-gears](http://packages.ubuntu.com/lucid/xul-ext-gears)) but haven't done this for such a long time I can't remember how to do it. Shame on me!

---

### Post by P4man on 2010-10-22
Firefox is still 32 bit (I think?)

---

### Post by al.adab on 2010-10-25
sorry I got a bit confused by the 32-bit vs 64-bit vis a vis Gears...

xul-ext-gears doesn't seem to be in the repositories any longer - any idea if a *sudo apt-get install xul-ext-gears* should ever work?

---

### Post by mcchots on 2010-10-30
xul-ext-gears 0.5.36 shows up for me in Ubuntu Software Center on 10.04.
Synaptics locates it in the universe repo.

---

### Post by pac0rro on 2010-11-11
For those who can not install Google Gears on Ubuntu 10.10: I have built the last version and you can download it from:

[https://sites.google.com/site/wadjakmanresources/]("https://sites.google.com/site/wadjakmanresources/gears-maverick-0.5.37.0.zip?attredirects=0")

For me works fine.

---

