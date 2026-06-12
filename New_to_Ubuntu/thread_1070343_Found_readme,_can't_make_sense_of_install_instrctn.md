---
title: "Found readme, can't make sense of install instrctns"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by Gelateria Punk on 2009-02-15
(SOLVED)
I'm trying to install Madfuload, whatever that is...I just need it.
I did finally get to the readme file, but don't know how to execute the instructions.  Could someone interpret the below and give me clear directions?  Thanks



Installing
----------

1) Run './configure'.

2) Run 'make'.

3) As root, run 'make install'.

---

### Post by golusweet on 2009-02-15
Go to Apps > Accessories > terminal

Enter these commands.

make sure you go to that folder of your game.

use cd to change directories.:P

---

### Post by Gelateria Punk on 2009-02-15
Yes, but what does it mean to run as root?

---

### Post by cariboo on 2009-02-15
It would be a lot easier if you went to System-->Aministration-->Synaptic Package Manager and installed the program, when you are aked for a password enter the one you created when you installed Ubuntu. Check this [Sticky]("http://ubuntuforums.org/showthread.php?t=801404"), it will answer a lot of your questions.

Jim

---

### Post by Nepherte on 2009-02-15
Cariboo's suggestion of installing is really the best way to do so, but for the sake of answering your question: running as root means you need to acquire root (read: admin) privileges for that specific command. This can be done by adding sudo in front of the command. In your case it would look like:
```
sudo make install
```
On a more general note, be careful with the sudo prefix. It basically means "I'm authoring you to do something that has system-wide effects".

---

