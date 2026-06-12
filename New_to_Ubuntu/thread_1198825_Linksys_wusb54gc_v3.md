---
title: "Linksys wusb54gc v3"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by wizme on 2009-06-27
Hi 

i installed the driver using ndiswrapper but my com still cant start the driver.

the logs i get was:

ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
ndiswrapper (import:242): unknown symbol: ntoskrnl.exe: 'MmGetSystemRoutineAddress'
ndiswrapper (load_sys_files:206): couldn't prepare driver 'rt2870'
ndiswrapper (load_wrap_driver:10:cool:: couldn't load driver rt2870; check system log for messages from 'loadndisdriver'
usbcore: registered new interface driver ndiswrapper

please help to solve this.

the hardware is detected in lsusb but not in lsmod.

---

### Post by hrsrd on 2009-06-28
hello !!

please take a look at the following thread

[http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926)

It might help, also look at the community paper or wiki at :

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

good luck . .  .

hrsrd

---

### Post by cariboo on 2009-06-28
Is the device being setected properly? What is the output of:

```
ndiswrapper -l
```

that's a lower case L.

It looks like ndiwrapper is loading, what is the output of:

```
lsmod | grep ndiswrapper
```

---

