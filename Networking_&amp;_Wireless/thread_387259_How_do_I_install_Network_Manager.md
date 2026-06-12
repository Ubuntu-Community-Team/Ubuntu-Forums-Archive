---
title: "How do I install Network Manager"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by AnthonyJK@gmail.com on 2007-03-18
I have Network manager installed through synaptics but it always says im not connected even though I am. So I was wondering How do i go about installing this.

[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

---

### Post by AnthonyJK@gmail.com on 2007-03-18
Update: I download the .tar.gz file for the program.

I extracted it to my desktop. 

Opened terminal and "cd" into the directory "/home/anthonyjk/Desktop/NetworkManager-0.6.4"

Type ./configure (It prints off a lot of checks)

Type "make" and I get this error:
anthonyjk@AnthonyJK:~/Desktop/NetworkManager-0.6.4$ make
make: *** No targets specified and no makefile found.  Stop.
anthonyjk@AnthonyJK:~/Desktop/NetworkManager-0.6.4$ 


I look in the NetworkManager folder and I see two Makefiles. One is called "Makefile.in" and the other is "Makefile.am" but there is no just plain Makefile.

I'm not quite sure where to go from here anyhelp would be appreciated!

---

### Post by AnthonyJK@gmail.com on 2007-03-18
anyone?

---

### Post by drewcoll on 2007-03-18
try a "sudo apt-get install network-manager-gnome"

that should be easier than using the tarball.

---

