---
title: "Install RTAI over Ubuntu 9.10 x64"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by Camusillo on 2010-04-11
Hi friends...

Please feel free to move this thread if you think this is not the right forum...

I want to install RTAI over Ubuntu 9.10 x64...

I was looking for documentation but I didn't find anything about the installation over Ubuntu 9.10 or x64 bits systems...

Is it possible install RTAI over x64 bits system or Ubuntu 9.10?

If anyone has some information, could you please help me?...

Thanks in advance...

Regards...

---

### Post by ochaloaa on 2010-04-25
[http://qrtailab.sourceforge.net/rtai_installation.html](http://qrtailab.sourceforge.net/rtai_installation.html)


see this 
i am also in trouble to install Rtai-lab  its very hard to install.

but now i install ubuntu 8.04 LTS and let see what happend

good luck for u.

---

### Post by methril on 2010-05-05
I successfully installed in a 9.10 x86 machine. The problem with x86_64 machines is that the rtai hal patch is really old.

I´m cleaning the patches to install with 2.6.31.11 & 2.6.31 karmic ubuntu version. I hope to send it to RTAI ml soon.

Best Regards.

---

### Post by Pestery on 2010-07-23
Hello, I'm also trying to install RTAI on Ubuntu 9.10 x86. I can compile the kernel but it won't start when I try to boot it. It gets through grub fine, but then just has a blank screen with a flashing cursor in the top corner. Any suggestions?

I'm currently trying rtai-3.8 and linux-2.6.31.8. For the config file I've tried the one stored in the grub folder (/boot/config-`uname -r`) and the one from the link that ochaloaa provided.

---

### Post by s3xs1 on 2011-05-01
Hi!

I have the same dilemma. I'm using the latest version of ubuntu: 11.04 x64, on virtualbox, with win7 as host os.

I've tried to follow the steps shown in the rtai-ubuntugutsy-matlab.txt, but it gave me an error while trying to compile/maker/whatever is the correct term ... and then it said that the package creation was aborted, or something like that.


By the way, do I have to change something in those line said to be inserted via nano? ... I didn't. I've changed  everything else to their latest versions though.

---

### Post by jbohren on 2011-06-23
Apparently the x86_64 and x86 branches were merged together, so for newer kernels (past 2.6.24), 64-bit machines can just use the patches in arch/x86

[https://mail.rtai.org/pipermail/rtai/2010-July/023463.html](https://mail.rtai.org/pipermail/rtai/2010-July/023463.html)

---

