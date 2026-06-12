---
title: "Need  help  with DVD please."
date: 2009-09-26
forum: New to Ubuntu
---

### Post by 289531.EXE on 2009-09-26
[RIGHT]When  I put ina 16x speed blank DVD into my LT,  it doesn't show up.

Audio CDs are fine and appear on the desktop but DVDs don't and even when I check  the home folder, theres no DVD in the options.

Can someone help or suggest a  solution to this problem?
[/RIGHT]

---

### Post by nhasian on 2009-09-26
what is the make/model of your dvd-rom?  Perhaps it doesnt read discs that fast, or maybe it doesnt like that brand of media.  you can see if your dvd burner has a firmware update from the manufacturer.

> **289531.EXE said:**
> [RIGHT]When  I put ina 16x speed blank DVD into my LT,  it doesn't show up.

Audio CDs are fine and appear on the desktop but DVDs don't and even when I check  the home folder, theres no DVD in the options.

Can someone help or suggest a  solution to this problem?
[/RIGHT]

---

### Post by tryinghard on 2009-09-26
maybe use a lens cleaner?

---

### Post by 289531.EXE on 2009-09-26
> **nhasian said:**
> what is the make/model of your dvd-rom?  Perhaps it doesnt read discs that fast, or maybe it doesnt like that brand of media.  you can see if your dvd burner has a firmware update from the manufacturer.


how do igo about doing this?

---

### Post by nhasian on 2009-09-26
> **289531.EXE said:**
> how do igo about doing this?

at a terminal prompt, type:

```
sudo lshw
```

mine says:

>            *-cdrom
                description: DVD-RAM writer
                product: DVD A  DS8A1H
                vendor: Slimtype
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: WH66
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc


Also it usually says on the bios post screen when you first turn on your computer.

---

### Post by RedRat on 2009-09-26
How old is this RAM writer. I haven't seen one of these for awhile. It appears that it can read but not write to either DVD-R or DVD+R.

---

### Post by nhasian on 2009-09-27
Its the standard dvd writer that came in HP laptops two years ago.  Its burned every media i've tried throwing at it except some TDKs that were 8x only.  they wouldnt allow me to write to them at 2.4X

I've used brasero, gnomebaker, and imgburn (via wine) just fine in ubuntu.

> **RedRat said:**
> How old is this RAM writer. I haven't seen one of these for awhile. It appears that it can read but not write to either DVD-R or DVD+R.

---

### Post by 289531.EXE on 2009-09-29
apparently my dvd drive is just a reader-----BAH! does anyone know what a good price would be for a notebook dvd writer drive?

---

