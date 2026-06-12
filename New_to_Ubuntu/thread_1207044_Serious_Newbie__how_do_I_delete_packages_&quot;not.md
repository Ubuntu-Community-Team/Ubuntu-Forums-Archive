---
title: "Serious Newbie:  how do I delete packages &quot;not installed?&quot;"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by Machta on 2009-07-07
Good afternoon, all!

I've just purchased a Dell Mini with Ubuntu 8.04LTS.  I managed to get it to connect to my wi-fi, but for some reason it started and then aborted the updater a number of times.

As a result, I think I've got a problem.  See if this sounds like it to you:  in the Synaptic Package Manager, when I click on "All" it says that I have 24084 packages listed, 1182 installed, 0 broken, 0 to install/upgrade, 0 to remove.

When I click on "Status" and then "Not installed," it says that I have 22902 packages listed, 1182 installed, 0 broken, 0 to install/upgrade, 0 to remove.

When I try to run openoffice, it tells me I'm out of disk space.  Coincidence?  I think not.

So how do I delete the packages that seemed to have downloaded but didn't install?

Thanks in advance for all your help!

---

### Post by oldos2er on 2009-07-07
The "22902 packages listed" refers to packages in the repositories, not on your system, if that's what you meant. You can clear /var/cache/apt/archives by running **sudo apt-get clean**. **sudo apt-get autoremove** will clear out unneeded dependencies.

 To check your disk space, run **df -h**.

---

### Post by Machta on 2009-07-07
Ah, that helps!  That freed up about half a gig of storage.  Is it normal for /dev/sda2 to use 2.7 gigs just for the operating system and initially installed software?  I would like to free up another gig if possible.  This is a really cute little machine, but it is pretty light on storage (only 4 gigs total).

Thank you for your help!

---

### Post by Celauran on 2009-07-07
2.7GB is about right for a standard Ubuntu install. There are a handful of packages you can remove, but you're unlikely to free up a full gig. You might want to look at something like Netbook Remix.

---

### Post by aysiu on 2009-07-07
Netbook Remix is even bigger, actually, so don't go for that.

Just go through Synaptic Package Manager and uninstall packages you don't need. It'll warn you if removing a certain package will also remove other packages.

You won't get another full gig of space, though, unless you remove practically everything useful.

---

### Post by llamabr on 2009-07-07
On a new system with a fresh install, you shouldn't need space.  Post the output of 

```
df -h
```

---

### Post by Celauran on 2009-07-07
He's only got a 4GB SSD. It'll be tight.

UNR being bigger than Ubuntu.. wow. Kinda defeats the purpose.

---

### Post by abhiroopb on 2009-07-07
2.7G on a fresh install? I usually use up about 2G with a fresh install. Whats in your home folder?

---

### Post by aysiu on 2009-07-07
> **Celauran said:**
> He's only got a 4GB SSD. It'll be tight.

UNR being bigger than Ubuntu.. wow. Kinda defeats the purpose.
Well, UNR isn't really well-done, actually. It's supposed to be optimized for netbooks, but it's bigger, and it doesn't even use the lpia kernel. So all it really has to offer is the Netbook Remix interface with the large icons.

---

### Post by oldos2er on 2009-07-08
Install and run the program **localepurge**, it should free up more space for you.

---

