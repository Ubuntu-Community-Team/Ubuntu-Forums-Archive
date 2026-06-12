---
title: "Determine apt-get repositories"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by WitchCraft on 2009-04-07
Hi, I'm currently trying red-flag linux (a red hat enterprise linux bases distro)

So far it works fine, but I already hate yum and want to get apt-get to work.
The problem is I don't have a list of repositories to add to /etc/apt/sources.list

How can I find out apt-get sources?

---

### Post by kellemes on 2009-04-07
Surely you have to ask this at the red flag community.
Ubuntu's repositories are not the ones you need anyway.

---

### Post by WitchCraft on 2009-04-07
> **kellemes said:**
> 
Ubuntu's repositories are not the ones you need anyway.

That I know ;)

---

### Post by WitchCraft on 2009-04-07
Oh, I found it, their community is under the category 'RED' - very intuitive...
:lolflag:

Dedusting & practising my few bits of Chinese language knowledge now ;-)))



Ay, it's fun :lolflag:

---

### Post by kellemes on 2009-04-07
> **WitchCraft said:**
> 
Dedusting & practising my few bits of Chinese language knowledge now ;-)))


At least you have some ;-)

---

### Post by WitchCraft on 2009-04-07
> **kellemes said:**
> At least you have some ;-)

Comes in handy for the first time ;-)

---

### Post by ibuclaw on 2009-04-07
Fedora doesn't use apt. The distro instead uses **yum**.

The configuration file, along with sources, can be found here:
```
/etc/yum.conf
```

Yum has a rather different interface to apt, and one that you may not be very familiar with.

However, you can install apt on fedora. To which details of transitioning yum sources to apt sources can be [found here]("http://www.brandonhutchinson.com/Fedora_apt_and_yum_repositories.html").

Regards
Iain

---

