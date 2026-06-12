---
title: "ubuntu 10.10 GUI not loading"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by awal57 on 2010-12-16
I have installed ubuntu 10.10 32 bit on an old dell pe 1550 i686 with 512mb of ram. i raided 2 drives and attempted the install and it says that it is complete but it asks me to login in a command prompt that looks like DOS and I never get to a GUI am I missing something or should I expect a GUI? somebody help I'm lost!

---

### Post by TeoBigusGeekus on 2010-12-16
What are you pc specs? Especially your graphics card.

---

### Post by awal57 on 2010-12-16
two 1133mhz processors and the ram is actually 1024mb, it says that the video memory is 4mb sdram, other than that I have no clue. I bought it for 40 bucks and thought I could experiment with linux and building a web and mail server, but I was expecting a GUI since I'm pretty green when it comes to command prompts and the like.

---

### Post by seawolf167 on 2010-12-16
If you have a capable video card and have the GUI installed (versus the server option), try entering this: (assuming you are getting a command line login option)

```
startx
```

You can try to start the script manually by doing:

```
sudo /etc/init.d/gdm start
```

Though in 10.10 this should work too:

```
sudo service gdm start
```

If that doesn't start, you can attempt to reconfigure the xserver

```
sudo dpkg-reconfigure xserver-xorg
```

Then follow the prompts

---

### Post by TeoBigusGeekus on 2010-12-16
If the above commands don't work, find your graphics card with
```
lshw | grep VGA
```

---

### Post by awal57 on 2010-12-16
that my be an answer to my problem, I installed the server edition but I'll look to see what my graphics card is. thanks

---

### Post by seawolf167 on 2010-12-16
The server edition does not come with a GUI installed. Since you just installed Ubuntu on your computer it might be easiest to just reinstall with the non-server (i.e. Desktop) version (ensuring that everything works properly), otherwise [this thread ]("http://ubuntuforums.org/showthread.php?t=268037")has info on installing the gui.

Its basically just:

```
sudo apt-get install ubuntu-desktop 
```

---

### Post by awal57 on 2010-12-16
ok by installing the non server edition I can still run a wab and mail server correct? and I wouldnt lose any functionality would I?

---

### Post by seawolf167 on 2010-12-16
You will lose CPU cycles due to the computer running the GUI, you will gain a GUI and some additional installed programs.

Basically, no, you won't lose functionality

---

