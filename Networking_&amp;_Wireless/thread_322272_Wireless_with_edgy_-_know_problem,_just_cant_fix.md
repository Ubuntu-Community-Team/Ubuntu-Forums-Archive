---
title: "Wireless with edgy - know problem, just cant fix"
date: 2006-12-20
forum: Networking &amp; Wireless
---

### Post by 101linux_mike101 on 2006-12-20
I have the problem outlined here, i've been using xp ever since edgy release as I cant get the  internet to work - the problem outlined here with some solutions, the problem is im still learning and dont really understand the solutions. 

[https://launchpad.net/distros/ubuntu/+source/ndiswrapper/+bug/59983](https://launchpad.net/distros/ubuntu/+source/ndiswrapper/+bug/59983)

I really want to continue using Ubuntu and hopefully someone can help me fix this problem, could someone give me a solution in noob hopefully that way I wont mess up, I have been trying for a long time to fix this but with to no avail, even a webpage or link to more help would be greatly appreciated.

Thanks in advance,

Mike

---

### Post by n00b@linux on 2006-12-20
You could try opening a terminal and typing the following commands in sequence:```
sudo apt-get install ndiswrapper-utils-1.8
sudo ln -s /usr/bin/ndiswrapper-1.8 /usr/bin/ndiswrapper
```Then go about your business as normal and see if it works.
 
I'm going to try it when I get home tonight.  I've been ](*,) with my WG111T USB 2.0 Wireless Network Adapter and ndiswrapper.  I just hope the above is the solution to my problem.

---

### Post by 101linux_mike101 on 2006-12-20
correct me if i'm wrong but do those commands use my internet connection to get ndiswrapper 1.8? the only access to the internet I have at the moment is by using my XP partition.

---

### Post by 101linux_mike101 on 2006-12-22
Sorry to *bump* but I really need some help with this...

---

### Post by floke on 2006-12-22
Mike, from your post it's not clear exactly what the problem is.
Could you state it more clearly, and give your specs (it's clear that you can;t use wireless - but e.g. are you using a wireless USB card or in-built? Which make / router etc.)?

Could you also go into the terminal (found under Applications / Accessories) and post the readout from 'iwconfig'.

By providing more information in this way, you stand more chance of someone being able to help.

---

