---
title: "dead in the water"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by mapman88 on 2010-09-22
New to Ubuntu this year. 4 year old gateway with a new 320 gb drive, no dual boot, running only 9.10 since January, upgraded to 10.04 in April. Two weeks ago, failed to boot up. Tried numerous things booting off live CD to repair system, finally reloaded 10.04, still could not boot. Installed 9.10 two days ago - on boot up I get;
 
**unit: mountall main process (463) terminated with status 1**
**General error mounting filesystems**
**A maintenance shell will now be started**
**CONTROL-D will terminate this shell and retry**
*** Setting preliminary keymap...**
**[  378.137184]  ACPI: I/O resource nForce2_smbus [  0x1c40-0x1c7f] conflicts with region SMOO [  0x1c40-0x1c45]**
**[ 378.137236] nForce2-smbus 0000:00:001:Error probing SMB2**
***Starting Apps Process**
 
**udevd [481]: worker [537] unexpectadly returned with status 0X0100**
 
**udevd [481]: worker [537] failed while handling '/devices/pci0000:00/00**
 
**udevd [481]: worker [536] unexpectadly returned with status 0X0100**

**udevd [481]: worker [536] failed while handling '/devices/pci0000:00/00**
 
**udevd [481]: worker [534] unexpectadly returned with status 0X0100**
 
**udevd [481]: worker [534] failed while handling '/devices/pci0000:00/00**
 
**udevd [481]: worker [507] unexpectadly returned with status 0X0100**

**udevd [481]: worker [507] failed while handling '/devices/pci0000:00/00**
 
**udevd [481]: worker [498] unexpectadly returned with status 0X0100**

**udevd [481]: worker [498] failed while handling '/devices/pci0000:00/00**  
 
Then I get the shell to open, and 9.10 runs extremely slow. I was able to get my wireless working, and I got to the internet. Thats where I'm at - so I assume I am running in a "shell"??. DOes this look like a hardware failure of some sort, or does anyone have any ideas?
 
I have been very happy running Ubuntu, and hope I can figure this out. thanks in advance....

---

### Post by sandyd on 2010-09-22
> **mapman88 said:**
> New to Ubuntu this year. 4 year old gateway with a new 320 gb drive, no dual boot, running only 9.10 since January, upgraded to 10.04 in April. Two weeks ago, failed to boot up. Tried numerous things booting off live CD to repair system, finally reloaded 10.04, still could not boot. Installed 9.10 two days ago - on boot up I get;

  unit: mountall main process (463) terminated with status 1
**General error mounting filesystems**
A maintenance shell will now be started
CONTROL-D will terminate this shell and retry
* Setting preliminary keymap...
[  378.137184]  ACPI: I/O resource nForce2_smbus [  0x1c40-0x1c7f] conflicts with region SMOO [  0x1c40-0x1c45]
[ 378.137236] nForce2-smbus 0000:00:001:Error probing SMB2
*Starting Apps Process

  udevd [481]: worker [537] unexpectadly returned with status 0X0100

  udevd [481]: worker [537] failed while handling '/devices/pci0000:00/00

  udevd [481]: worker [536] unexpectadly returned with status 0X0100

 udevd [481]: worker [536] failed while handling '/devices/pci0000:00/00

  udevd [481]: worker [534] unexpectadly returned with status 0X0100

  udevd [481]: worker [534] failed while handling '/devices/pci0000:00/00

  udevd [481]: worker [507] unexpectadly returned with status 0X0100

 udevd [481]: worker [507] failed while handling '/devices/pci0000:00/00

  udevd [481]: worker [498] unexpectadly returned with status 0X0100

 udevd [481]: worker [498] failed while handling '/devices/pci0000:00/00  
 
Then I get the shell to open, and 9.10 runs extremely slow. I was able to get my wireless working, and I got to the internet. Thats where I'm at - so I assume I am running in a "shell"??. DOes this look like a hardware failure of some sort, or does anyone have any ideas?
 
I have been very happy running Ubuntu, and hope I can figure this out. thanks in advance....
Time to check your hard disks.

---

