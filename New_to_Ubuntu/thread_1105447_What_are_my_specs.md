---
title: "What are my specs?"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by listerdl on 2009-03-24
Hi, how do I find out what graphics card and other specs that my machine is running? thanks

---

### Post by UbuntuNerd on 2009-03-24
try System Info in a terminal type this:
```
sudo aptitude install sysinfo
```
after you install it you can find it by going to Applications > System Tools > Sysinfo it should display just about all the info you need.

---

### Post by listerdl on 2009-03-24
AMAZING reply....thanks...... :)

---

### Post by mvalviar on 2009-03-24
On the terminal type ```
lshw -html > spec.html
```. You'll have an html file on your current working directory that you can view on you browser which is nicely formatted for you convenience.

Cheers!

---

### Post by listerdl on 2009-03-24
> **mvalviar said:**
> On the terminal type ```
lshw -html > spec.html
```.....You'll have an html file on your current working directory...................



Can I ask you what you mean by 'directory'? Sorry just that i am still learning the basics with ubuntu, (I have it working very nicely but I still dont really get what is going on under the hood...

---

### Post by mvalviar on 2009-03-24
> **listerdl said:**
> Can I ask you what you mean by 'directory'? Sorry just that i am still learning the basics with ubuntu, (I have it working very nicely but I still dont really get what is going on under the hood...

The terminal is under Applications>Accesories. When launched it points to your home directory. So when you issue that command the "spec.html" file it creates lands on your home directory/folder.

Added: On a side note. The the string of characters you see before the cursor on the terminal is the prompt. Its to be read as ```
<name of user>@<name of machine>:<current working directory>$
```. So when you launch a terminal the current working directory is '~' which equivalent to your home directory/folder or /home/<name of user>.

---

### Post by UbuntuNerd on 2009-03-24
you can also try this commands in a terminal:
specific graphic card model
```
lspci | grep VGA
```
graphics card vendor
```
glxinfo | grep vendor
```
details about the Xserver, and your graphics card
```
glxinfo
```
also
```
lspci
```

---

### Post by lisati on 2009-03-24
> **listerdl said:**
> Can I ask you what you mean by 'directory'? Sorry just that i am still learning the basics with ubuntu, (I have it working very nicely but I still dont really get what is going on under the hood...

A "directory" in Ubuntu corresponds to a "directory" in Windows. It's also known as "folder", and is a convenient place to group related files together on your computer's file system.

Have a look here for a more detailed explanation: [http://en.wikipedia.org/wiki/Directory_(file_systems](http://en.wikipedia.org/wiki/Directory_(file_systems))

---

### Post by spcwingo on 2009-03-24
You can also type in the terminal:

```
sudo lshw
```

It'll output the results in the terminal window.

---

