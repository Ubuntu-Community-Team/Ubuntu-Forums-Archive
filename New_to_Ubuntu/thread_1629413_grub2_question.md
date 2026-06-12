---
title: "grub2 question"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by oboedad55 on 2010-11-23
I'm running Ubuntu Lucid on the first partition of my SATA drive. So far so good. I installed Debian Squeeze on an IDE drive which then overwrote the original grub. I want to restore the grub install from the original lucid install. The problem seems to be how each program determines hard drive numbering. Gparted sees the sata drive as sda. It seems grub sees the ide drive as sda. The debian install sees the order the same way. What's my plan?

---

### Post by drs305 on 2010-11-23
Boot to your Ubuntu installation, then just run 
```
sudo grub-install /dev/sda
```
It will write to the sata MBR and copy the files to your Ubuntu partition. Do not include the partition designation.
```
sudo grub-install /dev/sda
```
Unless you disable it, Grub2 uses UUIDs for it's identifications so it should solve your problem for you.

You can actually install Squeeze's bootloader on the ide drive, as long as BIOS points to your sata drive first. That way if Grub fails you can simply change the BIOS boot order and regain a bootloader.

Nothing else should be required, but there is also the option of creating a *device.map* file where you can specify things (sudo grub-mkdevicemap). It's located in /boot/grub but you probably won't need to create one.

---

### Post by oboedad55 on 2010-11-23
Thanks for the reply. I had already tried what you suggested. I think the problem may be that the bios sees the ide drive as the first drive. No clue why that is, but there's no way to change it. I tried installing grub to sdb but it wouldn't overwrite the debian grub.If I unplug the ide drive then I get the usual Ubuntu grub. It's a kludge but that may be the only solution.  Any other thoughts? Never mind, I figured it out. The computer was built with the CD drives on the second ide connection and I was running, therefore, my hard drive on the first ide port. So.... I switched them. Problem solved, all is right oncew again with the world. I feel like Homer Simpson. "I am so smart, I am so smart, smrt, smrt, I mean smArt" Doh! Thanks for responding so quickly.

---

### Post by drs305 on 2010-11-23
Disclaimer: I feel like I'm missing something obvious here but I'm about to log off. You might wait for a better solution...

I don't know why Debian wouldn't let you overwrite an MBR but I've never used it. I have mixed drives and my BIOS allows me to switch between them. 

If you are sure that isnt' possible with your BIOS, you could try writing lilo to the ide MBR. If it does, I know Grub2 can overwrite lilo.

You could backup both MBRs before you start playing with them with the following commands. The '512' entries include the partition table.
```

sudo dd if=/dev/sda of=sda.MBR.446.img bs=446 count=1 
sudo dd if=/dev/sda of=sda.MBR.512.img bs=512 count=1 
sudo dd if=/dev/sdb of=sdb.MBR.446.img bs=446 count=1 
sudo dd if=/dev/sdb of=sdb.MBR.512.img bs=512 count=1 

```

Install lilo with the following. Don't worry about the messages about not installing/configuring lilo completely.
```
sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr
```

At that point lilo should be written to the MBR and you should be able to overwrite it and install Grub2 to the sdb MBR.

If you need to restore the old MBR:
```
dd of=/dev/sd**X** if=/**path/filename.img** bs=**446** count=1
```

---

### Post by oboedad55 on 2010-11-23
I guess didn't see my edit. I had the ide hard drive on the master and the CDs on the secondary. I switched the cables. Now it makes sense. SATA is hda, and IDE is hdb. Before each system thought it was on drive 1 regardless. I don't care what Debian thinks, I just want Ubuntu handling the boot loader. Thanks again for the help.

---

### Post by drs305 on 2010-11-23
> **oboedad55 said:**
> I guess didn't see my edit. I had the ide hard drive on the master and the CDs on the secondary. I switched the cables. Now it makes sense. SATA is hda, and IDE is hdb. Before each system thought it was on drive 1 regardless. I don't care what Debian thinks, I just want Ubuntu handling the boot loader. Thanks again for the help.

I guess the 'something obvious' from my post was that you had already found a solution!  ;-)

Would you mind marking the thread 'solved' via the 'Thread Tools' link near the top right of the first post. Thanks.

Happy Ubuntu-ing !

---

### Post by oboedad55 on 2010-11-23
> **drs305 said:**
> I guess the 'something obvious' from my post was that you had already found a solution!  ;-)

Would you mind marking the thread 'solved' via the 'Thread Tools' link near the top right of the first post. Thanks.

Happy Ubuntu-ing !

Will do, thanks a heap. After your first post I put my brain in gear...

---

