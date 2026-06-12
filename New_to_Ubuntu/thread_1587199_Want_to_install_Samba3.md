---
title: "Want to install Samba3"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by Albert the boat on 2010-10-03
I've been trying to install samba on my shiny new Ubuntu machine. 
 
When I try typing 'samba' in the terminal it tells me that Samba is not installed but I can install it by typing :sudo apt-get install samba4.
 
I tried that and got a whole string of 'unrecognised parameter' errors. Having discovered that Samba4 is still experimental I tried uninstalling it, via the Ubuntu Software Centre, and then issued the same command without the 4: 'sudo apt-get install samba'.
 
It appears to install but when I try to issue any commands (e.g. 'samba start' or 'samba restart') it tells me that 'Samba is not installed' but that I can install it by typing : 'sudo apt-get install samba4'. I DON'T WANT SAMBA 4!!!! However, when I try to install again using 'sudo apt-get install samba' it tells me 'samba is already the newest version'.
 
My Windows machine can see the Ubuntu box, but I can't configure user access. I've tried doing it directly and via GADMIN-SAMBA and I can't even stop, and start Samba.
 
Hellllllp!
 
Albert

---

### Post by sikander3786 on 2010-10-03
Try removing Samba and reinstalling.

```
sudo apt-get remove --purge samba
```

```
sudo apt-get update && sudo apt-get install samba
```

Start samba by,

```
sudo service smbd start
```

```
sudo service nmbd start
```

It is not **samba start**, it is **smbd** and **nmbd** start.

**_EDIT:_** samba is not the name of any service. See my output.

```
malik@server:~$ sudo service samba start
samba: unrecognized service
```

Why does it say "Samba is not installed" on your system?

---

### Post by Albert the boat on 2010-10-03
Thanks, sikander.
 
I've been basing what I'm doing on information from a couple of threads that are presumably out of date. That's where I got 'samba restart' etc. from
Following your post I've done some more digging and found a couple of threads that claim to be up to date as of Lucid Lynx. I'll try those.
 
As for 'Why does it say "Samba is not installed" on your system?' I can only guess that it's because it seems to assume that any reference to samba means samba4! I'm the noob, so I'm guessing!
 
By the way, having followed your reinstall instructions (below) I can't see any reference to samba in my Ubuntu Software Centre's Installed Software list, but if I search for it it pops up together with some other related stuff. Is this normal?
 
Similarly, I've installed the Samba Documentation, samba-doc, via the Software Centre but can't find it on my machine. I searched in File System for 'samba' and got 101 hits -- where are the docs likely to live?
 
Thanks again
 
Albert

Code:
sudo apt-get remove --purge samba
Code:
sudo apt-get update && sudo apt-get install samba

---

### Post by sikander3786 on 2010-10-04
> where are the docs likely to live?

You'll find docs under usr/share/doc/samba-doc.

> but if I search for it it pops up together with some other related stuff. Is this normal?

Absolutely normal. Software Center's search is a bit wide-spread. If you some times want to search by the exact package name, go to System > Administration > Synaptic Package Manager and search for Samba. It'll return the exact same results.

Post back in case you've any other issues.

Regards.

---

