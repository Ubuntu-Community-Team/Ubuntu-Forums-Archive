---
title: "Connecting 2 ubuntu PCS"
date: 2006-12-27
forum: Networking &amp; Wireless
---

### Post by n.aggel on 2006-12-27
hi,

i would like to connect two **Ubuntu6.10** machines{laptop and desktop}.
Both of them are connected to a linksys WAG354G router with dhcp.](*,) 

i am a real newbie when it comes to networks, so if anyone has to suggest sites for reading, it would be great...:D 

thanks
N.A

---

### Post by capitalistpiglet on 2006-12-27
What do you mean by connect to each other, are you unable to ping one machine from the other? Or do you mean you want to set up some sort of shared folders.

---

### Post by n.aggel on 2006-12-28
How can i find the ip of each computer{the router uses dhcp}?then, i want to be able to share folders between the 2 computers...

---

### Post by tribaal on 2006-12-28
Well open a terminal on the computer you want the know the IP from.

Type in "ipconfig" (without ""), and the ip shows up in the output.

- trib'

---

### Post by Titus A Duxass on 2006-12-28
I use ssh to connect my 5 PCs together, here is a good HowTo:
[http://users.bigpond.net.au/hermanzone/p11.htm](http://users.bigpond.net.au/hermanzone/p11.htm)

---

### Post by n.aggel on 2006-12-28
> **Titus A Duxass said:**
> I use ssh to connect my 5 PCs together, here is a good HowTo:
[http://users.bigpond.net.au/hermanzone/p11.htm](http://users.bigpond.net.au/hermanzone/p11.htm)
thanks for your answers...

some more general questions....i've been told that i should use nfs.Which one is better nfs or SSH{basically, i want to transfer files...}.If i use ssh, i could share files with a windows box?

---

### Post by capitalistpiglet on 2006-12-28
A good way to share files using ssh is sshfs [http://ubuntuforums.org/showthread.php?t=275856](http://ubuntuforums.org/showthread.php?t=275856) .
But if your also got a windows box as well then samba would probably be the best bet [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

