---
title: "Package upgrade"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by big_ipaq on 2011-03-05
My hosted server has Ubuntu 10.04 LTS installed. Lately I receive the following from it:

> The following packages are currently pending an upgrade:

	linux-firmware 1.34.4
	linux-image-2.6.32-29-server 2.6.32-29.58
	linux-image-server 2.6.32.29.35


However I am scared to run aptitude full-upgrade...

In a motd message, the hosting company from which I rent my dedicated server, wrote:

> This server comes with a custom e1000e network driver in a dkms package.
Do not remove the e1000e-dkms package. After kernel updates you have to
execute /usr/local/sbin/dkms-update once to make sure the driver is built
correctly and included in initramfs. If you skip this, networking will not
work any longer after the next reboot.

If you want to use your own kernel, please make sure you don't touch the
kernel boot parameters (append) as some of our hardware requires the
parameters acpi=ht and/or noapic.


So, probably I can ruin completely the linux install. What you advise me to do?

---

### Post by big_ipaq on 2011-03-05
Should I just run aptitude full-upgrade then run dkms-update?

How can I make sure then I can reboot the server and anything is ok?

If I reboot and networking is not working, I won't have access to do anything to it.

---

### Post by big_ipaq on 2011-03-06
No advice from anybody?

---

### Post by ikt on 2011-03-06
> **big_ipaq said:**
> No advice from anybody?

Sorry it's a fairly unique situation, I personally would email the company hosting the server to make sure that you can, and why they are running a "custom e1000e network driver".

---

### Post by big_ipaq on 2011-03-06
Thanks. Will ask them this question and get back here for more info.

---

### Post by big_ipaq on 2011-03-06
They were very blunt that what is installed on the server is my responsability. :(

I did upgrade, but not get the courage to reboot just yet. 

dkms-update does not report anything. How can I check it worked?
In grub, there is now acpi=ht for 2.6.32-29-server which was not present before for  2.6.32-28-server. What should I do about it?

---

### Post by ikt on 2011-03-06
> **big_ipaq said:**
> They were very blunt that what is installed on the server is my responsability. :(

Yeah but if the server doesn't work, then it's THEIR responsibility, that's really bad customer service tbh, it's almost like they're begging for you to submit a bunch of support requests that the server is broke.

---

### Post by Habeouscorpus on 2011-03-06
Well, whatever happens, you'll still have the other kernels to boot into. (I believe. Not well versed about servers.) So if things go south, go from there. Or, you could uninstall the kernel and apt-pin the current kernel + the headers.

---

### Post by big_ipaq on 2011-03-07
Problem is that my server si 1000 miles away so I can only see it through a SSL remote contection. I do not get to choose at boot anything.

---

