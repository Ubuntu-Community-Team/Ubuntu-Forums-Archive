---
title: "Problem with DVD drive"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by yhertz on 2009-01-02
Hey, 
I just installed ubuntu 8.10 . 
I've got 2 dvd drives on my computer, one of them works properly and reads all of my discs, but the other one doesn't... it only reads the ubuntu installation cd and some cd's with mp3 files and nothing else. 
It used to read everything fine when I was working with windows before.

Suggestions anyone ?  Would appreciate all help I can get... :)

---

### Post by donkyhotay on 2009-01-02
Please post the results of:
```
dmesg | grep -i dvd && dmesg | grep -i cdrom
```

---

### Post by yhertz on 2009-01-02
these are the results:

> [   15.236248] ata9.00: ATAPI: LITE-ON DVDRW LH-20A1P, KL0A, max UDMA/66
[   15.236264] ata9.01: ATAPI: SONY DVD-ROM DDU1615, FYS1, max UDMA/33
[   15.656102] scsi 10:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1P   KL0A PQ: 0 ANSI: 5
[   15.657063] scsi 10:0:1:0: CD-ROM            SONY     DVD-ROM DDU1615  FYS1 PQ: 0 ANSI: 5
[   16.296361] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray



---

### Post by yhertz on 2009-01-03
can anyone help? :confused:

---

