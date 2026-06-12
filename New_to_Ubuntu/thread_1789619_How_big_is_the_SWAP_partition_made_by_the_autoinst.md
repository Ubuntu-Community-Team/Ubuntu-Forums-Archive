---
title: "How big is the SWAP partition made by the autoinstall"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by MorrisseyJ on 2011-06-24
Hi, 

I am doing an dual boot install on my parents computer and have a question about the size of the SWAP partition created by the automatic install, on the live USB (Natty install, 64 bit).

To date i have only installed Ubuntu on my own computer which has a small amount of RAM. In this case the auto installer has made a SWAP partition large enough to allow my machine to hibernate etc.

On my parents computer there are 4GB of RAM. My question is whether the auto install will check the amount of RAM on the machine and make an appropriately large SWAP partition or whether it will just make a standard SWAP partition which might not allow for my parents to get the full use of their machine - 64bit etc.

Could someone tell me if the auto-installer checks the RAM size and makes the SWAP partition accordingly, or whether i need to manually set the SWAP partition. In the latter case, if anyone knows of a solid tutorial on how to do so, a link would be much appreciated.

Thanks.

---

### Post by jtarin on 2011-06-24
Do it manually. [Your prayers are answered]("http://www.cyberciti.biz/tips/linux-swap-space.html").:P

---

### Post by CaptainMark on 2011-06-24
it chooses the size based on your ram but it totally over does it nowadays, i have 4gb ram too and autoinstall tries to make 8gb of swap, i changed it to 2gb and ive never even noticed that being used, with 4gb of ram your pc is not likely to run out in a hurry

---

### Post by ahso4271 on 2011-06-24
make it the same size as RAM for hibernation

---

### Post by MorrisseyJ on 2011-06-24
Great,

Thanks for the info. Good to know how it is calculated and that it might be excessive.

---

### Post by Paqman on 2011-06-24
The system does calculate, but all it does is give you 2xRAM, which is going to be huge overkill on any machine with more than about 512MB of RAM.

---

### Post by MorrisseyJ on 2011-06-29
For a more complete (and technical) account see the following:

[http://askubuntu.com/questions/50308/what-is-the-default-swap-size](http://askubuntu.com/questions/50308/what-is-the-default-swap-size)

---

