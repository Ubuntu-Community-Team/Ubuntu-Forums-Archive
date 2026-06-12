---
title: "Internet not working"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by ddama on 2011-05-23
Hi,
 
I recently installed Ubuntu(first experience with a non windows machine :( ) ver. 11.04 with VMPlayer on my windows machine.
I can browse web on windows machine but not on Ubuntu machine.
I am using wireless connecton for my internet.
 
Any sort of help is deeply appreciated.
 
Thanks.

---

### Post by zkriesse on 2011-05-25
What sort of wireless card/chip are you using?

---

### Post by Rakeshvijayan on 2011-05-25
check driver for wireless card is installed or not

the way for checking system , administration ,hardware drivers

---

### Post by Swagman on 2011-05-25
Who is your ISP ?

---

### Post by The Cog on 2011-05-25
I think you should have a look at the network settigns in vmplayer - when in a VM, the network connectivity depends on the virtual network hardware emulated by the VM. Installing the drivers for the real hardware won't help. You might have to install drivers for the vmplayer network - I'm not familiar with vmplayer. 


I know that Ubuntu works in virtualbox with its default network settings (emulates an ethernet card even if the host OS is connected to wifi).

---

