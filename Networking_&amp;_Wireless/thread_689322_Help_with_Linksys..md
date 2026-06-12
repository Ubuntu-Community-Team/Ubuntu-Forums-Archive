---
title: "Help with Linksys."
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by slats on 2008-02-06
i started to follow this tutorial [http://ubuntuforums.org/showthread.php?t=687716](http://ubuntuforums.org/showthread.php?t=687716)
but ran into a problem when i got to here
> Step 1 - Install NDISWrapper

* Extract NDISWrapper
* In a terminal window, navigate into the NDISWrapper folder
* Type the following:
sudo make uninstall
make
sudo make install
sudo ndiswrapper -m

i keep getting this when i type in those commands

```
slats@Slat-Machine:~$ cd /home/slats/Desktop/ndiswrapper*

slats@Slat-Machine:~/Desktop/ndiswrapper$ sudo make uninstall

[sudo] password for slats:

make: *** No rule to make target `uninstall'.  Stop.

slats@Slat-Machine:~/Desktop/ndiswrapper$ make

make: *** No targets specified and no makefile found.  Stop.

slats@Slat-Machine:~/Desktop/ndiswrapper$ sudo make install

make: *** No rule to make target `install'.  Stop.

slats@Slat-Machine:~/Desktop/ndiswrapper$ sudo ndiswrapper -m

sudo: ndiswrapper: command not found

slats@Slat-Machine:~/Desktop/ndiswrapper$
```

Can someone please help me?
It would be very appreciated, because i would like use Ubuntu but I'm not going to use it if i don't have any internet.
 so please someone help.

---

### Post by Hightide on 2008-02-06
Hi slats

if its a problem with ndiswrapper, try Kevdog's [tutorial]("http://ubuntuforums.org/showthread.php?t=574501")

regards

:)

---

### Post by faulkes on 2008-02-06
If you unpacked the ndiswrapper in ~/Desktop/ndiswrapper, see what is in the folder

```

ls ~/Desktop/ndiswrapper

```

It looks like it isn't finding the makefile associated for the source, which gives me the impression that there is a subdirectory in ~/Desktop/ndiswrapper you may have to cd into.

You might also want to consider installing ndiswrapper from the synaptic package manaer first, before trying the source version.

Faulkes

---

### Post by d0nny2600 on 2008-02-06
Don't forget the console is case sensitive!!

---

### Post by slats on 2008-02-06
> **faulkes said:**
> If you unpacked the ndiswrapper in ~/Desktop/ndiswrapper, see what is in the folder

```

ls ~/Desktop/ndiswrapper

```

It looks like it isn't finding the makefile associated for the source, which gives me the impression that there is a subdirectory in ~/Desktop/ndiswrapper you may have to cd into.

You might also want to consider installing ndiswrapper from the synaptic package manaer first, before trying the source version.

Faulkes  

where do i get this synaptic package?

---

### Post by slats on 2008-02-06
i feel like such an idiot
i forgot to extract thats why i got those problems

---

### Post by slats on 2008-02-06
well  now im getting errors when i try to install
awesomeeeee
can some one help me

---

