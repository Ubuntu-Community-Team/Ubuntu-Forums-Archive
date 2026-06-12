---
title: "[SOLVED] Re-Installation"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by mjheagle8 on 2008-12-29
I want to create a /home partition in my free space, but gparted tells me that i cant have more than 4 primary partions. what can i do? i want to save all my custom configurations and i have a bunch of software installed that i dont want to lose.
thanks for all help!

---

### Post by taurus on 2008-12-29
You need to convert one of those 4 primary partitions into an extended partition.  Then, create a logical partition, /dev/sda5, under that extended partition.

---

### Post by blueridgedog on 2008-12-29
You can only have 4 primaries, but you shoudl be able to make an extended partition with gparted and then create a usable partition inside it.  Can you convert one of your primaries to an extended?

---

### Post by mjheagle8 on 2008-12-29
i cant create any partition. how do i convert it to extended?

---

### Post by blueridgedog on 2008-12-30
An extended partition would count as one of the four, so prior to creating an extended partition, which would allow you to create more than four total usable partitions, you would need to delete one of your current partitions.  

What is your current partition structure?

---

### Post by mjheagle8 on 2008-12-31
I solved this problem. Using the GParted CD, I deleted the swap partition, then created a logical partion containing my /home and swap in the free space.  Thanks everyone for help!

---

