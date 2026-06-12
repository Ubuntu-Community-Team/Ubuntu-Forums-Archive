---
title: "ubuntu install fails in windows 7 virtual machine"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by jumbojake on 2010-09-27
I want to install ubuntu as a virtual machine within windows 7(pro) virtual machine (I'm running a vostro 3700).

When I point to the *.iso, it starts and (occasionally) gets as far as asking for language, but immediately fails and the virtual machine powers down.

Is there anything special I need to configure to make it work :confused: or is there a compatibility problem with windows virtual machine??

(I have already tried a static drive - 10G)

---

### Post by Hippytaff on 2010-09-27
A long shot, but I spent days working out why I couldn't boot a live usb or run a virtual machine with an ISO and it turned out the ISO I downloaded was corrupt - I was advised to check the md5 Sum was correct, or just download it again

---

### Post by jumbojake on 2010-09-27
Thanks for your reply.

I've tried a few downloads .. and checking their md5's, they are all the same.

---

### Post by eeffoc on 2010-09-27
> **jumbojake said:**
> I want to install ubuntu as a virtual machine within windows 7(pro) virtual machine (I'm running a vostro 3700).
Which virtualization software are you using? VMware?

---

### Post by jumbojake on 2010-09-27
I'm using Windows Virtual pc, which came with my windows7pro (32bit)

the XP (came pre-installed) seems to work pretty well, so am hoping ubuntu will also work ok

---

### Post by eeffoc on 2010-09-28
> **jumbojake said:**
> I'm using Windows Virtual pc, which came with my windows7pro (32bit)

the XP (came pre-installed) seems to work pretty well, so am hoping ubuntu will also work ok

Which version of Ubuntu are you attempting to install? I know that some versions must be installed via 'safe mode' through Virtual PC, as they are not officially supported.

---

### Post by jumbojake on 2010-09-28
No wories..... problem solved ....  after an attempt to install fedora finding the same problem, I abandoned the Windows Virtual Machine and moved to use the old favourite VMware .... worked first time.

So, for anyone else with the same problem .. my advise is don't waist your time with windows virtual machine...

---

### Post by eeffoc on 2010-09-28
> **jumbojake said:**
> No wories..... problem solved ....  after an attempt to install fedora finding the same problem, I abandoned the Windows Virtual Machine and moved to use the old favourite VMware .... worked first time.

So, for anyone else with the same problem .. my advise is don't waist your time with windows virtual machine...

I concur! VMware works great! Glad you got it going!

---

