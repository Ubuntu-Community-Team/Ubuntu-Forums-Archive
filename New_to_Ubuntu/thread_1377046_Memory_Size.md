---
title: "Memory Size"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by Papabravo on 2010-01-09
I have a Dell Inspiron 537-ST that is supposed to have 4GB of memory according to the sales order.  In the System Monitor (System | Administration | System Monitor ) It says there is 3.0 GiB of memory.  So I think I know what a GiB is but are these two "claims" compatible based on some memory size counting mechanism that is less than obvious.

Can the total amount of memory be independently verified by another means?

---

### Post by 3rdalbum on 2010-01-09
> **Papabravo said:**
> I have a Dell Inspiron 537-ST that is supposed to have 4GB of memory according to the sales order.  In the System Monitor (System | Administration | System Monitor ) It says there is 3.0 GiB of memory.  So I think I know what a GiB is but are these two "claims" compatible based on some memory size counting mechanism that is less than obvious.

Can the total amount of memory be independently verified by another means?

The BIOS will tell you the total memory installed.

If you are running a 32-bit operating system, your system will be able to use less than 3.5 GiB of RAM (exact amount depending on what hardware is in your computer). This is probably what your problem is. You should either install 64-bit Ubuntu (preferred) or the server kernel (which can use 36-bit memory addresses).

---

### Post by Papabravo on 2010-01-09
Yes indeed the BIOS shows 4096 MB as expected and then says 3072 MB are available.

I'm not sure I understand the implications of either of the alternatives mentioned in your post(64-bit Ubuntu or server kernel).  To use the 64-bit implementation the processor needs to one (a 64-bit one that is)  So I guess I need to establish it's pedigree.  It is an Intel Core 2 quad Q8200.  So is 64-bit Ubuntu a possibility?

---

### Post by x33a on 2010-01-09
yes your processor is 64-bit one. also, if it weren't then why would the company put 4 GB there in the first place.

you can download 64 bit ubuntu from here.

[]("http://www.ubuntu.com/getubuntu/download")[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

There's not much difference b/w 32 and 64 bit versions of ubuntu in terms of usability, though you might experience problems with certain softwares.

---

### Post by 3rdalbum on 2010-01-09
All Core 2 processors are 64-bit. So yes, 64-bit Ubuntu is a good solution for you. 64-bit Ubuntu is a seamless experience, I run it - just make sure you use the 64-bit Flash player rather than just the "flashplugin-nonfree" package.

For operations such as video encoding and 3D work you will see a bit of a speed boost as well due to the 'native' use of 64-bit long numbers.

---

### Post by 3rdalbum on 2010-01-09
> **x33a said:**
> yes your processor is 64-bit one. also, if it weren't then why would the company put 4 GB there in the first place.

I hate to nitpick, but there are plenty of companies out there that put in 6 GiB of RAM into a machine, two big 1 GiB graphics cards and a 32-bit operating system; the high amount of RAM is nothing more than a marketing ploy because less than 2 GiB of it will be addressable!

> There's not much difference b/w 32 and 64 bit versions of ubuntu in terms of usability, though you might experience problems with certain softwares.

If this were Windows, then what you say would be true. However on Ubuntu I haven't seen these problems.

---

### Post by 73ckn797 on 2010-01-09
> **3rdalbum said:**
> You should either install 64-bit Ubuntu (preferred) or the server kernel (which can use 36-bit memory addresses).


Karmic now has a PAE enabled kernel for 32 bit system in Synaptic. I have started using it and it reports proper memory of 6GiB (actually 5.9GiB).

I had tried the server kernel on earlier versions but it was not satisfactory for my desires. I was using 64 bit Ubuntu but with the PAE enabled I actually feel the system runs faster, at least slightly. 

I discovered the PAE kernel on an initial install of Karmic after its release. The installation used the PAE kernel and I did not even know it was going to do that.

---

### Post by Papabravo on 2010-01-09
On the consistency front If the processor was a 64-bit processor and the machine came with 9.04 preinstalled it would seem that it would have been the 64-bit verson.  So when I went to do the upgrade to 9.10 it would seem reasonable that I'd get the 64 bit version of 9.10

Thing is that the pre-installed 9.04 also said there was only 3 GiB AND the BIOS says 3072 available so I'm beginning to think there may be more than meets the eye here.  Any thoughts out there?

---

### Post by apt_fanatic on 2010-01-09
Copy and paste this command in a terminal to enable PAE which lets you use all your memory: ```

```

---

### Post by Papabravo on 2010-01-09
With all due respect that looks like a very strange and highly suspicious way to do anything so obvious

---

### Post by 73ckn797 on 2010-01-09
There are plenty of earlier posts about how memory is read. Search using [http://www.uboontu.com](http://www.uboontu.com) and you should find more than enough info to answer your question.

---

### Post by Papabravo on 2010-01-09
So is there a way to tell if the PAE kernel is being used or not?

---

### Post by 73ckn797 on 2010-01-09
Look under System/Administration/System Monitor/System. It will show the information about installed kernel. PAE will be shown in kernel version info.

---

### Post by starcannon on 2010-01-09
You should be able to see what kernel your running with this command:
```

uname -r

```Also, you can find out more about any commands that people give you by first using this command:
```

man <somecommand>

```GL and HF

Edit: or better still use the gui method hehe, sorry didn't think of it.

---

### Post by 73ckn797 on 2010-01-09
> **starcannon said:**
> or better still use the gui method hehe, sorry didn't think of it.

hehehehe! Cool!

---

