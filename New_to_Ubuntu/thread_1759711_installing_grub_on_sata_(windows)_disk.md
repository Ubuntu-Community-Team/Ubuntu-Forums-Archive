---
title: "installing grub on sata (windows) disk"
date: 2011-05-16
forum: New to Ubuntu
---

### Post by Boris-- on 2011-05-16
Hi guys, again I have a problem.

I have installed ubuntu on my stationary pc, on my spare IDE drive (sda).

There were some problems with installing grub and it used to go straight to windows xp because the SATA disk (sdb) is the master drive.

Trying to install grub myself I've of course managed to corrupt the MBR and now my pc won't boot:D.

So my question is, how do I install grub on my master (sdb; SATA, windows xp) drive with least pain? I think it should all be ok if I install it there.

Thanks for your help!

Boris

---

### Post by Hedgehog1 on 2011-05-16
Reinstall Grub on Hard Drive from Live CD

Please boot off your LiveCD/LiveUSB, select 'TRY'

Determine what partition holds your Ubuntu root.  In the examples below, they assume that /dev/sd**a5** is your Ubuntu partition.  Yours may be /dev/sd**b5** or /dev/sd**a3** or /dev/sd**b3** or whatever...  Use that.  Also note that your drive MAY be /dev/sd**b**.

In the Terminal (Menu to: Applications >> Accessories >> Terminal):

```
sudo mount /dev/sd**a5** /mnt
```
```
sudo grub-install --root-directory=/mnt /dev/sd**a**
```

***The Hedge***

:KS

---

### Post by seawolf167 on 2011-05-16
See hedgehog1's post, [here ]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")is the official how-to link for reinstalling grub off the LiveCD

---

### Post by Dreigo42 on 2011-05-16
I would boot the live USB/CD. 
Choose "Try Ubuntu"
Open terminal
Run "sudo grub-install sdb"
Run "sudo update-grub"
(all without quotes)
This should overwrite the mbr on sdb and install grub in it's place. 
Update grub should put Ubuntu and Windows into the boot loader menu.

Not 100% on accuracy but this would probably be the easiest way to just install grub on your windows Hard Drive.

---

