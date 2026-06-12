---
title: "How to uninstall a app installed from source"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by madu on 2009-02-02
Hello,

recently I installed the nvclock 0.8(beta) from source. I am not very linux savvy and I used the readme to install it. It installed fine and worked fine. I am not sure if it is because of this, but after using nvclock to change fan/clock/memory of my GTX260, I have been having quite a bit of problems. Firstly, my Nvidia drivers seized to work giving me a x-server error in the boot up and starting in low-graphics mode. And finally yesterday when I shut down, it went in to a long beep and when I manually restarted, all my bios settings were gone. Very strange and although I dont think nvclock caused this, I have been having zero problems until I installed it. So now I want to get rid of it.

I used ./autogen.sh -> make -> make install, to install the nvclock. Now I want to know how to uninstall it.. please advice.

Thank you very much.

---

### Post by taurus on 2009-02-02
Go into the directory where you ran the **sudo make install**, now you just run

```
sudo make uninstall
```

---

### Post by shifty_powers on 2009-02-02
[http://ubuntuforums.org/showthread.php?p=6528685](http://ubuntuforums.org/showthread.php?p=6528685)

will give you some pointers...

---

### Post by madu on 2009-02-02
Thanks a lot guys.
But for some reason I cannot seem to find that directory. I distinctly remember I put the contents in /tmp. Even history says that I have put invoked the make from there. But the folder is not there anymore.
Is it possible for me to download the source files again and run uninstall?

cheers.

---

### Post by taurus on 2009-02-02
Stuff in /tmp will get deleted upon boot so if you saved your stuff in there, it's bye-bye baby.

Yes, you need to download the same version and run through all the step except instead of running **sudo make install**, you would run **sudo make uninstall**, assuming you use the default settings.

---

### Post by madu on 2009-02-02
Thanks taurus..
just to be clear and not to mess up, I do until 'make' right?
and do 'make uninstall' instead of 'make install'?

---

### Post by madu on 2009-02-02
So I did the make unistall, and it did remove some files.. but seems the cpmmand is still working.. what gives guys?

here is the output:

[B]/tmp/nvclock0.8b4$ sudo make uninstall
removing /usr/local/share/doc/nvclock/ABOUT
removing /usr/local/share/doc/nvclock/AUTHORS
removing /usr/local/share/doc/nvclock/ChangeLog
removing /usr/local/share/doc/nvclock/FAQ
removing /usr/local/share/doc/nvclock/README
rm -f /usr/local/man/man1/nvclock.1
echo "removing $mandir/man1/nvclock.1" ; \

removing /man1/nvclock.1
rm -f /usr/local/share/applications/nvclock.desktop
echo "removing $prefix/share/applications/nvclock.desktop" ; \
	rm -f /usr/local/share/icons/hicolor/48x48/apps/nvclock.png
removing /share/applications/nvclock.desktop
echo "removing $prefix/share/icons/hicolor/48x48/apps/nvclock.png" ; \

removing /share/icons/hicolor/48x48/apps/nvclock.png
make -C src uninstall
make[1]: Entering directory `/tmp/nvclock0.8b4/src'
make[2]: Entering directory `/tmp/nvclock0.8b4/src/backend'
make[2]: Nothing to be done for `uninstall'.
make[2]: Leaving directory `/tmp/nvclock0.8b4/src/backend'
make[2]: Entering directory `/tmp/nvclock0.8b4/src/nvcontrol'
make[2]: Nothing to be done for `uninstall'.
make[2]: Leaving directory `/tmp/nvclock0.8b4/src/nvcontrol'
make[2]: Entering directory `/tmp/nvclock0.8b4/src/gtk'
make[2]: `uninstall' is up to date.
make[2]: Leaving directory `/tmp/nvclock0.8b4/src/gtk'
make[2]: Entering directory `/tmp/nvclock0.8b4/src/qt'
make[2]: `uninstall' is up to date.
make[2]: Leaving directory `/tmp/nvclock0.8b4/src/qt'
rm -f /usr/local/bin/smartdimmer
make[1]: Leaving directory `/tmp/nvclock0.8b4/src'[/B]

when I try $nvclock, it still works.. :(

---

### Post by madu on 2009-02-02
Sorry for bumping this up.
But really need help on this fellas... :(

---

### Post by taurus on 2009-02-02
Remember, **sudo make uninstall** is not the magic pill.  Sometimes it works; sometimes it doesn't.  It all depends on who wrote the Makefiles.  Therefore, you have to go in an remove it by hand.

See if it is still on your machine, the binary.

```
whereis nvclock
-or-
sudo find / -name *nvclock* -print
```

---

### Post by AlucardArg on 2009-02-02
I'm new in Linux too, and I'm now starting to understand installs, configuring, sources, and stuff...
Anyway, just a thought:
Go to Synaptic, and look if what you installed is there. If it is, right click it, and do a complete removal.
Or, a quick way to check if you have packages installed, is to open a terminal, and do "dpkg -s [package_name]"


Or, now I remember... Try to do:
$apt-get purge nvclock
That'll remove it completely.

---

### Post by handydan918 on 2009-02-02
> **AlucardArg said:**
> I'm new in Linux too, and I'm now starting to understand installs, configuring, sources, and stuff...
Anyway, just a thought:
Go to Synaptic, and look if what you installed is there. If it is, right click it, and do a complete removal.
Or, a quick way to check if you have packages installed, is to open a terminal, and do "dpkg -s [package_name]"


Or, now I remember... Try to do:
$apt-get purge nvclock
That'll remove it completely.

Programs installed form source, or any other way not involving the package manager usually aren't known to the package manager. 
That's why it's best to stick with the package manager...

---

### Post by igknighted on 2009-02-02
There is a version of nvclock in the repos, I bet a lot of the files are named the same.  You could install that one, which would likely overwrite much of your current install, then run 'sudo apt-get remove --purge nvclock' to completely remove it.

BTW... it sounds like you may have clocked your GPU too high so it is becoming unstable, be it from heat or whatever else.  I would be careful and make sure that the changes you made are in fact undone by removing the program, and not stored on the card's bios or something.

EDIT: Next time you install from source, instead of 'make install' for the last step, try installing the package checkinstall and using 'make checkinstall'.  This will make a quick deb package and install it via dpkg, making removal a breeze, and making the package system aware that you installed it.

---

### Post by madu on 2009-02-02
Thanks a lot guys.
I'm not at the pc right now.. will try it soon as I got home..


> **igknighted said:**
> 

BTW... it sounds like you may have clocked your GPU too high so it is becoming unstable, be it from heat or whatever else.  I would be careful and make sure that the changes you made are in fact undone by removing the program, and not stored on the card's bios or something.


Actually I underclocked it. Because I don't do any gpu intensive apps I wanted to lower the clocks to reduce heat and necessary power.
I do hope nvclock didnt mess up anything internally.. it works fine and shows the correct clocks in XP.. I guess its ok...

Thanks a lot again guys..

---

### Post by madu on 2009-02-03
I tried installing from Synapting and running 'sudo apt-get remove --purge nvclock".. but its still there...

what should I do guys? :(

here is the output of where the files are:

[B]@desktop:~$ sudo find / -name *nvclock* -print
/var/cache/apt/archives/nvclock_0.8b3-1ubuntu1_i386.deb
/var/cache/apt/archives/nvclock-gtk_0.8b3-1ubuntu1_i386.deb
/var/cache/apt/archives/nvclock-qt_0.8b3-1ubuntu1_i386.deb
/home/madu/.nvclock
/home/madu/Desktop/nvclock0.8b4.tar.gz
/usr/local/bin/nvclock
/usr/local/share/doc/nvclock
[/B]

Any suggestions...

---

### Post by taurus on 2009-02-03
> **madu said:**
> I tried installing from Synapting and running 'sudo apt-get remove --purge nvclock".. but its still there...

what should I do guys? :(

here is the output of where the files are:

[B]@desktop:~$ sudo find / -name *nvclock* -print
/var/cache/apt/archives/nvclock_0.8b3-1ubuntu1_i386.deb
/var/cache/apt/archives/nvclock-gtk_0.8b3-1ubuntu1_i386.deb
/var/cache/apt/archives/nvclock-qt_0.8b3-1ubuntu1_i386.deb
/home/madu/Desktop/nvclock0.8b4.tar.gz
/usr/local/bin/nvclock
/usr/local/share/doc/nvclock
[/B]

Any suggestions...

I assume you have removed it (using synaptic) from your machine.  Then, you need to remove the binary in /usr/local/bin/nvclock since that is the version that you installed from source.

```
sudo rm /usr/local/bin/nvclock
```
You can also remove the nvclock directory in /usr/local/share/doc too if you wish.

```
sudo rm -rf /usr/local/share/doc/nvclock
```
And of course, you should remove the nvclock's config file from your $HOME.

```
rm -rf ~/.nvclock
```

---

### Post by madu on 2009-02-03
Thanks a lot taurus..
I used 'apt-get remove --purge' to remove after installing from Synaptic.. when I went to Synaptic the packages are removed...

There are some .deb files left in /cache but I guess thats alright..

Thanks a lot mate..
Cheers.

---

### Post by taurus on 2009-02-03
You can clean out the cache too if you wish.

```
sudo apt-get clean
```
You can also remove the download file that you saved to your desktop.

```
rm ~/Desktop/nvclock0.8b4.tar.gz
```
Now, there shouldn't be any trace of nvclock on your machine.

---

### Post by XanTrax on 2009-02-03
> **taurus said:**
> Go into the directory where you ran the **sudo make install**, now you just run

```
sudo make uninstall
```

Ive seen "make uninstall" with no target 'uninstall' in 'make' plentyyy of times lol.  I havent had one thats been able to "make uninstall clean" in awhile, usually only on FreeBSD I have seen that as a standard.

---

### Post by madu on 2009-02-03
Thanks guys..
Emptied the trash too and no trace of nvclock anywhere  :)

Cheers for all the help fellas...

---

