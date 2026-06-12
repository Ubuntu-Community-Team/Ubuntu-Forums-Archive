---
title: "I delete ubuntu partiation from Vista"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by zuber786 on 2010-03-21
I am stuck now
I started by install ubuntu on my laptop
I had like 150 gb on it
100 for vista & 50 for ubuntu

so I created partition while installing ubuntu. 
after using ubuntu for while 
I decided I want to install it on my desktop so I wanted to remove it from my laptop.
so I went to control panel > comp management .... and all that and from there I deleted partition of my ubuntu. 

after that I restarted my lappy I get this error 
```

GRUB loading
error unknown filesystem
grub rescue>

```
please help me
my vista won't load back up
I think I need to remove GRUB loader.

---

### Post by zuber786 on 2010-03-21
dude please help me

---

### Post by zuber786 on 2010-03-21
I am stuck now
I started by install ubuntu on my laptop
I had like 150 gb on it
100 for vista & 50 for ubuntu

so I created partition while installing ubuntu.
after using ubuntu for while
I decided I want to install it on my desktop so I wanted to remove it from my laptop.
so I went to control panel > comp management .... and all that and from there I deleted partition of my ubuntu.

after that I restarted my lappy I get this error
Code:
```

GRUB loading
error unknown filesystem
grub rescue>
```

please help me
my vista won't load back up
I think I need to remove GRUB loader.

---

### Post by dagdeniz on 2010-03-21
Ummm... I think here you can find something useful (the first post of th thread): 

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

---

### Post by Mark Phelps on 2010-03-21
To restore the Vista boot loader, you will have to boot from a Visa Install DVD or a Vista Repair CD.  Since you probably have neither, go to the NeoSmart Technology forums and download the Vista Repair CD ISO image, burn that to CD, and boot from that into Startup Repair.

You will have to run Startup Repair three times to get the MBR replaced because it replaces that on the third pass.

If you had come to these forums first and aeked BEFORE you did this, you would have found out that you could have downloaded EasyBCD from the same website, installed that on your PC, and used it to restore the Vista MBR from inside Vista. Then you could have used the Vista Disk Management utility to remove the Ubuntu partition and not had to go through any of this work!

---

### Post by zuber786 on 2010-03-21
Hey
Thanks for reply
it is my mistake, I took another step. I went and Installed ubuntu again on the same partition, and after that I will follow your steps you mentioned in last phrase.
hope it will work 
I will sure come back after ubuntu is done installing on my laptop again.

---

### Post by wilee-nilee on 2010-03-21
You need to reload the Vista bootlaoder in the MBR here is a recovery disc link.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
I am not sure but this may be what works if you know how to use it. It basically gets you to the prompts that the install DVD would. 
Here is a link to instructions using this recovery disc.
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by overdrank on 2010-03-21
Please do not create multiple threads on the same issue. Threads merged.

---

### Post by zuber786 on 2010-03-21
hey I installed & I also installed EASY BCD
can you please guide me what to do
thank you

---

### Post by wilee-nilee on 2010-03-21
> **zuber786 said:**
> hey I installed & I also installed EASY BCD
can you please guide me what to do
thank you

You might find somebody who knows whether easybcd works to reinstall the MBR here but I doubt it, it is a Ms based product this is a Linux Forum, although it is full of knowledgeable people. 

I think the links I gave you for the recovery and how to use it will work.

---

### Post by Tom.Gee on 2010-03-21
If you are interested in a third party solution that is SUPER good at not having MBR problems, I've used the OSL2000 boot manager to boot multiple OS.  It knows how to boot Linux, Vista, XP, MSDOS, probably 7 by now, and it will let you boot from any partition.  

You might go to Bootdisk.com and download a dos 7.1 Bootdisk and do an FDISK /MBR.  I know it works up to XP, and it won't make things any worse.

---

### Post by Mark Phelps on 2010-03-22
> **zuber786 said:**
> Hey
Thanks for reply
it is my mistake, I took another step. I went and Installed ubuntu again on the same partition, and after that I will follow your steps you mentioned in last phrase.
hope it will work 
I will sure come back after ubuntu is done installing on my laptop again.

The steps I outlined will not FIX your problem.  They are steps to take to PREVENT the problem that happened to you.

You will still have to restore the Vista MBR in order to boot into it.

---

### Post by SushiR on 2010-03-22
[Let me google it for you...]("http://lmgtfy.com/?q=windows+vista+fix+bootloader")

---

