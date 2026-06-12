---
title: "How can I get Ubuntu to use all of my 6 GB RAM?"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by vallvi on 2011-02-05
On my Aspire AX3810 I've 6 GB RAM, but my Ubuntu 10.04 only recognizes 3 GB. The dualboot Windows recognizes all the RAM

I've seen somewhere that this problem can be solved by installing the 64bit version of Ubuntu (I run the 32bit version). But don't want to re-install. 

So: can I get mycurrent Ubuntu to read all my RAM?

Thanks for any help!

---

### Post by sanderj on 2011-02-05
You could run my script from [http://www.appelboor.com/check-my-hardware.py](http://www.appelboor.com/check-my-hardware.py) to see what's going on: hardware, bios, cpu, OS, etc

Get and run the script like this:


```

cd
wget http://www.appelboor.com/check-my-hardware.py
sudo python check-my-hardware.py 

```

Most easy thing is to install the 32-bit PAE kernel. But first run my script to check the settings ...

---

### Post by marin123 on 2011-02-05
you need to install pae kernel. open synaptic and type "linux pae" without the quotes and install it. reboot with new kernel and thats it.

PAE means physical address extension, it handles ram addressing different so you can use all of the 6 G of ram.

---

### Post by vallvi on 2011-02-05
Thanks, Marin,
That souns quite straightforward.
.... but, synaptic returns dozens of possible things to install when searching for linux pae. Which one do I choose?

---

### Post by mcduck on 2011-02-05
The package that's called "linux-generic-pae" will give you everything you need (note that you'll also of course have to choose to use that kernel in the Grub menu when starting the computer).

---

### Post by ikt on 2011-02-05
> **vallvi said:**
> On my Aspire AX3810 I've 6 GB RAM, but my Ubuntu 10.04 only recognizes 3 GB. The dualboot Windows recognizes all the RAM

I've seen somewhere that this problem can be solved by installing the 64bit version of Ubuntu (I run the 32bit version). But don't want to re-install. 

So: can I get mycurrent Ubuntu to read all my RAM?

Thanks for any help!

I know you don't want to but I would reinstall w/64 bit version, 10.10 takes like 4 minutes to install.

---

### Post by realzippy on 2011-02-05
> **marin123 said:**
> you need to install pae kernel. open synaptic and type "linux pae" without the quotes and install it. reboot with new kernel and thats it.

PAE means physical address extension, it handles ram addressing different so you can use all of the 6 G of ram.


...pae should be installed automatically if more than 3.5Gb RAM.
Guess RAM is not fully "seen" by the system...what does it report?


BTW,
+1 for 64 bit.

---

### Post by sanderj on 2011-02-05
> **realzippy said:**
> ...pae should be installed automatically if more than 3.5Gb RAM.
Guess RAM is not fully "seen" by the system...what does it report?


... hopefully the OP runs my script; the script will tell it all ...

---

### Post by waynefoutz on 2011-02-05
I had a myriad of problems last time I tries a PAE kernel. I would go with the reinstall. There are ways to do it painlessly without losing your data.

---

### Post by TBABill on 2011-02-05
Although you will be able to use more RAM with the PAE, Phoronix tested 3 Ubuntu kernels against each other. The 32 bit, 32 bit PAE and 64 bit. The PAE was slower in several instances than the 32 bit standard kernel, and the 64 bit won in speed in every test they ran. Sometimes the difference was small, but in others it was significant.

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

---

### Post by vallvi on 2011-02-05
Hi all,
Thanks for your feedback & advice. My conclusion: you guys convinced me that I've to install the 64 bit version. Buty I'm going to hold off doing that till April when 11.04 is out - no time now. 

Thnx!

---

