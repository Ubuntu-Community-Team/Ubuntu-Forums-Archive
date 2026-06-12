---
title: "grub2 takes several minutes to show menu in Ubuntu 10.04 dual boot with XP"
date: 2010-11-05
forum: New to Ubuntu
---

### Post by sunewbie on 2010-11-05
Hi,

I upgraded from Karmic to Lucid as my grub took time (about 15 to 20 seconds) to show the selection / OS choice menu.  

I have XP and Ubuntu 10.04 dual boot. 

I cleaned up the grub (not by directly editing the read only grub.cfg file) and 
1. removed older kernels of linux. 
2. Added Splash screen.
3. Removed Mem test entries.
4. Edited 40_custom and added XP manually

After i select any OS and then restart it. Then there is no time delay in Grub show menu. In 2 seconds it shows up the OS choices menu.

I tried to search the forums, but found only one unsolved thread ( [http://ubuntuforums.org/showthread.php?t=1286608]("http://ubuntuforums.org/showthread.php?t=1286608") ) for Ubuntu Karmic posted in Oct 2009. 

Should an upgrade to 10.10 solve this problem.

Is the dual boot causing problem and Grub takes time to find another OS.

I am very new to ubuntu and not have much technical knowledge.

Found this on launchpad [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933") 

Thanks

---

### Post by mistypotato on 2010-11-05
First BIOS loads, then Grub, then OS

Since you say the delay is for GRUB to load, I would think there is a BIOS delay for some reason.

Anytime you run a mem test on boot, it will add time to the booting process.  The 4 things you did seemed to work so that would indicate that's what was causing your boot delay.

Check the total free space on your hard drive to make sure it's not nearing full.

I can't really see where anything needs "fixing".  See if your bios is running any kind of virus scan.

If you add a bios mem test, a splash screen or other BIOS related pre OS load options, it's going to take a bit longer before the OS loads.

---

### Post by sunewbie on 2010-11-05
Thanks for the reply. 

Bios is not running any kind of virus scan. As soon as i power on, in 2-3 seconds, I get an Intel bios screen saying (press F2 to edit bios). Then the cursor keeps blinking to load Grub. 

I did not run mem tests any time, just removed it using this command 

```
sudo chmod -x /etc/grub.d/20_memtest86+
```

and updated grub.

I have 50 GB of space for ext3 partition, only 5 GB is used. 

I have Virtualbox 3 PEUL with XP installed as Guest OS and have dedicated 40 GB. But i rarely use it. 

Is this causing the problem?

Why is GRUB loading faster when i restart any OS. Only when I shut down, power off and then start again, the GRUB takes time to load.

I again Tried and removed Splash screen, but of no use. 

Anyways, thanks for the help.

---

### Post by Hippytaff on 2010-11-05
Might be worth checking the boot logs after a slow boot to see if there are any clues there.
They can be found here
```

/var/logs

```
and I don't know if a quick look at
 
```

dmseg | less

```
might shed some light too?

---

### Post by sunewbie on 2010-11-06
Hi,

I boot.log file shows this

```
fsck from util-linux-ng 2.17.2
/dev/sdb9: clean, 251743/4440064 files, 3744991/17757841 blocks
 * Starting AppArmor profiles       [200G Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox

[194G[ OK ]
 * Setting sensors limits       [200G 
[194G[ OK ]
 [33m*[39;49m Speech-dispatcher configured for user sessions
WARNING: All config files need .conf: /etc/modprobe.d/aliasesbackup, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/aliases, it will be ignored in a future release.
```

Is this could be of any help?

the command  dmseg | less shows:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-25-generic (buildd@palmer) (gcc version 4.4.
3 (Ubuntu 4.4.3-4ubuntu5) ) #45-Ubuntu SMP Sat Oct 16 19:48:22 UTC 2010 (Ubuntu 
2.6.32-25.45-generic 2.6.32.21+drm33.7)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f23a000 (usable)
[    0.000000]  BIOS-e820: 000000007f23a000 - 000000007f27d000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f27d000 - 000000007f355000 (reserved)
[    0.000000]  BIOS-e820: 000000007f355000 - 000000007f365000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f365000 - 000000007f3e1000 (reserved)
:

```

Thanks

---

