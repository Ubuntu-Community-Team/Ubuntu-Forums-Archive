---
title: "Partitioning on a mac and rEFIt questions"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by Sparky88 on 2009-10-31
I am planing on on installing Ubuntu on my Macbook. Wanted a little more info on the partitions and free space so I dont screw up anything and this rEFIt thing and what it does exactly.

My setup. Macbook 3,1 , Snow Leopard 10.6.1 , 160 gig HD it is currently partitioned into 3 partitions made with disk utility NOT Bootcamp. In the ubuntu install Prepare Partions stage it has these partitions listed across the top.

free space 3kB
sda1 (fat32) 200.0MB
sda2(hfs+) 112.1GB = Macintosh HD
free space 128MB
sda3 (hfs+) 18.6GB = Storage
free space 128MB
sda4 (fat32) 17.7 GB = UBUNTU (where I want to install it)
free space 128MB

First of all I know this is probably a stupid question but what do I  partition the sda4  section as? I am in Specify Partitions Manually. I double click on the sda4 partition. What is the correct thing to pick in the USE AS drop down and the MOUNT POINT drop down?


The other question has to do with rEFIt I keep reading about. Seems to just be a chooser for whe you boot up. is there anything more to it that that? Cuz I honestly prefer to just use the Option key to boot when i want to boot into ubuntu. I dont want a chooser coming up every time since 95 percent of the time I will want to boot into OS X. (Unless Unubtu ends up impressing me that much). Anyway if thats all rEFIt is I rather not use it. So is there something else special it does?

I realise these questions are probably answered elsewhere with super basic steps but I haven't found them. I do appreciate any help or a point in the right direction

Thanks

---

### Post by RC1139 on 2009-10-31
This link might help you out:[ https://help.ubuntu.com/community/MacBook]("https://help.ubuntu.com/community/MacBook")
As for formatting the partition the default for 9.10 is ext4 and you want your mount point to be " / ".  Sorry I can't be of more help.

---

### Post by Sparky88 on 2009-10-31
thanks that did help some

---

