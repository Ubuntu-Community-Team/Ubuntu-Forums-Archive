---
title: "Is it possible for lucid to get infected with some rubbish viruses ?"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by Trinity33 on 2010-08-18
i run scan used  rkhunter and i have got some warning and need to ask if i should worry about it or not? i mean even if there is a virus i can remove it but i need to be sure it is virus. could please someone advice me ?

[06:11:34] Info: Starting test name 'filesystem'
[06:11:34] Info: SCAN_MODE_DEV set to 'THOROUGH'
[06:11:34]   Checking /dev for suspicious file types         [ Warning ]
[06:11:34] Warning: Suspicious file types found in /dev:
[06:11:34]          /dev/shm/pulse-shm-334664941: data
[06:11:34]          /dev/shm/pulse-shm-3293802749: data
[06:11:34]          /dev/shm/pulse-shm-2631787153: data
[06:11:34]          /dev/shm/pulse-shm-820611920: data
[06:11:34]          /dev/shm/pulse-shm-2996596839: data
[06:11:34]          /dev/shm/pulse-shm-3896618210: data
[06:11:34]          /dev/shm/pulse-shm-4073435596: data
[06:11:34]          /dev/shm/pulse-shm-410924515: data
[06:11:35]          /dev/shm/pulse-shm-3700436098: data
[06:11:35]          /dev/shm/pulse-shm-1348544048: AmigaOS bitmap font
[06:11:35]          /dev/shm/pulse-shm-2832935303: data
[06:11:35]   Checking for hidden files and directories       [ Warning ]
[06:11:35] Warning: Hidden directory found: /etc/.java
[06:11:35] Warning: Hidden directory found: /dev/.udev
[06:11:35] Warning: Hidden directory found: /dev/.initramfs
[06:11:42]
[06:11:42] Info: Test 'apps' disabled at users request.

---

### Post by bodhi.zazen on 2010-08-18
There are no know active viruses for Linux.

I am sorry to say that if you are not willing to google search the results and warnings of rkhunter it is probably best not to use such tools.

You need to start on a known good system, and then understand what those warnings are telling you.

rootkits are not viruses and Linux security is different from Windows security, I suggest you read the security sticky.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

[http://librenix.com/?inode=21](http://librenix.com/?inode=21)

[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

---

### Post by Devastator9 on 2010-08-18
Well said bodhi

---

### Post by pzkfw on 2010-08-18
If you're new to rkhunter, remember that if you upgrade the package (typically through apt) then that will set off the changed hash or whatever it had stored and thinks it's malicious.  It's only because you upgraded and it sees it as a different version.  The idea is, if you DIDN'T upgrade, then those flags mean something.  Also, depending on your distro, some things will always show "Warning" no matter what.  Use this to reset it: ```
 #rkhunter --propupd 
```

---

### Post by bodhi.zazen on 2010-08-18
> **pzkfw said:**
> If you're new to rkhunter, remember [s]that if you upgrade the package (typically through apt) then that will set off the changed hash or whatever it had stored and thinks it's malicious.  It's only because you upgraded and it sees it as a different version.  The idea is, if you DIDN'T upgrade, then those flags mean something.  Also, depending on your distro, some things will always show "Warning" no matter what.  Use this to reset it:[/s] Read the documentation.

Fixed that for you :lolflag:

Seriously, I do not intend to be harsh, but root kits are quite sophisticated and unless users first use these tools on a known good system and unless users are willing to put the time into researching the warnings, we are not doing them any favors.

Although there are false positives and warnings , unless you have intimate knowledge of the system and what, if any, changes have been made and what services have been added, you really can not advise people to ignore such warnings and it is poor forum to assume that they are false positives.

---

