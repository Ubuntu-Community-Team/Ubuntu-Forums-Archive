---
title: "lucid not booting after grub"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by a.sarkar on 2010-05-21
I was trying to install ubuntu lucid in my parents computer (dual boot with windows xp).
Installation was smooth. However after installation, the computer wouldn't boot into ubuntu after I select the kernel 2.6.32.21 in the grub menu. It shows a whold page of error. Something like

```

[2.148016]  blk_unplug
[2.148016]  blk_backing_dev
...
[2.148016]  vfs_read
...
Rebooting in 30 seconds

```Even recovery mode of the grub menu has the same problem.

Strange thing is, if after selecting ubuntu kernel 2.6.32.21, I plug in the live cd, its booting just fine.
Note that It's not booting from the live cd, since I have to use the username and password (that I had chosen during installation) to login. I can also remove the live-cd once I have logged in.

Even updating the kernel to 2.6.32.22 didn't help.

Tried using
```

sudo e2fsck /dev/sda5

```where sda5 is my / partition. Shows it is clean. 
I am at my wits end. Any help would be appreciated.
Thanks again for your time.

---

### Post by -humanaut- on 2010-05-21
Try reinstalling Grub from the LiveCD environment what kind of Computer is it? any proprietary graphics card?

---

### Post by a.sarkar on 2010-05-21
@humanaut
Thanks for your quick reply.

Its a pretty old computer
It's specification is:
Intel Pentium 4 @ 2.40 GHz, 
1.25 GB of RAM.

I understand that the RAM is low, but according to Ubuntu website, even 256 MB RAM should do the job.

From the windows part I see that it has Intel 82845G Graphics Controller driver installed.

I don't think it is a problem of the grub, since grub menu shows up. However, will try re-installing grub from the live-cd as you have suggested.

---

### Post by -humanaut- on 2010-05-21
That graphics card is going to give you problems with X theres a number of people on here where X simple fails on those cards. If you can get it too load login in via TTY and update it before using X it should help.

---

### Post by a.sarkar on 2010-05-21
Dear -humanaut-
Thanks for your answer.
Could you be bit more specific on how I can  login via TTY before X. 
How do I update my graphics card?
Will 
```

sudo apt-get update && sudo apt-get upgrade

```work?

---

### Post by oldfred on 2010-05-22
When you boot with the liveCD, do you have to use f6 and choose boot options to get it to boot. Older system often have to have irqpoll or noirqpoll or acpi etc

[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp
irqpoll

---

### Post by a.sarkar on 2010-05-22
@oldfred,
No, I don't have to use f6 and choose boot options to get it to boot when using livecd.

Checked couple of forums and found out the graphics card that I have (Intel 82845G) apparently doesn't work with Ubuntu that well. There are a couple of fixes on the net available, but none of these worked for me :(.

Removed compiz: that didn't solve the problem.

Really frustating :(, since the live-cd works just fine. Also works, if I plug in the live-cd AFTER the grub menu comes up. Live-cd must be using some graphics drivers which is not installed by default. Don't how to figure out which driver the live-cd is using.

---

### Post by oldfred on 2010-05-22
With my nvidia card I had to add nomodeset to get into it with low graphics. Supposedly works for other video cards also.
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)


if you've got an intel graphics card, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by a.sarkar on 2010-05-23
Dear oldfred,
Thanks for your reply. Unfortunately, I had to give up trying to install lucid in my parents comp, since I had to get back to my institute. Will probably try your instructions, when I go home again. 
Thanks once again.

---

