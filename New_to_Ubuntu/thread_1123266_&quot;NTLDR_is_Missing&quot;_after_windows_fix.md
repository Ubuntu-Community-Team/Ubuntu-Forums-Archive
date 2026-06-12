---
title: "&quot;NTLDR is Missing&quot; after windows fix"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by Omegaxis on 2009-04-12
First, the setup.
I have a 250gb hdd with windows installed on it, connected by IDE.
I also have a 500gb hdd with Ubuntu on it, connected by SATA.

Originally I had Windows, unfortunately the MBR was corrupted and I didn't know how to fix it.
Luckily, I had just purchased a 500gb hdd, and I installed Ubuntu on it. I just recently found my windows install disk, and used the 

```
fixboot 
cfgboot /rebuild
```

This enabled me to run widows, however I now cannot boot Ubuntu, I get the

```
NTLDR is missing......

```
message and then It then boots the widows hdd (the next in the boot order).

I have a feeling I messed up the Ubuntu boot record.
If I did is there any way to fix this?



UPDATE:
I can get as far as the Ubuntu loading screen, but it just hangs there. After about a minute it gives me....
```
Loading.....
Gave up waiting for root..
```

---

### Post by Peasantoid on 2009-04-12
Reinstall GRUB?
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

