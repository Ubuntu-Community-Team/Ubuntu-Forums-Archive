---
title: "64 Bit CPU, but 32 bit Operating System"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by newport_j on 2009-05-06
This is clearly an absolute begginer question. I see that most new PC workstations are available with only 64 bit CPU. I am also reluctant because of what I read on forums like this to use a 64 bit verison of Ubuntu. 
 
The question then arises: can you run Ubuntu 32 bit 8.04 LTS on a 64 bit processor and not experience any fall off in performance or any other important measure of a CPU's metric's (like memory handling). I have read elsewhere on the web that a 64 bit CPU (say an i7) can easily run 32 bit operating systems. No problem. true? 
 
 
newport_j

---

### Post by stchman on 2009-05-06
> **newport_j said:**
> This is clearly an absolute begginer question. I see that most new PC workstations are available with only 64 bit CPU. I am also reluctant because of what I read on forums like this to use a 64 bit verison of Ubuntu. 
 
The question then arises: can you run Ubuntu 32 bit 8.04 LTS on a 64 bit processor and not experience any fall off in performance or any other important measure of a CPU's metric's (like memory handling). I have read elsewhere on the web that a 64 bit CPU (say an i7) can easily run 32 bit operating systems. No problem. true? 
 
 
newport_j

Nearly every 64 bit CPU will support the 32 bit version of Windows, Linux, etc.  The thing is is that the CPU has more capability and you are restricting it.  Go 64 bit.

---

### Post by mcduck on 2009-05-06
> **newport_j said:**
> This is clearly an absolute begginer question. I see that most new PC workstations are available with only 64 bit CPU. I am also reluctant because of what I read on forums like this to use a 64 bit verison of Ubuntu. 
 
The question then arises: can you run Ubuntu 32 bit 8.04 LTS on a 64 bit processor and not experience any fall off in performance or any other important measure of a CPU's metric's (like memory handling). I have read elsewhere on the web that a 64 bit CPU (say an i7) can easily run 32 bit operating systems. No problem. true? 
 
 
newport_j

64-bit processors are fully compatible with 32-bit applications, which means that you will be able to run 32-bit OS without any problems. You will of course loose the benefits of using 64-bit system but for most user's this isn't something you would ever notice (apart from 32-bit systems being limited to max 4GB of RAM).

---

### Post by NightwishFan on 2009-05-06
What is the limit on RAM for the 32-bit PAE kernel?

---

### Post by 73ckn797 on 2009-05-06
9.04 64 bit ext4 with 6Gib RAM runs very well. The 6Gib in Windows with PAE enabled is a screamer and much faster but I rarely boot into it these days.

---

### Post by mcduck on 2009-05-06
> **NightwishFan said:**
> What is the limit on RAM for the 32-bit PAE kernel?

64GB (on a 32-bit CPU).

Of course you still need to have a CPU that supports PAE, and remember that enabling PAE has also negative effects on performance so unless you really have that much RAM, really need it, and just can't use 64-bit system, you shouldn't use it. In other words make sure that the performance benefit from having more RAM is bigger than the performance decrease caused by using PAE on a 32-bit CPU..

For most desktop users I'd say that 32 bits is just fine, only a few of the tasks people usually do with their computers get any performance boost from 64 bits. On the other hand, if you happen to have a 64-bit CPU you won't loose anything either by running a 64-bit OS. ;)

---

### Post by presence1960 on 2009-05-06
> **newport_j said:**
> This is clearly an absolute begginer question. I see that most new PC workstations are available with only 64 bit CPU. I am also reluctant because of what I read on forums like this to use a 64 bit verison of Ubuntu. 
 
newport_j

I can't imagine what you have been reading, unless it is old material. Check this out from our forum : [http://ubuntuforums.org/forumdisplay.php?f=343](http://ubuntuforums.org/forumdisplay.php?f=343) 

64 bit on Ubuntu is running very smoothly with basically just about all the same software in the 64 bit repositories that are in the 32 bit repositories. Java and Flash are running good now. I would use the instructions in the stickys of the x86-64 Users forum to insure proper install of Flash and java for 64 bit. 

Now 64 bit Windows is a whole different story...but I won't comment on that. You use Ubuntu- go 64 bit OS.

---

### Post by NightwishFan on 2009-05-06
> **mcduck said:**
> 64GB (on a 32-bit CPU).

Of course you still need to have a CPU that supports PAE, and remember that enabling PAE has also negative effects on performance so unless you really have that much RAM, really need it, and just can't use 64-bit system, you shouldn't use it. In other words make sure that the performance benefit from having more RAM is bigger than the performance decrease caused by using PAE on a 32-bit CPU..

For most desktop users I'd say that 32 bits is just fine, only a few of the tasks people usually do with their computers get any performance boost from 64 bits. On the other hand, if you happen to have a 64-bit CPU you won't loose anything either by running a 64-bit OS. ;)

What kind of performance impacts? OpenSUSE installs PAE by default, and they say it offers some enhanced security for those with under 4gb, but nothing about negative impact. Forgive me if this is off topic, I believe it is possibly relevant though.

---

### Post by mcduck on 2009-05-06
> **NightwishFan said:**
> What kind of performance impacts? OpenSUSE installs PAE by default, and they say it offers some enhanced security for those with under 4gb, but nothing about negative impact. Forgive me if this is off topic, I believe it is possibly relevant though.
First comes the overhead at CPU level caused by more complex memory management. Having to do more work to do the same tasks will not go without effects on performance.

Axctually I'll redirect you to our "competitor's" web site about PAE. (Works fine as it's mainly a hardware level issue and same things apply no matter what OS you use. Besides, the page has a good explanation about the problems), just scroll down to the section titled "Technical Issues with Large Memory Support in IA32":
[http://www.microsoft.com/whdc/system/platform/server/PAE/pae_os.mspx]("http://www.microsoft.com/whdc/system/platform/server/PAE/pae_os.mspx")

In the end the point is that things like 64-bit computing and PAE are not magical solutions that will improve everybody's life with computers without also having their bad sides. In some cases they give you better performance, in some cases worse, and in case of typical desktop users there will be no noticeable difference which ever way you go. :D

---

### Post by 73ckn797 on 2009-05-06
Do I recall correctly that to have PAE enabled on a 32bit Ubuntu that you would have to use the server edition?

I have not looked into it recently.

---

### Post by mcduck on 2009-05-06
> **73ckn797 said:**
> Do I recall correctly that to have PAE enabled on a 32bit Ubuntu that you would have to use the server edition?

I have not looked into it recently.

Yes, the server kernel has PAE enabled while generic kernel doesn't. If you need it, you have to wither use the server kernel or compile the generic one yourself and enable PAE.

---

### Post by 73ckn797 on 2009-05-06
> **mcduck said:**
> Yes, the server kernel has PAE enabled while generic kernel doesn't. If you need it, you have to wither use the server kernel or compile the generic one yourself and enable PAE.

Compiling is not for me and since I am running on a 64 system, not necessary. Would installing the server kernel to an existing 32 bit system be possible or would it have to be a fresh server install then installing the Gnome desktop, etc....? I have read that can be done. I will have to search for the info I seem to recall.

---

### Post by mcduck on 2009-05-06
> **73ckn797 said:**
> Compiling is not for me and since I am running on a 64 system, not necessary. Would installing the server kernel to an existing 32 bit system be possible or would it have to be a fresh server install then installing the Gnome desktop, etc....? I have read that can be done. I will have to search for the info I seem to recall.

The server kernel is available in repositories just like any other package, and can be installed on existing systems.

Just make sure that any restricted drivers or 3rd party drivers you might be using are supported with server kernel as well. (although if you can't bother with that, you can safely just give it a try. The server kernel will appear as it's own option in Grub menu so you can always switch back to generic one if some thing doesn't work correctly.

---

### Post by 73ckn797 on 2009-05-06
> **mcduck said:**
> The server kernel is available in repositories just like any other package, and can be installed on existing systems.

Just make sure that any restricted drivers or 3rd party drivers you might be using are supported with server kernel as well. (although if you can't bother with that, you can safely just give it a try. The server kernel will appear as it's own option in Grub menu so you can always switch back to generic one if some thing doesn't work correctly.

Roger that mcduck and thanks for the refresher information.

---

### Post by jackmetal on 2009-05-06
In the past, I ran 32bit Ubuntu on all of my 64bit systems, and I had run that way for the last year or so.  32bit OS's will run without any issues on a 64bit CPU.

...But...

Recently, I moved all of my 64bit systems to 64bit Unbuntu and have been VERY happy with the results (No Problems at ALL, and a number of things are much faster now)..

---

### Post by NightwishFan on 2009-05-07
There are also odd improvements I have noticed. For example, when I hibernate on 32-bit, Rhythmbox is locked up on resume and I have to restart it, on 64-bit this is not the case.

The only 'downside' I see is that it uses more RAM, and that is inconsequential.

---

