---
title: "serious problem with apt"
date: 2010-11-12
forum: New to Ubuntu
---

### Post by The_Pirate_King on 2010-11-12
I tried installing recommended updates and it said there was an issue with a package.  So I tried fixing it through Synaptic and it returned some kind of error.  

Now a number of essential programs won't run and apt seems to be broken as well, because any time I try to run a command (like sudo apt-get -f install) it just says there's a segmentation fault.

---

### Post by bioterror on 2010-11-13
You can try:

sudo rm -rf /var/cache/apt/*

---

### Post by The_Pirate_King on 2010-11-13
Already did. 

I also tried installing apt from [this package]("http://packages.ubuntu.com/lucid/i386/apt/download") using dpkg.

Still getting the same problem.

---

### Post by bioterror on 2010-11-13
> **The_Pirate_King said:**
> Already did. 

I also tried installing apt from [this package]("http://packages.ubuntu.com/lucid/i386/apt/download") using dpkg.

Still getting the same problem.

try ```
sudo apt-get update -o APT::Cache-Limit=23000000;
```

---

### Post by The_Pirate_King on 2010-11-13
Seems like any command run using apt returns a segmentation fault.

---

### Post by hunter99507 on 2010-11-13
I have a similar issue and i dont know how to get it to work. None of the ubuntu programs will start, (software center, snaptics, ect.  I get this error and i dont know how to clear it out.

watts@Ubuntu:~$ sudo apt-get update
E: Type '‘deb' is not known on line 59 in source list /etc/apt/sources.list
E: Type '‘deb' is not known on line 1 in source list /etc/apt/sources.list.d/libreoffice.list
E: The list of sources could not be read.

How do i remvoe these. I believe this will fix my issue

---

### Post by bioterror on 2010-11-13
Remove stuff from your sources.list.
[http://ubuntuforums.org/showpost.php?p=2545209&postcount=9]("http://ubuntuforums.org/showpost.php?p=2545209&postcount=9")

---

### Post by bioterror on 2010-11-13
> **hunter99507 said:**
> I have a similar issue and i dont know how to get it to work. None of the ubuntu programs will start, (software center, snaptics, ect.  I get this error and i dont know how to clear it out.

watts@Ubuntu:~$ sudo apt-get update
E: Type '‘deb' is not known on line 59 in source list /etc/apt/sources.list
E: Type '‘deb' is not known on line 1 in source list /etc/apt/sources.list.d/libreoffice.list
E: The list of sources could not be read.

How do i remvoe these. I believe this will fix my issue

alt+f2 and:
```
gksudo gedit /etc/apt/sources.list
gksudo gedit /etc/apt/libreoffice.list
```

---

### Post by randumnumber on 2010-11-13
Have you tried this?
```

sudo dpkg --configure -a
sudo apt-get install -f

```
I got this at the link below it might be a good resource for your problem.

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by The_Pirate_King on 2010-11-13
Here's the output of sudo strace apt-get -f install: 

```
execve("/usr/bin/apt-get", ["apt-get", "-f", "install"], [/* 16 vars */]) = 0
brk(0)                                  = 0x9fb0000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7810000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=88711, ...}) = 0
mmap2(NULL, 88711, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb77fa000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libapt-pkg-libc6.10-6.so.4.8", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`\270\1\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=826072, ...}) = 0
mmap2(NULL, 829684, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x25a000
mmap2(0x322000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xc7) = 0x322000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libutil.so.1", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\0\n\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=9748, ...}) = 0
mmap2(NULL, 12424, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xe86000
mmap2(0xe88000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xe88000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libstdc++.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000r\4\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=975088, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb77f9000
mmap2(NULL, 1004428, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xc38000
mprotect(0xd21000, 4096, PROT_NONE)     = 0
mmap2(0xd22000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xe9) = 0xd22000
mmap2(0xd27000, 25484, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xd27000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libm.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`4\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=149392, ...}) = 0
mmap2(NULL, 151680, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x110000
mmap2(0x134000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x23) = 0x134000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libgcc_s.so.1", O_RDONLY)    = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0p#\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=120368, ...}) = 0
mmap2(NULL, 123432, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x136000
mmap2(0x153000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1c) = 0x153000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000m\1\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1405508, ...}) = 0
mmap2(NULL, 1415592, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x517000
mprotect(0x66a000, 4096, PROT_NONE)     = 0
mmap2(0x66b000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x153) = 0x66b000
mmap2(0x66e000, 10664, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x66e000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@\n\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=9736, ...}) = 0
mmap2(NULL, 12408, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x917000
mmap2(0x919000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0x919000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb77f8000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb77f7000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb77f76d0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0x919000, 4096, PROT_READ)     = 0
mprotect(0x66b000, 8192, PROT_READ)     = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++
Segmentation fault

```

---

### Post by hunter99507 on 2010-11-13
Thank you bioterror. That worked!!! Thank you

---

### Post by bioterror on 2010-11-13
> **The_Pirate_King said:**
> Here's the output of sudo strace apt-get -f install: 

```
execve("/usr/bin/apt-get", ["apt-get", "-f", "install"], [/* 16 vars */]) = 0
brk(0)                                  = 0x9fb0000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7810000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=88711, ...}) = 0
mmap2(NULL, 88711, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb77fa000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libapt-pkg-libc6.10-6.so.4.8", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`\270\1\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=826072, ...}) = 0
mmap2(NULL, 829684, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x25a000
mmap2(0x322000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xc7) = 0x322000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libutil.so.1", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\0\n\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=9748, ...}) = 0
mmap2(NULL, 12424, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xe86000
mmap2(0xe88000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xe88000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libstdc++.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000r\4\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=975088, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb77f9000
mmap2(NULL, 1004428, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xc38000
mprotect(0xd21000, 4096, PROT_NONE)     = 0
mmap2(0xd22000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xe9) = 0xd22000
mmap2(0xd27000, 25484, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xd27000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libm.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`4\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=149392, ...}) = 0
mmap2(NULL, 151680, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x110000
mmap2(0x134000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x23) = 0x134000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libgcc_s.so.1", O_RDONLY)    = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0p#\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=120368, ...}) = 0
mmap2(NULL, 123432, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x136000
mmap2(0x153000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1c) = 0x153000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000m\1\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1405508, ...}) = 0
mmap2(NULL, 1415592, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x517000
mprotect(0x66a000, 4096, PROT_NONE)     = 0
mmap2(0x66b000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x153) = 0x66b000
mmap2(0x66e000, 10664, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x66e000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@\n\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=9736, ...}) = 0
mmap2(NULL, 12408, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x917000
mmap2(0x919000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0x919000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb77f8000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb77f7000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb77f76d0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0x919000, 4096, PROT_READ)     = 0
mprotect(0x66b000, 8192, PROT_READ)     = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++
Segmentation fault

```

This is what I would do:
Figure out your version of ubuntu, head your browser towards [http://archive.ubuntu.com/ubuntu/pool/main/a/apt/]("http://archive.ubuntu.com/ubuntu/pool/main/a/apt/")
and wget matching version of apt. 

Then:
```

sudo dpkg -P apt
sudo dpkg -i apt

```

And remember to keep track of the dependencies.

You've really messed up your apt, and that is quite a accomplishment\\:D/

---

