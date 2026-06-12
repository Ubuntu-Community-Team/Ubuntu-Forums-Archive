---
title: "Increase partition"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by FM101 on 2010-05-27
I have a duel boot, win 7 and ubuntu 10.04.
I am getting a low disk space error
How can you increase the Ubuntu partition?


[IMG]http://img46.imageshack.us/img46/8370/lowdiskspace002.jpg[/IMG]

---

### Post by Ozymandias_117 on 2010-05-28
Boot to a liveCD, use GParted to make the Windows partition smaller, then increase Ubuntu's partition. (Make sure to back up important files before doing any repartitioning just in case)

[IMG]http://desmond.yfrog.com/Himg43/scaled.php?tn=0&server=43&filename=screenshotresizemovedev.png&xsize=640&ysize=640[/IMG]

---

### Post by bumanie on 2010-05-28
Firstly try and clear some space > sudo apt-get autoclean > sudo apt-get cleanFirst command clears out old, left over files and removes package files that can no longer be downloaded, and are largely useless. Second command clean clears out the local repository of retrieved package files. It removes everything but the lock file from /var/cache/apt/archives/  and /var/cache/apt/archives/partial/. That's a good starting point before playing with repartitioning. After doing that, post the output of command > df -h

---

### Post by Nedabiah on 2010-05-28
Thanks bumanie. The df -h command is great. It's a much quicker way to find out disk space than by using the disk analyzer gui.

---

### Post by Jakiejake on 2010-05-28
> **Nedabiah said:**
> Thanks bumanie. The df -h command is great. It's a much quicker way to find out disk space than by using the disk analyzer gui.

Yeah But I recommend Using Gparted to equal out the space

---

### Post by Elfy on 2010-05-28
When you boot the livecd swap will be mounted - you'll need to turn that off - right click the swap partition - swapoff.

You will like also need to resize the extended partition (makes assumption you have one) BEFORE you can expand the ubuntu partition.

---

### Post by crackpotfox on 2010-06-27
ok, i went onto windows vista and shrank the volume. Unallocated space

when i booted from live cd and used the terminal command "sudo gparted", it wouldn't let me expand or move any of my ubuntu partition. also, the partition had a lock beside it at the bottom area of the window.

---

### Post by Mark Phelps on 2010-06-28
> **crackpotfox said:**
> ok, i went onto windows vista and shrank the volume. Unallocated space

when i booted from live cd and used the terminal command "sudo gparted", it wouldn't let me expand or move any of my ubuntu partition. also, the partition had a lock beside it at the bottom area of the window.

That's because the Ubuntu partition is probably mounted.  Try unmounting it in GParted and then see if it will let you do anything to it.

---

### Post by mikechant on 2010-06-28
> That's because the Ubuntu partition is probably mounted.

More likely the swap partition is mounted (see comment #6 above).

---

### Post by crackpotfox on 2010-06-28
ok, sorry, but what doyou mean by "mounted" and how do i unmount it

edit: ok i'll try to unmount

another edit: i unmounted, and the repartitioning worked.  One last question: do i need to remount the thing i unmounted.... i think it is swap

---

### Post by Dave68 on 2010-06-28
Open a Terminal and type in:
 
apropos unmount
 
 
 
You could also use:
 
man unmount
 
 
 
Both of these commands will give you a definition of the funtion.
 
Just a couple of things (commands) that are really handy when not familiar with the Terminal.
 
Thanks,
Dave

---

### Post by Elfy on 2010-06-28
> **crackpotfox said:**
> ok, sorry, but what doyou mean by "mounted" and how do i unmount it

edit: ok i'll try to unmount

another edit: i unmounted, and the repartitioning worked.  One last question: do i need to remount the thing i unmounted.... i think it is swap

```
sudo swapon -a
```

---

### Post by crackpotfox on 2010-06-28
ok, i got it to work... just right clicked the swap and unmounted (can't remember what it said), and expanded the partition

Thanks Everyone!

---

