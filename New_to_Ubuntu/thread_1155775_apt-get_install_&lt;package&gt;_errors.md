---
title: "apt-get install &lt;package&gt; errors"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by goodvikings on 2009-05-11
Hey everyone.

This forums title explains me perfectly... well, I spose n00b would be more appropriate...

I have just installed Ubuntu 9.04 and I'm having problems with apt-get. Whenever I try to use it, it comes up with the same error no matter what the package. For example, sudo apt-get install nedit -

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nedit

or sudo apt-get install g++

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package g

you get the idea.

So how do I fix this?

Thanks,

Damian

---

### Post by skymera on 2009-05-11
```
 sudo apt-get update 
```

---

### Post by Lampi on 2009-05-11
try rebuilding the package database:

'apt-get update' (use root privileges or sudo)


'apt-get install nedit'

---

### Post by Peter09 on 2009-05-11
Where are you getting the package names from, are you sure they are valid packages.

Try

```
sudo apt-get install htop
```

(Running htop in a terminal shows you what is happening on your system)

To remove it replace 'install' with 'remove' in the command line above.

---

### Post by pro003 on 2009-05-11
you probably don't type the correct names of those packages. I suggest you to try to either use synaptic which you can find in System > Administration > Synaptic 

..or if you would like to use terminal then use aptitude search before trying to install some package
```

# sudo aptitude search package
# sudo aptitude install package
```

---

### Post by goodvikings on 2009-05-11
I tried sudo apt-get update and got something similar - 

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

however htop worked ok

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  htop
0 upgraded, 1 newly installed, 0 to remove and 65 not upgraded.
Need to get 55.5kB of archives.
After this operation, 201kB of additional disk space will be used.
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/universe htop 0.8.1-4ubuntu1 [55.5kB]
Fetched 55.5kB in 2s (26.7kB/s)
Selecting previously deselected package htop.
(Reading database ... 102003 files and directories currently installed.)
Unpacking htop (from .../htop_0.8.1-4ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up htop (0.8.1-4ubuntu1) ...

at which point the update manager (gui) opened up...

still not working for nedit though

---

### Post by _Purple_ on 2009-05-11
Go to System > Administration > Software Sources. Check if download from is set to main server. Then run
```
sudo apt-get update
sudo apt-get install nedit

```

---

### Post by goodvikings on 2009-05-11
It sounds like since the package manager (gui) opened up, I cannot use the command line get-apt install - would that be right?

---

### Post by _Purple_ on 2009-05-11
Yes if Synaptic Package Manager is open, you cannot install using terminal. You have to close the Synaptic Package Manager first.

---

### Post by goodvikings on 2009-05-11
Ahh beautiful! Working like a dream!

Thanks for all the help guys - and so quickly too!

Damian

---

