---
title: "Geotagging and Eye of Gnome"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by Toddyboy on 2010-02-19
Hi all!

I am new to Ubuntu and love it, but sometimes I hit big brick walls, curse, and get scared I will return to windows (tho that's an empty threat - it will never happen)! :D

Can anyone help with my latest problem: I want to view geotagged photos in EOG.

I have read that you can install plugins for EOG, called Map. I tried to do so following the following pages advice:

[http://live.gnome.org/EyeOfGnome/Plugins](http://live.gnome.org/EyeOfGnome/Plugins)

However, I get this when I try to install it:

tae@Dark-Knight:~$ cd $HOME/.gnome2 
[EMAIL="tae@Dark-Knight:%7E/.gnome"]tae@Dark-Knight:~/.gnome[/EMAIL]2$ # ln -s . lib 
[EMAIL="tae@Dark-Knight:%7E/.gnome"]tae@Dark-Knight:~/.gnome[/EMAIL]2$ #
[EMAIL="tae@Dark-Knight:%7E/.gnome"]tae@Dark-Knight:~/.gnome[/EMAIL]2$ # git clone git://git.gnome.org/eog-plugins
[EMAIL="tae@Dark-Knight:%7E/.gnome"]tae@Dark-Knight:~/.gnome[/EMAIL]2$ cd eog-plugins
[EMAIL="tae@Dark-Knight:%7E/.gnome"]tae@Dark-Knight:~/.gnome[/EMAIL]2/eog-plugins$ ./autogen.sh --prefix=$HOME/.gnome2/
You need to install gnome-common from the GNOME Subversion
[EMAIL="tae@Dark-Knight:%7E/.gnome"]tae@Dark-Knight:~/.gnome[/EMAIL]2/eog-plugins$ 

Anyone able to give step by step help? from this point on.....I also get the following message when I try to install assocated packages. 

tae@Dark-Knight:~$ sudo apt-get install eog-dev python-gnome2-desktop-dev libexif-dev libexif-gtk-dev postr libclutter-0.8-dev libclutter-gtk-0.8-dev
Could not locate any suitable fingerprints matched with available hardware.
[sudo] password for tae: 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libclutter-0.8-dev
tae@Dark-Knight:~$ 

And have no idea how to install libchamplain-0.2 and libchamplain-gtk-0.2 from the [libchamplain download page]("http://projects.gnome.org/libchamplain/download") .... I tried!

Anyone able to help me?

Todd

---

