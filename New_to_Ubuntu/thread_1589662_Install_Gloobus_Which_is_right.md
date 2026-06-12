---
title: "Install Gloobus? Which is right?"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by juil on 2010-10-06
It annoys me that things are so unclear in the ppa website it gives me the below instruction for covergloobus.

> Covergloobus doesn't need an install, just download the tar.gz file and uncompress it wherever you want.
Then launch covergloobus-config.py (double clicking it and choose execute or from terminal python /path/to/covergloobus-config.py)

This is the configuration utility, here you can choose your theme and you player. When finished click save and you're ready to open covergloobus.py (The same way you opened covergloobus-config.py).

If you want covergloobus to be launched when you open your session just add "python /path/to/covergloobus.py" without quotes, into you start up applications.

Thats all, enjoy it and feel free to donate me something or report bugs!!

So that's what I did. I downloaded the tar.gz, extracted it in my Music folder. When I double click on the covergloobus.py though it just opens a gedit file. When I use exaile, it doesn't do squat.

Then I ran into this website that tells me a whole different way of installing it.

[http://www.omgubuntu.co.uk/2010/02/covergloobus-1-6-wow-lives-up-to-its-name/](http://www.omgubuntu.co.uk/2010/02/covergloobus-1-6-wow-lives-up-to-its-name/)

Can someone tell me which is the correct way?

---

### Post by hhh on 2010-10-06
[http://gloobus.net/wiki/index.php?title=Install#Installing_CoverGloobus_from_the_PPA](http://gloobus.net/wiki/index.php?title=Install#Installing_CoverGloobus_from_the_PPA)
Installing from PPA will be easier than from source.

---

### Post by juil on 2010-10-06
where did it install it?
How do i configure it?

---

### Post by hhh on 2010-10-06
Programs installed system-wide are usually installed to /usr/bin, as in this case.

You're right, those Launchpad instructions suck. I went ahead and installed it (I have no use for it at this time, but whatever) and to configure, I ran covergloobus-config in a terminal. To run it, I entered covergloobus in the run dialog (Alt+F2), I clicked the desktop and hit the Esc key to close it. You can add covergloobus to your startup programs if you want it to run, you know, at startup.

Hope that helps.

---

