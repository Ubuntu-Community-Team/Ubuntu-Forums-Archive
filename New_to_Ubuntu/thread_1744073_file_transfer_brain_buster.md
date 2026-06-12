---
title: "file transfer brain buster"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by josephmills on 2011-04-30
Hi there 
I have a files that I would like to move to a friends computer. The total size of it all is about 3gb these are the things that I have laying around. 
1) one cat5 cable 
2) two computers one with ubuntu 10.10 and the other is the same
3) a stack of cd mile high 
4) cd burner 
5) dvds 
6) 3 broken thumb drives 
So what do you think how can I get these files over to the other computer. With out going to wall mart right now. Should I set up ssh or vnc to transfer the file that way? what would you do if you where in my shoes? thanks for your time

---

### Post by Bucky Ball on 2011-04-30
Well, the obvious choice is one blank DVD. It will hold over 4Gb and you only need 3Gb.

[http://en.wikipedia.org/wiki/DVD](http://en.wikipedia.org/wiki/DVD)

---

### Post by josephmills on 2011-04-30
> **Bucky Ball said:**
> Well, the obvious choice is one blank DVD. It will hold over 4Gb and you only need 3Gb.

[http://en.wikipedia.org/wiki/DVD](http://en.wikipedia.org/wiki/DVD)

no dvd burner

---

### Post by fabricator4 on 2011-04-30
> **josephmills said:**
> Hi there 
I have a files that I would like to move to a friends computer. The total size of it all is about 3gb these are the things that I have laying around. 
1) one cat5 cable 
2) two computers one with ubuntu 10.10 and the other is the same
3) a stack of cd mile high 
4) cd burner 
5) dvds 
6) 3 broken thumb drives 
So what do you think how can I get these files over to the other computer. With out going to wall mart right now. Should I set up ssh or vnc to transfer the file that way? what would you do if you where in my shoes? thanks for your time

Well, since you don't have a router, you can't use the cat5 cable.  A _twisted_ cat5 cable would be a different matter, I use this all the time to let other computers use the 3G internet from my Eee PC.

Procedure is: 1) plug cable (twisted cat5) in. 2) Install Firestarter and configure it as a DHCP server.

Given your options, I'd burn a DVD, as long as that isn't broken too (and isn't actually on a CD burner as you seem to imply. ;-)

Time to buy some new USB thumbdrives?  I just bought a new Verbatim 8GB one for $15.  (Is it just me, or were the 1GB ones almost $100 only five/six years ago?)

Chris.

---

### Post by Megaptera on 2011-04-30
> **Bucky Ball said:**
> Well, the obvious choice is one blank DVD. It will hold over 4Gb and you only need 3Gb.

[http://en.wikipedia.org/wiki/DVD](http://en.wikipedia.org/wiki/DVD)

+1 to that, keep it simple. Plus this way you've also got a back-up that you can lock safely away somewhere. :D

---

### Post by josephmills on 2011-04-30
**I DONT HAVE A DVD BURNER ** I do have a router

---

### Post by Bucky Ball on 2011-04-30
Next option: Get both machines on a network and transfer. Have plenty of coffee or the beverage of choice as this could take awhile. Maybe an overnight job would be easiest. ;)

(Or find someone with a portable DVD burner; still by far the easiest option). 

Weird; two computers, no DVD burner ...

---

### Post by fabricator4 on 2011-04-30
> **josephmills said:**
> **I DONT HAVE A DVD BURNER ** I do have a router

Yes, but you've only got one cat5 cable. :-)

---

### Post by fdrake on 2011-04-30
use samba to share the folder, with the 3g data, in the network with the other computer. the other computer is in the same house or in another house?

---

### Post by josephmills on 2011-04-30
> **Bucky Ball said:**
> Next option: Get both machines on a network and transfer. Have plenty of coffee or the beverage of choice as this could take awhile. Maybe an overnight job would be easiest. ;)

(Or find someone with a portable DVD burner; still by far the easiest option). 

Weird; two computers, no DVD burner ...

the one computer the one with out the file on it has a dvd burner. I know I downloaded the iso on the wrong computer.. It took 8 hours or so. I started the download on the one with the dvd burner. I know that I cant compress iso can I?

---

### Post by josephmills on 2011-04-30
> **fdrake said:**
> use samba to share the folder, with the 3g data, in the network with the other computer. the other computer is in the same house or in another house?

both computers are in the same house looking into samba

---

### Post by fdrake on 2011-04-30
or you can do quicker by burning the file in 5-6 cd-rom if you don't mind wasting some of them...

use the "split" command to split the .iso images in 6 pieces or 600mb each. burn each piece in the cd. copy the content of the cd in the 2nd pc. and use 'cat to combine them'
```

#to split
split <size> file.iso
#to merge
cat file.1 file.2 file.3 >file.iso

```
split is very fast to so i would consider it to as a solution if you problem setting up samba

---

### Post by graffiX on 2011-04-30
> **josephmills said:**
> Hi there 
I have a files that I would like to move to a friends computer. The total size of it all is about 3gb these are the things that I have laying around. 
1) one cat5 cable 
2) two computers one with ubuntu 10.10 and the other is the same
3) a stack of cd mile high 
4) cd burner 
5) dvds 
6) 3 broken thumb drives 
So what do you think how can I get these files over to the other computer. With out going to wall mart right now. Should I set up ssh or vnc to transfer the file that way? what would you do if you where in my shoes? thanks for your time


haha... I love point 2 on your list.

BTW.  The days of requiring twisted pairs are almost over.  Almost all NIC's will autoswitch.  So...  I would plug the cat 5 cable between the two.

You'll have to set fixed IP addresses tho... use two different ones on the same subnet.  For example, one computer 10.1.1.2 and the other 10.1.1.3 then turn on samba, and with your file manager go to smb://10.1.1.2 or whatever computer has the files share on.  They likely won't discover each other automatically but will link if you type the numerical addresses.

If you're lucky you'll have gigabit in both computers and you'll be done before you know it.

---

### Post by Linux&amp;Gsus on 2011-04-30
> **josephmills said:**
> the one computer the one with out the file on it has a dvd burner. I know I downloaded the iso on the wrong computer.. It took 8 hours or so. I started the download on the one with the dvd burner. I know that I cant compress iso can I?

Instead of downloading the DVD again, how about downloading the CD image? Is only 1/4 of the size to download. Also, downloads potentially less software you don't need/want.
You can always install needed software afterwards. The things you really need...

---

### Post by Dondermans on 2011-04-30
> **josephmills said:**
> Hi there 
I have a files that I would like to move to a friends computer
(...)

I suppose I would try to connect the source drive directly to the motherboard of the target computer first.

---

