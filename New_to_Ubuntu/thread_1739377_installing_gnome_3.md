---
title: "installing gnome 3"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by skyzthelimit230 on 2011-04-25
I know this may be a bit premature right now, but I was wondering if it will be possible to install Gnome on ubuntu 11.04, or if there will be a gnome edition of ubuntu?

I've tried unity for a while and I don't really like it.

---

### Post by maverick555 on 2011-04-26
gnome 3 is a bit buggy in ubuntu right now.you have to wait till 11.10.If you desperately need to check out gnome 3 you should go with fedora 15.I used it for a while and i would rather stick with ubuntu.Also 11.04 is not yet released.

---

### Post by Krytarik on 2011-04-26
If you really want to try Gnome 3 on Natty 11.04, see here:
[http://www.omgubuntu.co.uk/2011/04/gnome-3-released-to-be-available-for-ubuntu-11-04-via-ppa/](http://www.omgubuntu.co.uk/2011/04/gnome-3-released-to-be-available-for-ubuntu-11-04-via-ppa/)
[http://ubuntuforums.org/showthread.php?t=1725221](http://ubuntuforums.org/showthread.php?t=1725221)

Greetings.

---

### Post by wolfen69 on 2011-04-26
What I do is install xubuntu 11.04 and put gnome 3 on top of it. Gnome 3 has no conflicts with xfce and works perfectly.
```
sudo add-apt-repository ppa:gnome3-team/gnome3
```
then
```
sudo apt-get update
```
then
```
sudo apt-get dist-upgrade
```
then
```
sudo apt-get install gnome-shell
```
then log out and select gnome shell session, then log in.

---

