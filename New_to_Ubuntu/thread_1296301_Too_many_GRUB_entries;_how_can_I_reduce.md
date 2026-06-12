---
title: "Too many GRUB entries; how can I reduce?"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by steve228 on 2009-10-20
Ok I am dual booting Ubuntu with XP, but I mostly use my ubuntu and if need-be, use WINE.

I am using Ubuntu 9.04.

My problem is that when GRUB loads, I see:
> 
Ubuntu 9.04 kernel 2.6.28-15 server
Ubuntu 9.04 kernel 2.6.28-15 server (recovery mode)
Ubuntu 9.04 kernel 2.6.28-15 generic
Ubuntu 9.04 kernel 2.6.28-15 generic (recovery mode)
Ubuntu 9.04 kernel 2.6.28-11 generic
Ubuntu 9.04 kernel 2.6.28-11 generic (recovery mode

and then the 
memtest

and the 
Windows XP Home Edition


Why do I have so many? Is it sort of like if something fails in my top choice, I can try using the other choices to fix a problem?

And if I wanted to, how could I remove one or some of them?


[I][B]Thanks in advance for any suggestions or solutions,
Steve[/B][/I]

---

### Post by sahabcse on 2009-10-20
comment out the unwanted entry in /boot/grub/menu.lst


eg)

#title           Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
#uuid            1a00a5d9-8ff1-40c2-b151-0b4701b269ea
#kernel          /boot/vmlinuz-2.6.28-15-generic #root=UUID=1a00a5d9-8ff1-40c2-b151-0b4701b269ea ro  single
#initrd          /boot/initrd.img-2.6.28-15-generic


put # infornt of the entry for comment out

---

### Post by howefield on 2009-10-20
The easy way is to install startupmanager with Synaptic Package Manager, the harder way is to edit your menu.lst file to what you want to see.

---

### Post by oldos2er on 2009-10-20
> **steve228 said:**
>  how could I remove one or some of them?


 Uninstall the older kernel using Synaptic Package Manager; your menu.lst will then be automatically updated.

---

### Post by John Bean on 2009-10-20
> **howefield said:**
> The easy way is to install startupmanager with Synaptic Package Manager, the harder way is to edit your menu.lst file to what you want to see.

True. But it's not hard, especially in this case. Locate this section:

```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=1

```Note the last line, in my case set to only show a single kernel.

The other common options are similarly self-documented.

---

### Post by steve228 on 2009-10-20
Thank you all for the responses.
***How do I mark this as "solved"***

I have one more question:
Does it benefit me to have that many entries?  Like if there was a problem loading the top entry, would there be a chance to repair in the 2.6.28-11 generic kernel?

---

### Post by LewRockwell on 2009-10-20
[http://www.linuxquestions.org/questions/linux-general-1/duplicate-kernel-entries-of-ubuntu-9.04-in-grub-loader-758468/?](http://www.linuxquestions.org/questions/linux-general-1/duplicate-kernel-entries-of-ubuntu-9.04-in-grub-loader-758468/?)

.

---

### Post by LewRockwell on 2009-10-20
> **steve228 said:**
> Does it benefit me to have that many entries?  Like if there was a problem loading the top entry, would there be a chance to repair in the 2.6.28-11 generic kernel?

normally when new kernels are installed via updates, the grub menu.lst file is updated so that the newer kernel may be booted and utilized

unless you are terribly cramped for space, there is no reason to remove/un-install previous kernels

as you note above, if you did have a problem or failure of a newer kernel you could just boot using one of your previous kernels

editing the menu.lst file can be done via many of the *nix distro LiveCDs and so it is quite simple to recover from a crashed/broken kernel(as long as you have another good one in reserve)

.

---

### Post by mlnease on 2010-12-23
> **sahabcse said:**
> comment out the unwanted entry in /boot/grub/menu.lst


eg)

#title           Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
#uuid            1a00a5d9-8ff1-40c2-b151-0b4701b269ea
#kernel          /boot/vmlinuz-2.6.28-15-generic #root=UUID=1a00a5d9-8ff1-40c2-b151-0b4701b269ea ro  single
#initrd          /boot/initrd.img-2.6.28-15-generic


put # infornt of the entry for comment out
Thanks--I tried this, but my /boot/grub/menu.lst file is blank.

I also installed updatemanager, but it doesn't seem to offer a solution either.

Many thanks in advance for any advice.

mike

---

### Post by oldos2er on 2010-12-23
Ubuntu's using grub2 now, the configuration of which is very different from legacy grub.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by mlnease on 2010-12-23
> **oldos2er said:**
> Ubuntu's using grub2 now, the configuration of which is very different from legacy grub.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Ah!  Er--thanks.

---

