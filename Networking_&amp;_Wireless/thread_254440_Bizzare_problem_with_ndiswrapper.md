---
title: "Bizzare problem with ndiswrapper"
date: 2006-09-10
forum: Networking &amp; Wireless
---

### Post by purplepencil on 2006-09-10
Hi there,

I've just yesterday installed Ubuntu for the first time, and I'm having real trouble getting my wireless USB adapter up and running. So far I've been trying to use ndiswrapper with the windows drivers. A few places I've seen have reported this working, albeit one of those on Fedora core 2. My problem is this, when I run the command ndiswrapper -l, it tells me there are two .inf files installed, and they are invalid drivers. When I use the command ndiswrapper -e to attempt to remove them, it says there are no drivers installed! How can this be? It just told me there were drivers installed! 

](*,) 

Can anybody help me out? I'd really like to get into Linux, but without an internet connection, it's pretty difficult to do very much.

Thanks,

Dave

---

### Post by purplepencil on 2006-09-10
Update:

Managed to copy the right .inf files over from windows, and have them running, they seem fine. Now I'm stuck loading the module. When I try modprobe ndiswrapper, it says cannot find ndiswrapper. I'm going to see if I can get a wired connection and download it again, and reinstall it. Any advice would be greatly appreciated.

Dave

---

### Post by sas01 on 2006-09-10
Can you post a log of what you did in terminal? I'm by no means an expert but it would be nice to see exactly what you did.

---

