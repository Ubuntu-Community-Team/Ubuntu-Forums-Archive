---
title: "Wireless working after 2.6.17-11 upgrade?"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by lojic on 2007-02-10
Does your wireless still work after the recent linux-image-generic 2.6.17-11 kernel update?

If so, would you mind posting your hardware info in the following thread?

[http://ubuntuforums.org/showthread.php?t=358004](http://ubuntuforums.org/showthread.php?t=358004)

I'm trying to collect info regarding what's broken and what's working with respect to wireless after the recent update to help whoever (someone I hope!) may be working on this issue. It seems to have hosed several types of wireless cards, but I think some are not having trouble.

Thanks!

---

### Post by Floppyjoe on 2007-02-11
Ndiswrapper reverts to version 1.22 or something like that after the Kernel update so anyone who has installed a non repository version of ndiswrapper may experience problems.

---

### Post by lojic on 2007-02-11
Thanks. I haven't installed an ndiswrapper. If your wireless works after the -11 update, it would be helpful for you to check out the thread in post #1.  A bug for wireless issues with -11 has been opened on launch pad and the thread has a link.

---

### Post by Floppyjoe on 2007-02-11
Ndiswrapper is a tool for installing windows drivers for wireless cards. I had problems with wireless cards where I used the latest version of ndiswrapper available from sourceforge.net but not with wireless cards where i used the most recent repository versions of the ndiswrapper utility. So the point I'm making is some people will have problems with their wireless cards because of the version of ndiswrapper they are using and some will have the same card and not have problems. Am I being clear here?

---

### Post by lojic on 2007-02-11
Yep. 

It just doesn't happen to be the problem I'm experiencing. It turns out there is a problem with the -11 update breaking Prism chipset drivers.

Elsewhere I had asked folks to post their hardware details on the thread in post #1 if they had problems, so the purpose of this particular thread was to add some examples of working cards/drivers to the thread to help discern the underlying issues. I probably didn't make that clear.

As we've seen with this latest update, there are a variety of problems and many different factors causing them. Thanks for bringing up the ndiswrapper issue - I expect there are folks experiencing that who will be helped.

---

### Post by sanjeevdas on 2007-02-14
> **lojic said:**
> Does your wireless still work after the recent linux-image-generic 2.6.17-11 kernel update?

If so, would you mind posting your hardware info in the following thread?

[http://ubuntuforums.org/showthread.php?t=358004](http://ubuntuforums.org/showthread.php?t=358004)

I'm trying to collect info regarding what's broken and what's working with respect to wireless after the recent update to help whoever (someone I hope!) may be working on this issue. It seems to have hosed several types of wireless cards, but I think some are not having trouble.

Thanks!

Nope, mine does not work after the -11 upgrade: Prism 2.5 Wavelan chipset

---

### Post by lojic on 2007-02-14
> **sanjeevdas said:**
> Nope, mine does not work after the -11 upgrade: Prism 2.5 Wavelan chipset
I was able to fix it by booting with the -10 kernel (hit ESC at grub menu) and then install the restricted modules in Synaptic, then booting normally and it was fine.

---

### Post by lojic on 2007-02-14
> **lojic said:**
> I was able to fix it by booting with the -10 kernel (hit ESC at grub menu) and then install the restricted modules in Synaptic, then booting normally and it was fine.
D'oh - my bad, scratch that. I just posted the solution to the Nvidia driver problem!

See the following thread for the blacklist solution to the Prism 2.5 wifi problem:
[http://ubuntuforums.org/showthread.php?t=358004](http://ubuntuforums.org/showthread.php?t=358004)

Sorry for the confusion.

---

### Post by stani on 2007-03-15
Help this bug out on Feisty, contribute by passing your details to launchpad:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989)

> Can everyone affected please attach (do not paste into comment) the output of "lspci -vv" and "lspci -vvn", make sure to name the file something like lspci-vv-<yourname>.txt

There is not much time left, please participate!

Stani

---

