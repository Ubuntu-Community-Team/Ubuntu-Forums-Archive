---
title: "IPW3945 Intel driver"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by IndigoMontoya on 2007-02-13
I saw (ok via Digg) that intel has released a new open source driver for the ipw3945 wireless chip.  I was wondering two things.

1.  Why is it "so much better" exactly?  I am currently using the sourceforge ipw3945 dirver and havent really noticed any issues with it.

2. Can I install this without throwing my system into a world of trouble?

Thanks
Scott

Relevant links:

[http://intellinuxwireless.org/?p=iwlwifi](http://intellinuxwireless.org/?p=iwlwifi)
[http://intellinuxwireless.org/?p=d80211](http://intellinuxwireless.org/?p=d80211)

---

### Post by Skadge on 2007-02-13
I tried today to install it.
* First, you need kernel > 2.6.18. Doesn't work with Edgy. I installed the 2.6.20-7 from Feisty repos without any troubles.
* Then, I installed the d80211 package following Intel guidelines. No troubles.
* To compile and install the iwlwifi driver itself on Ubuntu, you need to make a change in the Makefile: line 69
```
export KSRC := /lib/modules/$(KVER)/source
```
becomes
```
export KSRC := /lib/modules/$(KVER)/build
```
and line 71
```
KMISC_INC := /lib/modules/$(KVER)/source/include
```
becomes
```
KMISC_INC := /lib/modules/$(KVER)/build/include
```

It compiles a iwlwifi.ko module.
But then i'm stucked there. The provided "load" script doesn't work for me, and an
```
sudo insmod iwlwifi.ko
```
returns an error :
```
insmod: error inserting './compatible/iwlwifi.ko': -1 Unknown symbol in module
```

Help is welcome !

---

### Post by featherking on 2007-02-13
i was curious about this driver as well, they mentioned that they would try to have it included in the .22 kernel i think

---

### Post by sorcere on 2007-02-20
> **IndigoMontoya said:**
>  1.  Why is it "so much better" exactly?

I installed the new iwlwifi driver under Edgy running kernel-2.6.19.3 with no problems, it works great. The reason it will be a better alternative to the current ipw3945 Intel supplied driver is because it does not require the user space daemon.

More info can be [found here.]("http://kerneltrap.org/node/7704")

---

### Post by valium on 2007-06-03
hello.
I have  2.6.20-16-generic on Feisty 7.04 64bit...
can anyone tell me step by step to install a kernel source for this so i can install new mac and new iwlwifi packages please i need them .

---

### Post by chili555 on 2007-06-03
```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by valium on 2007-06-03
> **chili555 said:**
> ```
sudo apt-get install linux-headers-`uname -r`
```

yeah i got that, but when i try to install mac80211 it shows me this

Kernel Makefile not found at '/lib/modules/2.6.20-16-generic/source/'
If patch or script failed, check pre/ and post/ for current stage.
make: *** [compatible/modified] Error 1

---

### Post by octoberdan on 2008-04-05
> **valium said:**
> yeah i got that, but when i try to install mac80211 it shows me this

Kernel Makefile not found at '/lib/modules/2.6.20-16-generic/source/'
If patch or script failed, check pre/ and post/ for current stage.
make: *** [compatible/modified] Error 1

I seem to be experiencing the same issue. I installed the headers and verified the source was there. However, there is in fact no makefile in that location, just source... I wonder if the ubuntu provided sources are different than what is the norm. Perhaps we could download a source elsewhere and drop the makefile from that in? Sounds kind of nutty....:confused:

---

