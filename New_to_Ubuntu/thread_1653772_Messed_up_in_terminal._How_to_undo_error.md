---
title: "Messed up in terminal. How to undo error ?"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by grey1beard on 2010-12-27
In the course of installing a driver, I was following the **make config, config, make, make install** path, when my impatience (?) allowed me to type "make install", possibly before "make config" had finished.
The next lines in Terminal than threw "syntax error", followed by returning me to the module location I started with.

If I start again, will the system overwrite the same folders, or create duplicates with the possible problems that will make ?

John

---

### Post by seawolf167 on 2010-12-27
You should be ok to just run the commands again in the correct order. You can open the install file to read exactly what it does and where it places everything to be sure it overwrites, but I'd be willing to bet that it'll remove then copy or overwrite any existing files.

See [here ]("http://www.chemie.fu-berlin.de/chemnet/use/info/make/make_16.html")for a make example. This one looks like it cleans everything (removes, remakes the directory tree, then installs each time)

---

### Post by stmiller on 2010-12-27
There is no undo, unless that software creator has written something like 'make uninstall' or an uninstall script to remove the junk.

You should use [**checkinstall**]("https://help.ubuntu.com/community/CheckInstall") instead. checkinstall lets you compile from source and then gives you a little .deb at the end which you can easily install and easily uninstall.

```
sudo apt-get install checkinstall
```

Then do something like this when compiling:

```
./configure
make
sudo checkinstall
```

Then install the little deb it leaves right there:

```
sudo dkpg -i *.deb
```

You can easily remove that deb with apt or synaptic. 

Cheers,

---

### Post by grey1beard on 2010-12-27
Thanks good people :)

Seawolf - at least this is a clean install I'm building, so at worst a clean re-install wont be a major disaster, so I'll give it a try.

stmiller - that looks very useful. I've followed your link, and it seems to be something that I'll find a very useful method to learn.

Thanks both
John.

---

### Post by grey1beard on 2010-12-28
Just discovered that I need to be online to get checkinstall doh
Move desktop system downstairs to get wired lan connection in order to facilitate wireless connection upstairs. Ho hum.
Happy New Year all.

---

### Post by lkraemer on 2010-12-28
Also make sure you have build-essential and the linux headers installed.

Typically you need to install build-essential, and the headers for the
kernel you are running, if you are going to compile code.
```

uname -r

```
will tell you the kernel you are currently running.
```

sudo apt-get install build-essential linux-headers-$(uname -r)

```
will install the software needed to compile your code.


TYPICAL COMPILE STEPS: (from within your source directory)
```

cd /path/to/source
tar xvf packagename.tar.gz
cd /folder/of/extracted/source
./configure
make clean
make
sudo make install

```
"make clean" won't remove anything on the first compile, but will clean up
on a successive compile.

You can also use checkinstall to build a deb file.

REF:
[http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)


lk

---

### Post by grey1beard on 2010-12-28
Thanks Ik, I'll have another try when I've transferred both systems and restarted later this pm.
By the way, looking back I see that I haven't mentioned that the desktop I'm trying to set up has to be running Hardy Heron 8.04, so I hope that makes no extra problems !! It's only this laptop that is running 10.10
John.

---

### Post by grey1beard on 2010-12-28
Could you expand the last part of
**sudo apt-get install build-essential linux-headers-$(uname -r)**
I'm not clear on what the part after $ is. Or is it to be enterred as it is ?
Many thanks
John
EDIT OK worked it out, and carried it out, but it seems I already have the newest version !

---

### Post by matt_symes on 2010-12-28
Hi 

> Could you expand the last part of
sudo apt-get install build-essential linux-headers-$(uname -r)
I'm not clear on what the part after $ is. Or is it to be enterred as it is ?
Many thanks
John


Enter as is.

To see what it does open a terminal and type

```
matthew@matthew-laptop:/usr/bin$ echo linux-headers-$(uname -r)
```

produces (on my machine)

linux-headers-2.6.32-26-generic

so it will install linux-headers-2.6.32-26-generic among the others

Kind regards

---

### Post by grey1beard on 2010-12-28
Hi Matt, thanks for the post, and my regards to Bristol.
john

---

### Post by grey1beard on 2010-12-28
I now have checkinstall, build-essential, and linux-headers-$(uname -r), so I typed the instruction ./configure when in the source directory, as in - 

> john@fanshop:~/Desktop/driver/Module$ ./configure

and I got

> bash: ./configure: No such file or directory

??

---

### Post by grey1beard on 2010-12-28
I think I should end this thread as solved, as you guys have set me on a better path.
It's just unfortunate that my problem keeps shifting ;)

I now need to sort out a missing package, an rtai kernel(I think), so I'd best start another thread.
Many thanks all.
John

---

