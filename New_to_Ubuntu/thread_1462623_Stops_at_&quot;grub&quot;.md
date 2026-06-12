---
title: "Stops at &quot;grub&quot;"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by lilrabbit129 on 2010-04-25
I've run into a weird problem, after installing Ubuntu 9.10, my system simply stops with the word "GRUB". The grub menu doesn't come up, not even grub rescue. Just the word "GRUB".

Background:

I successfully installed Ubuntu 9.10 a week ago on this system and had it working pretty well. I installed it on a 500GB PATA drive. Today I installed 2 2TB HDs into the 2 SATA ports. It would no longer boot, complaining that there was no system files on the drives. Figuring that it was a grub problem I thought the simplest solution was to start from scratch and reinstall everything.

I installed on the 500GB hd, which is now /dev/sdc1. The 2TB hd's are sda and sdb. After reinstalling I can't even get to the grub menu, it simply stops after trying to boot, with the word "GRUB" on the screen.

Any ideas?

Thanks in advance,

---

### Post by friv_livs on 2010-04-25
Did you reinstall grub 2 from live CD yet?

---

### Post by lilrabbit129 on 2010-04-26
> **friv_livs said:**
> Did you reinstall grub 2 from live CD yet?

Just tried reinstalling by booting with the liveCD and doing this command:

```
sudo grub-install --root-directory=/mnt/ /dev/sdc
```

I got the following output:

> 
(hd0) /dev/sda
(hd1) /dev/sdb
(hd2) /dev/sdc


No change in behavior.

---

### Post by carl4926 on 2010-04-26
Grub needs to be on the first boot HD

---

### Post by oldfred on 2010-04-26
while moving drives should not make a difference since UUIDs are used for most things, you moved drive from sda to sdc. That would require a reinstall of grub just to make sure it sees the new drive.

Your reinstall should work but 
a: are you booting from sdc
b: when you installed the device map only had sda does it now have all three? If not grub will not see the third drive.

Should look like this:
/boot/grub/device.map
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc

I think you can manually edit or 
If it complains about a device map - I think this works from liveCD just like the reinstall grub.
sudo grub-mkdevicemap
sudo update-grub

---

### Post by lilrabbit129 on 2010-04-26
Not sure how, but after turning the machine off and leaving it for an hour, I came back and it boots fine.

Thanks for everyone's help. I'll reply again if things mysteriously break again. 

Thanks again.

> **oldfred said:**
> while moving drives should not make a difference since UUIDs are used for most things, you moved drive from sda to sdc. That would require a reinstall of grub just to make sure it sees the new drive.

Your reinstall should work but 
a: are you booting from sdc
b: when you installed the device map only had sda does it now have all three? If not grub will not see the third drive.

Should look like this:
/boot/grub/device.map
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc

I think you can manually edit or 
If it complains about a device map - I think this works from liveCD just like the reinstall grub.
sudo grub-mkdevicemap
sudo update-grub

---

### Post by lilrabbit129 on 2010-04-26
I guess it was too good to be true. After letting it run all night to update and create an mdadm RAID1 on the 2x2TB HDs, when I reboot the old problem comes back, ie "GRUB" after POST and nothing else happens.

I did notice that my DVD drive is Primary IDE Master and my 500GB HD, which I'm trying to boot off, is Primary IDE Slave. Would this affect anything?

Thanks for everyone's help.

---

### Post by oldfred on 2010-04-26
It may depend on your BIOS. New SATA drives have BIOS that let you select boot drive, mine calls it primary master. Old IDE drives required jumpers (or cable select position) to determine primary master and BIOS only booted from primary master as it was not smart enough to switch drives around.

---

### Post by lilrabbit129 on 2010-04-26
I do set in the BIOS for it to specifically boot from the 500GB drive. 

It seems strange that it could boot once but not anymore. I'll probably try switching the 500GB and the DVD drive, to make the 500GB the Primary Master, hopefully that will fix the issues. 

I'll keep everyone posted.

---

### Post by lilrabbit129 on 2010-04-28
I am able to get it to boot. The solution seemed to be to put the DVD as Secondary Master and the 500GB as the Primary Master. Also, I don't know how, but the boot priority was reverted to having one of the 2TB drives before the 500GB.

I'm not sure which of these, or what combination of these changes fixed the issue, but it seems to have.

Hopefully this will be of some use to anyone else that runs into this issue. 

Thanks for everyones help.

> **lilrabbit129 said:**
> I do set in the BIOS for it to specifically boot from the 500GB drive. 

It seems strange that it could boot once but not anymore. I'll probably try switching the 500GB and the DVD drive, to make the 500GB the Primary Master, hopefully that will fix the issues. 

I'll keep everyone posted.

---

