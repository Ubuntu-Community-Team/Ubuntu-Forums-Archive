---
title: "How to run .deb and tar.gz packages?"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by cblnchat on 2011-02-23
Kind of a noob question...but how do i run .deb and tar.gz packages??  I just downloaded the .deb level maker for xmoto and the tar.gz xmoto packages and i have no idea how to run them or make them work or install. plz help

Thanks

---

### Post by oldos2er on 2011-02-23
Double-click the *deb file to install. For the tar.gz, you'll need to extract it and tell us whether it contains source code or something else. There may be a README file to guide you.

---

### Post by seawolf167 on 2011-02-24
Like oldos2er said, just double click the .deb to run it.

tar.gz is simply a file archive (think .zip). If the file archive contains source code for compilation, then the general form of what you'll have to do is below (note to always read the READMEs as the commands can vary)

Open a terminal, Applications -> Accessories -> Terminal

browse to the file location

```
cd /location/of/filename.tar.gz
```the default firefox download location is

```
cd ~/Downloads
```extract the file

```
tar -zxvf filename.tar.gz
```cd to the created directory

```
cd filename/
```install the package

```
./configure
make
sudo make install
```

---

### Post by midjie on 2011-09-23
i try it,but still wont't work.here is my terminal status:

```
configure: error: "sqlite3 required"
username@ubuntu:~/Downloads/xmoto-0.5.7$ make
make: *** No targets specified and no makefile found. Stop.
username@ubuntu:~/Downloads/xmoto-0.5.7$ sudo make install
[sudo] password for username: 
xxxxxxx
Sorry, try again.
[sudo] password for username: 
make: *** No rule to make target `install'. Stop.
username@ubuntu:~/Downloads/xmoto-0.5.7$ 

```

and then I blurr out.please give me an idea how yo solve this.
p/s step-by-step please...

---

### Post by David Andersson on 2011-09-24
> **midjie said:**
> i try it,but still wont't work.


1) You should have started a new thread for your particular problem.

2) What do you really want to do? Compile the latest xmoto, or just install and have fun running the latest xmoto?

In the later case there is a .deb for ubuntu on the xmoto site [http://xmoto.tuxfamily.org/](http://xmoto.tuxfamily.org/) (download and double click the .deb file).

Or alternatively, there is a PPA with xmoto 0.5.7 (latest official) and another PPA with xmoto 0.5.8 (development version). See [https://launchpad.net/~x-moto-developers/+archive/releases](https://launchpad.net/~x-moto-developers/+archive/releases) (there is a link to instructions from that page)

(If you just want any xmoto, then xmoto 0.5.2 is in the Ubuntu Software Center.)

---

### Post by midjie on 2011-09-24
i've try the developer's site for your information.in fact,i got it from there.i know that xmoto is available in USC.but bcoz i've already dowloaded the package,i don't bother the one in the USC.but,nevermind...installed it already with the USC.now i have to delete the package filke in my folder.maybe bcoz i'm using Unity that i encountered this problem.can't wait for ver 11.10.

---

### Post by MG&amp;TL on 2011-09-24
..."maybe it's because I'm using Unity" Unity is just an interface, you have issues with package management and/or compiling from source, that would have happened in GNOME. Just saying. And I'm afraid Unity's in 11.10 too. :)

---

### Post by David Andersson on 2011-09-24
> **midjie said:**
> maybe bcoz i'm using Unity that i encountered this problem.can't wait for ver 11.10.

No, it was because you downloaded the source code and tried to compile it. It can be done, but requires more preparation. It is easier to install a .deb-file. Even easier is to install from the Software Center.

If you do exactly the same in 11.10 you will get the same error message.

Always first check in the Software Center (or in Synaptic) if the program you want is there.

(It's one of the most important differences between Linux and Windows. The "normal" way to install programs in Ubuntu, and many other Linuxes, is to use the built in package management and its software repository. It is not "normal" to search the internet and then download things. Compare with AppStore and AndroidMarket for phones, it's the same idea. You don't download things like in Windows there either.) (Isn't there an intro with this piece of info somewhere?)

---

