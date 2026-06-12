---
title: "List of &quot;linked programs&quot;"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by tekal on 2011-03-15
Hi,
is it possible to get a list of programs that are installed and startable through the Terminal? For example: 

I can open a Terminal and type, kate or mcedit or vim or etc.pp. . So is there a list of all those "Terminal links" ?

Sorry that i have to post it here, but i dont really know what words to search for!

---

### Post by Hippytaff on 2011-03-15
Are you talking about just starting the application, or command line applications (ones thst don't use a GUI)?

---

### Post by tekal on 2011-03-15
No, im talking about this: 

A list of all Terminal commands that can start an application (GUI or non GUI, doesn't matter), but not things like ls, sudo, chown etc.(which are system commands).

---

### Post by ~Plue on 2011-03-15
you could use ```
*ls /bin/ /usr/bin/ /usr/sbin/
```* but that would call ls/chown since they too are executable binaries (you could try try removing /bin from the above and it'll remove the basic stuff)

---

### Post by oldos2er on 2011-03-15
A link is something specific on Linux: [http://www.thelinuxlink.net/lvlinux/resources/commands/ln.html](http://www.thelinuxlink.net/lvlinux/resources/commands/ln.html)

Type the first two or three letters of the app you want to run, then press Tab and the shell will show you what's available.

---

