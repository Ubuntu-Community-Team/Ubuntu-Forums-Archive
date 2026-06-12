---
title: "Compile a kernel with no SSB support (conflict w/ ndiswrapper)"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by tak1150 on 2008-05-10
Hi,

If you have BCM43XX wireless card and are trying to use ndiswrapper, this problem will sound familiar to you:

Problem:
[LIST=1]
[*]ssb module is loaded by b44 and ohci_hcd, both of which are needed for ethernet and USB supports respectively. However, ssb is not necessarily needed.
[*]Blacklisting or rmmod'ing ssb via script, etc does not work, because ssb is loaded by those forementioned modules
[/LIST]

Possible solutions:
[LIST=1]
[*]use b43 module or b43legacy like the developers want you to
[*]compile a kernel without ssb tied to b44 or ohci_hcd (or without ssb altogether)
[/LIST]

Solution 1 is not the best since some of us want to use ndiswrapper for better performance. So please don't suggest to use b43. In this thread, I'd like to focus on the #2 solution.

Has anybody tried to build such a kernel (preferably 2.6.25 -ish)? If so, please tell us what configuration option to mess with! Thanks!

---

### Post by Ayuthia on 2008-05-10
> **tak1150 said:**
> Hi,

If you have BCM43XX wireless card and are trying to use ndiswrapper, this problem will sound familiar to you:

Problem:
[LIST=1]
[*]ssb module is loaded by b44 and ohci_hcd, both of which are needed for ethernet and USB supports respectively. However, ssb is not necessarily needed.
[*]Blacklisting or rmmod'ing ssb via script, etc does not work, because ssb is loaded by those forementioned modules
[/LIST]

Possible solutions:
[LIST=1]
[*]use b43 module or b43legacy like the developers want you to
[*]compile a kernel without ssb tied to b44 or ohci_hcd (or without ssb altogether)
[/LIST]

Solution 1 is not the best since some of us want to use ndiswrapper for better performance. So please don't suggest to use b43. In this thread, I'd like to focus on the #2 solution.

Has anybody tried to build such a kernel (preferably 2.6.25 -ish)? If so, please tell us what configuration option to mess with! Thanks!

I am not for sure if I fully understand your script problem.  Are you saying that a script is not able to remove the ssb module, load ndiswrapper, and then load ssb afterwards?  If you take a look at: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-a9c75e76532933266fabeef1b1aa742f3df4444c](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-a9c75e76532933266fabeef1b1aa742f3df4444c), it provides three different options that should be able to do this.

My other question is that you say that the b44 driver does not need to use ssb.  Have you seen it work without it?  I don't recall a way that you can remove ssb without unloading b43 and/or b44.  Both of those modules will automatically call ssb because they need it.  

As for ohci_hcd, I recall that ohci_hcd used to be tied to ssb, but I have not seen it tied to it once the Hardy release was made.  

As far as I know, there are a lot of Broadcom users that are using ndiswrapper and are able to load ssb after ndiswrapper without issue.  I am not saying that everyone is successful, but I am not confident that the users of the b44 drivers are going to be able to use their wired card if they remove ssb from their kernel.

Going to your #2 option, if you really wanted to remove ssb, it is located in the Device Drviers section under Sonics Silicon Backplane.  At least that is where I found it in 2.6.25.1.

---

### Post by tak1150 on 2008-05-10
Thanks Ayuthia.

No I have not seen b44 work without ssb in Hardy or lenny (kernel 2.6.24) because it is automatically loaded. Those scripts do work for some, but for many people, it disables the ethernet (ssb occupies the ethernet card just like it does w/ the wireless, which is the original problem w/ the new kernel).

see:
[http://linuxsalatiga.wordpress.com/2008/04/24/bcm43xx-ndiswrapper-in-hardy/](http://linuxsalatiga.wordpress.com/2008/04/24/bcm43xx-ndiswrapper-in-hardy/)
[http://readlist.com/lists/vger.kernel.org/linux-kernel/80/403431.html](http://readlist.com/lists/vger.kernel.org/linux-kernel/80/403431.html)

And yes, ohci_hcd is tied to ssb in hardy.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/182716/comments/17](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/182716/comments/17)

And yes, I can use ndiswrapper if I don't mind not being able to use the ethernet. At work, I have to switch b/w the two.

Thanks for the location of the ssb module in kernel config. I am now trying to set CONFIG_USB_OHCI_HCD_SSB to n and compile the kernel. My problem is that when I follow kernel compiling instructions like [this one]("http://howtoforge.com/kernel_compilation_debian_etch"), that option reverts to "not being set".

---

### Post by Ayuthia on 2008-05-10
> **tak1150 said:**
> Thanks Ayuthia.

No I have not seen b44 work without ssb in Hardy or lenny (kernel 2.6.24) because it is automatically loaded. Those scripts do work for some, but for many people, it disables the ethernet (ssb occupies the ethernet card just like it does w/ the wireless, which is the original problem w/ the new kernel).

see:
[http://linuxsalatiga.wordpress.com/2008/04/24/bcm43xx-ndiswrapper-in-hardy/](http://linuxsalatiga.wordpress.com/2008/04/24/bcm43xx-ndiswrapper-in-hardy/)
[http://readlist.com/lists/vger.kernel.org/linux-kernel/80/403431.html](http://readlist.com/lists/vger.kernel.org/linux-kernel/80/403431.html)

And yes, ohci_hcd is tied to ssb in hardy.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/182716/comments/17](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/182716/comments/17)

The first link was not loading for me.  However I was able to view the other two.  The second link was dated back in October 2007.  I am not for sure if that is valid anymore.  As for the third link, it does say that the bug was fixed in 2.6.24-12.18.  The rest of the comments afterwards are related to b43 and ssb, but I did not see any that commented about ohci_hcd.  So far with most of the people I have seen in the forum, when ssb was not able to be removed, it was because of b43 or b44 and not ohci_hcd.  I am not saying that you are incorrect but I just haven't seen anyone with ohci_hcd using the final release of Hardy.

> And yes, I can use ndiswrapper if I don't mind not being able to use the ethernet. At work, I have to switch b/w the two.Can't you just load b44 after ndiswrapper is loaded?

> Thanks for the location of the ssb module in kernel config. I am now trying to set CONFIG_USB_OHCI_HCD_SSB to n and compile the kernel. My problem is that when I follow kernel compiling instructions like [this one]("http://howtoforge.com/kernel_compilation_debian_etch"), that option reverts to "not being set".
Wouldn't that be the same thing?  I would think that if it is not set, you cannot say yes or no.

---

### Post by tak1150 on 2008-05-10
Thanks again for a quick reply!
I am not with an Ubuntu computer right now (I'm using Lenny), so I can't confirm that ohci_hcd is loaded or that it's tied to ssb in the final release. But I'm pretty sure that it is, but I could be wrong.

> Can't you just load b44 after ndiswrapper is loaded?
I have tried that and ethernet does not connect correctly if I load them in the following order (after removing them first):
1. ndiswrapper
2. b44
3. ssb

which is very puzzling.


> Quote:
Thanks for the location of the ssb module in kernel config. I am now trying to set CONFIG_USB_OHCI_HCD_SSB to n and compile the kernel. My problem is that when I follow kernel compiling instructions like this one, that option reverts to "not being set".
Wouldn't that be the same thing? I would think that if it is not set, you cannot say yes or no.

No it's not the same and that's where I need advice from people that are more familiar w/ compiling kernels than I. I write:
```
CONFIG_USB_OHCI_HCD_SSB=n
```
in /usr/src/linux-2.6.25.x/.config
but after I do "make menuconfig" and "make-kpkg clean" and "fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers", it reverts to it not being set. This happens even if I manually change the .config file after the "make menuconfig" step and/or "make-kpkg clean" step... ?

---

### Post by tak1150 on 2008-05-10
Oh, and I get the same result even if I just do (as you probably know already):

1. ndiswrapper
2. b44

---

### Post by Ayuthia on 2008-05-11
> **tak1150 said:**
> Thanks again for a quick reply!
I am not with an Ubuntu computer right now (I'm using Lenny), so I can't confirm that ohci_hcd is loaded or that it's tied to ssb in the final release. But I'm pretty sure that it is, but I could be wrong.


I have tried that and ethernet does not connect correctly if I load them in the following order (after removing them first):
1. ndiswrapper
2. b44
3. ssb

which is very puzzling.




No it's not the same and that's where I need advice from people that are more familiar w/ compiling kernels than I. I write:
```
CONFIG_USB_OHCI_HCD_SSB=n
```
in /usr/src/linux-2.6.25.x/.config
but after I do "make menuconfig" and "make-kpkg clean" and "fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers", it reverts to it not being set. This happens even if I manually change the .config file after the "make menuconfig" step and/or "make-kpkg clean" step... ?

I'll have to test out the b44 driver more when I get back home to my Dell laptop.

As for your kernel issue, I can't be much help.  I have not tinkered much with it.  I have done kernel compiling on Gentoo.

---

