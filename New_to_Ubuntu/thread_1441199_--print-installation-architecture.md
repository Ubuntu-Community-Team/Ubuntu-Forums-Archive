---
title: "--print-installation-architecture"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by Wulfeous on 2010-03-28
I've been following the guide at:

[http://n10.wikia.com/wiki/Linux_HOWTO](http://n10.wikia.com/wiki/Linux_HOWTO)

I've followed the instructions as best as I can, but I am new to this. 

when i put in 
sudo dpkg -i linux-headers-2.6.32.8_2.6.32.8-10.00.Custom_i386.deb

it goes a bit and gives me
dpkg: warning: obsolete option '--print-installation-architecture',  please use '--print-architecture' instead.

It makes sense that they would start using a shorter command to do  something, but why would they make the old command not work. 

in any case.. I have absolutely no idea what it means and after many  many hours of searching, I only seem to find bug reports on it with no  understandable actions to take to get by it. 

Any help please??

---

### Post by Wulfeous on 2010-03-29
Got an answer in another forum. Looks like it's just an old bug in  initramfs-tools that displays that text. the command goes through and  the compilation completes successfully, even though it doesn't say that  it did.

---

