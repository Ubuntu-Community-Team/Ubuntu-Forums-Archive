---
title: "Find Packages"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by sharbeloun on 2008-12-29
Hey all,

i did install a package called RDweather, like a weather monitor tool ! 
where i can find it ? how to use it now ?? 

thanks

---

### Post by howefield on 2008-12-29
Is it rrdweather ?

[http://www.wains.be/projects/rrdweather/](http://www.wains.be/projects/rrdweather/)

"....Download

Linux and Win32 versions : DOWNLOAD HERE
Deb package : this project is available under the Ubuntu Universe repository thanks to Lionel Porcheron. ..."

---

### Post by sharbeloun on 2008-12-29
yes it is .. but i did already install it from synaptic !

---

### Post by northern lights on 2008-12-29
I doubt that *rrdweather* is what you want. If you just want a few-day forecast, there's tons of more suiting and way easier tools out there (Forecastfox firefox extension, desklets, forecasts in conky, etc.).

Anyhow should you really want a tool like rrdweather, check [here]("http://www.wains.be/projects/rrdweather/") for info on how to set it up.

---

### Post by howefield on 2008-12-29
Sorry I misread your post, you have installed and now want to use it.

The link I provided has links to demos on it.

---

### Post by sharbeloun on 2008-12-29
first, thanks for ur help 

actually what i really need is s gadgets presenting weather !

---

### Post by northern lights on 2008-12-29
Either install *gdesklets* and add a weather desklet or check out *conky*. gdesklets is easier to set up, conky more powerful and more resource efficient.

First run```
sudo aptitude purge rddweather
``` to complete remove the now superfluous packages (should be 4, rddtool and 2 libraries).

Check out [Conky Weather Revisited V2]("http://ubuntuforums.org/showthread.php?t=666842")
or [http://www.gdesklets.de/]("http://www.gdesklets.de/")

---

### Post by sharbeloun on 2008-12-29
well, i installed the package conky from synaptic, what to do now ? how to use it, where i find it ? ( i never find packages i install )

---

### Post by northern lights on 2008-12-29
[http://linuxowns.wordpress.com/2008/04/04/create-a-custum-conky-setup/]("http://linuxowns.wordpress.com/2008/04/04/create-a-custum-conky-setup/")
[http://ubuntuforums.org/showthread.php?t=281865&highlight=post+your+conky]("http://ubuntuforums.org/showthread.php?t=281865&highlight=post+your+conky")

---

### Post by sharbeloun on 2008-12-29
thanks alot if i needed anything else i will reply again in here ;)

---

### Post by sharbeloun on 2008-12-29
man ! its very comlicated .. gdesklets maybe would be easier .. right ? i installed gdesklets and the weather desklet failed to give a weather broadcast

---

### Post by northern lights on 2008-12-29
In both cases you need your locations code from [weather.com]("http://weather.com").

gdesklets would be easier. I can't tell you anything else about it, as I despise it and never used it.

IMHO, gdesklets is superfluous eye-candy, whereas conky is at least arguably handy.

---

