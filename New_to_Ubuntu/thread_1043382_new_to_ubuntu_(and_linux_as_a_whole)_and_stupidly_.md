---
title: "new to ubuntu (and linux as a whole) and stupidly removed perl"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by jennwesxc on 2009-01-18
Hi,

I have to 2go PC  laptop which is the first laptop I've ever owned that uses linux. Yesterday when I tried to install updates I was told that I had a broken package. I'm a newbie, so it was my first time encountering such a thing. I used synaptic package manager to identify the broken package. It was perl. I tried the "fix broken packages" button, but it didn't help. I tried reinstalling perl, but that wasn't an option. so then, like an idiot, I chose to remove perl along with the couple hundred things associated with it.

In an effort to fix my problem, I've been on the forums. Advice in response to a problem similar to mine was to try "sudo apt-get install ubuntu minimal ubuntu desktop"  I tried that but was told "not enough free space in /var/cache/apt/archives"

I'm surprised that my space would be so small because I never had much on this computer beyond what came on it by default. That said, can anyone tell me how to free the space that I need? And, if I do that, does it seem reasonable that if I try the install ubuntu-minimal ubuntu-desktop command I could fix my problem?

Thank you very much for any help you can offer. I recognize that I was stupid.

Jenn

---

### Post by earthpigg on 2009-01-18
does the vendor of your laptop offer a system restore cd?

if its new and has nothing important on it, that may be the _easiest_ and _simplest_ way to get a clean start...

---

### Post by kansasnoob on 2009-01-18
Well, first of all, I must say I've never used Edubuntu so I'll do a little studying.

But do you have the Edubuntu live CD or any installation media whatsoever?

---

### Post by twright on 2009-01-18
the command apt-get clean should fix your space problem, then trying to reinstall ubuntu minimal might work. Otherwise a reinstall might be a better option. Just for your info, you can  fix broken packages by pressing escape at bootup when it prompts for the grub menu selecting the first recovery option and then selecting fix broken packages :-)

---

### Post by jennwesxc on 2009-01-18
My laptop didn't come with any installation CDs or anything (my laptop doesn't actually have a cd rom drive, although I could probably borrow one that'll plug into my USB). 

It's not too big of a deal to me if I lose the few files I had on my laptop; I just want to get the thing up and running again. 

I've browsed the ubuntu site and done some initial reading on how to install ubuntu, but it seems pretty intimidating based on my current knowledge (for example, they mention different partitions and that's something I don't really understand). Can you offer any advice as far as next steps for me?

Thanks a lot,

Jenn

---

### Post by jennwesxc on 2009-01-18
I just tried the command apt-get clean and got this:

E: could not open lock file/var/cache/apt/archives/lock - open (13 permission denied)

Do you know what that means?

Jenn

---

### Post by kansasnoob on 2009-01-18
> **jennwesxc said:**
> My laptop didn't come with any installation CDs or anything (my laptop doesn't actually have a cd rom drive, although I could probably borrow one that'll plug into my USB). 

It's not too big of a deal to me if I lose the few files I had on my laptop; I just want to get the thing up and running again. 

I've browsed the ubuntu site and done some initial reading on how to install ubuntu, but it seems pretty intimidating based on my current knowledge (for example, they mention different partitions and that's something I don't really understand). Can you offer any advice as far as next steps for me?

Thanks a lot,

Jenn

One of the reasons I asked if it came with any installation media (Live CD's) was to see if we could use the live CD to get some system info. Since that's not an option give us a chance.

The last post sounded promising to me.

---

### Post by ibuclaw on 2009-01-18
```
sudo apt-get clean
```
Then enter in your password.

Then run:
```
sudo apt-get install ubuntu-minimal
```
And hope for the best :)

Regards
Iain

---

### Post by kansasnoob on 2009-01-18
I just looked to see what all packages are removed with the removal of perl and it removes the entire ubuntu-desktop.

Now we can't tell how your machine is partitioned but if you can get back to the terminal try running:

```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by jennwesxc on 2009-01-18
Thanks for the advice everyone has offered so far. Here's where I'm at:

I just tried apt-get clean and (without hitting enter first) typed in my password (I don't know if that does anything, but last time I tried apt-get clean, it never prompted me for my password, it just gave me the error message that I posted earlier.) Anyway, when I did that nothing happened. It just went immediately back to "default@2gopc"

So then I tried just plan apt-get clean and it, too, went immediately back to default@2gopc

I tried once more sudo apt-get install ubuntu minimal. that went through and--if I'm reading everything right--it looks as though that's already on my system and, I think, in okay shape.

Then I tried sudo apt-get install ubunto-desktop again (I also tried (sudo apt-get install --reinstall ubunto-desktop) and it gave me the same error message I've been getting, saying that I don't have enough freespace in /var/cache/apt/arvhives

Any thoughts on what to try next?

Thanks,
Jenn

---

### Post by twright on 2009-01-18
if you did still want to reinstall ubuntu it is an easy process. You don't need to deal with partitioning if you just want to use your whole harddrive for the installation.

---

### Post by ibuclaw on 2009-01-18
> **jennwesxc said:**
> Thanks for the advice everyone has offered so far. Here's where I'm at:

I just tried apt-get clean and (without hitting enter first) typed in my password (I don't know if that does anything, but last time I tried apt-get clean, it never prompted me for my password, it just gave me the error message that I posted earlier.) Anyway, when I did that nothing happened. It just went immediately back to "default@2gopc"

Ah, ok. So your laptop was setup so you don't need a password for administrative work. No need to worry about passwords then. That is fine.

> 
Any thoughts on what to try next?

Thanks,
Jenn
Well, lets just start from the beginning, lets just remove all apt and dpkg type lists/packages.
```
sudo rm /var/lib/apt/lists/partial/*
```
```
sudo rm /var/cache/apt/archives/*
```
Copy and paste each line into the terminal followed by 'enter'.

Now run:
```
sudo apt-get update
```
```
sudo apt-get install ubuntu-minimal
```

If you get any problems, can you post the output of these commands?
They may give us a clue as to what is preventing you from running installs/updates.
```
df -ha
```
```
sudo du / -ha --max-depth=1 2>/dev/null
```
Regards
Iain

---

### Post by jennwesxc on 2009-01-18
> **tinivole said:**
> Ah, ok. So your laptop was setup so you don't need a password for administrative work. No need to worry about passwords then. That is fine.


Well, lets just start from the beginning, lets just remove all apt and dpkg type lists/packages.
```
sudo rm /var/lib/apt/lists/partial/*
```
```
sudo rm /var/cache/apt/archives/*
```
Copy and paste each line into the terminal followed by 'enter'.

Now run:
```
sudo apt-get update
```
```
sudo apt-get install ubuntu-minimal
```

If you get any problems, can you post the output of these commands?
They may give us a clue as to what is preventing you from running installs/updates.
```
df -ha
```
```
sudo du / -ha --max-depth=1 2>/dev/null
```
Regards
Iain

I just tried sudo rm /var/lib/apt/lists/partial/*

and got this message: "cannot remove 'var/lib/apt/lists/partial/*': no such file or directory

Then I tried sudo rum /var/cache/apt/archives/* and was told:

rm: cannot remove /var/cache/apt/archives/partial': Is a directory.

When I typed df -ha this is what I got:

Filesystem    size   Used   Avail   Use%  Mounted on
unionfs       335M   250M   86M     75%   /
proc          0      0      0       -     /proc
/sys          0      0      0       -     /sys
varrun        248M   72K    248M    1%    /var/run
varlock       248M   0      248M    0%    /var/lock
udev          248M   44K    248M    1%    /dev
devshm        248M   0      248M    0%    /dev/shm
devpts        0      0      0       -     /dev/pts
/dev/sda3     380M   143M   238M    38%   /var
/dev/sda4     35G   1001M   35G     3%    /home

When I tuped sudo du / -ha --max-depth=1 2>/dev/null

1.1.G  /usr
12K    /lost+found
75M   /lib
133M   /var
5.8M   /sbin
825M  /home
195K   /tmp
5.0M  /bin
1.0K  /media
110K  /root
1.9G  /rofs
7.5M /etc
772M  /boot
44K  /dev
0    /initrd
0    /initrd.img
0   /mnt
0    /opt
0   /proc
0   /srv
0   /sys
0   /vmlinuz
4.7G   /

Does that help at all?

Thanks,
Jenn

---

### Post by yeats on 2009-01-18
if you type 

```
df -h
```

This will give you a list of the space used and space free on each partition.  The output would probably be useful information to post here.  Also, do you have many files in the /var/cache/apt/archives folder?  You can discover this by typing

```
ls -la /var/cache/apt/archives
```

UPDATE - I see someone beat me to this advice :-) I was reading the top of the thread.  Good luck.

---

### Post by jennwesxc on 2009-01-18
> **twright said:**
> if you did still want to reinstall ubuntu it is an easy process. You don't need to deal with partitioning if you just want to use your whole harddrive for the installation.

If I'm understanding the edubuntu website right, in order to reinstall edubuntu I need to download a CD, then burn it onto a CD, right? Once I've done that, will it be clear (given that I'm new to all this) what I need to do?

Also, my computer came with edubuntu and, while I'm happy to put that back on (I just want my computer to work again), I'd rather have just plain ubuntu. Can I do that, or does my computer (Intel 2go PC) need to use edubuntu?

Thanks, Jenn

---

### Post by kansasnoob on 2009-01-18
Two Cd's for Edubuntu:

[http://www.edubuntu.org/Download](http://www.edubuntu.org/Download)

> Install Edubuntu
Install Edubuntu Desktop

In order to install Edubuntu 8.10 Desktop permanently on a computer, you will need the following two CDs

   1. Get the Ubuntu 8.10 Desktop CD - You are free to choose the Alternate CD, if you prefer a text-based installer.
   2. Get the Ubuntu Education CD 8.10

---

### Post by jennwesxc on 2009-01-18
> **chrissharp123 said:**
> if you type 

```
df -h
```

This will give you a list of the space used and space free on each partition.  The output would probably be useful information to post here.  Also, do you have many files in the /var/cache/apt/archives folder?  You can discover this by typing

```
ls -la /var/cache/apt/archives
```

UPDATE - I see someone beat me to this advice :-) I was reading the top of the thread.  Good luck.

This is what I get when I type ls -la /var/cache/apt/archives:

total 13
drwxr-xr-x 3 root root 11264 2009-01-18 19:42 .
drwxr-xr-x 3 root root 1024  2009-01-18 14:09 ..
-rw-r----- 1 root root   0 2009-01-18 19:43 lock
drwxr-xr-x 2 root root 1024 2009-01-17 21:14 partial

also, I don't know if it matters, but the "." ".." and word "partial" that are at the end of the lines are in blue, rather than white like everything else.

Thanks,
Jenn

---

### Post by ibuclaw on 2009-01-18
> **jennwesxc said:**
> 
When I typed df -ha this is what I got:

Filesystem    size   Used   Avail   Use%  Mounted on
unionfs       335M   250M   86M     75%   /
proc          0      0      0       -     /proc
/sys          0      0      0       -     /sys
varrun        248M   72K    248M    1%    /var/run
varlock       248M   0      248M    0%    /var/lock
udev          248M   44K    248M    1%    /dev
devshm        248M   0      248M    0%    /dev/shm
devpts        0      0      0       -     /dev/pts
**/dev/sda3     380M   143M   238M    38%   /var**
/dev/sda4     35G   1001M   35G     3%    /home

Your /var directory is a mounted filesystem with 238MB free.
I'm not such of the significance of this, but it may appear that ubuntu-minimal is too large to keep inside this partition.
To resolve this, we'll have to figure out how to copy the data out of the partition into a directory, umount the filesystem, and move the copied directory to the original location.

If anyone would like to help, please do.
But the way I am thinking this through, we'll need a LiveCD in order to carry out the task either way.

Regards
Iain

---

### Post by jennwesxc on 2009-01-18
> **tinivole said:**
> Your /var directory is a mounted filesystem with 238MB free.
I'm not such of the significance of this, but it may appear that ubuntu-minimal is too large to keep inside this partition.
To resolve this, we'll have to figure out how to copy the data out of the partition into a directory, umount the filesystem, and move the copied directory to the original location.

If anyone would like to help, please do.
But the way I am thinking this through, we'll need a LiveCD in order to carry out the task either way.

Regards
Iain

This is probably a dumb question (then again, it's coming from the person who hit "yes" to deleting perl and everything associated with it...), but what is a LiveCD? Is that the edubuntu CD that I'd download or order from the website?

Thanks for the time and effort you all are putting into this. I really appreciate it.

Jenn

---

### Post by kansasnoob on 2009-01-18
Live CD burning info:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by yeats on 2009-01-18
Actually, this line in your df -h concerns me:

> /dev/sda4 35G 1001M 35G 3% /home

it looks like your home partition has the majority of the hard disk space.  perhaps this would be solved with resizing your existing partitions - again a live CD task ...

---

### Post by jennwesxc on 2009-01-18
My laptop doesn't have a CD drive, so I'll have to find one that I can plug into my USB. It might be a couple days before I'm able to do that, so I'll sign off for now here.

Thanks so much for all your ideas and advice.

Jenn

---

### Post by ibuclaw on 2009-01-20
> **chrissharp123 said:**
> Actually, this line in your df -h concerns me:



it looks like your home partition has the majority of the hard disk space.  perhaps this would be solved with resizing your existing partitions - again a live CD task ...

Chris Sharp++

But, in order to resize the partitions, they still must be unmounted. And that requires for you to be at least booted in a LiveCD environment.

I've just assigned myself to this thread, so if the OP replies back, I'll give directions on resizing.

Regards
Iain

---

