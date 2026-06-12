---
title: "problems installing emacs locally (non-sudoer user)"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by minsf on 2009-11-07
i'm trying to install emacs (23.1) in my home on a machine running ubuntu 9.04 for which i do not have root permissions (i'm not a sudoer).
[COLOR="Red"]question#1: is there a way to use apt-get to install something locally on my home, without root permissions?[/COLOR]
i'm guessing the answer is no. 

so i used 
```
tar -xvzf emacs-file.tar.gz
cd emacs-dir
./configure --without-x
make

```

the reason for the --without-x is that otherwise the configure complains that it cannot find the Gtk+ libraries.
[COLOR="red"]question#2: where are my Gtk+ libraries? how do i tell the configure to use them?[/COLOR]

assuming i don't care about X, and i use the above --without-x, the make produces an executable /home/minsf/emacs-dir/src/emacs
when i try to run it, it fails, and i get the following error:
```
emacs: Cannot open termcap database file
```
[COLOR="Red"]question #3(and most important): any clue how to get emacs to run?[/COLOR] thanks

---

### Post by yeats on 2009-11-07
> i'm trying to install emacs (23.1) in my home on a machine running ubuntu 9.04 for which i do not have root permissions (i'm not a sudoer).

Any reason the owner of the computer would object to your installing this?  Seems to me you should have that person do it, or ask them for sudo permissions.

---

### Post by minsf on 2009-11-07
> **chrissharp123 said:**
> Any reason the owner of the computer would object to your installing this?  Seems to me you should have that person do it, or ask them for sudo permissions.

that system has close to 200 users, so if i were they, i wouldn't give me sudo permissions... (i could very easily break something accidently);
by the time they approve my request to install emacs, i probably won't need it...
so thanks a lot for taking the time to respond, but i really am trying to install it locally on my user.
after all, multi-user should be one of the biggest advantages of linux/unix; so i should be able to install locally with no effect on the system/the other users, shoudn't i?

---

### Post by twisted_steel on 2009-11-07
This is what I found regarding the error you were getting:

[http://www.mail-archive.com/help-gnu-emacs@gnu.org/msg03547.html](http://www.mail-archive.com/help-gnu-emacs@gnu.org/msg03547.html)
[FONT=Verdana]
Either you have to install [/FONT][FONT=Verdana]"libncurses5-dev" (or the newest one) or run emacs from within screen.  Do you have access to screen by any chance?
[/FONT]

---

### Post by yeats on 2009-11-08
> multi-user should be one of the biggest advantages of linux/unix; so i should be able to install locally with no effect on the system/the other users, shoudn't i?

Even on multi-user systems, software installation is an administrative-level task...  Even a USB-drive installation of Ubuntu will allow you to install this sort of thing yourself and can run on nearly anything...  Those are just my suggestions though - feel free to keep going in the direction you're going. :-)

---

### Post by kurniawan11b on 2011-08-30
Hi dear. I'm absolute beginner to Ubuntu (and Unix-like OS). Now I'm installing 11.04. I have some problems regarding emacs installation. So to fix this problem, I can either install libcurese.lib or run emacs inside screen. Could anyone please explain how to "run emacs inside screen". Thanks you.

---

