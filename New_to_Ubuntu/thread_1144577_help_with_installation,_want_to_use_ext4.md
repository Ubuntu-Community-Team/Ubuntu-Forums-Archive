---
title: "help with installation, want to use ext4"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by db4sn3r on 2009-04-30
Hi all,

I am a very very very noobish Ubuntu user, I am going to install ubuntu 9.04 onto my samsung nc10.  I was going through the menus looking for the new-fangled ext4 that I heard about from a friend who uses ubuntu also.  I eventually found it in the advanced section of the installer, however, I have no idea what mount point I would like to do, how would I figure this out.  I would like to install this next to some of my other partitions, not over the entire drive, what do I do?  If you need to ask questions about my system I will gladly provide them, if I can figure out how to find the info you want that is.  If you could tell me EXACTLY what to type in that would be amazing as I really don't want to mess my system up

Thank you all vey much it is greatly appreciated,
db4sn3r

---

### Post by yoasif on 2009-04-30
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

obviously use ext4 where it says ext3.

---

### Post by db4sn3r on 2009-04-30
> **yoasif said:**
> [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

obviously use ext4 where it says ext3.
so it should be / ? it says something about making a /home, but it says that is more of a backup type of thing, and in the diagram/photo on the site, it reads 

Ubuntu    /    ext3

 so which do you think I should use?  sorry about being annoying, I really appreciate it!

---

### Post by yoasif on 2009-04-30
I would make a separate /home but that is optional. 

At the minimum, you need / and swap (make swap 1.5x the amount of ram in your machine -- if you have 2 gb, use 3 gb for swap). 

20 gb for / and the rest for /home works well for most people, along with swap. if you have a smaller hard drive, obviously work with that.

---

### Post by db4sn3r on 2009-04-30
hi I am again very sorry for botheringyou or anyone viewing this thread, but I got an error

Error informing the kernel about modifications to partition /dev/sda5 -- Device or resource busy. This means Linux won't know about any changes you made to /dev/sda5 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.

 I haven't hit the ignore button yet, is this a very bad error? I am not sure what sda5 contains, I don't know how to check without restarting the entire installer.

---

### Post by TheNosh on 2009-04-30
> **yoasif said:**
> I would make a separate /home but that is optional. 

At the minimum, you need / and swap (make swap 1.5x the amount of ram in your machine -- if you have 2 gb, use 3 gb for swap). 

20 gb for / and the rest for /home works well for most people, along with swap. if you have a smaller hard drive, obviously work with that.

actually swap is not required, just highly suggested. for instance gparted gives me an error messege if i try to make my hard drive in to more than 4 partitions. i got it with vista and a "RECOVERY" partition (which i'm not sure if i need cause i don't really care about vista but i'm to lazy to screw with it) and i insist on a separate /home for myself so that uses all four leaving no room for swap and i run jaunty just fine.

that being said, if at all possible you should tr to have a swap partition, separate /home is a good idea too so if you're comfortable setting it up go for it

---

### Post by TheNosh on 2009-04-30
> **db4sn3r said:**
> hi I am again very sorry for botheringyou or anyone viewing this thread, but I got an error

Error informing the kernel about modifications to partition /dev/sda5 -- Device or resource busy. This means Linux won't know about any changes you made to /dev/sda5 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.

 I haven't hit the ignore button yet, is this a very bad error? I am not sure what sda5 contains, I don't know how to check without restarting the entire installer.

never gotten that, personally i would do what it says and reboot , then try again

or google the error to see what if i can find any info on it

---

