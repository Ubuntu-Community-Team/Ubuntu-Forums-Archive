---
title: "I Don't understand using the UUID in GRUB - tri booting with win 7"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by stoer on 2009-02-07
Hi everybody,

I guess that I've a pretty typical question as regards a pretty typical problem.

On my laptop I'm currently double booting Ubuntu 8.10 with windows XP, OK straight forward.
Now I want to trial the Windows 7 beta, So now I want to tri -  boot.

I understand that when I install win 7 I'll lose GRUB, but that it's possible to reinstall GRUB and set both win xp and win 7 as options within the start up menu.
[B][U]
The following guide sort of makes this sound pretty simple...[/U][/B]

.....Then, you either need to adjust the W7 boot loader with EasyBCD (instructions can be found on the apcmag guides) or, preferably, reinstall the GRUB Boot loader by doing the following:

Insert the Ubuntu Live CD (or flash disk or whatever) and select "Try without changes to computer." Once it loads up, open a terminal and type "sudo grub"

Then enter the following commands in order.

```

- root (hd0,0)
- setup (hd0)
- quit
- exit 

```

Reboot, and it will go directly back to Ubuntu. Now you'll need to edit GRUB to get the Windows partitions. You have two options - enter BOTH Windows partitions into GRUB, or just enter W7, and use the W7 bootloader to then select XP. To edit grub, key into the terminal "sudo gedit /boot/grub/menu.lst" (or replace gedit with whatever program you prefer) and make sure that the option "hiddenmenu" has a '#' in front of it to make it visible. Then go to the very bottom where all the Ubuntu kernels are listed and add the following **_(NOTE: The location (hdX,X) may be different for your install):_**

```

title Windows XP
root (hd0,1)
makeactive
chainloader +1 

title Windows 7
root (hd0,2)
makeactive
chainloader +1 

```


My problem is with not understanding what to do with UUIDS.
Im happy with hd0,0 etc but what do I do with   **uuid     22cd1ee4-c7b3-4259-97ce-7d1dc60ed939 ??**

For example I need to enter the following..

```

- root (hd0,0)
- setup (hd0)
- quit
- exit 

```

But if on my system windows **xp is sitting nicely at (HD0,0)**

and presumably Ubuntu starts on (HD0,1) and so on 

(see code)

```

s -l /dev/disk/by-uuid/

total 0

lrwxrwxrwx 1 root root 10 2009-02-07 22:24 19c3fba1-5c7b-4780-badb-d820bb8543a4 -> ../../sda5


lrwxrwxrwx 1 root root 10 2009-02-07 22:24 22cd1ee4-c7b3-4259-97ce-7d1dc60ed939 -> ../../sda2


lrwxrwxrwx 1 root root 10 2009-02-07 22:24 74F809DBF8099C8C -> ../../sda1


lrwxrwxrwx 1 root root 10 2009-02-07 22:24 defa2a5f-afb1-487e-9d13-842ca482acf8 -> ../../sda6



```

How do I proceed further???
Any help will be very greatly appreciated.

---

### Post by theozzlives on 2009-02-07
I wonder if there's a way to use the Windows Boot Menu after grub to decide which Windows you want. So you go to grub, select Windows, then select which one. You would have to install through XP instead of booting off the CD. That's a theory any comments?

---

### Post by kansasnoob on 2009-02-07
Go to terminal and run:

```
cat  /boot/grub/menu.lst
```

Copy-n-paste it to your email account, and print it (just in case).

Of course that assumes that you're repartitioning doesn't result in changing the UUID(s).

Then when you restore GRUB you'll need to know which partitions your 2 Win OS's are on! And remember that GRUB starts numbering with 0 (zero)!

---

### Post by stoer on 2009-02-07
> **kansasnoob said:**
> Go to terminal and run:

```
cat  /boot/grub/menu.lst
```

Copy-n-paste it to your email account, and print it (just in case).

Of course that assumes that you're repartitioning doesn't result in changing the UUID(s).

Then when you restore GRUB you'll need to know which partitions your 2 Win OS's are on! And remember that GRUB starts numbering with 0 (zero)!

Thanks for replying.
Xp is installed first, before Ubuntu on my laptop. (hd 0,0)
I'll partition my xp partition to create the room for win7 - is it logical to think that win xp (hd 0,0) will result in win 7 being created at (hd 0,1)? **or is that a dangerous assumption??**
And how can i then check this?

Do you mean that the Ubuntu posisitions / UUIDS won't need to be altered in /boot/grub/menu.lst  Only if the UUID changes as a result of partitioning?
Thus-
1. create the partition
2. Check to see if the UUID'S are changed
   If they are changed what do i need to do then?


I've read that i can either choose to select just win 7 in grub, which will then, if chosen at start up, present me with a choice of booting win 7 or "older os" (xp).
or
to enter both os's in grub as seperate options to start up.

---

### Post by stoer on 2009-02-08
Ok..
dumb.... i went ahead anyway.

I'd like to amend my question to,
How to restore grub after installing xp  ;)

I took a look at win 7, ok didn't blow me away.
took care of removing it and restored the xp boot loader.

Now i'd just like to getback into my shiny working and reliable Ubuntu, please anyone?

There's a load of info on restoring the grub, the following was a typical example
[http://ubuntuforums.org/showthread.php?t=42030](http://ubuntuforums.org/showthread.php?t=42030)
Another guide showed how to mount your system whilest working in a live cd enviroment

Unfortunately neither method seems to work for me.
The first method fails at find /boot/grub/stage1
and the second method failed to mount anything....

I tried starting via a live cd version of ubuntu,
then from terminal
[B]1. Boot from a Live CD
2. Open a Terminal. Go SuperUser
3. Type "grub".
4. Type "find /boot/grub/stage1". = eg "(hd0)" 
5. Type "root (hd0,3)".
6. Type "setup (hd0,3)".[/B] This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".
7. Type "quit"

Anyone got a link to something els i could read, what about "super-grub"? or easyBCD (anyone any experience with that?)

I would really, appreciate any tips that you might think to be usefull.
Cheers.:p

---

### Post by Kellemora on 2009-02-08
Hi stoer

Don't know if this will help you or not, but it might help?

It's for fixing the MBR so it points to GRUB........

In Terminal type "sudo grub" without the quotes.
Then type in "find/boot/grub/stage1" again without the quotes.
You use this info to SET the root device!

Then you would type "root (hd0,1)"  IF 1 is Grub, could be 2, 3, etc.
Then you would type "setup (hd0)"
then type "quit"

TTUL
Gary

---

### Post by stoer on 2009-02-08
> **Kellemora said:**
> Hi stoer

Don't know if this will help you or not, but it might help?

It's for fixing the MBR so it points to GRUB........

In Terminal type "sudo grub" without the quotes.
Then type in "find/boot/grub/stage1" again without the quotes.
You use this info to SET the root device!

Then you would type "root (hd0,1)"  IF 1 is Grub, could be 2, 3, etc.
Then you would type "setup (hd0)"
then type "quit"

TTUL
Gary

Hi Garry,
Thanks alot for replying.
Sorry for not making myself clearer in the last post.
The steps you mention are precisely the steps i have tried...
It falls down on 
**find/boot/grub/stage1**
which didn't deliver an output.

trying randomly with 
Root (hd0,**X**) and Setup (hd0) obviously isn't delivering anything either.

I think this is possibly something to do with access permissions - using a live cd, because if i look up the grub setup file, on my system everything is write/access protected.

Another approach i scanned (yet another guide), was to mount the necessary files and change the access permissions.... Unfortunately i didn't manage to get past the first two lines of this guide having received a warning that the file didn't exist or was possibly busy.

But, thanks for taking the time, appreciate it.
Cheers.;)

---

### Post by lswest on 2009-02-08
Be sure to have a space between find and the search term (in this case /boot/grub/stage1).

Don't know if this covers anything you didn't know, but there's a guide on my blog which details this: [http://lswest-ubuntu.blogspot.com/2008/06/installing-bootloader-how-to.html](http://lswest-ubuntu.blogspot.com/2008/06/installing-bootloader-how-to.html)

Also, post the output of ```
sudo fdisk -l
```

(or, if you want to go ahead without input from me or anyone else, take the result of the above output, which should look like "/dev/sda6           16071       18490    19438618+  83  Linux", take the "/dev/sdaX" from the result and subtract 1 from the number at the end, so in my case it would be 5, and use that as the value for root(hd0,5), then setup(hd0))

Also, note the lack of spaces in "root(hdx,x)" and "root(hd0)"

---

### Post by stoer on 2009-02-08
Hi Kellemora and lswest,
Firstly i'd really like to thank the two of you for taking the time, i really appreciate it.
I followed the advice from both of you to the letter, the only thing i have done differently tonight is use a different version of the Ubuntu live cd (my earlier attempts were with an old beta) and tonight with a recently downloaded version.

Kellemora - i may have already tried what you suggested, but to be sure i tried again.
**find/boot/grub/stage1** (no spaces) returned an unknown command error.

** find /boot/grub/stage1** (with space) returned an (hd0,1)


lswest
sudo fdisk -l gave me  /dev/sda2   and so subtracting 1 gave me (hd0,1)

**root(hd0,x)**   no spaces returned an unknown command error, whilest

**root (hd0,x)**  with space did the trick :D

setup was the same as root, with a space it did what you both said it should.
A final "quit" and voilla!!

Why it worked now and not earlier today?, i can't tell you.

But i will thank you both again, i've got my shiny bright Ubuntu back where it belongs,
CHEERS!!!:D

---

### Post by lswest on 2009-02-09
Great :)  I'm glad you got it working again, and I'm not sure why it didn't work before, maybe you missed a space, had a space too many, or something seemingly arbitrary like that.  In any case I'm glad I could help.

Lswest

---

