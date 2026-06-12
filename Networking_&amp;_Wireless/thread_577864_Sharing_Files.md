---
title: "Sharing Files"
date: 2007-10-16
forum: Networking &amp; Wireless
---

### Post by c_cammann on 2007-10-16
I have a small network on Feisty. I am trying to share certain files on my Laptop with my user on the another computer. I would like ideally to be able to share it with the entire network.

I can do it with 'chown' but then when I try to access the files in my Laptop I no longer am the owner of the 'files' within the folder I want to access. I remain the owner of the 'folder' itself, but all the files within that folder become owned by '1007.1007' (which is my UID on the other computer) and I can't access them on the laptop itself. In this way I gain access to those files on the network, but loose access directly from my laptop. 

I can then change the ownership back to my username and have access directly on my laptop again, but I loose the access on the Network. 

What I am looking for is the small network equivilient to sharing the folders on a network in windows.

I want to to maintain access on both my laptop and on the network.

So My question is: 
Is there another command than 'chown', or an easy way within the 'chown' command to simply add users that can access the files instead of changing the ownership of the files? Or any way that anyone knows to change ownership in such a way that I won't loose local usage of the files on my laptop, but I can still get to them on the network.

I am pretty new to networking so any suggestions are welcome.

I feel like there must be a very simple way to change permissions without changing ownership, but I don't know what it is...

Any help  at all will be greatly appreciated.

---

### Post by c_cammann on 2007-10-29
No one has any ideas?? Anything that could point me in a possible right direction?

---

