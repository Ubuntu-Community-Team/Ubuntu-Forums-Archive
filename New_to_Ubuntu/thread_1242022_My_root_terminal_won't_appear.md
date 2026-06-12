---
title: "My root terminal won't appear?"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by cat2005 on 2009-08-16
I just installed Ubuntu for the 1st time.  

I need to get into root terminal to do some stuff needed to install virtual box ([http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)).  I can get into synaptic but not into the root terminal.

I am in my 1st created account.  I place it in the "admin" group so it should have "sudo" access, shouldn't it?

I will try to attach a screenshot to show my meaning:

[http://img232.imageshack.us/img232/1099/rootterminal.png](http://img232.imageshack.us/img232/1099/rootterminal.png)

Look in the lower left corner.  You will see my mouse pointer next to the terminal.  When I click to bring access the terminal, nothing happens.

How do I fix this problem?

Thank you in advance.

---

### Post by wojox on 2009-08-16
Okay open a terminal from Applications > Accessories > Terminal

```
sudo apt-get update
```

```
sudo apt-get install virtualbox-ose virtualbox-ose-source

```

---

### Post by Buuntu on 2009-08-16
Unless you are doing lots of work needing root powers, I suggest using sudo instead.  To get into a "root terminal" you can type ```
sudo su
``` from your regular terminal (Applications > Accesories > Terminal).  
However, this can be dangerous because of the fact that it doesn't prompt you for your password, so you can do quite a bit of damage accidentally.

---

### Post by llamabr on 2009-08-16
I don't have any idea what you're trying to do.  That's a firefox window you've posted a picture to.  To open the terminal, do:

```
Applications>Accessories>Terminal
```

We're verboten from showing you how to have root access, but you can run any program with root access by beginning with sudo:

```
sudo nano /etc/fstab
```

---

### Post by Bachstelze on 2009-08-16
If you need a root shell, use [font=monospace]sudo -i[/font]. However, as wojox pointed out, you shouldn't need it since VirtualBox is available in the repositories.

---

### Post by cat2005 on 2009-08-16
Oh...I see....there is a "root terminal" and "terminal".  I thought those were 2 words for the same 1 thing.  I didn't know they were 2 separate things.  

I do not actually need "root terminal", just "terminal".

Problem solved.

Thanks!

---

### Post by Tyson D on 2009-08-16
I know when I installed root terminal under system tools it never worked so instead i simply used: 
$ sudo -s

---

### Post by Bachstelze on 2009-08-16
> **Tyson D said:**
> 
$ sudo -s

**DO NOT** do that. Use [font=monospace]sudo -i[/font].

---

### Post by earthpigg on 2009-08-16
> **HymnToLife said:**
> If you need a root shell, use [font=monospace]sudo -i[/font]. However, as wojox pointed out, you shouldn't need it since VirtualBox is available in the repositories.

virtualbox open source edition, from the repos, is handicapped intentionally.

virtual box from the Sun website, though not Free and Open Source Software, is a far superior product with superior functionality.

---

### Post by colau on 2009-09-01
> **Tyson D said:**
> I know when I installed root terminal under system tools it never worked so instead i simply used: 
$ sudo -s
Did you install root terminal from System>Administration>Synaptic Package Manager ?

---

### Post by cat2005 on 2009-09-01
SOLVED:  see post # 6

---

