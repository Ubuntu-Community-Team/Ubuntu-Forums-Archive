---
title: "How do I get my grub2 bootloader to over take the..."
date: 2011-04-03
forum: New to Ubuntu
---

### Post by Zanderist on 2011-04-03
...Linux mint bootloader?

I've recently installed linux mint on my machine, and would like to know how I could revert back to my original boot loader I used with ubuntu.

My laptop now is a triple boot, Ubuntu, Windows, Linux Mint.
[I]
PS: (Not that I don't like ubuntu, I just decided to go further down the linux rabbit hole with linux mint)[/I]

---

### Post by cbowman57 on 2011-04-03
Boot into Ubuntu & reinstall grub.  You can do that with synaptic or from the command line: sudo apt-get install grub-pc --reinstall

---

### Post by beew on 2011-04-03
Boot into Ubuntu, then run ```
sudo grub-install --recheck /dev/sda 

``` assuming that sda is the (internal) drive where you install Ubuntu and Mint. This will transfer grub back to Ubuntu.

Then in Ubuntu, run 
```
sudo update-grub

``` This will add Mint to the boot menu.

Next time if you do a dual boot/multi boot of different Linuxes and want to let the original Linux OS to control grub, make sure you either don't install a bootloader or install it in the partition where the newly added OS is in case the option of not installing a bootloader is not available, that would be the case if you dual boot two versions of Ubuntu(i.e. put the bootloader in say sda2 rather than sda)

---

### Post by beew on 2011-04-03
> **cbowman57 said:**
> Boot into Ubuntu & reinstall grub.  You can do that with synaptic or from the command line: sudo apt-get install grub-pc --reinstall

I am not 100% sure, but I think if OP does this controlling grub will revert back to Mint when there is an update  for grub -pc in Mint next time

---

### Post by Zanderist on 2011-04-04
Okay it worked everyone, the bad news is I forgot to make a swap partition, though I've found an [article ]("http://mentoliptus.blogspot.com/2008/03/linux-mint-wifi-howto.html")that tells me how to make a swap file instead.

Thanks.

---

