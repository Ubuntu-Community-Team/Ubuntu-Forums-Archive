---
title: "the disappearance of Windows 7"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by matrioska on 2011-04-27
:(:(:(:(
I've been using dual partition for awhile and everything was fine.
but today Windows7 doesn't appears in the booting list and if I try to reach the system from places in Ubuntu, well the computer switches off...
is that a bad sign?
I need Windows for a Premiere project I am working on... please save me!!!!

---

### Post by jtarin on 2011-04-27
Try the command in a terminal ```
sudo update-grub2
```

---

### Post by matrioska on 2011-04-27
I´ve just tried but Win7 doesn´t appear in the terminal list... :cry: i also check any problem in the system when booting, but none apparently...

---

### Post by Arand on 2011-04-27
```
sudo fdisk -l
```Should list your partitions, note which one is the windows one (e.g. sda2).

When in the grub menu, press [c] and try these commands:```
set root=(hd0,2)
## This corresponds to sd[a][2], i.e. a=0 2=2
## If your windows partiton is differently named, change accordingly
chainloader +1
boot
```Does this give any visible errors?

If it worked, make sure to schedule a chkdsk from windows, a messy filesystem might be the cause of grub not detecting it.

If none of this works, download the latest [Boot Info Script]("http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob;f=boot_info_script.sh")and post the contents of RESULTS.TXT here

- arand

---

### Post by Zanderist on 2011-04-27
Are you using wubi?

Don't try anything without reporting in this thread first, because when I had troubles with ubuntu and windows 7 I ended up losing both Operating Systems, though I eventually got ubuntu back and then windows 7.

Get the Grub customizer.

```
sudo apt-get install grub-customizer
```

---

### Post by K9Crunch on 2011-04-27
Might be partition errors, will have to boot from the windows cd into recovery and run a check on it.

---

