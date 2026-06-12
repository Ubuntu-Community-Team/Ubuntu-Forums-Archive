---
title: "Cannot format USB flash drive"
date: 2011-06-20
forum: New to Ubuntu
---

### Post by yc2 on 2011-06-20
Hello,

This is a Windows problem, but I hope I can ask here. There are many knowledgeable people here and maybe Ubuntu has a solution.

Copying in Win7 from my USB-stick it got write protected!

In Win 7 I have tried the following to remove wp:
1. changing properties

2. Change keys in regedit regedit (HKEY_LOCAL_MACHINE\SYSTEM\CurrrentControlSet\Control\ and select New -> Key.
Enter the name StorageDevicePolicies ... )

3. Format in DOS-prompt, Win7 or Linux

4. Low level format with two different pgms (LLF and one from apacer, apacer pgm did not find stick though)

5. diskpart (attributes disk clear readonly

6. Linux: null device with dd. Chmod, rm -R *

7. Total Commander, Gparted.

8. testdisk

[COLOR="Red"][B]It is not possible to remove the write protect. I cannot use the stick.
[/B][/COLOR]
In Linux it looks like I can read and write the stick but not format it. But it only looks like files get written to the stick. At next mount the files are not there. (I naturally use "safe removal".)

Unmounting and trying to format with disk utility in Ubuntu I get this:
Error creating file system: helper exited with exit code 1: Error calling fsync(2) on /dev/sdc1: Input/output error


In Linux the behavior is strange to me: rm -R * will work on the stick (led flashes) and the files seem to be removed, but they reappear at next mount. testdisk option erase MBR will make led flash but nothing happens.

i must use my  stick under Ubuntu and Win too. It seems I have to throw it away and buy a new ??? Usually I find computer problems interesting, but if they force me to buy new hardware they get irritating. I blame Win 7 that for unknown reasons set wp on my stick during normal copy from the stick.

Thanks

ycc

EDIT:
I have worked several hours on this before writing here. I more and more think the flash drive has had a hardware crash. Tried putting it into an XP system. The diod flashed, but neither XP nor LowLevelFormatting programs could identify it. Will consider buying a new one unless some solution appears.

---

### Post by yc2 on 2011-06-21
I gave up on it and deleted personal data according to
rm -R --Frodo * ;)
I whacked it between two stones while reading spells over Transcend. Then I bought a new one.
Thread solved.

---

