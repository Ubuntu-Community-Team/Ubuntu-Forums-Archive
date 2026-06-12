---
title: "[SOLVED] Driver compile/install for a noob"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by Kain000 on 2008-05-12
Hey everyone,
Im new to the forum, tho i've been here many times in the last week, (installed Ubuntu ver 8 hearty herron last monday)  and i LOVE IT!
It's so easy to use for the most part, and im sure once i've seen the light on this issue it will have become a duh moment.   
so here's my problem...
I was happy to see that upon the original install my intel 2200 wireless card worked just right with the OS but when i tried it out with wireshark it didnt see the card at all.   From what i've gathered from here and there, my problem was that the one size fits all driver works to get me online but i need the intel driver for linux to make it work with wireshark.

I've downloaded the tarball linux driver from intel, and from what i've read I now need to compile or configure or something like that in the terminal.  
So the basic problem is with the install of the driver, and i am totally lost.  I've just read Ubuntu for non-Geeks and my heads still underwater.

any help would be much appreciated.

Thanks 
-sean

---

### Post by hermes0710 on 2008-05-12
First of all you will need some packages installed. Run a terminal (a.-> <alt>+F2 and type "gnome-terminal" or b.-> Applications>Accessories>Terminal) and type:

```
sudo apt-get install build-essential
```.

Let's suppose you have you driver downloaded in /home/yourusername/Desktop.

In the console type:

```
cd /home/yourusername/Desktop
```

Let's also suppose your driver name is foo.tar.gz. You will unpack it running the following:

```
tar xvf foo.tar.gz
```

Logically a new folder must have been created with name "foo". Type ```
cd foo
ls
```

The ls command will give you the contents of the folder. There must be a README or INSTALL (or both) file in there so see it's contents by typing ```
cat INSTALL
``` or ```
cat README
``` accordingly.

These files containt info about installing the driver and you should proceed according to them.

Generally, what you do is: 

```
sudo ./configure
sudo make
sudo make install
```

Hope I gave you the basic picture of how you should proceed

---

### Post by breadlord on 2008-05-12
You say you've also got some drivers for your card working already, if that's the case then you're probably going to need to find out which driver (Generally called Kernel modules, or just "modules") are loaded for it, because you're going to need to "blacklist" them, which stops them from being loaded. Otherwise you're going to end up trying to stick the new ones on top of the old - which is going to cause you no end of problems...

Look up "kernel module blacklisting for ubuntu" and all will be well.

---

