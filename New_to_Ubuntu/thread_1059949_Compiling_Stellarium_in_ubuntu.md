---
title: "Compiling Stellarium in ubuntu"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by t4ggs on 2009-02-04
Hi, I've followed all the instructions here:

[http://stellarium.org/wiki/index.php/Compilation_on_Linux](http://stellarium.org/wiki/index.php/Compilation_on_Linux)

From getting all the dependencies to sudo make install and did it with out getting any errors, the problem is I don't know how to start the program, it's not under Applications, Education, Stellarium. And if I type stellarium I get..

The program 'stellarium' is currently not installed.  You can install it by typing:
sudo apt-get install stellarium
bash: stellarium: command not found

but if I do sudo apt-get install stellarium, it will install from the repositories that is an old version.

What should I do?

---

### Post by taurus on 2009-02-04
What's the output of this command from a terminal?

```
sudo find / -name stellarium -print
```

---

### Post by t4ggs on 2009-02-04
thank u it was /opt/mylocation/bin/stellarium

---

### Post by taurus on 2009-02-04
Then you need to add that directory to your path so you can just type stellarium any where to run it. 

Edit ~/.bashrc

```
gedit ~/.bahsrc
```
and add these two lines to the end of it.

```
PATH=$PATH:/opt/mylocation/bin
export PATH
```
Save it and exit gedit window.  Now run

```
source ~/.bashrc
stellarium
```

---

### Post by egrpioneer on 2009-03-29
> **taurus said:**
> Then you need to add that directory to your path so you can just type stellarium any where to run it. 

Edit ~/.bashrc

```
gedit ~/.bahsrc
```
and add these two lines to the end of it.

```
PATH=$PATH:/opt/mylocation/bin
export PATH
```
Save it and exit gedit window.  Now run

```
source ~/.bashrc
stellarium
```

Taurus - 
I'm over here on North Captiva killing time until it stops raining. I've gone thru the process, but still can't load anything except the old version.
Here's code for sudo find / -name stellarium -print

/opt/stellarium
/opt/stellarium/bin/stellarium
/opt/stellarium/share/stellarium
/usr/share/stellarium
/usr/share/stellarium/bin/stellarium
/usr/share/stellarium/share/stellarium
/home/steve/stellarium-0.10.2/po/stellarium
/home/steve/stellarium-0.10.2/builds/unix/po/stellarium
/home/steve/stellarium-0.10.2/builds/unix/src/stellarium

How is process different using above code.

Thanks in advance!!!

---

