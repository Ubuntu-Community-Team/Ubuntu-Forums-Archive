---
title: "XMMS in Karmic"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by comsparks on 2009-11-03
I was wondering if anyone has compiled XMMS to work in Karmic. I know that it is an old and non supported program but I still enjoy it. I had it working in Jaunty. I would like to stay with Karmic but will revert back if I can't get XMMS to work. Thank You

---

### Post by kellemes on 2009-11-03
Isn't [this]("http://www.pvv.ntnu.no/~knuta/xmms/") working?

---

### Post by comsparks on 2009-11-03
Thank you. I'm willing to learn but don't know how to compile yet. I'm not sure what the <arch> means and have done some research on it but still confused on it.

---

### Post by comsparks on 2009-11-03
I'm stuck in DEP Hell. I've spent two days solid trying to get this to work to no avail. I'm going back to Jaunty where everything seems to work. Thanks for all the help.

---

### Post by timwaters on 2009-11-03
Well I'm not sure why it says "[SOLVED]" I think it's pretty clear that the original poster did not solve their problem.

From this [http://www.pvv.ntnu.no/~knuta/xmms/](http://www.pvv.ntnu.no/~knuta/xmms/)
and using the instructions for Jaunty, since at time of writing there isn't something for Karmic

gives:
The following packages are BROKEN:
  xmms 
...
The following packages have unmet dependencies:
  xmms: Depends: libglib1.2ldbl (>= 1.2.10-18) which is a virtual package.
        Depends: libgtk1.2 (>= 1.2.10-4) which is a virtual package.

Has anyone managed to get xmms working with Karmic?

---

### Post by comsparks on 2009-11-03
I solved the problem by going back to Jaunty where everything now works the way I want it.

---

### Post by Tyke91 on 2009-11-03
comsparks

why not just use Audacious? It works the same as xmms (same playlists, even the same themes. Can also use winamp themes)

---

### Post by fawcetda on 2009-11-03
> **kellemes said:**
> Isn't [this]("http://www.pvv.ntnu.no/~knuta/xmms/") working?

Yes it works in Karmic !!
[http://www.pvv.ntnu.no/~knuta/xmms/](http://www.pvv.ntnu.no/~knuta/xmms/)

---

### Post by comsparks on 2009-11-03
Tyke91 XMMS plays everything I throw at it. I can record late night talk shows and store it in MP3 format and listen to them in the morning. I used audacious and didn't like it.

fawcetda I went to that page and ran into countless dependency issues trying to get the programs to work. If you got it working then my hats off to you.

Regardless I'm happy now and everything is working.

Thanks for all your responses.

---

### Post by zeus.jay on 2009-11-06
Comsparks you gave up too easily man



Guys to get xmms on karmic

Install jaunty versions of (for your architecture)

in order of install
libglib1.2ldbl_1.2.10-19build1
libglib1.2-dev_1.2.10-19build1

libgtk1.2-common_1.2.10-18.1build2_all.deb
libgtk1.2_1.2.10-18.1build2

Then install the jaunty version

[http://www.pvv.ntnu.no/~knuta/xmms/](http://www.pvv.ntnu.no/~knuta/xmms/)

Only thing I noticed it it didn't install a launcher in Sound & Video, Easy enough to call from temrinal or open music file with custom command xmms.

I'm sure someone can let us know how to create correct xmms.desktop file for it.

---

### Post by ihitf13anddied on 2009-11-08
Here are the steps I took to install XMMS on Karmic 64-bit. My XMMS is currently playing.

1. Add the necessary repositories:

```
deb http://www.pvv.ntnu.no/~knuta/xmms/karmic ./
deb-src http://www.pvv.ntnu.no/~knuta/xmms/karmic ./
```

2. GTK1.2 is broken in Karmic, we must fix that:

```
sudo apt-get build-dep libglib1.2-dev
```

```
apt-get -b source libglib1.2-dev
```

```
sudo dpkg -i libglib1.2-dev_1.2.10-19build1_*.deb libglib1.2ldbl_1.2.10-19build1_*.deb
```

```
sudo apt-get build-dep libgtk1.2
```

```
apt-get -b source libgtk1.2
```

```
sudo dpkg -i libgtk1.2_1.2.10-18.1build2_*.deb libgtk1.2-common_1.2.10-18.1build2_all.deb libgtk1.2-dev_1.2.10-18.1build2_*.deb
```

3. Next we rebuild XMMS

```
sudo aptitude install fakeroot
```

```
sudo apt-get build-dep xmms
```

```
sudo apt-get -b source xmms
```

4. Now that we have the support, we can install XMMS:

```
sudo dpkg -i xmms_1.2.11-1_amd64.deb
```

I think for 32-bit its the same except you replace 'amd64' in the line above with 'i386'. If someone has 32-bit you could verify...

Attached is a desktop shortcut for XMMS. Just extract the archive to your desktop or anywhere to have a launcher.

Good luck!

---

### Post by Paradigm_Shift on 2009-11-15
ihitf13anddied, thank you very much! I have a lot of music in .shn format and xmms is essential for me. I could not have succeeded in installing xmms without your help!

Quick note, I am not sure if a couple of the commands in your tutorial accidentally omitted "sudo" at the beginning. I used "sudo" successfully. Also, you are correct about the name of the 32-bit package.

For those who also want to play .shn files, you can easily compile a plugin for xmms.

First grab it from etree.org:
```
wget http://etree.org/shnutils/xmms-shn/dist/src/xmms-shn-2.4.1.tar.gz
```

Now, uncompress the file:
```
tar -xvzf xmms-shn-2.4.1.tar.gz
```

Now, go into the directory where the plugin source is located:
```
cd xmms-shn-2.4.1
```

Finally, compile the source:
```
./configure && make && sudo make install
```

For those who might want to add an icon for xmms, I found one here: [http://linuxcrazy.com/fluxboxfun/baricons/xmms.png]("http://linuxcrazy.com/fluxboxfun/baricons/xmms.png").

If you want to put the icon in /usr/share/pixmaps where most other application icons reside, open a terminal in the directory where you downloaded the xmms.png file and use the following command:
```
sudo cp xmms.png /usr/share/pixmaps/
```

Thanks again! You made my day!

---

### Post by sigurnjak on 2009-11-29
Thank you , very much folks ! Audacious was killing me and Streamtuner !
Life is good again !

---

### Post by ihitf13anddied on 2009-11-30
> **Paradigm_Shift said:**
> ihitf13anddied, thank you very much! I have a lot of music in .shn format and xmms is essential for me. I could not have succeeded in installing xmms without your help!

Quick note, I am not sure if a couple of the commands in your tutorial accidentally omitted "sudo" at the beginning. I used "sudo" successfully. Also, you are correct about the name of the 32-bit package.



You're very welcome. I can not live without my XMMS! I'm glad others made use of this guide. For those couple commands where I have omitted it, I do not believe that I needed sudo to properly run them. If someone could test this, please let me know and I will update the guide. Thank you for helping with the 32-bit package names Paradigm :D

---

### Post by sigurnjak on 2009-12-02
I s there a way for XMMS to use Pulse audio so when Flash playes in  FF it does not stop playing ?

It is just something audacious has no problem with .

---

### Post by ChEeZeBaLL on 2009-12-11
Thanks very much ihitf13anddied. I downloaded your shortcut and it works great, but any idea on how to make it have the official xmms program icon?

---

### Post by ihitf13anddied on 2009-12-13
> **ChEeZeBaLL said:**
> Thanks very much ihitf13anddied. I downloaded your shortcut and it works great, but any idea on how to make it have the official xmms program icon?

Please see my attachment, it has an XMMS icon.

---

### Post by WarrenSH on 2010-03-18
I have an error 

E: Unable to find a source package for libglib1.2-dev

---

### Post by shantiq on 2010-05-27
[B][COLOR="Blue"]hi guys big fan of xmms


to my mind the best of the pick   although qmmp is close behind and aqualung is sweet to me too

thanx for all the info


I have zipped and ed2k'ed all of the plugins for lossless formats here  ```
ed2k://|file|codecs%20for%20XMMS%20and%20EAC.zip|4025814|545CE4D43D87716EF857DD27DF628672|/
```

which you can grab through Amule in your synaptic

here is a picture of the content

[CENTER][IMG]http://img227.imageshack.us/img227/791/screenshot1ov.png[/IMG][/CENTER]

you need to place these into /home/yourname/.xmms/plugins


and most work straight off on reloading


if you cannot be bothered with ed2k drop me a line i shall email them to you (528KB) I am a huge fan of the shorten (here libshn.so) format which to my mind is clearer than all of the others

for shorten you also may need [==>xmms-shn-2.4.0.tar.gz]("http://www.sourcefiles.org/Multimedia/MP3/XMMS_Plugins/xmms-shn-2.4.0.tar.gz")

and for wavpack

ok wavpack is fine too you need [==>xmms-wavpack-1.0.2.tar.bz2]("http://www.hqshare.net/redirector.php?url=http%3A%2F%2Fftp.riken.go.jp%2Fpub%2FFreeBSD%2Fdistfiles%2FRESTRICTED%2Fxmms-wavpack-1.0.2.tar.bz2")
and to install it you need to first install libwavpack-dev from the synaptic
easy and might be what some of you want


Hope they are of use to some of you

Xmms Still the best   ps   many more plugins ====>[http://www.sourcefiles.org/Multimedia/MP3/XMMS_Plugins/]("http://www.sourcefiles.org/Multimedia/MP3/XMMS_Plugins/")

The cuefile one is an absolute beauty [xmms-cueinfo-0.2.0]("http://www.sourcefiles.org/Multimedia/MP3/XMMS_Plugins/xmms-cueinfo-0.2.0.tar.gz")


Shan[/COLOR][/B]

---

