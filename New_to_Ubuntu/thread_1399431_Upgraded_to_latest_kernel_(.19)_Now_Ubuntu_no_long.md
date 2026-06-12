---
title: "Upgraded to latest kernel (.19) Now Ubuntu no longer starts."
date: 2010-02-05
forum: New to Ubuntu
---

### Post by manaboutdog on 2010-02-05
My box is running 9.10 as the only OS on the box so normally boots straight into Ubuntu.

So I just upgraded my box this evening, and I noticed that one of the upgrades was the latest kernel version ending in .19, anyway I proceeded with the upgrade, rebooted, then after a while I get the error message

[FONT=Courier New]error: You need to load the kernel first.

Failed to boot default entries.

Press any key to continue...
[/FONT]  
Pressing a key here made no difference and I had to use the power button to turn it off, when it came back on it booted to the list of installed kernels so I selected the previous version which I am on now and it worked fine.

Is there anything else I need to do after the upgrade to ensure it works?

---

### Post by llawwehttam on 2010-02-05
lol, I had problems with the last kernel and .19 works fine.
I guess your a bit unlucky.
Hope you get it fixed.

---

### Post by manaboutdog on 2010-02-06
Nobody able to shed light on this problem?

Can someone at least tell me how to set my system up to boot into the older kernel version by default instead?

Right now when it starts up from cold I need to let it fail to load .19 before power cycling and then the menu with the various options appears.

How do I get it to boot the older kernel as the default setting?

---

### Post by mushwars on 2010-02-06
to boot your old kernel you need to get the grub menu..
to do this hold down the shift key ( havent tried it been told it works )
then choose your old kernel.

then you can edit your /boot/grub/grub.cfg and move your old kernel to the top of the list so that way it boots automatically.

---

### Post by Leppie on 2010-02-06
> **mushwars said:**
> to boot your old kernel you need to get the grub menu..
to do this hold down the shift key ( havent tried it been told it works )
yes, you need to hold the shift key to get to the boot menu.

you can try to re-install the 19 kernel packages:
```
sudo apt-get purge linux-headers-2.6.31-19 linux-headers-2.6.31-19-generic linux-image-2.6.31-19-generic
sudo apt-get install linux-headers-2.6.31-19 linux-headers-2.6.31-19-generic  linux-image-2.6.31-19-generic
```

---

### Post by Elfy on 2010-02-06
better to edit the grub file than the grub.cfg file

```
gksudo gedit /etc/default/grub
```

find the GRUB_DEFAULT=0 line and change the number - starts counting from zero, so assuming you have -19 and then -19 recovery mode then -18 will be 2 

after saving and closing the file - update grub

```
sudo update-grub
```

Alternatively you can edit the same file so that you see the menu on boot

#GRUB_HIDDEN_TIMEOUT=0

once again any changes to the file need update-grub to be run

---

### Post by manaboutdog on 2010-02-06
> **Leppie said:**
> yes, you need to hold the shift key to get to the boot menu.

you can try to re-install the 19 kernel packages:
```
sudo apt-get purge linux-headers-2.6.31-19 linux-headers-2.6.31-19-generic linux-image-2.6.31-19-generic
sudo apt-get install linux-headers-2.6.31-19 linux-headers-2.6.31-19-generic  linux-image-2.6.31-19-generic
```

Ok, tried reinstalling 19 as above, but now it seems to have screwed the box completely. 
During boot up it goes into a disk check mode, this doesn't complete and I get transferred to a command prompt with the following text on top:
[FONT=Courier New][SIZE=3]
Mount of filesystem failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
root@manaboutdog:~#[/SIZE][/FONT]

Pressing ctrl-d just gets me back to the same place. I've tried this with the old & new kernel versions and both are the same.

Anything I can do from the maintenance shell to fix this? Or do I need to reload from scratch?

---

### Post by 73ckn797 on 2010-02-06
If you can get into Ubuntu again via an earlier kernel, you can remove the 19 kernel in Synaptic. You can also get "Startup Manager" from Synaptic and use that to designate the default kernel to boot from.

I just had issues with my laptop. Running fsck I saw there were problems with the 19 kernel. Let the check run and answer the prompts "yes". It took a few minutes but on reboot all was right again.

Something was written to the drive incorrectly which caused the issue. I think.

---

### Post by Leppie on 2010-02-06
yes, do a fsck. it may be useful with the options p (automatically repair) and f (force):
```
fsck -pf /ubuntu/partition
```

---

