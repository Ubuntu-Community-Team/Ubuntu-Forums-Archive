---
title: "Ubuntu updates"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by lover_of_sc on 2009-08-25
Hi guys,

How do I disable the kernel software updates so that the Update manager doesn't include them? 

Also, is it possible to disregard the linux backport module updates from that list?

Thanks

---

### Post by MrWES on 2009-08-25
> **lover_of_sc said:**
> Hi guys,

How do I disable the kernel software updates so that the Update manager doesn't include them? 

Also, is it possible to disregard the linux backport module updates from that list?

Thanks

I believe you can 'lock in' the kernel version in the Synaptic Package Manager.

Bill

---

### Post by snowpine on 2009-08-25
This command updates the kernel:

```
sudo apt-get dist-upgrade
```

This command does not:

```
sudo apt-get upgrade
```

---

### Post by mcduck on 2009-08-25
> **snowpine said:**
> This command updates the kernel:

```
sudo apt-get dist-upgrade
```

This command does not:

```
sudo apt-get upgrade
```

Both these commands will upgrade the kernel. 

The only difference between the two is that "apt-get upgrade" may only upgrade packages and add new ones if required, while "apt-get dist-upgrade" can also remove existing packages it that's necessary. Updating with the Update Manager is same as using "apt-get upgrade", while upgrading in Synaptic behaves like "apt-get dist-upgrade".

The way to stop updates for a certain package is, like MrWES pointed out, pinning the package version. Just select the packages to pin, and then use Package/Lock Version.

To pin kernel version you'd have to lock *linux-generic, linux-image-generic, linux-headers-generic* and *linux-restricted-modules-generic*.

However, since kernel updates are rather important security updates, I'd recommend trying to solve the issue with any possible means first and disabling kernel updates only if nothing else works.

---

### Post by lover_of_sc on 2009-08-26
Thank you for your responses, cI am still very new to this, could you please describe in more detail how to do this?

To pin kernel version you'd have to lock linux-generic, linux-image-generic, linux-headers-generic and linux-restricted-modules-generic.

The reason whyt I want to do it is that I have just got a new sony vaio w series laptop snd there is a bug in the most recent kernel that prohibits my network card from working, I have really tried everything I know to get it working with the newest updates (you can see my previous 2 threads posted - none which anyone could help me with....)

Best Regards
Anders

---

### Post by Luca_turicci on 2009-08-26
I use the upgrade manager (the graphical one) and when don't want to update the kernel just read the whole list of updates and uncheck the one that updates the kernel image =)

---

### Post by brunogirin on 2009-08-26
Here's the howto on pinning: [https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

However, before you do that, can you ensure that you file a bug in launchpad with the details of what doesn't work please? At least, that gives the devs a chance to have a look at it and correct the problem in a future version of the kernel.

---

### Post by mcduck on 2009-08-26
> **lover_of_sc said:**
> Thank you for your responses, cI am still very new to this, could you please describe in more detail how to do this?

To pin kernel version you'd have to lock linux-generic, linux-image-generic, linux-headers-generic and linux-restricted-modules-generic.

The reason whyt I want to do it is that I have just got a new sony vaio w series laptop snd there is a bug in the most recent kernel that prohibits my network card from working, I have really tried everything I know to get it working with the newest updates (you can see my previous 2 threads posted - none which anyone could help me with....)

Best Regards
Anders

Just use the Search in Synaptic to find those packages I listed, then select them, and after that select Package->Lock Version from the menu. That's it. :)

---

### Post by snowpine on 2009-08-26
Alternate solution: Install the new kernel, but don't use it... your old (non-broken) kernel will still be available in the Grub menu. (And you can edit /boot/grub/menu.lst to make the old kernel the default.)

I agree however that pinning is the more elegant solution.

---

### Post by lover_of_sc on 2009-08-26
Thanks guys, very helpful as always. I have locked down the 4 packages as in above comment. Lets hope that helps... :-) THANKS GUYS

---

