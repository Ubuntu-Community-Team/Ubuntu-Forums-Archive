---
title: "Need a translation, please."
date: 2011-07-12
forum: New to Ubuntu
---

### Post by Inodoro Pereyra on 2011-07-12
I'm trying to install emc2 in my computer. I'm running Ubuntu 10.04.

In the install instructions, it says:

> The build process follows the standard Linux convention:

From the top level directory, switch to the source directory:

cd src

In the source directory, build EMC2:

./configure
make clean
make
sudo make install

Afterwards you need to issue 'emc' and you'll get emc2 running.


Now, I'm pretty sure all that will be perfectly clear for most of you guys, but, for me, it may as well be written in Swahili.
I've tried running those instructions on the terminal, with no luck. Can anybody please guide me?

Thanks in advance. :)

---

### Post by realzippy on 2011-07-12
Why do you want to compile it yourself?
There are precompiled packages for 10.04 out there:

[http://wiki.linuxcnc.org/emcinfo.pl?Installing_EMC2#On_Ubuntu_10_04_using_precompiled_EMC2_packages](http://wiki.linuxcnc.org/emcinfo.pl?Installing_EMC2#On_Ubuntu_10_04_using_precompiled_EMC2_packages)

---

### Post by dcsoldschool53 on 2011-07-12
> **Inodoro Pereyra said:**
> I'm trying to install emc2 in my computer. I'm running Ubuntu 10.04.

In the install instructions, it says:



Now, I'm pretty sure all that will be perfectly clear for most of you guys, but, for me, it may as well be written in Swahili.
I've tried running those instructions on the terminal, with no luck. Can anybody please guide me?

Thanks in advance. :)

What it is says is, in a terminal, ```
cd ~/src
``` which means, you are going to change to the directory called src. Once you are in the directory or folder src, you type the command.```
./configure
```Let the command finish running until it returns to a command prompt. Then, type the command```
make clean
```Let it finish running too. Now type```
make
```Let it finish doing its thing like the first two commands.```
sudo make install
```It is the last one. Now, type in a password. Let it run, and now you will be finished. The program should now be installed. Remeber everything is done in a terminal.

---

### Post by realzippy on 2011-07-12
@dcsoldschool53

cd ~/src
will give him a "no such file or directory" error.
Also compiling EMC needs a few more things,like adding the
*linuxcnc repository* to the sources.list,check if universe is enabled,
install build-dep,git for updates,aso.
The install.sh script might be much easier.

---

### Post by dcsoldschool53 on 2011-07-12
> **realzippy said:**
> @dcsoldschool53

cd ~/src
will give him a "no such file or directory" error.
Also compiling EMC needs a few more things,like adding the
*linuxcnc repository* to the sources.list,check if universe is enabled,
install build-dep,git for updates,aso.
The install.sh script might be much easier.

I put it like that because I don't know if the directory is in home, Downloads, Desktop, or etc. he could also do it this way ```
cd /home/user-name/src
```if he wants too. As long as he knows where he put the folder.
 I would rather have him find a .deb file to download, instead of doing it from source any day.

---

### Post by dcsoldschool53 on 2011-07-12
he could also get it from Synaptic Package manager.
[B]
By the way, at **Inodoro Pereyra where is your src folder located.**[/B]

---

### Post by realzippy on 2011-07-12
I know,I was not referring to the "~/".
But src will be inside the downloaded source package (likely emc2-dev),
so cd ~/src won't find it,and I am not sure if OP knows to navigate there before..
Of course your "translation" is correct...

---

### Post by dcsoldschool53 on 2011-07-12
> **realzippy said:**
> I know,I was not referring to the "~/".
But src will be inside the downloaded source package (likely emc2-dev),
so cd ~/src won't find it.
I see what you mean, but he posted cd src in his first post. I took it at face value as changing into another directory. What I do know is, that if he downloads emc2, it will create a folder called emc2, in which you would cd into.

---

### Post by Inodoro Pereyra on 2011-07-12
Thank you both for taking the time.

Realzippy: I didn't really "want" to compile it myself. That's what I found.
Actually, not only I didn't know I was trying to compile it, but I don't have a clue what compiling is...:oops:

dcsoldschool53: I followed your instructions. It took some doing, to find the right path, but finally I got it. Everything went well, until I executed the last instruction. Once I put my password, I got this:

> install -d -m 0755 -o root  /usr/realtime-2.6.24-16-rtai/modules/emc2 \
        /usr/bin \
        /etc/emc2
install -m 0644 -o root ../rtlib/*.ko /usr/realtime-2.6.24-16-rtai/modules/emc2
install: cannot stat `../rtlib/*.ko': No such file or directory
make: *** [install-kernel-dep] Error 1

And the program still doesn't show up in the Applications menu.
What did I mess up?

---

### Post by Inodoro Pereyra on 2011-07-12
Ok, done! :D

Realzippy: I followed the link you posted, installed it, and everything is working perfectly.

Thank you both again for the help. :D

---

