---
title: "Ubuntu from perfect to messed up in a couple days?!?"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by kramer65 on 2009-05-18
Hello,


I've been using my Ubuntu install for more than a year with a lot of ease. But the past couple days the whole system suddenly seems to be broken. First it started with an error message on my home screen which appeared out of nothing (see attached image), but pressing ok, gets me through. Today flash suddenly didn't play youtube movies anymore, and just now I found out my printer doesn't work anymore either. It doesn't give an error or anything, but it simply doesn't do anything anymore.

The strangest thing is that I didn't upgrade or install anything new. I've got Ubuntu upgrades set to automatic so it could have upgraded by itself, but I don't know about that. 

For the first error I tried 
```
sudo chown my-username .dmrc
chmod 644 .dmrc
``` Which didn't help anything.

For flash I tried uninstalling and then reinstalling using the .deb from the flash website. That didn't work so I went into synaptic which said I could upgrade the flash package. After doing that I got an error saying this: ```
E: Unable to write mmap - msync (28 no space for machine)
E: The package list or status file could not be read.
E: _cache->open() failed, please report.
```
(The error above could be slightly different since I translated the error from Dutch into English).

Whenever I now open synaptic it gives me the same error and I can't do anything with synaptic anymore.

To be honest, the last problem is even the most problematic since I use this pc for business as well (hence the reason I still use 8.04). I really NEED to print something tonight since I need to hand that in in the early morning tomorrow.
I uninstalled and re-installed the printer and powered it on and off a couple times; no effect.


How can Ubuntu be so perfect for me for so long, and then all of a sudden break down within a single day?!?

Please help help! Especially with the printer problem I could really use help now!!

---

### Post by BDNiner on 2009-05-18
It maybe your entire home directory got its permissions messed up. are you the owner of your home directory and the only one that can write to it?

---

### Post by kramer65 on 2009-05-18
AFAIK yes..

Now that you mention it I did create a new user and gave it administrator rights. But that was just an experiment, and for now nobody could have logged into that account. I just deleted it to see what happens.. No result..

Any ideas what I could do..?

---

### Post by BDNiner on 2009-05-18
what are the persmissions for the home directory? If they are not set correctly i would try to take ownership of the home directory and then make sure the permissions are 644.

---

### Post by bacardiandwatermelon on 2009-05-18
I think you have to do something like this.. change <user> to your username

```
sudo chmod 644 /home/<user>/.dmrc
sudo chown <user> /home/<user>/.dmrc
sudo chmod -R 700 /home/<user>
sudo chown -R <user> /home/<user>
```

---

### Post by Paqman on 2009-05-18
To restore all your folders and files to default settings you can use the following commands:

Folders:
```
find . -type d -exec chmod 755 {} \;
```

Files:
```
find . -type f -exec chmod 644 {} \;
```

---

### Post by kramer65 on 2009-05-18
How do I see what permissions the home folder has?

---

### Post by billgoldberg on 2009-05-18
> **kramer65 said:**
> How do I see what permissions the home folder has?

in a terminal:

cd /

after that do:

ls -l

The first part is the permission part, it should stay this: drwxr-xr-x

-----------

This short article on Linux file permission should be useful if you don't know what it means: [http://www.freeos.com/articles/3127/](http://www.freeos.com/articles/3127/)

---

### Post by kramer65 on 2009-05-18
I do know what file-permissions are, I'm just a bit unaware of all the commands.

If I run that command I get this:

```
drwxr-xr-x   5 root root  4096 2009-05-11 12:34 home
```

So as far as I know that is ok right?
But it says root, so I guess I am not the owner? How do I set that?

I'm sorry, but I'm a bit lost with all the commands listed above. Which one should I use now..?

---

### Post by Paqman on 2009-05-18
> **kramer65 said:**
> 
So as far as I know that is ok right?
But it says root, so I guess I am not the owner? How do I set that?


Everything in your home folder should be owned by you, not by root.

To take ownership of a folder and all it's contents:
```

sudo chown -R username:username /folder

```

chown = change ownership.
-R = recursive, affects all folders inside that one too.
username:username = your user and group

---

### Post by kramer65 on 2009-05-19
Alright thanks! And what should I fill in for my group?

[edit]
I tried this:
```
sudo chown -R my-username:my-username /home/my-username
```

But it says this:
chown: can't get access to ‘/home/my-username/.gvfs’: Access denied
(translated from Dutch)

What should I do now?

---

### Post by mc4man on 2009-05-19
You may wish to read thru here and I'd stress "read" to see if if any of the scenarios are applicable to you before running commands


[http://ubuntuforums.org/showthread.php?t=976610](http://ubuntuforums.org/showthread.php?t=976610)

---

### Post by kramer65 on 2009-05-19
Alright. I used that link and I now fixed the login error. The main problem turned out that my home folder had 777 rights. Why..? I have no clue..

However, to be honest that was the least of my worries. Can anybody help me getting my  printer working again? Strangely enough, the scanner (in the printer) does work using xsane, but printing something doesn't work at all.

Any ideas?

---

