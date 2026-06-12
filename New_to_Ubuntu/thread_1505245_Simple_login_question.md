---
title: "Simple login question"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by Fizzzy on 2010-06-08
Hello,
I was wondering if there was a way for ubuntu set up to start at the terminal, then go to the login screen (i'd have to type a certain CLI command to get to it.)
I swear I bookmarked a way to do this before, but I can't seem to find it :\

Thanks in advance!

---

### Post by pizza-is-good on 2010-06-08
I know that you can login to a terminal session, not a gnome one, but I'm not sure that you can do what you want. That sounds like a good security measure, but I don't think it exists.

I just realized however, that when you are using the terminal, it is always
```
yourusername@yourcomputername: -$
```, which makes me think that you would need to be logged in to use a terminal at all, so that you can have determined user privileges.

---

### Post by Windows Nerd on 2010-06-08
> **pizza-is-good said:**
> I know that you can login to a terminal session, not a gnome one, but I'm not sure that you can do what you want. That sounds like a good security measure, but I don't think it exists.

I just realized however, that when you are using the terminal, it is always
```
yourusername@yourcomputername: -$
```, which makes me think that you would need to be logged in to use a terminal at all, so that you can have determined user privileges.
Well, you could always login via the CLI, then startx to get to your normal stuff. I am sure there is a way to set Ubuntu to automatically boot to only a CLI.

---

### Post by Fizzzy on 2010-06-08
> **Windows Nerd said:**
> Well, you could always login via the CLI, then startx to get to your normal stuff. I am sure there is a way to set Ubuntu to automatically boot to only a CLI.

Thats exactly what I meant to say.


I tried one thing I found from googling:
```
sudo update-rc.d -f gdm remove
```
...and it didn't seem to work, hope it didn't screw anything up :X.

---

### Post by ssulaco on 2010-06-08
[http://www.linuxquestions.org/questions/ubuntu-63/booting-into-the-terminal-in-ubuntu-550831/](http://www.linuxquestions.org/questions/ubuntu-63/booting-into-the-terminal-in-ubuntu-550831/)

> While in the GUI (Gnome), I went to System>Administration>Services and un-checked "Graphical Login Manager." I'm sorry if the wording is not exact, but, with that, I re-booted and was greeted with a terminal screen. I loaded the X-server, by typing "startx." Hope that helps.

---

### Post by pizza-is-good on 2010-06-08
> **Windows Nerd said:**
> Well, you could always login via the CLI, then startx to get to your normal stuff. I am sure there is a way to set Ubuntu to automatically boot to only a CLI.

That's a good point. You're right, if you disable x, then you'll have a cli. You'd then have to start x from the cli, and then log in.

I have no idea how to go about it.... lol

---

### Post by drhrich on 2010-09-14
Hi, this whas managed in the old times whit the runlevels. Now ubuntu use upstart, but emulate the older behavior.

You could pass a number to the kernel in boot time to start only in cli mode, rescue mode, grafical mode, etc. The particular number is dependent in the distribution.

I think that runlevel 3 is cli. I google it, but not confirm myself.

Try edit de boot option via grub appending a number 3 to the kernel line. 

kernel  /boot/vmlinuz-2.6.17-11-386 root=/dev/sda1 ro quiet splash **3**

That must do the job. If work make the changes in the configuration of grub to make it permanent.

Bye

---

