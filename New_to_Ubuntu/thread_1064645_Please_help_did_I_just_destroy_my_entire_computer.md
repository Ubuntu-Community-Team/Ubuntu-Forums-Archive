---
title: "Please help did I just destroy my entire computer?"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by SilentJ on 2009-02-09
Ok i have an eeepc 100H with a 160 gb hard drive. It came with windows xp and was stupidly formated with windows on an 80 gb partition c and a 80gb partition d .i installed ubuntu on partition d and allocated 30 gb for it. figureing that i could just resize the windows partition with qparted later on. I left it as it was for over a month then i started to run out of space so i decided to try and format the qindows drive because i didnt use windows Once in the last month. So i loaded uo qparted clicked on the 80 gb windows partition but it wouldnt let me format it it just turned it black and said it,was unknown format so i couldnt even mount it anylonger. So i again clicked onit and the only avaiable option was to make a new partition table which i  assumed would let me make changes as i liked however instantly my entire drive was gray unallocated space... I assumed i messed up but i was still using ubuntu fine so it couldnt have deleted everything. The most important thing was the d partition because i have been using it as storage everything important was theere.  I held my breath and restarted my machine and sure enough all i got was a grub 22 error. i dont think 160 gb of data could have been instantly vaporized i am assuming i just lost the partition structure? Can i get it back? Or did i destroy everything ? Please help. Let me know if there is any way i can save my data and/or my ubuntu install (i had a backup on the 30gb d drive) or if i should just take a bath w/ my computer.

---

### Post by mpl34 on 2009-02-09
You could try usig a ubuntu live disc to view the drivers and data then copy whateva is necessary. 

Another option could be to insert your windows disc and click the repair option which will search your drives for windows operating installations and may also want to run a check of your disc and try fix any abnomalties. 

If windiws does not require to check your disc run the command prompt and use the command fixmbr and fixboot.

However i am talking from experience with vista and may differ from xp.

---

### Post by hyper_ch on 2009-02-09
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by Le-Dart on 2009-02-09
OK, the last post was correct but didn't provide you with any of the help you're needing! Forum protocols are all very well, but you're here asking primarily for help. 

I would first of all try to re-install grub from the Ubuntu CD, how to here:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

If that succeeds then at least you can boot Ubuntu and that's a step in the right direction.

I do have difficulty understanding which partition you've deleted. I assume you've deleted the Windows partition - hence the grub 22 error - and the storage partition (50GB?)

The data WILL still be there, but it will depend on exactly what you did when you tried to change the partition table as to how immediately recoverable it is. If you can re-install grub and boot Ubuntu you need to mount the partition(s) you've lost and see what, if anything, is visible. If the data you've lost isn't visible then your options are a professional data recovery service, costs money but will recover your data, or using recovery software yourself. I've successfully used such software but only on Windows.

You may have to ask yourself how important the data really was, chalk it up to experience and start over from scratch. 

You've done what a lot of other people have done, myself included. It's all part of learning.

If there's any more help you need post back here.

---

### Post by arjuntank on 2009-02-09
the problem lies with the mbr
so fortunately your data is intact :)
i do have difficulty understanding ur question but i think u should use testdisk, backup data from drive c: and install a fresh copy of grub.
just follow these commands from the ubuntu live cd(open terminal first :P):
```

sudo grub
find /boot/grub/stage1

```
You will get something like hd0,0
type it here instead of hd0,0
```

root (hd0,0)
setup (hd0)

```
then a simple reboot would fix things!

---

