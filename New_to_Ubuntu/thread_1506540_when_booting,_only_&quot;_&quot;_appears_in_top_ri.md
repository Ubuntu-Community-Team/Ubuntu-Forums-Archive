---
title: "when booting, only &quot;_&quot; appears in top right corner"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by joenewtzie on 2010-06-10
When I boot and load GRUB then select Ubuntu with linux then normally everything loads BUT now only "_" appears and keeps blinking forever.  Any suggestions how to fix this?  Everything was running perfectly before any of this...

---

### Post by joenewtzie on 2010-06-10
> **joenewtzie said:**
> When I boot and load GRUB then select Ubuntu with linux then normally everything loads BUT now only "_" appears and keeps blinking forever.  Any suggestions how to fix this?  Everything was running perfectly before any of this...


Can anyone help me? haha, I'm so confused, why won't Ubuntu boot up?!

---

### Post by anglican on 2010-06-10
> **joenewtzie said:**
> When I boot and load GRUB then select Ubuntu with linux then normally everything loads BUT now only "_" appears and keeps blinking forever.  Any suggestions how to fix this?  Everything was running perfectly before any of this...
Instead of booting normally, choose recovery mode from the Grub menu and see where the booting process gets to. To see the menu you will need to hold down the Shift key while booting (assuming Grub2 otherwise it's the Escape key).

H

---

### Post by joenewtzie on 2010-06-10
> **anglican said:**
> Instead of booting normally, choose recovery mode from the Grub menu and see where the booting process gets to. To see the menu you will need to hold down the Shift key while booting (assuming Grub2 otherwise it's the Escape key).

H

I did that and it just kept going to like the 148th line of stuff said some errors, Ubuntu kept flashing in but it was un-available. I'll try again now.

---

### Post by anglican on 2010-06-10
> **joenewtzie said:**
> I did that and it just kept going to like the 148th line of stuff said some errors, Ubuntu kept flashing in but it was un-available. I'll try again now.
Um, that's as clear as mud! Could you be a bit more specific about "some errors" basically the last line(s) on the screen should tell you where it's getting stuck at.

H

---

### Post by joenewtzie on 2010-06-10
> **anglican said:**
> Um, that's as clear as mud! Could you be a bit more specific about "some errors" basically the last line(s) on the screen should tell you where it's getting stuck at.

H


Yeah, i'm doing it again now, it just keeps repeating...

right now it says

109......ata3.00: status: { DRDY ERR}
109......ata3.00: error : {UNC} 
109......ata3.00: configured for UDMA/100
109......ata3.00: EH complete 

that just keeps refreshing and 109 keeps counting up...its at 220 now.

---

### Post by joenewtzie on 2010-06-10
it also kee[ps saying failed command: READ DMA EXT

---

### Post by joenewtzie on 2010-06-10
any ideas?!

---

### Post by anglican on 2010-06-11
> **joenewtzie said:**
> any ideas?!
Looks like a possible hardware problem. You could try checking the disk connections, maybe replacing the cable or trying plugging it into another sata port. You might also want to boot from a live CD and install smartmon to test the disk:
```
sudo smartctl -a /dev/sdb
(your disk might be sda, sdc or sdd)
```

H

---

### Post by cryptotheslow on 2010-06-11
By any chance is your hard drive a Seagate 7200.11 or Maxtor DiamondMax?

---

### Post by ScottinSoCal on 2010-06-11
My work laptop does this two or three times a week. I've traced it down to a timing problem with my external USB drive not "waking up" when I power up the computer. I can usually hard power down and power up again, and it clears up.

If you don't have an external USB drive, I'd look at either a failing HDD, or BIOS issues.

---

### Post by ScottinSoCal on 2010-06-11
Oh, yeah ^^

The very few times that cycling the power doesn't work, unplugging the external HDD until I'm booted always works.

---

### Post by joenewtzie on 2010-06-11
> **cryptotheslow said:**
> By any chance is your hard drive a Seagate 7200.11 or Maxtor DiamondMax?

I'm using a WDC WD2500BEVS-60UST0 ATA

---

### Post by joenewtzie on 2010-06-11
> **ScottinSoCal said:**
> Oh, yeah ^^

The very few times that cycling the power doesn't work, unplugging the external HDD until I'm booted always works.

So you're saying that if you have Ubuntu boot up installed on a external HD?

---

### Post by joenewtzie on 2010-06-12
What if I just re-install Ubuntu overtop of the old one. I wanted the netbook edition anyway and I installed the new desktop version...

---

