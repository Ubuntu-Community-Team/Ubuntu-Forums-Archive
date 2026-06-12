---
title: "Windows 7/Ubuntu dual boot partition sizes"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by pugrat on 2009-11-20
I have a Dell Inspiron Core Duo E1505 laptop that I plan on upgrading to 500 GB hard drive.  
 
I want to dual boot Windows 7 and Ubuntu.  
 
What would be the appropriately sized hard drive allocation partitions preferred to accomplish this?
 
I would mainly be using the Windows 7 for daily use but would like to play around with the Ubuntu partition as I learn the OS.  I don't want the Ubuntu partition to be too small in case I really get into it and find out I miscalculated.
 
Thanks, p.

---

### Post by ST3ALTHPSYCH0 on 2009-11-20
I would setup 60-80 Gb for the Win7 install, 15-20 Gb for the Ubuntu, Swap=RAM, and the rest NTFS for shared storage. You might want to break that storage space up further, but that's up to you. I would also save all your document, pix, etc in the shared storage so you can access from either OS.... and if anything happens to an OS install you don't have to worry about trying to get back to your personal stuff.

---

### Post by Abadon125 on 2009-11-20
I have the same setup but left about 100GB for windows.  Once you get a bunch of programs installed you will be glad to have that extra space so it doesnt take forever to boot up.  I then put in 40 for Ubuntu and the rest for storage.

---

### Post by Gaweph on 2009-11-20
As stated by previous people: I would suggest around 100Gb for windows, 20-40Gb or ubuntu.  Then the rest for your /home partition.

Having a seperate /home partition will be very helpfull if you ever have to reinstall your ubuntu partition, and your windows install should be aable to see it fine (using tools such as EXT2IFS).

Gaw

---

### Post by darkksyde on 2009-11-20
If your using a 500gb drive, i'd go 320 for windows 2xyourram for swap and the rest for ubuntu

---

### Post by r.mariappan on 2009-11-20
I am not a genius.
But as far as i am concerned 20 GB is enough for ubuntu since you are only using that for learning and fun.
And 400 for data and rest for windows 7.

---

### Post by ST3ALTHPSYCH0 on 2009-11-20
I can definitively say that a vanilla install of 9.04 takes only 2.7Gb, so you can go from there with your Ubuntu partition. Just keep in mind that drives survive better if you don't fill up more than 80-90% of a partition.

---

