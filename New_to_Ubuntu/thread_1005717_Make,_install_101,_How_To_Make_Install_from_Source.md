---
title: "Make, install 101, How To Make Install from Source, General Understanding"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by cwmoser on 2008-12-08
I think I am a little unclear on the basic methodology of installing software from source.

I found a new network-manager-pptp at:

[https://edge.launchpad.net/ubuntu/in...ubuntu1.8.10.1](https://edge.launchpad.net/ubuntu/in...ubuntu1.8.10.1)

How do you make this and install it?

In the archive I can see files like configure.in, INSTALL, Makefile.am, nm-pptp-service.conf, nm-pptp-service.name.in, and nm-pptp.desktop.in

Just running make or configure don't seem to work.

I'm a little unclear on the process of installing packages like this.

Thanks

Carl

---

### Post by taurus on 2008-12-08
Just look at the INSTALL to see what you have to do.

```
more INSTALL
```
And by the way, the link doesn't work because it has ... in it.

---

### Post by jmontelius on 2008-12-08
There is often a script called "configure", this script will check for needed software and create a file called "Makefile". In this process it will use skeleton files such as Makefile.am etc. Once you have a Makefiel you kan call the make command and it will use the content of the Makefile to compile all code etc. You can often give argumnets to the make command such as #make install" that will take the compiled binaries and copu them to /usr/bin/ or whatever.

Well that was the one minute answer.

And seeing that yiu have a Makefile.am I guess you should firts do a automake.

---

### Post by Sealbhach on 2008-12-08
Download the source tar.gz, extract and cd into the newly created folder.

The three stages are usually:

```
./configure
```

Checks for dependencies.

```
make
```

Builds the binary package.

```
make install
```

Installs.

Please anyone feel free to correct me if I'm misunderestimating my knowledge.:p


.

---

### Post by taurus on 2008-12-08
> **Sealbhach said:**
> 
```
make install
```

Installs.

Please anyone feel free to correct me if I'm misunderestimating my knowledge.:p


You need to include the _sudo_ in front to install it unless you specifically tell it to install to your own $HOME in ./configure.

---

### Post by Keith Hedger on 2008-12-08
most installs go to /usr/local/bin (unless you tell it to install elsewhere) so you probably need to use```
sudo make install
```
if there is a file called autogen.sh then run that```
./autogen.sh
``` and that will build your configure script that you can then run etc etc

---

### Post by nhasian on 2008-12-08
before you can build debian packages you need to install the build essentials

```
sudo apt-get install build-essential
```

---

