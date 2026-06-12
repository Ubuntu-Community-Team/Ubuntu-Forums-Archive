---
title: "Gparted having error of &quot;fatal server error: no screen detected&quot;"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by alfa_80 on 2011-08-15
Hi,

I want to use Gparted, unfortunately, I'm stuck with an error "fatal server error: no screen detected, bla2" I've been searching and trying workarounds from the internet  about 10 hours already, but, none of them is working for this problem..

Any thoughts?

---

### Post by snip3r8 on 2011-08-15
Try running gparted in terminal and posting the messages it prints out.

---

### Post by alfa_80 on 2011-08-15
> **snip3r8 said:**
> Try running gparted in terminal and posting the messages it prints out.

I would rather prefer to have GUI running since I'm just a newbie..the message is as I wrote previously..What is actually wrong with my machine visualization tool? Any prediction?

---

### Post by snip3r8 on 2011-08-15
Running it in the terminal still brings up gui but thats not whats important,whats important is that when you run programs in the terminal they print out alot more information about what is going wrong.

---

### Post by snip3r8 on 2011-08-15
run it as :
```
sudo gparted
```
in the terminal

---

### Post by alfa_80 on 2011-08-15
> **snip3r8 said:**
> Running it in the terminal still brings up gui but thats not whats important,whats important is that when you run programs in the terminal they print out alot more information about what is going wrong.

The problem is that I cannot type all of the lines(too long lines) or copy and paste it since I only can work on console on that machine, while I'm writing this thread using another machine..Any suggestion, how to still publish the output?

Thanks anyway..

---

### Post by alfa_80 on 2011-08-15
> **snip3r8 said:**
> run it as :
```
sudo gparted
```in the terminal

By using Gparted cd, it says: "(gpartedbin:2421): Gtk-WARNING **: cannot open display:"

Perhaps I've a problem with Gtk, am I right?

---

### Post by snip3r8 on 2011-08-15
what do you mean by "Gparted cd" ? are you running off an ubuntu live CD?

And you are probably right about the GTK problem

---

### Post by alfa_80 on 2011-08-15
> **snip3r8 said:**
> what do you mean by "Gparted cd" ? are you running off an ubuntu live CD?

And you are probably right about the GTK problem

It's just a live cd of gparted, it's not ubuntu live cd..Any opinion to resolve GTK problem?

---

### Post by snip3r8 on 2011-08-15
I would say there might be a problem with the gparted live cd,if u have an ubuntu cd somewhere ,try booting that and using gparted on there,i know the 9.10 live cd has gparted pre-installed on it,im not sure about the newer versions but you can have a look.

---

### Post by alfa_80 on 2011-08-18
> **snip3r8 said:**
> I would say there might be a problem with the gparted live cd,if u have an ubuntu cd somewhere ,try booting that and using gparted on there,i know the 9.10 live cd has gparted pre-installed on it,im not sure about the newer versions but you can have a look.

I've tried with another computer, the gparted CD just works fine, so the problem is nothing to do with the CD itself.

---

### Post by snip3r8 on 2011-08-18
the PC it doesnt work on may require a graphics driver to run it

---

### Post by alfa_80 on 2011-08-18
> **snip3r8 said:**
> the PC it doesnt work on may require a graphics driver to run it

Thanks anyway, I've just used Disk Utility on Mac to free the partition instead..

---

