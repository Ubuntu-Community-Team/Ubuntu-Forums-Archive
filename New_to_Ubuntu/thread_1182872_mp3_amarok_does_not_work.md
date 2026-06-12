---
title: "mp3 amarok does not work"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by cmaranhao on 2009-06-09
i am trying to listen to mp3 using amarok but i have an error message with some terminal commands.

i once installed mp3 in amarok using the following line but it does not work now:

> 
sudo apt-get install gstreamer0.10-plugins-ugly libxine-extracodecs

can someone give me a boost here?

---

### Post by murray92 on 2009-06-09
I'm not sure if this is what you're after but try it

[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)

If you have already done that, can you play mp3s in another program like rythmbox?

---

### Post by cmaranhao on 2009-06-16
> **murray92 said:**
> I'm not sure if this is what you're after but try it

[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)

If you have already done that, can you play mp3s in another program like rythmbox?

is does not work but i can listen to mp3 with rythmbox!! in amarok it gives me the following message:

> Amarok could not find any collection plugins. Amarok is now updating the KDE configuration database. Please wait a couple of minutes, then restart Amarok.
If this does not help, it is likely that Amarok is installed under the wrong prefix, please fix your installation using:
$ cd /path/to/amarok/source-code/
$ su -c "make uninstall"
$ ./configure --prefix=`kde-config --prefix` && su -c "make install"
$ kbuildsycoca4 --noincremental
$ amarok
More information can be found in the README file. For further assistance join us at #amarok on irc.freenode.net.

i need additional help

---

### Post by SuperSonic4 on 2009-06-16
I believe amarok uses the libxine-ffmpeg library. I can never remember the package name whether it is **libxine-ffmpeg** or **libxine1-ffmpeg** - Synaptic should tell you

---

### Post by LowSky on 2009-06-16
ubuntu
sudo apt-get install ubuntu-restricted-extras

kubuntu
sudo apt-get install kubuntu-restricted-extras

---

### Post by cmaranhao on 2009-06-16
> **SuperSonic4 said:**
> I believe amarok uses the libxine-ffmpeg library. I can never remember the package name whether it is **libxine-ffmpeg** or **libxine1-ffmpeg** - Synaptic should tell you

> **LowSky said:**
> ubuntu
sudo apt-get install ubuntu-restricted-extras

kubuntu
sudo apt-get install kubuntu-restricted-extras

tried both options and it still gives me

> Amarok could not find any collection plugins. Amarok is now updating the KDE configuration database. Please wait a couple of minutes, then restart Amarok.
If this does not help, it is likely that Amarok is installed under the wrong prefix, please fix your installation using:
$ cd /path/to/amarok/source-code/
$ su -c "make uninstall"
$ ./configure --prefix=`kde-config --prefix` && su -c "make install"
$ kbuildsycoca4 --noincremental
$ amarok
More information can be found in the README file. For further assistance join us at #amarok on irc.freenode.net.

i am with ubuntu 9.04

---

### Post by Amilo1718 on 2009-06-16
> **cmaranhao said:**
> i am with ubuntu 9.04
i thought amarok was KDE instead of gnome... [-o<

---

### Post by gn2 on 2009-06-16
Have you tried [Atunes]("http://www.atunes.org/") or Exaile yet?

---

### Post by cmaranhao on 2009-06-16
> **gn2 said:**
> Have you tried [Atunes]("http://www.atunes.org/") or Exaile yet?

no.. but it looks good although i have not seen the new amarok version..

can anyone help me install atunes?

---

### Post by gn2 on 2009-06-16
You just download the Deb Package (from the [Atunes Download Page]("http://www.atunes.org/?page_id=6")) to your desktop and double click it.

---

