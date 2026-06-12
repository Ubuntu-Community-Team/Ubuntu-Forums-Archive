---
title: "Can't access encrypted flash drive after fresh 10.10"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by lkejke on 2010-12-24
I recently encrypted my 4GB ScanDisk Cruzer Blade using Disk Utility. The partition on it is formatted with Ext4.

After freshly installing Ubuntu 10.10, I can't access the drive. It says my passphrase is wrong, but I'm 99.9% sure it isn't. I have two USB drives, a 320GB WD MyPassport and a 4GB SD Cruzer Blade. Both were Ext4 and encrypted and had the same password. I'd been using them regularly for the past week, entering the password each time I mounted the drives.

Now that I've installed a fresh Ubuntu 10.10, I can't get to my files on these drives.

Is there any obvious thing I should try?

---

### Post by lkejke on 2010-12-24
More info...

When I use the file browser to select the drive and enter the password, I get this error:

> **Error**
**Unable to mount 4.0 GB Encrypted**
Error starting job: Failed to execute child process "cryptsetup" (No such file or directory

---

### Post by lkejke on 2010-12-24
I may have found an answer. There might be something I still need to install.

[INDENT][https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/429987]("https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/429987")

Michael-250 wrote:
> It seems that the package cryptsetup is missing in the standard installation. After installing that package I didn't get the 'No such file or directory' error anymore.

But then I got another error msg 'Error creating partition: timeout (10s) waiting for partition to show up'. Any hints?[/INDENT]

However, he had a different problem to me.

---

### Post by lkejke on 2010-12-24
SOLVED!

```
sudo apt-get install cryptsetup
```

---

