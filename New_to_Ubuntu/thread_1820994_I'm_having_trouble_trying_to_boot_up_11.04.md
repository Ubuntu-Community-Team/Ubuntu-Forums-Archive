---
title: "I'm having trouble trying to boot up 11.04"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by L Campbell on 2011-08-08
I have a 20GB Quantum fireball hard drive on my PC and just installed 11.04 on it.
Everything seemed to go well and I used it for about an hour, then shut it down.

When I tried to re-boot I got the message "System disk failure, insert system disk and press enter".

Since then I have tried putting the Master connection into the hard drive, the Slave connection and tried putting the 'jumper' into all of the 5 positions but NO combination will get it to work.

I would appreciate it if you would give me a suggestion.

TIA

---

### Post by oldfred on 2011-08-08
If this is an older IDE system, then you can only boot from primary master. Somewhat newer systems used cable select and jumpers have to be set to cable select. Some also have a master with slave jumper. But jumpers have to be correct for your configuration.

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

### Post by L Campbell on 2011-08-08
> **oldfred said:**
> If this is an older IDE system, then you can only boot from primary master. Somewhat newer systems used cable select and jumpers have to be set to cable select. Some also have a master with slave jumper. But jumpers have to be correct for your configuration.

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

Thanks for your suggestions here.

I only have the one Hard Drive (an IDE) in my PC so I will try messing with it again tomorrow.

It seems logical to me that, if I try each jumper setting with the Master connection and then each jumper setting with the Slave, I should have covered every option.  This is why I am confused.

Kind regards.

---

### Post by oldfred on 2011-08-08
Often the CD drive is a slave, or it has its own cable so it is on the secondary channel and separate from the primary channel.

Often there is  a label on the drive or you can look on the Internet for the correct jumper settings for your model of drive.

---

### Post by amjjawad on 2011-08-08
Oldfred, last time I did my test if you still remember, my IDE HDD was Slave and it worked without issues. Unless I'm missing something here :)

@OP:
Make sure that your BIOS does detect your HDD first.
Also, make sure you set the correct jumper and connect it to the correct cable. Usually IDE Cables have two ends, one is Master and the other is Slave.
If your BIOS is able to detect your HDD then we can check the OS but first, the hardware must be checked whether it's detected or not.

Edit:
Sorry oldfred, just ignore my comment!

---

### Post by retchid on 2011-08-08
it worked and then it did not
obvious error is boot sector corrupted
Set boot option to USB or DVD and use a UBUNTU Live DVD or USB

If gets into live mode and you can see your drive (either in MY computer or through the partitioner program) it is clearly not dead which is highly unlikely anyway given that it worked before

option is to reinstall grub/ubuntu or reformat your drive to get rid of errors and reinstall

Depend if you want to waste days chasing your tail everytime this happens with UBUNTU or XP for that matter- although XP will let you recover with a repairi disk

- I installed Opensuse KDE instead and now no longer get black screens after the computer shuts down or crashes.


PS. The problem was not the drive but corrupt boot sector
switching jumper just confused things but should not really make much of a difference just use a USB or DVD to Live install your Drive will probably show up whether its set to master or slave provided its connected

---

### Post by westie457 on 2011-08-08
What has bootinfoscript got to say about you hard drive. Download and instructions are available[ here]("http://bootinfoscript.sourceforge.net/")

---

### Post by L Campbell on 2011-08-10
> **amjjawad said:**
> Oldfred, last time I did my test if you still remember, my IDE HDD was Slave and it worked without issues. Unless I'm missing something here :)

@OP:[B]
Make sure that your BIOS does detect your HDD first.
Also, make sure you set the correct jumper and connect it to the correct cable. Usually IDE Cables have two ends, one is Master and the other is Slave.
If your BIOS is able to detect your HDD then we can check the OS but first, the hardware must be checked whether it's detected or not.

Edit:
Sorry oldfred, just ignore my comment!

Well, it seems that this is the solution:-

"Make sure that your BIOS does detect your HDD first."

I typically have my BIOS set to boot from 'CDROM' but switching back to 'HDD' has enabled me to get my hard drive to boot.

Many thanks to all of you for all the helpful suggestions.

---

### Post by amjjawad on 2011-08-10
> **L Campbell said:**
> Well, it seems that this is the solution:-

"Make sure that your BIOS does detect your HDD first."

I typically have my BIOS set to boot from 'CDROM' but switching back to 'HDD' has enabled me to get my hard drive to boot.

Many thanks to all of you for all the helpful suggestions.

You Welcome and glad you managed to fix it :)

Checking BIOS and/or Hardware must be the first step.

Good luck and enjoy :D

---

