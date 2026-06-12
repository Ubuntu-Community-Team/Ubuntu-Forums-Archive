---
title: "rkhunter results"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by maxmem on 2010-10-19
Hi all,
I'm an absolute beginner who just 'inherited a Debian3 installation. Since it was 'broken' (did not boot-up having some messy fstab I suppose) I just ended up installing Ubuntu 10.10; the very first thing I did was running rkhunter, and the log showed me the following warnings:

[17:11:31] Info: Starting test name 'filesystem'
[17:11:31] Info: SCAN_MODE_DEV set to 'THOROUGH'
[17:11:32]   Checking /dev for suspicious file types         [ Warning ]
[17:11:32] Warning: Suspicious file types found in /dev:
[17:11:32]          /dev/shm/pulse-shm-925659494: data
[17:11:32]          /dev/shm/pulse-shm-1581426552: data
[17:11:32]          /dev/shm/pulse-shm-604933372: data
[17:11:32]          /dev/shm/pulse-shm-2009766174: data
[17:11:32]   Checking for hidden files and directories       [ Warning ]
[17:11:32] Warning: Hidden directory found: /dev/.udev
[17:11:32] Warning: Hidden directory found: /dev/.initramfs

I could find no references to such files searching through the forums.
...should I be concerced about the above lines?

Thanks for any hints.
MaxM

---

### Post by GabrielYYZ on 2010-10-19
i'd say those are false positives, but i'd advise you to wait for a 2nd opinion, hopefully from a more experienced user.

---

### Post by rburkartjo on 2010-10-19
max here is a thread from the forms that should answer your question

(in a nutshell not to worry)

[http://ubuntuforums.org/archive/index.php/t-774783.html](http://ubuntuforums.org/archive/index.php/t-774783.html)

---

### Post by gandaran on 2010-10-19
nothing wrong there, those results are normal output, if you don't want them to show up just edit the rkhunter configuration file
```
sudo gedit /etc/rkhunter.conf 
```

---

### Post by CharlesA on 2010-10-19
> **gandaran said:**
> nothing wrong there, those results are normal output, if you don't want them to show up just edit the rkhunter configuration file
```
sudo gedit /etc/rkhunter.conf 
```

Use gksudo instead of sudo for graphical apps.

@OP: If that's your first time running rkhunter, I would suggest you read the [security sticky]("http://ubuntuforums.org/showthread.php?t=510812").

---

### Post by rburkartjo on 2010-10-19
while we are on the subject what about this warning from my run

[10:32:59] /usr/bin/ldd                                      [ Warning ]
[10:32:59] Warning: The file properties have changed:
[10:32:59]          File: /usr/bin/ldd
[10:32:59]          Current hash: 3aa1f12481dc8aee1a60a343c7a6b46a9a289403
[10:32:59]          Stored hash : 38716f3fb2717b91e2fdeb0e6f5605de067ff8bb
[10:32:59]          Current inode: 137791    Stored inode: 137824
[10:32:59]          Current file modification time: 1286703836 (10-Oct-2010 04:43:56)
[10:32:59]          Stored file modification time : 1284143534 (10-Sep-2010 13:32:14)
[10:32:59] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.

---

### Post by gandaran on 2010-10-19
> **rburkartjo said:**
> while we are on the subject what about this warning from my run

[10:32:59] /usr/bin/ldd                                      [ Warning ]
[10:32:59] Warning: The file properties have changed:
[10:32:59]          File: /usr/bin/ldd
[10:32:59]          Current hash: 3aa1f12481dc8aee1a60a343c7a6b46a9a289403
[10:32:59]          Stored hash : 38716f3fb2717b91e2fdeb0e6f5605de067ff8bb
[10:32:59]          Current inode: 137791    Stored inode: 137824
[10:32:59]          Current file modification time: 1286703836 (10-Oct-2010 04:43:56)
[10:32:59]          Stored file modification time : 1284143534 (10-Sep-2010 13:32:14)
[10:32:59] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.
thats because you have installed some updates so the files have changed
run
```
sudo rkhunter --propupd
```
to update file list.

---

### Post by rburkartjo on 2010-10-19
tks gan i will remember that

---

