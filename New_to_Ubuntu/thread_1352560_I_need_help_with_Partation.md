---
title: "I need help with Partation"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by zuber786 on 2009-12-11
I install Kubuntu 
I made partition of 140 gb hdd
when I installed Ubuntu first time
I made like 70 gb for Ubuntu n rest for vista which was already installed,
for some reason my Ubuntu died and I reinstalled it, but now this time on partition screen it says to make partition again, and I made paraation again I wasn't able to go lower than 70 gb on Ubuntu to  I added 2 gb so Ubuntu is 72 gb n vista is rest, 
now everything works fine, but when I am on Ubuntu it says i only have 60 mb memory left, 
and i still see my old Ubuntu on the boot up screen.
please help me delete the old Ubuntu installation.

---

### Post by cholericfun on 2009-12-11
i dont get why you "have" to use more than 70GB space.
tapping in the dark: maybe you mounted the "old" ubuntu in the new one somewhere?
i.e. when you install you have to select your partitions to mount as / or /home etc. Did you do anything there?

maybe a look at how many partitions you have now would help:

```
sudo fdisk -l
```

you GRUB menu by the way is just outdated. just manually remove the options in menu.lst (after reading through it to see what is what...!)

back up that menu.lst file before though so you can restore it from a liveCD for example.

its in /boot/grub

---

### Post by zuber786 on 2009-12-11
yes it showed me some old settings screen and i made check mark on that screen
 I still don't know wht to do
there is screen shot of 
```
sudo fdisk -l
```

---

### Post by cholericfun on 2009-12-11
you've got 2*SWAP and 2*Linux partitions

looks like your other install is among the half-dead.

since you just recently installed i'd recoment another go at a fresh install. before you do, boot into the liveCD and go to "gparted" partition manager and reformat (and thus remove all linux installs) that mess to something usefull when installing. (say 1GB SWAP, 15GB / and rest for /home - see other recomendations for / though, not sure how much is needed there).
then install from cd, grub will be rebuild and show your vista and freshly installed ubuntu.


ok , hope i dont misinterpret anything, a bit unusual to have 3 ntfs part.

---

### Post by zuber786 on 2009-12-11
Hey 
you got it right on the money
I want to do everything over again
where can I find gparted, when I run the live cd?

---

### Post by harrisonk on 2009-12-11
[SIZE=4]In the  "system -> Administration" Menu[/SIZE].

---

### Post by cholericfun on 2009-12-11
ok, 
cool, just as a little confusion on my side

how did you manage to put 8 partitions in your HD without knowing bout gparted?

---

### Post by zuber786 on 2009-12-11
I don't know which one to remove

---

### Post by zuber786 on 2009-12-11
I don't know man, I just followed installation on ubuntu installation process

---

### Post by harrisonk on 2009-12-11
[SIZE=4]Why would you have 4 Linux-swap partitions and no EXT3 partition?

I would suggest backing up your data and then do the following:

On a live CD go to GParted and remove the 4 swap partitions and then reinstall Ubuntu (or Kubuntu you mentioned something about Kubuntu)

Hope your problem gets solved :D

Harrisonk
[/SIZE]

---

### Post by zuber786 on 2009-12-11
I am trying to delete the paration 
but it won't allow me 
it says
"Unable to delete /dev/asa6!
Please unmount any logical partitions having a number higher than 6."

---

### Post by zuber786 on 2009-12-11
oky
so this is how it looks


it turned off all the swap and deleted them

here is screen shot

---

### Post by harrisonk on 2009-12-11
[SIZE=4]Ok now reinstall Ubuntu, and it should solve your problems(I hope).

 [/SIZE]

---

### Post by cholericfun on 2009-12-11
i'd go and remove merge all that continuous empty space and start a new extended partition and then make a swap root and home partition in there.

---

### Post by harrisonk on 2009-12-11
> **cholericfun said:**
> i'd go and remove merge all that continuous empty space and start a new extended partition and then make a swap root and home partition in there.

[SIZE=4]That would be a good idea but I didn't want t say anything because I don't know how to do that.[/SIZE]

---

### Post by zuber786 on 2009-12-11
> **harrisonk said:**
> [SIZE=4]In the  "system -> Administration" Menu[/SIZE].

lol 
My friend behind me know all this very well
I didn't ask him for help
than I realised I might try asking him
he is Linux certified 

so this is how it looks now

now wht I want to know when I install ubunutu 
what should I do when I see
where to install ubuntu screen

---

### Post by zuber786 on 2009-12-11
how can I get rid of unallocated and merge it with my vista and I will create new partition during installation process.

---

### Post by harrisonk on 2009-12-11
> what should I do when I see
where to install ubuntu screen
[SIZE=4]I would think there would be an option on the installation that you could tell it to install on you ext3 file system.
If not delete the ext3 partition with GParted and then in the installer chose the largest amount of continues free space.

I am still a amateur so get verification before trying this :D

Hope this helps.

Harrisonk
[/SIZE]

---

### Post by zuber786 on 2009-12-11
he knows all but he doesn't know how to merge the unallloacted n primary space (vista)

---

### Post by zuber786 on 2009-12-11
here is where it gets confusing 
remember 53~ gb partition I had made, I dont see it.
what should I do.

---

### Post by dhysk on 2009-12-11
have you merged/gotten rid of all the partitions?  Second did format the 'new' merged block.  I can't remember but I had a simular problem with the installer not seeing it and it was because I eather had or didn't have the blocks partitions.  For the life of me I can't remember.

also since I'm not sure exactly ware you are at could you give us another 

```
sudo fdisk -l
```

---

### Post by harrisonk on 2009-12-11
[SIZE=4]Another reason is that when you dual boot you will have to move that slider, that 53 GB partition is the one that says "sda5".
[/SIZE]

---

### Post by harrisonk on 2009-12-11
[SIZE=4]I have the feeling everyone has gone to bed (at least in north America) but if I'm wrong I hope I haven't killed this thread:D

Harriosnk
[/SIZE]

---

### Post by zuber786 on 2009-12-12
Kool you all
I finally got it
all I had to do is swap partation n delete 
than it does to
unalllocated
than after that just make new partation TYPE EXT3.
trying installing ubuntu when it comes to where to install part
be carefull here
click on advance and there u will c the partition you made..
you might have to root it by typing "/" or "\" 
thank you all for help again
SOLVED.
love you ubuntu

---

