---
title: "Accessing files from windows via SCP/FTP. No national symbols? ÅÄÖ"
date: 2008-02-13
forum: Networking &amp; Wireless
---

### Post by ballongen on 2008-02-13
Hi.

I have a newly installed Ubuntu 7.10

I can create files and directorys with swedish special symbols (ÅÄÖ) inside home catalog, and mount a local windows ntfs drive to /media/hdb1 and create files there.

I have no problem reading the files or creating new. everything is normal.

** On Windows Client:**

On a windows machine, i connect to the ubuntu box
Through FTP (using FlashFXP or TotalCommander-clients).
or via SCP (winscp)

Connection is fine and i can transfers file.

However, all the files and directorys containing swedish symbols ÅÄÖ (A with two dots)
they are filenames are viewed incorrect.

**On another Ubuntu client:**
FTP and SCP works fine, every file and directorys are viewed and read correctly.

I guess this problem is because ubuntu uses UTF and not ISO8859-15 as Windows(sweden) are using.

I try finding some answers on google and ubuntuforums but no luck. 

What should i do to get my files viewed correctly?

Can i force the SSH (SCP) or FTPd (proftpd) to use ISO8859-15 on clients?

Please help me

Best Regards

Ballongen

---

