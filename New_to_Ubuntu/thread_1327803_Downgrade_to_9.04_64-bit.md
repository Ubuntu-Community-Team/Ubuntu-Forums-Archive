---
title: "Downgrade to 9.04 64-bit"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by Aaris on 2009-11-15
After upgrading to Ubuntu 9.10, I have been dissatisfied with its performance and I would like to go back to 9.04. I have made a Live CD with the ISO on it, but I can't figure out how to do a clean install over the existing Ubuntu. I haven't been able to find any easy instructions for this, as most people switch from Windows to Ubuntu, rather than doing a "downgrade." Could someone help me with this?

---

### Post by Bios Element on 2009-11-15
Do it the same way you would any other install. Assuming you don't have another Operating system installed, just let the installer handle the partitions and tell it to use all available space. It'll automatically create the needed partitions and format the old data.

---

### Post by dalee on 2009-11-15
Hi,

I had to do that myself the first go around with Karmic. But I just simply did a normal install. Jaunty will run on Ext4 just fine.

---

### Post by Aaris on 2009-11-15
So an automatic installer should pop up? Because one isn't, so perhaps something is wrong with the live CD I made.

---

### Post by theozzlives on 2009-11-15
> **Aaris said:**
> After upgrading to Ubuntu 9.10, I have been dissatisfied with its performance and I would like to go back to 9.04. I have made a Live CD with the ISO on it, but I can't figure out how to do a clean install over the existing Ubuntu. I haven't been able to find any easy instructions for this, as most people switch from Windows to Ubuntu, rather than doing a "downgrade." Could someone help me with this?

If you have a seperate /home partition, you just select manual at the partitioner and format the / partition. If not, you'll need to backup your /home. /home is basically all you need to preserve.

---

### Post by ArinSky on 2009-11-15
If you dual boot windows, you could save all your files on your windows partition, boot from a windows CD, reformat the partitions, reinstall ubuntu and move everything back. 

Though I'm guessing you're looking for a way that doesn't involve windows, or repartitioning :p

---

### Post by falconindy on 2009-11-15
> **theozzlives said:**
> If you have a seperate /home partition, you just select manual at the partitioner and format the / partition. If not, you'll need to backup your /home. /home is basically all you need to preserve.
/etc, /var, and /usr can also have very useful things that one might want to save.

---

### Post by Aaris on 2009-11-15
Unfortunately, I am confused. I have everything backed up that I feel that I need to save. I'm also currently running Ubuntu 9.10 only. My laptop doesn't boot to any other OS. The only problem I'm having now is getting the installer to run.

No automatic installer runs when I insert the live CD. If one is supposed to run, then I've done something wrong. Otherwise, I can only guess that I should use Synaptic to install from the CD.

---

### Post by SPazzo on 2009-11-15
Is it just not booting from the CD?  When the computer boots try going to the boot menu and booting from the CD drive (with the disc in the drive).

That happened with my computer.

---

### Post by Aaris on 2009-11-15
> **SPazzo said:**
> Is it just not booting from the CD?  When the computer boots try going to the boot menu and booting from the CD drive (with the disc in the drive).

That happened with my computer.

Thanks, I will try this.

---

### Post by Aaris on 2009-11-15
> **SPazzo said:**
> Is it just not booting from the CD?  When the computer boots try going to the boot menu and booting from the CD drive (with the disc in the drive).

That happened with my computer.

Alright, I tried to do this, but no luck. I restarted a couple of times, looking for a way to boot from the CD in the boot menu, but to no avail. I found the System Utilities and the GRUB 2 menu. Is there a way to boot from the CD once Ubuntu has started? The .exe file doesn't work.

---

### Post by Aaris on 2009-11-15
Nevermind, I'm going to try something else.

---

### Post by pablolie on 2009-11-15
You need to tell the BIOS to first start from the CD. Typically you accomplish this by hitting DEL or some F key right after turning on the computer. Be careful when you mess around with BIOS. But in there, the boot device priority can be defined. It sounds like your computer is set up to ignore the CD when booting.

I would be interested - which aspect of 9.10 performance that turned you off.

---

