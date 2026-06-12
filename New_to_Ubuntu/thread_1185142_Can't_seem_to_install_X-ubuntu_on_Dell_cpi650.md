---
title: "Can't seem to install X-ubuntu on Dell cpi650"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by mistypotato on 2009-06-11
Hi,
I have an older Dell cpi that I use in the garage as a data center.

It doesn't have to do much...just connect to my server and the Internet basically.

So I tried to install X-Ubuntu and the result is kind of weird.

It seems to go through the entire install just fine...all 7 steps complete what seems normally. 

But then when it restarts, it seems that none of the installation actually stayed on the hard drive.  When it starts, it's just the Live CD desktop and if I turn off the computer and try to boot from the Harddrive it complains that there is not startup disk (boot disk) etc.

I tried it 3 times and enough's enough.

Wasn't xubuntu designed for older less endowed computes like this Dell cpi?

Any suggestions?

Thx

---

### Post by john.nicholls on 2009-06-12
Are you using the "normal" or the "alternate" version? The alternate version should work better on older hardware.

---

### Post by mistypotato on 2009-07-01
John,

Thx for the suggestion.

I was able to successfully install the alternate version as you suggested.

Only a minor networking issue stands in the way of complete success.


CHEERS!

---

### Post by scrooge_74 on 2009-07-01
Need any help with the networking? With Xubuntu sometimes is easier to do it from the command line

---

### Post by mistypotato on 2009-07-01
Hi Scrooge,

Yes PLEASE ! :p

I can ping out but no inbound pings are received.

It's as if I have a firewall blocking ALL inbound traffic....but it's a plain vanilla install and by default, xbuntu alternate version does not install a firewall as far as I can tell?

---

### Post by halitech on 2009-07-01
(X)(K)Ubuntu by default uses IPtables that are active right from the get-go. What are you trying to do?

---

### Post by scrooge_74 on 2009-07-01
the firewall is in the kernel, usually you don't need to config it, are you trying to set up some services? For example if you want to access it from another PC you only need to install the ssh server on it, and then from another PC you can just do a ssh user@IP_of_that_pc and you can log into it.

If you want to share disks you set up NFS and it will let you mount the drives

About the firewall, you could install some front end like firestarter that will let you do some configs to the iptables if needed. For example none of my 3 PCs have any front end installed, since I only use SSH, SAMBA and from time to time NFS inside my network, I don't need to tweak iptables anymore (I used to have a PC acting as router which needed to have some tweaks for that)

---

