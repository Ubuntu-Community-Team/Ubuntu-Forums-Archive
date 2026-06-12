---
title: "How do I stop ubuntu asking me for the CD when downloading apps.?"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by Robert Buckmaster on 2010-06-22
Hi.

I've just recently installed Ubuntu 10.04 on my laptop, which doesn't have a CD player. On my attempting to download new apps., however, the system asks me to insert the ubuntu CD into the disk drive. How do I disable this prompt so that I may download the aps from the internet instead of from the CD? I should prefer to solve the problem using the visual interface, and without altering the source code.

Thanks!

Rob

---

### Post by Robert Buckmaster on 2010-06-22
Hi.

I've just recently installed Ubuntu 10.04 on my laptop, which doesn't  have a CD player. On my attempting to download new apps., however, the  system asks me to insert the ubuntu CD into the disk drive. How do I  disable this prompt so that I may download the aps from the internet  instead of from the CD? I should prefer to solve the problem using the  visual interface, and without altering the source code.

Thanks!

Rob

---

### Post by wilee-nilee on 2010-06-22
Go to system-admin software sources and tick the from cd off in the first tab.

---

### Post by Robert Buckmaster on 2010-06-22
I ticked the box in the first tab under 'Installable from the CD-ROM/DVD'. But on closing the window the system said the information about available software was out-of-date and had to be reloaded. I clicked 'Reload'. Then an error came up saying the repository could not be downloaded owing to nework problems. I am at a library. I wonder if the wifi here won't let me download the repository, or something else is the problem.

---

### Post by wilee-nilee on 2010-06-22
> **Robert Buckmaster said:**
> I ticked the box in the first tab under 'Installable from the CD-ROM/DVD'. But on closing the window the system said the information about available software was out-of-date and had to be reloaded. I clicked 'Reload'. Then an error came up saying the repository could not be downloaded owing to nework problems. I am at a library. I wonder if the wifi here won't let me download the repository, or something else is the problem.

Hmm hard to say can you post the list from the terminal.
```
cat /etc/apt/sources.list
```
I'm just trying to make sure your download list is correct, this wont fix a network problem though, unless its got some problems.

You can also from that software sources page 1st tab try the other drop-down and select best server and see if it is a server problem.

---

### Post by slooksterpsv on 2010-06-22
Click Applications -> Accessories -> Terminal

Type in:
```

gksudo gedit /etc/apt/sources.list

```

If the first line reads:
```

deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid m

```

Put a # in front of deb on that line:
```

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid m

```

Save exit, then run
```

sudo apt-get update

```

To refresh the packages/repositories.

---

### Post by plucky on 2010-06-22
> **Robert Buckmaster said:**
> Hi.

I've just recently installed Ubuntu 10.04 on my laptop, which doesn't have a CD player. On my attempting to download new apps., however, the system asks me to insert the ubuntu CD into the disk drive. How do I disable this prompt so that I may download the aps from the internet instead of from the CD? I should prefer to solve the problem using the visual interface, and without altering the source code.

Thanks!

Rob

**System > Administration > Software Sources** and un-tick the CD as a source.

Good Luck

---

### Post by yetiman64 on 2010-06-22
> **slooksterpsv said:**
> Click Applications -> Accessories -> Terminal

Type in:
```

sudo gedit /etc/apt/sources.list 
```....

@slooksterpsv, could you consider altering "sudo" to "gksudo" as gedit is a graphical application, see link #4 in my sig, scroll down the page to the "Graphical Sudo" section for a full explanation. Cheers Yetiman64.

---

### Post by slooksterpsv on 2010-06-22
> **yetiman64 said:**
> @slooksterpsv, could you consider altering "sudo" to "gksudo" as gedit is a graphical application, see link #4 in my sig, scroll down the page to the "Graphical Sudo" section for a full explanation. Cheers Yetiman64.

Thank you, I did not know about gksudo, I'll have to start using that now. SUDO with some graphical apps have worked for me, like gedit, but others haven't, so that's why.

---

### Post by Robert Buckmaster on 2010-06-22
Problem solved, I think. There was a box for 'cdrom...' under the tab Other Software, which I unchecked.I managed to download one application without the annoying prompt preventing me. I presume the others won't ask me for the CD.

---

### Post by yetiman64 on 2010-06-22
> **Robert Buckmaster said:**
> Problem solved, I think. There was a box for 'cdrom...' under the tab Other Software, which I unchecked.I managed to download one application without the annoying prompt preventing me. I presume the others won't ask me for the CD.

That sounds good now. If all works well could you mark the thread solved (link #5 in my sig has instructions) 

By the way, this is a duplicate thread with one in General Help so I'll send a message to the mods to merge them. Cheers, Yetiman64.

---

### Post by overdrank on 2010-06-22
Threads merged. :)

---

### Post by wizard_karan on 2010-07-11
Hey guys!

Many thanks, i just solved my problem.:grin:

i just commented the lines containg deb cd-rom in the beginning in the /etc/apt/sources.list file and it solved my problem.

Now Ubuntu never asks for the CD-ROM!!=D>

thanks again!

from
Karan Pratap Singh
Chandigarh, India

P.S. Do not trust the evil :twisted: GUIs, the configuration files are the true good beings O:) in the world of LINUX.

---

