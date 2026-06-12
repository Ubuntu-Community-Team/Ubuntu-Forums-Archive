---
title: "Disable Ubuntu password requests"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by ChadBJX on 2009-12-20
[SIZE=5]Hi,
I have difficulties with the keyboard & most often type using the Universal Keyboard. (a virtual on-screen keyboard where you type by clicking keys w/ the mouse) For me it's a pain having to enter a login password. Before upgrading to 9.10 no login password was needed. You can't enter that password using the [/SIZE][SIZE=5]Universal Keyboard. How can I disable that password request?

I would also, if possible, like to turn off the password prompt when installing software.

No one has acess to or uses this computer but me. I just don't need this much security.
Thanks,
Chad[/SIZE]

---

### Post by Merk42 on 2009-12-20
You can change your login to be automatic.
System > Administration > Login Screen

As far as needing a password to install software (and to do what I mentioned above).  That's by design, and I believe against the forum rules to provide a work around.

---

### Post by audiomick on 2009-12-20
Hallo. Can't help with the log-in, sorry.

Installing software has to be done as root. With Ubuntu, the default state is that you can't log in as root. Even if you could, it is extremely inadvisable (on any linux system) to work as root all the time. This would compromise much of the security of a linux system.

The mechanism in Ubuntu for doing things that require root privileges involves sudo
[http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo)
which is what makes the password request.
I am afraid you can't cancel the password request.

---

### Post by milosz.galazka on 2009-12-20
Password requests (for sudo/gksu) can be omitted.
Open gnome-terminal and enter
```
sudo su
```
Enter your password for the last time.
```
VISUAL=gedit visudo
```
at the end of file add line:
```
chad ALL=(ALL) NOPASSWD: ALL
```
Where chad is your user. Save and close. That's all.

---

### Post by danny4700 on 2009-12-21
I inistalled ubuntu some months ago.  Now I am trying to use it but I have no idea what my user ID and password are, hence can't get in.  How can I find it or disable it?
 
Dan Purrington
Tulane

---

### Post by milosz.galazka on 2009-12-21
> **danny4700 said:**
> I inistalled ubuntu some months ago.  Now I am trying to use it but I have no idea what my user ID and password are, hence can't get in.  How can I find it or disable it?
 
Dan Purrington
Tulane

Search for ubuntu single user mode -> [http://www.robertdepriest.com/2008/03/ubuntu-single-user-mode.html](http://www.robertdepriest.com/2008/03/ubuntu-single-user-mode.html)
You should start new topic ;p

---

### Post by estyles on 2009-12-21
Dan - you should really start a new thread instead of tacking on to this one.  FYI - the answer to your question will involve booting up in recovery mode, but I'm not sure of the exact steps.  You may want to search for "recovery mode".

---

