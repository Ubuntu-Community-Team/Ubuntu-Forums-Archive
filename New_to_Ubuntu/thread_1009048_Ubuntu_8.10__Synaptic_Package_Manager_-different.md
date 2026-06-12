---
title: "Ubuntu 8.10  Synaptic Package Manager -different"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by Robster2 on 2008-12-12
New Ubuntu 8.10 (64 Bit)

I have been running Hardy Herron prior to that Gusty Gibbon on my desktop machine. 

Recently I bought a Laptop and installed Ubuntu 8.10 on it.

I find that that when I use the synaptic package manager I don't find nearly the same number of things that I find on my desktop system.

For example a search on MySQL found nothing.   I have installed an entire LAMP system on my desktop with the synaptic package manager.

I remember adding repositories to my desktop system manually so that I could play DVDs  has that got something to do with it?

---

### Post by EdThaSlayer on 2008-12-12
I would advise you to replace your repositories or at least update them.
If you aren't scared of the command line:

> sudo apt-get update

and if you want to change your repositories visiting
[http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Add_Extra_Ubuntu_Repositories](http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Add_Extra_Ubuntu_Repositories)
should do the trick.

---

### Post by Paqman on 2008-12-12
> **Robster2 said:**
> 
I remember adding repositories to my desktop system manually so that I could play DVDs  has that got something to do with it?

Yep. You can check what repos you're connecting to by going to System > Admin > Software Sources.

---

### Post by Mucho on 2008-12-12
or you can modify /etc/apt/sources.list

---

### Post by zvacet on 2008-12-12
@ **Robster2**

Probably this is not a case but check it anyway.In synptic search box be sure that you are searching files by **name and description**.

---

### Post by Robster2 on 2008-12-12
Thanks for all replies.

In fact a new quick search box is present in this version which makes the old search icon drop off - fixed this removing the text from th toolbar.

Not the best solution.

---

