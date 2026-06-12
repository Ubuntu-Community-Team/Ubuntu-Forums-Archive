---
title: "Low memory issues"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by buntu2011 on 2011-03-25
Hello All, 

Complete Ubuntu newbie here. I installed Ubuntu 10.10 a week ago and was blown away. 
I used a live cd to install. I currently have a dual boot setup with xp (pre-existing) and ubuntu. 

Today when I logged in I kept getting constant messages reminding me of very low space. I searched around a bit and as suggested on some forums tried the df -h. the output 

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             2.6G  2.5G  924K 100% /
none                  495M  256K  494M   1% /dev
none                  500M  368K  500M   1% /dev/shm
none                  500M   92K  500M   1% /var/run
none                  500M     0  500M   0% /var/lock
/dev/sda3             7.8G  2.1G  5.4G  28% /media/de8551f4-0888-4940-a17c-b6311994fd9b

And I have no clue where to proceed from here//what to do. Suggestions/help will be greatly appreciated. 

Thank You :)

---

### Post by blind2314 on 2011-03-25
You're getting the alerts because / (your root partition, the one where all your system files reside) is 100% full. This is a bad thing.
 
Using gparted (which is on the Ubuntu Live CD) will be your best bet for fixing it. Boot off the live CD again, and run gparted. There are options to grow/shrink partitions, but it's not something you want to do unless you're sure of what you're doing (it's a safe procedure, but very easy to make mistakes if you don't pay attention). Google around for "growing a partition with gparted", and you should find some nice tutorials.
 
If you have more questions or run into issues, post back and myself or someone else can help you out.

---

### Post by crispy_420 on 2011-03-25
How big is that hard drive? Like mentioned earlier, 100% in use is not good no matter the OS. So you need need to expand the drive as blind2314 stated or start trimming what is there. With only 2.6GB dedicated you may what to opt for increasing available space.

---

### Post by buntu2011 on 2011-03-25
hi ,

i ran gparted off live cd and this is what it says 
[IMG]https://lh4.googleusercontent.com/-cy5pm4XBulE/TYy4z-B8ZUI/AAAAAAAAIZA/6k14Ht7ycOQ/s1600/Screenshot.jpg[/IMG]

[https://lh4.googleusercontent.com/-cy5pm4XBulE/TYy4z-B8ZUI/AAAAAAAAIZA/6k14Ht7ycOQ/s1600/Screenshot.jpg](https://lh4.googleusercontent.com/-cy5pm4XBulE/TYy4z-B8ZUI/AAAAAAAAIZA/6k14Ht7ycOQ/s1600/Screenshot.jpg)


Can you please suggest how to proceed from here. I am a bit tensed as i dont want to mess with any of the NT partitions. 

[IMG]file:///home/ubuntu/Desktop/Screenshot.jpg[/IMG]

---

### Post by r-senior on 2011-03-25
If you want to claw back some space in the short term, you could:

a. Empty your trash

b. Empty the cache in Firefox

c. Clean out any unused software packages

```

$ sudo apt-get update
$ sudo apt-get autoremove

```

(This may or may not remove packages).

d. Clean out archived log files

```

$ cd /var/log
$ sudo rm *.gz

```

This won't delete current log files, only those that have been moved into archives.

That might give you enough space to move, then you can go to Software Centre or Synpatic and perhaps remove some packages you don't need. If you don't use Open Office, that would be a big chunk gone.

Generally speaking, aim for at least 6-8GB (excluding your own files) for an Ubuntu installation. If you are starting again, it's a really good idea to have a separate /home partition from your root partition so that you can upgrade more easily. 

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by r-senior on 2011-03-25
How much memory (RAM) is there in that machine buntu?

---

### Post by buntu2011 on 2011-03-25
1 gb. is it ok if i delete /dev/sda3 (ext4,7.89 gb) from /dev/sda and reassign the empty space to sda 6 ?

---

### Post by stoogiebuncho on 2011-03-25
> **buntu2011 said:**
> 1 gb. is it ok if i delete /dev/sda3 (ext4,7.89 gb) from /dev/sda and reassign the empty space to sda 6 ?

You'll probably want to check what's saved in there, first.  It looks like you have over 2 gigs of data there.

---

### Post by blind2314 on 2011-03-25
> **buntu2011 said:**
> 1 gb. is it ok if i delete /dev/sda3 (ext4,7.89 gb) from /dev/sda and reassign the empty space to sda 6 ?
 
 
Yes, that's fine. However, as mentioned, make sure you copy anything you want off of there first.

---

### Post by buntu2011 on 2011-03-25
how do i  go about reassigning the space gained by erasing/deleting  /dev/sda3 (ext4,7.89 gb) to sda 6 ?

Thank you all for your replies and help. Much appreciated. 



Today you... Tomorrow me

---

### Post by Dutch70 on 2011-03-25
Looks to me like you need to wipe them all and start over. You also have 2 Swap partitions which is 1 too many, but both of them together aren't large enough. Don't forget to back up your files!
Sorry to say, you've got quite a mess there.

I'd wipe everything but sda1. Use the entire space to create an extended partition. Inside that make 2 partitions. 
1. Swap partition equal to the size of your RAM.
[[COLOR="RoyalBlue"]SwapFaq[/COLOR]]("https://help.ubuntu.com/community/SwapFaq")

2. "/" aka "root" = the remainder of your hdd space. 

[[COLOR="RoyalBlue"]Gparted Tutorial[/COLOR]]("http://www.dedoimedo.com/computers/gparted.html")

---

