---
title: "Question about RAM upgrading, really general"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by RandomP on 2010-06-06
Ok, so I am running Ubuntu 10.04 LTS i386. Currently I only have 512mb of RAM. I want to upgrade that as much as I can, 4GB. My PC has 4 slots for RAM with each being able to have up to a 1GB stick. Now in Windows, it could not recognize more than 3gb of ram since I only had the regular "home" version and not the 64 bit or whatever. Does ubuntu have this same limitation or will it recognize all 4GB?

---

### Post by an0dos on 2010-06-06
> **RandomP said:**
> Ok, so I am running Ubuntu 10.04 LTS i386. Currently I only have 512mb of RAM. I want to upgrade that as much as I can, 4GB. My PC has 4 slots for RAM with each being able to have up to a 1GB stick. Now in Windows, it could not recognize more than 3gb of ram since I only had the regular "home" version and not the 64 bit or whatever. Does ubuntu have this same limitation or will it recognize all 4GB?

The 3GB limit is related to whether the OS is 32bit or 64bit. You have installed the 32bit version of Ubuntu therefore it will only recognize 3GB unless you install a PAE enabled kernel. If you want to go higher your best bet is to install 64bit Ubuntu (unless your computer can't run a 64bit OS).

---

### Post by Zzl1xndd on 2010-06-06
I am using the PAE Kernel mentioned above and it works really well. But either option should do the job.

---

### Post by Windows Nerd on 2010-06-06
> **RandomP said:**
> Ok, so I am running Ubuntu 10.04 LTS i386. Currently I only have 512mb of RAM. I want to upgrade that as much as I can, 4GB. My PC has 4 slots for RAM with each being able to have up to a 1GB stick. Now in Windows, it could not recognize more than 3gb of ram since I only had the regular "home" version and not the 64 bit or whatever. Does ubuntu have this same limitation or will it recognize all 4GB?
Do you have the 32 bit version or 64-bit verison of Ubuntu? 

32 bit version=maximum 3Gb
64 bit version=maxiumum 128+ Gb of RAM (not really sure what the number is, but itwill definately recongized 4Gb of RAM)

It is possible to have a 32 bit Ubuntu system recognize more RAM by using a PAE kernel, though that is a difficult process that may be too advanced (given that you are posting in this section of the forums I am assuming that it is too advanced).

Scott

---

### Post by RandomP on 2010-06-06
I am sure my processor would be able to handle the 64bit version of ubuntu, I just currently do not have the minimum amount of RAM. On the other hand I have heard of many people having problems with 64bit ubuntu....

PAE Kernel does not sound like something I would want to do.

---

### Post by Zzl1xndd on 2010-06-06
Enabling the PAE Kernel isn't that bad really.

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

### Post by RandomP on 2010-06-06
> **tweakedenigma said:**
> Enabling the PAE Kernel isn't that bad really.

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

Still does not really sound like something I would really want to do. However seems like the easy way of installing it is just to reinstall ubuntu with an install/LiveCD while having 3+GB of RAM installed. Might be something I experiment with when I get my RAM.

---

### Post by bodhi.zazen on 2010-06-06
> **RandomP said:**
> Still does not really sound like something I would really want to do. However seems like the easy way of installing it is just to reinstall ubuntu with an install/LiveCD while having 3+GB of RAM installed. Might be something I experiment with when I get my RAM.

First , Linux does not have the types of restrictions Windows does, so on that front you should be good to go.

Second, if you do a fresh install of 10.04, 32 bit, it will automatically install the PAE kernel, there is nothing special you need to do.

With all that in mind, if you have a 64 bit CPU I advise 64 bit Ubuntu.

---

### Post by an0dos on 2010-06-06
I haven't had any problems with 64bit Ubuntu; however, your mileage may vary. 

If you do a fresh install of Ubuntu 10.04 from a 32bit live cd, have more than 3GB of ram, and have a network connection, the installer will automatically install the PAE kernel.

or you can just run the following command from the terminal: [FONT=monospace]

[/FONT]```
sudo apt-get install linux-generic-pae linux-headers-generic-pae
```

---

### Post by RandomP on 2010-06-06
The sempron processor this PC has is a Socket 939. According to everywhere that I have read, 939 socket AMD sempron processors are 64bit processors. 

Once I get my RAM, I think I will just install the 64bit version of Ubuntu. If I don't like it I will switch back to 32bit and try the PAE kernel method.

Anyway, thank you all for the replies.

---

### Post by RJ12 on 2010-06-06
I think all AMD Processeors are 64-bit capable

---

