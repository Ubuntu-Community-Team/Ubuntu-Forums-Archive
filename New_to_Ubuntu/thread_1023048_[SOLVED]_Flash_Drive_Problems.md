---
title: "[SOLVED] Flash Drive Problems"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by brenan on 2008-12-27
I think I corrupted my flash drive. I wrote a script to put a tarball of my media on it as backup, but it stopped halfway through, and now I can't delete files off of it, put new files on, or read the ones that are already on it. So how do I fix it?
Here's the script:
 # !/bin/bash
# Copies stuff to flash drive.

to="/media/PATRIOT"
cd
rm -r $to/*
tar -czf $to/backup.tgz bin Documents Images Library Music /usr/share/backgrounds

---

### Post by mkvnmtr on 2008-12-27
If you have Gparted installed you can open that and reformat or do just about anything you want. If you don't have it installed it takes about 2 minutes.

---

### Post by brenan on 2008-12-27
Alright thanks. I just unmounted it and it seems to be working fine now.

---

