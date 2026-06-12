---
title: "Natty apt-get error"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by anthonyp on 2011-05-06
Hi,

I am an on again, off again user of Ubuntu. I am very much a newbie and i have the following error;

I had an Internet drop out when using the package manager and ever since then apt-get and the package manager are corrupt.

In the top menu bar (to the right) I have red symbol that is notifying me of the error. It states the error as - 'Opening the cache'

I attempted to use the terminal to update the packages and I get the following error;
> Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

I have absolutely no idea how to fix this error, nor am i aware on the correct procedure to report this bug?

If anyone could help me out it would be much appreciated.

Cheers
Grimace

---

### Post by anthonyp on 2011-05-06
Also I get numerous errors if I try to do anything withing the package manager. Such as;
> Could not initialize the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by jramshu on 2011-05-06
Just going to take a shot in the dark here. Seems like a few people are having some problems updating, just not this one. Have you tried using aptitude to update?

EDIT: I found this for an older distro, sounds similar.

[http://ubuntuforums.org/showthread.php?t=863742](http://ubuntuforums.org/showthread.php?t=863742)

---

### Post by anthonyp on 2011-05-06
> **jramshu said:**
> Just going to take a shot in the dark here. Seems like a few people are having some problems updating, just not this one. Have you tried using aptitude to update?

I have not. I am not even sure what aptitude is :confused::popcorn:

---

### Post by jramshu on 2011-05-06
From what I've read it probably won't work. The way you use it is the same as apt-get.

```
sudo aptitude update
```Shoot, if it's a fresh install you could try a method I read about in the thread posted above. If it all goes to crap you can re-install from disk. I read further along in the thread that it works in 11.04.

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

EDIT: The latest report the above method worked in 11.04 was from 4 days ago.
[http://ubuntuforums.org/showthread.php?t=863742&page=5](http://ubuntuforums.org/showthread.php?t=863742&page=5)

---

### Post by anthonyp on 2011-05-06
> **jramshu said:**
> From what I've read it probably won't work. The way you use it is the same as apt-get.

```
sudo aptitude update
```Shoot, if it's a fresh install you could try a method I read about in the thread posted above. If it all goes to crap you can re-install from disk. I read further along in the thread that it works in 11.04.

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

EDIT: The latest report the above method worked in 11.04 was from 4 days ago.
[http://ubuntuforums.org/showthread.php?t=863742&page=5](http://ubuntuforums.org/showthread.php?t=863742&page=5)

IT WORKED!!!

Thank you! I gave that rm and update a go and it seems to have worked!
As soon as the instruction had completed the update manager opened with a list of updates to be installed. Installing now!
So I guess this is now solved.

Thanks again, Much appreciated.

Cheers
Grimace

---

### Post by jramshu on 2011-05-07
> **anthonyp said:**
> IT WORKED!!!

Thank you! I gave that rm and update a go and it seems to have worked!
As soon as the instruction had completed the update manager opened with a list of updates to be installed. Installing now!
So I guess this is now solved.

Thanks again, Much appreciated.

Cheers
Grimace

Great!!!! I'm thrilled it worked for you. No problem with the help. That's one of the major advantages of Ubuntu, and Linux in general, the free assistance with solving problems. I give all the credit to the original person who solved it, jabrown65.

People always ask, "Why should I make the switch from windows?" Try getting any free help for windows, it's a nightmare without $$$$$$$$$>

One last thing, when your problem has been solved, go to thread tools and mark it as "solved." 

Thanks and enjoy!:guitar:

---

### Post by anthonyp on 2011-05-07
> **jramshu said:**
> Great!!!! I'm thrilled it worked for you. No problem with the help. That's one of the major advantages of Ubuntu, and Linux in general, the free assistance with solving problems. I give all the credit to the original person who solved it, jabrown65.

People always ask, "Why should I make the switch from windows?" Try getting any free help for windows, it's a nightmare without $$$$$$$$$>

One last thing, when your problem has been solved, go to thread tools and mark it as "solved." 

Thanks and enjoy!:guitar:

Thanks a heap to your self and jabrown65!

I also want to thank you for explaining how to mark the thread as solved. I tried to do this originally via the 'edit' command but could not locate it.

Cheers

---

### Post by anthonyp on 2011-05-08
wah... its broken again :(

---

