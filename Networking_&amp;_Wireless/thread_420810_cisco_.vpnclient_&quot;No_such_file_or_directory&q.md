---
title: "cisco ./vpnclient &quot;No such file or directory&quot; on Feisty fawn"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by jasonw on 2007-04-23
I just installed feisty fawn x86_64. Then unpacked vpnclient-linux-x86_64-4.8.00.0490-k9.tar.gz

I've noticed the vpnclient executable is not working on this OS. Here's what I see:

# ls -l vpnclient/vpnclient
-rwxr-xr-x 1 503 uucp 666260 2005-11-22 01:43 vpnclient/vpnclient
# strace vpnclient/vpnclient
execve("vpnclient/vpnclient", ["vpnclient/vpnclient"], [/* 15 vars */]) = -1 ENOENT (No such file or directory)
dup(2)                                  = 3
fcntl(3, F_GETFL)                       = 0x8002 (flags O_RDWR|O_LARGEFILE)
fstat(3, {st_mode=S_IFCHR|0600, st_rdev=makedev(136, 4), ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2b49347fe000
lseek(3, 0, SEEK_CUR)                   = -1 ESPIPE (Illegal seek)
write(3, "strace: exec: No such file or di"..., 40strace: exec: No such file or directory
) = 40
close(3)                                = 0
munmap(0x2b49347fe000, 4096)            = 0
exit_group(1)                           = ?
Process 7145 detached

Has anyone else seen this problem?

---

### Post by senyahnoj on 2007-07-16
Yes I have the same problem. Kernel 2.6.20-16 on feisty fawn x86_64. I'm a ubuntu newbie, but I've had the vpnclient successfully running in the past on Gentoo and Fedora.

Had earlier problems installing which were solved with the patch from [http://tuxx-home.at/cmt.php?article=/2007/05/29/T16_34_26/index.html](http://tuxx-home.at/cmt.php?article=/2007/05/29/T16_34_26/index.html) but now I'm stuck :confused:

Did you ever get to the bottom of this?

Thanks!

---

### Post by senyahnoj on 2007-07-17
solved it - the vpnclient was trying to link to /lib/lib-linux.so.2 (which should be a symlink to /lib32/ld-linux.so.2)

installed lib32gcc1 (gcc 32-bit compatibility library) and this sorted it :KS

---

