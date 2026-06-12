---
title: "how do I find out if my dvd-rw can burn to dl dvds?"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by nolliecrooked on 2009-05-27
is there a Terminal command or something?

---

### Post by mapes12 on 2009-05-28
Have you tried a GUI application such as K3b or K9copy. You can search for and install them via Synaptic.

---

### Post by nhasian on 2009-05-28
also it would say DL on the drive itself.  alternatively you can check the make & model on the internet for specs.

---

### Post by nandemonai on 2009-05-28
On the front of the drive tray it'll have a bunch of stuff written on it (most do anyway). My LG has this: 'RW: DVD-R **DL**'

If it has DL written there then it supports Dual Layer ;)

---

### Post by MrWES on 2009-05-28
> **nandemonai said:**
> On the front of the drive tray it'll have a bunch of stuff written on it (most do anyway). My LG has this: 'RW: DVD-R **DL**'

If it has DL written there then it supports Dual Layer ;)

type
```
sudo lshw -C Disk
```
from the terminal, and it should output the acceptable types of media.

Bill

---

### Post by nandemonai on 2009-05-28
> **MrWES said:**
> type
```
sudo lshw -C Disk
```
from the terminal, and it should output the acceptable types of media.

Bill

Ah good point but, though lshw displays acceptable media types, to my knowledge it doesn't show whether a drive supports Dual Layer disks or not.

Perhaps I'm missing something? I know for a fact my burner will handle Dual Layer discs but alas it doesn't list DL anywhere except on the drive itself.

```
  *-cdrom                 
       description: DVD-RAM writer
       product: DVD-RAM GSA-H22N
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.00
       serial: [HL-DT-STDVD-RAM GSA-H22N1.0006/08/05
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
```

---

### Post by MrWES on 2009-05-28
> **nandemonai said:**
> Ah good point but, though lshw displays acceptable media types, to my knowledge it doesn't show whether a drive supports Dual Layer disks or not.

Perhaps I'm missing something? I know for a fact my burner will handle Dual Layer discs but alas it doesn't list DL anywhere except on the drive itself.

```
  *-cdrom                 
       description: DVD-RAM writer
       product: DVD-RAM GSA-H22N
```

I just googled DVD-RAM GSA-H22N and came up with tons of hits of reviews, etc.
[http://www.cdfreaks.com/reviews/LG-GSA-H22N-Super-Multi-DVD-Burner-Review/DVD-RAM-writing-performance.html]("http://www.cdfreaks.com/reviews/LG-GSA-H22N-Super-Multi-DVD-Burner-Review/DVD-RAM-writing-performance.html")

---

### Post by newbee70 on 2009-05-28
> **nandemonai said:**
> Ah good point but, though lshw displays acceptable media types, to my knowledge it doesn't show whether a drive supports Dual Layer disks or not.

Perhaps I'm missing something? I know for a fact my burner will handle Dual Layer discs but alas it doesn't list DL anywhere except on the drive itself.

```
  *-cdrom                 
       description: DVD-RAM writer
       product: DVD-RAM GSA-H22N
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.00
       serial: [HL-DT-STDVD-RAM GSA-H22N1.0006/08/05
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
```

Same here both show on the face they write dl -r's

```

  *-cdrom:0
       description: DVD writer
       product: DVDRW SOHW-832S
       vendor: LITE-ON
       physical id: 2
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: VS0E
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=open
  *-cdrom:1
       description: DVD-RAM writer
       product: DVDRW LH-20A1H
       vendor: LITE-ON
       physical id: 3
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: LL0B
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open

```

---

