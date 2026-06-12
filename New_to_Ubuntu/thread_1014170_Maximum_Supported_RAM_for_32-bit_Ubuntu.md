---
title: "Maximum Supported RAM for 32-bit Ubuntu?"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by looi76 on 2008-12-17
What is the maximum supported ram size for 32-bit Ubuntu?

---

### Post by Michael.Godawski on 2008-12-17
4GB
correct me if I am wrong...

---

### Post by ubuser_7 on 2008-12-17
Wasnt it 3.5?

---

### Post by mrbiggbrain on 2008-12-17
> **ubuser_7 said:**
> Wasnt it 3.5?

3.2 - 3.4 depending on your setup for most systems

---

### Post by Michael.Godawski on 2008-12-17
[LIST]
[*][http://ubuntuforums.org/showthread.php?t=757722](http://ubuntuforums.org/showthread.php?t=757722)
[*][http://www.uluga.ubuntuforums.org/showthread.php?t=627108](http://www.uluga.ubuntuforums.org/showthread.php?t=627108)
[/LIST]
4 gb but there are some exceptions... see above

---

### Post by philinux on 2008-12-17
The graphics card has to be **addressed** withing the 4 gig ram. So if you've got a 1gig graphics card only 3 will be left for the system.

You could use pae.
[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

---

### Post by deputy on 2008-12-17
Theoretical max memory supported in any 32-bit OS is 4gb. If you want to know why let me know.

---

### Post by looi76 on 2008-12-17
My laptop ram is 4GB DDR2 but when I go to System > Administration > System Montior > Resources it shows that I only have 3GB of RAM! Look at the screenshot:
[[IMG]http://img241.imageshack.us/img241/9697/86022137jp0.th.png[/IMG]](http://img241.imageshack.us/my.php?image=86022137jp0.png)

---

### Post by deputy on 2008-12-17
How much memory does your BIOS say you have? Another limiting factor is the motherboard itself and/or the CPU.

---

### Post by philinux on 2008-12-17
> **deputy said:**
> Theoretical max memory supported in any 32-bit OS is 4gb. If you want to know why let me know.

Not true windows has had access to more than 4gig for a long time with pae. They chose not to include it in xp and vista 32bit for their own reasons.
[http://www.microsoft.com/whdc/system/platform/server/PAE/PAEmem.mspx](http://www.microsoft.com/whdc/system/platform/server/PAE/PAEmem.mspx)

---

### Post by redandgreen on 2008-12-17
> Not true windows has had access to more than 4gig for a long time with pae. They chose not to include it in xp and vista 32bit for their own reasons.

Really? I thought 4Gb was a hardware limit.

*goes off to google pae*

---

### Post by jenkinbr on 2008-12-17
Ubuntu (and linux in general) can support 64GB of ram with a kernel compiled with PAE support.  I have no expertise in this, but you might want to check out [this ]("http://ubuntuforums.org/showthread.php?t=855511&highlight=pae+64+bit")thread if you are interested...

---

### Post by deputy on 2008-12-17
Wow, I've never heard of PAE that's pretty amazing. I'll be sure to try that out next time I install 32-bit Ubuntu. But again the motherboard is a limiting factor also. The most I've seen a motherboard support is 16gb. Of course this is for mainstream pc's.

---

### Post by looi76 on 2008-12-17
In the BIOS it appears that my memory size is 4096MB, check out the picture:
[[IMG]http://img254.imageshack.us/img254/9859/17122008313ub9.th.jpg[/IMG]](http://img254.imageshack.us/my.php?image=17122008313ub9.jpg)

---

### Post by nhasian on 2008-12-17
any reason why you dont want to run 64-bit Ubuntu?  if your CPU architecture supports it, it is recommended to run the 64 bit OS anyway :)

---

### Post by looi76 on 2008-12-17
Actually, Yestarday I have uninstalled 64-bit Ubuntu and then installed 32-bit Ubuntu. It's hard to find softwares for 32-bit Ubuntu so imagine 64-bit! That's why I have change to 32-bit... What do you think?

---

