---
title: "tar compilation"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2010-12-11
I was trying to install the xine lib files from tat.gz file, while trying to install through the konsole i got message after that i was not able to install it


[B]kevin@kevin-desktop:~/xine-lib-1.1.1$ make
make: *** No targets specified and no makefile found.  Stop.
kevin@kevin-desktop:~/xine-lib-1.1.1$ make makefile.in
make: *** No rule to make target `makefile.in'.  Stop.
kevin@kevin-desktop:~/xine-lib-1.1.1$ make install
make: *** No rule to make target `install'.  Stop.
kevin@kevin-desktop:~/xine-lib-1.1.1$ [/B]

I did the instructions give in the readme and install file pls help

---

### Post by qamelian on 2010-12-11
Is there some reason you need to install it this way, instead of just installing it from Software Center or Synaptic? Unless you have a very specific reason for compiling from source, you're usually better off sticking to the versions in the Ubuntu repositories.

---

### Post by 1991sudarshan on 2010-12-11
> **qamelian said:**
> Is there some reason you need to install it this way, instead of just installing it from Software Center or Synaptic? Unless you have a very specific reason for compiling from source, you're usually better off sticking to the versions in the Ubuntu repositories.

i do not have internet that is why i am trying this and any can you tell me from where can i get the codecs for playing mp3 file in amarok

---

### Post by oldos2er on 2010-12-11
> **1991sudarshan said:**
> i do not have internet that is why i am trying this and any can you tell me from where can i get the codecs for playing mp3 file in amarok

To compile xine, you'd still need to download its dependencies.

If you have access to another computer with internet, try Keryx: [http://keryxproject.org/](http://keryxproject.org/)

---

### Post by khelben1979 on 2010-12-11
To be able to compile the source code using the make command, you haveto start with **./configure** first. The ./configure command starts a process where it checks your system for installed libraries which is needed by the configure script.

If you're an Ubuntu newbie, you should stick with what is provided by the [Ubuntu Software Center]("http://en.wikipedia.org/wiki/Ubuntu_Software_Center") as has been suggested in this thread.

---

### Post by nothingspecial on 2010-12-11
To make, you need a make file. Is there one?

Because your output says

```
no makefile found
```Is there a README file?

Also, if you do not have an internet connection, it is much better to download the debs from here

[http://packages.ubuntu.com/maverick/](http://packages.ubuntu.com/maverick/)

Anything you do download will need the dependencies (red dot next to them), then you have to check the dependencies for dependencies and so on and so on forever until you decide to go to an internet cafe :)

And it dawns on you why they developed package managers in the first place......

---

