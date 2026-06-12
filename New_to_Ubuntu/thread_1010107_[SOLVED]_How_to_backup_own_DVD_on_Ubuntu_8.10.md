---
title: "[SOLVED] How to backup own DVD on Ubuntu 8.10?"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by resander on 2008-12-13
This is a 36 min video Albert Lee Master Session bought four weeks ago. Filesystem is UDF. Size 1.7GB. The dvd has two directories Audio_TS and Video_TS. The Audio_TS is empty and Video_TS contains parts like:

Video_TS.BUP, Video_TS.ifo, Video_TS.vob
VTS_01.BUP, Vts_01.ifo, Vts_01.00, vts_01.01
.... 
VTS_04.BUP, Vts_04.ifo, Vts_04.00, vts_04.01

Tried the following:

Brasero:  the 'Copy' button was greyed out.

K3b:      'data encrypted - could not copy' it said

K9copy:   on click on 'copy dvd' icony got 'DVD not opened' message

Gnomebaker:  did not have a copy dvd function

X-CD Roast:  immediately got message 'No root config file found or not readable'

So not much joy. 

Will I be able to backup my DVD?

---

### Post by billgoldberg on 2008-12-13
[http://linuxowns.wordpress.com/2008/10/07/how-to-rip-a-dvd-in-ubuntu-to-avi-the-easy-way/](http://linuxowns.wordpress.com/2008/10/07/how-to-rip-a-dvd-in-ubuntu-to-avi-the-easy-way/)

Try this (don't miss the link to the codecs !!!).

---

### Post by mikeyphi on 2008-12-13
Try dvdrip, available through Applications - ADD/REMOVE

---

### Post by albinootje on 2008-12-13
Did you install libdvdcss2 ?
One way to install it is through : [http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by resander on 2008-12-14
The backup is working.

libdvdcss2 was needed (installed  via synaptic); it was not installed as part of the 'restricted' package script that I used after installing Ubuntu.

But libdvcss2 is not enough. Brasero and k3b both failed. Brasero: error in reading video DVD (error in vts css key) and k3b: failed to retrieve all css keys. Decryption failed.

However, k9copy worked perfectly and was simple to use. It generated an iso image which I burned to a backup dvd using Brasero. The whole process finished in less than 15 minutes on my 2.4GHz P4 with 2 GB of memory.
 
I also installed and tried dvd::rip which did the decryption and put the results into an AVI directory and VOB directory. Process took about an hour, but I could not figure out how to use the various output parts to make an iso dvd backup with original scene select menus intact.

Many thanks.

---

### Post by chitarrino on 2009-02-11
I successfully used **dvdbackup** for this task.

```
dvdbackup -M -o ~/Desktop/
```

-M (mirror) copies the whole DVD structure.

---

### Post by Dayylin on 2009-02-26
Found a good blog that tells how to do it.

[http://davestechsupport.com/blog/2009/02/04/how-to-backup-a-dvd-with-ubuntu-linux/]("http://davestechsupport.com/blog/2009/02/04/how-to-backup-a-dvd-with-ubuntu-linux/")

---

