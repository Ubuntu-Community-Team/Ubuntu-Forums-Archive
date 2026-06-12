---
title: "Problem with ntfs-config software"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by BLiNOK on 2010-10-18
Hi guys,
I have a problem regarding the NTFS Configuration Tool software. When I try to start it in Terminal I get the following error:
ntfs-config
Traceback (most recent call last):
  File "/usr/bin/ntfs-config", line 102, in <module>
    main(args, opts)
  File "/usr/bin/ntfs-config", line 75, in main
    app = NtfsConfig()
  File "/usr/lib/pymodules/python2.6/NtfsConfig/NtfsConfig.py", line 56, in __init__
    os.mkdir(HAL_CONFIG_DIR)
OSError: [Errno 2] No such file or directory: '/etc/hal/fdi/policy'

and it won't start. Can anyone help ? I didn't have this problem on ubuntu 9.04. I now have ubuntu 10.10

---

### Post by Morbius1 on 2010-10-18
You're using 10.10? It looks like a known bug: [https://bugs.launchpad.net/ntfs-config/+bug/657965](https://bugs.launchpad.net/ntfs-config/+bug/657965)

Looks like you're going to have to do it the old way. For example:
**STEP 1: Find out how the system sees your partitions**
```
 sudo blkid -c /dev/null
```This will output for example, among other things the following partition that I want to mount at boot:
>  [COLOR=Blue]/dev/sda1[/COLOR]: UUID="DA9056C19056A3B3" LABEL="WinXPD" TYPE="ntfs"**STEP 2: Create a mount point for your partition to live in**
```
 sudo mkdir /media/WinD
```**STEP 3: Add a line to /etc/fstab/ to have this partition mount at boot:**
```
/dev/sda1 /media/WinD ntfs defaults,nls=utf8,umask=007,gid=46 0 0 
```[COLOR=Blue]* Note: you can even make it simpler than that:*[/COLOR]```
/dev/sda1 /media/WinD ntfs defaults 0 0
```**Step 4: Mount them by executing the new fstab**
```
 sudo mount -a
```[B]
[COLOR=Blue]
[/COLOR][/B]

---

### Post by coffeecat on 2010-10-18
Consider this a blessing. Ntfs-config has been an unmaintained project since very shortly after it was first coded, and has been credited with doing some very unfortunate things.

However, if you do want to use it on 10.10, try installing the package hal. This will at least get it to open for you but whether it will work properly thereafter I have no idea. Or at least work as properly as it ever did.

Even if this is a solution for 10.10 it is not a long-term one since hal is being deprecated from Ubuntu (I believe).

---

### Post by Morbius1 on 2010-10-18
> **coffeecat said:**
> Consider this a blessing. Ntfs-config has been an unmaintained project since very shortly after it was first coded, and has been credited with doing some very unfortunate things.
Amen :)

---

### Post by BLiNOK on 2010-10-18
I managed to fix it. Thank you all for your good support as always. U guys are the best.

---

