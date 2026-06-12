---
title: "Drive Partitions"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by keygiwawah on 2008-12-12
I'm partitioning my drive and installing ubuntu.  How large should I make the partition?  My hard drive is about 40 gb.

---

### Post by LowSky on 2008-12-12
I assume 40GB turns into 37GB so...
15GB for root, 20GB for home, 2GB for Swap

---

### Post by SuperSonic4 on 2008-12-12
What else is to go on the drive?

Assuming the full disc I would go

/ = 15gb
swap = 2*ram or 2gb max
/home = 23gb (ie the rest)

---

### Post by keygiwawah on 2008-12-12
I'm partitioning the drive and leaving windows on it... I don't want to use up all of it for ubuntu, I just want a little more memory than required to run it.

---

### Post by Paqman on 2008-12-12
How much of the drive is Windows already using? Could be a fairly tight fit on 40GB.

---

### Post by keygiwawah on 2008-12-12
I don't need much room for the xp, I'll just delete stuff from it and make more room.  I have not made the partition yet... I'm just waiting until I know how much space ubuntu should have.

---

### Post by az on 2008-12-12
> **keygiwawah said:**
> I don't need much room for the xp, I'll just delete stuff from it and make more room.  I have not made the partition yet... I'm just waiting until I know how much space ubuntu should have.

If you are just going to use your computer for everyday work, then give it 10 gigs of free space and let the installer create the / (root) and swap partition out of that.  Don't create the partitions yourself, there is no need to do that.  There is no real reason to create a separate home partition either.

The installation itself only requires about 2 gigs of disk space.  It just depends what you do with your computer.  Do you download a lot of big files?  Do you store your lifelong photo collection on your drive?  What do you do that requires disk space?

---

### Post by keygiwawah on 2008-12-12
I just have a lot of movies and stuff on my computer.  Thats all thats on the xp really

---

### Post by tomtom1982 on 2008-12-12
For running rationally, XP need to have 10 GB (if you've much software, you'll need more space).

You can also install ubuntu and let it reduce your XP-partition (it's the first option which is displayed on partition-screen during installation). It will suggest to take 50 % of the partition-size, but you can also choose lower space. If you'll do it so, you won't have a seperate /home partition, but the SWAP will be generated automaticly.

---

### Post by Duck2006 on 2008-12-12
[http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)

---

### Post by Paqman on 2008-12-12
> **keygiwawah said:**
> I just have a lot of movies and stuff on my computer.  Thats all thats on the xp really

Give XP as much space as it needs, plus about 5-10GB. Use the rest for Ubuntu (you'll need at least about 10GB). Ubuntu will need a swap partition the same size as your RAM if you want to use hibernation, otherwise max 1GB.

---

