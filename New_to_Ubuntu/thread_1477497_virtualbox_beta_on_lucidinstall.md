---
title: "virtualbox beta on lucidinstall"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by mrsray on 2010-05-08
Hello everyone,

I installed Lucid and would like to

Install the virtual box Lucid package from here:

[http://download.virtualbox.org/virtualbox/3.2.0_BETA1/](http://download.virtualbox.org/virtualbox/3.2.0_BETA1/)

I am looking for step by step instructions.

Anyone?

Thanks in advance

---

### Post by Naitsirhc Hsem on 2010-05-08
did you download virtualbox-3.2_3.2.0~beta1-60785~Ubuntu~lucid_i386.deb   

you should be able to double click on it and install it

---

### Post by Djalmahal on 2010-05-08
At the bottom of the link page you'll find the .deb files for lucid, choose 64 or 32-bit depending what you're running, then once downloaded, just opden it and it should install.

---

### Post by mrsray on 2010-05-08
wow, you guys are fast.  

I'm downloading it now, I am just wondering if there is a special step to do so the package ensures that the VirtualBox host kernel modules are properly updated if the Linux kernel version changes

thanks again

---

### Post by sandyd on 2010-05-08
> **mrsray said:**
> wow, you guys are fast.  

I'm downloading it now, I am just wondering if there is a special step to do so the package ensures that the VirtualBox host kernel modules are properly updated if the Linux kernel version changes

thanks again
no, you don't need special steps.

dkms will take care of the kernel modules section (if you have it installed that is!)

---

### Post by mrsray on 2010-05-08
ok, last question then, how do I confirm it is installed?

and ps ... thanks so much for all the help

---

### Post by sandyd on 2010-05-08
> **mrsray said:**
> ok, last question then, how do I confirm it is installed?

and ps ... thanks so much for all the help
what installed?
the kernel modules?

---

### Post by CharlesA on 2010-05-08
> **carlee said:**
> what installed?
the kernel modules?

Guessing they mean dkms.

```
dpkg -l dkms
```

It was installed on my machine when I added the virtualbox repo and installed it with apt-get.

---

### Post by mrsray on 2010-05-09
yes I meant dkms

thanks .... vb is up and working great!  Lucid too!

I love you guys!

I usually find answers to what I have questions for without posting, so this was kinda new for me ... and so satisfying.  

this forum does rock!

---

