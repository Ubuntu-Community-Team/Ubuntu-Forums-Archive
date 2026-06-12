---
title: "synaptic package manager error"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by Panda1 on 2010-03-02
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'n' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list, E:The list of sources could not be read.'

The above is the error message I get when I try to run Synaptic Package Manager. I think this started after the last update.
Any ideas??

regards,
Dale

---

### Post by undecim on 2010-03-02
Can you post the contents of /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list?

---

### Post by Panda1 on 2010-03-03
I am new to ubuntu linux so I have lots of learning to do. Please instruct me on how to get the information your looking for and I'll try my best to post it.

 Dale

---

### Post by alexandari on 2010-03-03
```
 cat /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list 
```

in the terminal

and then copy the output here :)

---

### Post by undecim on 2010-03-03
> **alexandari said:**
> ```
 cat /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list 
```

in the terminal

and then copy the output here :)

Alternatively, you can press Alt+F2 and type "gedit /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list" to get a graphical viewer.

---

### Post by Panda1 on 2010-03-03
Here is what i have......

dale@dale-desktop:~$  cat /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list
n
dale@dale-desktop:~$ sudo  cat /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list
[sudo] password for dale: 
n
dale@dale-desktop:~$ 


i guess "n" is whats there?

i"ll check back later, that work thing again!

---

### Post by 3rdalbum on 2010-03-03
Panda, what you need to do is remove the /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list file. You can do this by opening a file browser as root and navigating to the file and removing it, or by running this command:

```
sudo rm /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list
```

If you were following a HOWTO about installing the latest version of Wine, then try following it again. Or try using the version of Wine that's in the Ubuntu repositories. (or, what I always suggest, try using native Linux programs wherever possible, instead of attempting to emulate Windows programs... Wine only works on a small percentage of Windows programs)

---

### Post by Panda1 on 2010-03-04
Thank you all for your replys. I ran the code 3rdalbum provided and this resolved my problem.
I sure wish XP had this support and was this user friendly, you have a good thing going here. 

I have downloaded the Ubuntu Pocket guide and it has answer some of my other questions.
Its sure nice to know you are all here to help!
Cheers,
Panda

---

