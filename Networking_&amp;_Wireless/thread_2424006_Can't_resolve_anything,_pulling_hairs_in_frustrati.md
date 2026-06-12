---
title: "Can't resolve anything, pulling hairs in frustration"
date: 2019-08-01
forum: Networking &amp; Wireless
---

### Post by daddad62 on 2019-08-01
I installed Ombi for my Plex which downgraded my libcurl4 a few versions to allow for some dependencies. The day after I accidentally tried to put too much on 1 partition and was moving some things around from my Plex Library folders.
After having it down for a restart it couldn't resolve anything. This machine has been restarted many many times before this without issue.

Currently using systemd-resolved on Ubuntu server 18.04.
Using cloudflares 1.1.1.1 dns server.
The issue started with being up to 30 seconds for a resolve with systemd-resolved and non functioning nslookup and ping. Then it became a Connection timed out; No servers reached. Now I just have System error.



I got terabytes of data on this machine, so a fresh install is not an option.



What information do you need to assist me? I've been wasting days trying to figure this out.

---

### Post by chili555 on 2019-08-01
Please run and post:

```
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
ls -al /etc/resolv.conf
cat /etc/netplan/*.yaml
```

Thanks.

---

### Post by daddad62 on 2019-08-02
&#9584;&#9472;# ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=56 time=13.7 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=56 time=13.9 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=56 time=13.9 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 13.782/13.881/13.940/0.119 ms
&#9581;&#9472;root@mail ~ 
&#9584;&#9472;# ping -c3 [www.ubuntu.com](www.ubuntu.com)
ping: [www.ubuntu.com:](www.ubuntu.com:) System error
&#9581;&#9472;root@mail ~ 
&#9584;&#9472;# ls -al /etc/resolv.conf2 &#8629;
lrwxrwxrwx 1 root root 27 Aug  1 21:05 /etc/resolv.conf -> /run/resolvconf/resolv.conf
&#9581;&#9472;root@mail ~ 
&#9584;&#9472;# cat /etc/netplan/*.yaml
zsh: no matches found: /etc/netplan/*.yaml

---

### Post by daddad62 on 2019-08-02
I ran a strace ping [www.ubuntu.com]("http://www.ubuntu.com") as well.

```
&#9584;&#9472;# strace ping -c1 [www.ubuntu.com]("http://www.ubuntu.com")                                                                                                                                                      2 &#8629;
execve("/bin/ping", ["ping", "-c1", "www.ubuntu.com"], 0x7fff5f847170 /* 24 vars */) = 0
brk(NULL)                               = 0x55aa1809c000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=87818, ...}) = 0
mmap(NULL, 87818, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fd2b4c56000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libcap.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\20\30\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=22768, ...}) = 0
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd2b4c54000
mmap(NULL, 2117976, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd2b483f000
mprotect(0x7fd2b4843000, 2097152, PROT_NONE) = 0
mmap(0x7fd2b4a43000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x4000) = 0x7fd2b4a43000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libidn.so.11", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0+\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=206872, ...}) = 0
mmap(NULL, 2302000, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd2b460c000
mprotect(0x7fd2b463e000, 2093056, PROT_NONE) = 0
mmap(0x7fd2b483d000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x31000) = 0x7fd2b483d000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libnettle.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340\200\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=219304, ...}) = 0
mmap(NULL, 2314384, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd2b43d6000
mprotect(0x7fd2b440a000, 2093056, PROT_NONE) = 0
mmap(0x7fd2b4609000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x33000) = 0x7fd2b4609000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libresolv.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\00008\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=101168, ...}) = 0
mmap(NULL, 2206336, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd2b41bb000
mprotect(0x7fd2b41d2000, 2097152, PROT_NONE) = 0
mmap(0x7fd2b43d2000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x17000) = 0x7fd2b43d2000
mmap(0x7fd2b43d4000, 6784, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fd2b43d4000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\260\34\2\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=2030544, ...}) = 0
mmap(NULL, 4131552, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd2b3dca000
mprotect(0x7fd2b3fb1000, 2097152, PROT_NONE) = 0
mmap(0x7fd2b41b1000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1e7000) = 0x7fd2b41b1000
mmap(0x7fd2b41b7000, 15072, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fd2b41b7000
close(3)                                = 0
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd2b4c52000
arch_prctl(ARCH_SET_FS, 0x7fd2b4c52f00) = 0
mprotect(0x7fd2b41b1000, 16384, PROT_READ) = 0
mprotect(0x7fd2b43d2000, 4096, PROT_READ) = 0
mprotect(0x7fd2b4609000, 8192, PROT_READ) = 0
mprotect(0x7fd2b483d000, 4096, PROT_READ) = 0
mprotect(0x7fd2b4a43000, 4096, PROT_READ) = 0
mprotect(0x55aa16ecd000, 4096, PROT_READ) = 0
mprotect(0x7fd2b4c6c000, 4096, PROT_READ) = 0
munmap(0x7fd2b4c56000, 87818)           = 0
brk(NULL)                               = 0x55aa1809c000
brk(0x55aa180bd000)                     = 0x55aa180bd000
capget({version=_LINUX_CAPABILITY_VERSION_3, pid=0}, NULL) = 0
capget({version=_LINUX_CAPABILITY_VERSION_3, pid=0}, {effective=1<<CAP_CHOWN|1<<CAP_DAC_OVERRIDE|1<<CAP_DAC_READ_SEARCH|1<<CAP_FOWNER|1<<CAP_FSETID|1<<CAP_KILL|1<<CAP_SETGID|1<<CAP_SETUID|1<<CAP_SETPCAP|1<<CAP_LINUX_IMMUTABLE|1<<CAP_NET_BIND_SERVICE|1<<CAP_NET_BROADCAST|1<<CAP_NET_ADMIN|1<<CAP_NET_RAW|1<<CAP_IPC_LOCK|1<<CAP_IPC_OWNER|1<<CAP_SYS_MODULE|1<<CAP_SYS_RAWIO|1<<CAP_SYS_CHROOT|1<<CAP_SYS_PTRACE|1<<CAP_SYS_PACCT|1<<CAP_SYS_ADMIN|1<<CAP_SYS_BOOT|1<<CAP_SYS_NICE|1<<CAP_SYS_RESOURCE|1<<CAP_SYS_TIME|1<<CAP_SYS_TTY_CONFIG|1<<CAP_MKNOD|1<<CAP_LEASE|1<<CAP_AUDIT_WRITE|1<<CAP_AUDIT_CONTROL|1<<CAP_SETFCAP|1<<CAP_MAC_OVERRIDE|1<<CAP_MAC_ADMIN|1<<CAP_SYSLOG|1<<CAP_WAKE_ALARM|1<<CAP_BLOCK_SUSPEND|1<<CAP_AUDIT_READ, permitted=1<<CAP_CHOWN|1<<CAP_DAC_OVERRIDE|1<<CAP_DAC_READ_SEARCH|1<<CAP_FOWNER|1<<CAP_FSETID|1<<CAP_KILL|1<<CAP_SETGID|1<<CAP_SETUID|1<<CAP_SETPCAP|1<<CAP_LINUX_IMMUTABLE|1<<CAP_NET_BIND_SERVICE|1<<CAP_NET_BROADCAST|1<<CAP_NET_ADMIN|1<<CAP_NET_RAW|1<<CAP_IPC_LOCK|1<<CAP_IPC_OWNER|1<<CAP_SYS_MODULE|1<<CAP_SYS_RAWIO|1<<CAP_SYS_CHROOT|1<<CAP_SYS_PTRACE|1<<CAP_SYS_PACCT|1<<CAP_SYS_ADMIN|1<<CAP_SYS_BOOT|1<<CAP_SYS_NICE|1<<CAP_SYS_RESOURCE|1<<CAP_SYS_TIME|1<<CAP_SYS_TTY_CONFIG|1<<CAP_MKNOD|1<<CAP_LEASE|1<<CAP_AUDIT_WRITE|1<<CAP_AUDIT_CONTROL|1<<CAP_SETFCAP|1<<CAP_MAC_OVERRIDE|1<<CAP_MAC_ADMIN|1<<CAP_SYSLOG|1<<CAP_WAKE_ALARM|1<<CAP_BLOCK_SUSPEND|1<<CAP_AUDIT_READ, inheritable=0}) = 0
capget({version=_LINUX_CAPABILITY_VERSION_3, pid=0}, NULL) = 0
capset({version=_LINUX_CAPABILITY_VERSION_3, pid=0}, {effective=0, permitted=1<<CAP_NET_ADMIN|1<<CAP_NET_RAW, inheritable=0}) = 0
prctl(PR_SET_KEEPCAPS, 1)               = 0
getuid()                                = 0
setuid(0)                               = 0
prctl(PR_SET_KEEPCAPS, 0)               = 0
getuid()                                = 0
geteuid()                               = 0
openat(AT_FDCWD, "/usr/lib/locale/locale-archive", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=4592464, ...}) = 0
mmap(NULL, 4592464, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fd2b3968000
close(3)                                = 0
capget({version=_LINUX_CAPABILITY_VERSION_3, pid=0}, NULL) = 0
capget({version=_LINUX_CAPABILITY_VERSION_3, pid=0}, {effective=0, permitted=1<<CAP_NET_ADMIN|1<<CAP_NET_RAW, inheritable=0}) = 0
capset({version=_LINUX_CAPABILITY_VERSION_3, pid=0}, {effective=1<<CAP_NET_RAW, permitted=1<<CAP_NET_ADMIN|1<<CAP_NET_RAW, inheritable=0}) = 0
socket(AF_INET, SOCK_DGRAM, IPPROTO_ICMP) = -1 EACCES (Permission denied)
socket(AF_INET, SOCK_RAW, IPPROTO_ICMP) = 3
socket(AF_INET6, SOCK_DGRAM, IPPROTO_ICMPV6) = -1 EACCES (Permission denied)
socket(AF_INET6, SOCK_RAW, IPPROTO_ICMPV6) = 4
capget({version=_LINUX_CAPABILITY_VERSION_3, pid=0}, NULL) = 0
capget({version=_LINUX_CAPABILITY_VERSION_3, pid=0}, {effective=1<<CAP_NET_RAW, permitted=1<<CAP_NET_ADMIN|1<<CAP_NET_RAW, inheritable=0}) = 0
capset({version=_LINUX_CAPABILITY_VERSION_3, pid=0}, {effective=0, permitted=1<<CAP_NET_ADMIN|1<<CAP_NET_RAW, inheritable=0}) = 0
socket(AF_UNIX, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, 0) = 5
connect(5, {sa_family=AF_UNIX, sun_path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(5)                                = 0
socket(AF_UNIX, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, 0) = 5
connect(5, {sa_family=AF_UNIX, sun_path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(5)                                = 0
openat(AT_FDCWD, "/etc/nsswitch.conf", O_RDONLY|O_CLOEXEC) = 5
fstat(5, {st_mode=S_IFREG|0644, st_size=593, ...}) = 0
read(5, "# /etc/nsswitch.conf\n#\n# Example"..., 4096) = 593
read(5, "", 4096)                       = 0
close(5)                                = 0
stat("/etc/resolv.conf", {st_mode=S_IFREG|0644, st_size=363, ...}) = 0
openat(AT_FDCWD, "/etc/host.conf", O_RDONLY|O_CLOEXEC) = 5
fstat(5, {st_mode=S_IFREG|0644, st_size=92, ...}) = 0
read(5, "# The \"order\" line is only used "..., 4096) = 92
read(5, "", 4096)                       = 0
close(5)                                = 0
openat(AT_FDCWD, "/etc/resolv.conf", O_RDONLY|O_CLOEXEC) = 5
fstat(5, {st_mode=S_IFREG|0644, st_size=363, ...}) = 0
read(5, "# Dynamic resolv.conf(5) file fo"..., 4096) = 363
read(5, "", 4096)                       = 0
close(5)                                = 0
uname({sysname="Linux", nodename="mail", ...}) = 0
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 5
fstat(5, {st_mode=S_IFREG|0644, st_size=87818, ...}) = 0
mmap(NULL, 87818, PROT_READ, MAP_PRIVATE, 5, 0) = 0x7fd2b4c56000
close(5)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libnss_files.so.2", O_RDONLY|O_CLOEXEC) = 5
read(5, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P#\0\0\0\0\0\0"..., 832) = 832
fstat(5, {st_mode=S_IFREG|0644, st_size=47568, ...}) = 0
mmap(NULL, 2168632, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 5, 0) = 0x7fd2b3756000
mprotect(0x7fd2b3761000, 2093056, PROT_NONE) = 0
mmap(0x7fd2b3960000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 5, 0xa000) = 0x7fd2b3960000
mmap(0x7fd2b3962000, 22328, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fd2b3962000
close(5)                                = 0
mprotect(0x7fd2b3960000, 4096, PROT_READ) = 0
munmap(0x7fd2b4c56000, 87818)           = 0
openat(AT_FDCWD, "/etc/hosts", O_RDONLY|O_CLOEXEC) = 5
fstat(5, {st_mode=S_IFREG|0644, st_size=831, ...}) = 0
read(5, "### Hetzner Online GmbH installi"..., 4096) = 831
read(5, "", 4096)                       = 0
close(5)                                = 0
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 5
fstat(5, {st_mode=S_IFREG|0644, st_size=87818, ...}) = 0
mmap(NULL, 87818, PROT_READ, MAP_PRIVATE, 5, 0) = 0x7fd2b4c56000
close(5)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/tls/haswell/x86_64/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib/x86_64-linux-gnu/tls/haswell/x86_64", 0x7ffce34ad500) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/tls/haswell/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib/x86_64-linux-gnu/tls/haswell", 0x7ffce34ad500) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/tls/x86_64/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib/x86_64-linux-gnu/tls/x86_64", 0x7ffce34ad500) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/tls/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib/x86_64-linux-gnu/tls", 0x7ffce34ad500) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/haswell/x86_64/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib/x86_64-linux-gnu/haswell/x86_64", 0x7ffce34ad500) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/haswell/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib/x86_64-linux-gnu/haswell", 0x7ffce34ad500) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/x86_64/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib/x86_64-linux-gnu/x86_64", 0x7ffce34ad500) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib/x86_64-linux-gnu", {st_mode=S_IFDIR|0755, st_size=16384, ...}) = 0
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/tls/haswell/x86_64/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/x86_64-linux-gnu/tls/haswell/x86_64", 0x7ffce34ad500) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/tls/haswell/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/x86_64-linux-gnu/tls/haswell", 0x7ffce34ad500) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/tls/x86_64/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/x86_64-linux-gnu/tls/x86_64", 0x7ffce34ad500) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/tls/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/x86_64-linux-gnu/tls", 0x7ffce34ad500) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/haswell/x86_64/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/x86_64-linux-gnu/haswell/x86_64", 0x7ffce34ad500) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/haswell/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/x86_64-linux-gnu/haswell", 0x7ffce34ad500) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/x86_64/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/x86_64-linux-gnu/x86_64", 0x7ffce34ad500) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/x86_64-linux-gnu", {st_mode=S_IFDIR|0755, st_size=73728, ...}) = 0
openat(AT_FDCWD, "/lib/tls/haswell/x86_64/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib/tls/haswell/x86_64", 0x7ffce34ad500) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/tls/haswell/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib/tls/haswell", 0x7ffce34ad500) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/tls/x86_64/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib/tls/x86_64", 0x7ffce34ad500) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/tls/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib/tls", 0x7ffce34ad500)        = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/haswell/x86_64/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib/haswell/x86_64", 0x7ffce34ad500) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/haswell/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib/haswell", 0x7ffce34ad500)    = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib/x86_64", 0x7ffce34ad500)     = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
openat(AT_FDCWD, "/usr/lib/tls/haswell/x86_64/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/tls/haswell/x86_64", 0x7ffce34ad500) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/tls/haswell/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/tls/haswell", 0x7ffce34ad500) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/tls/x86_64/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/tls/x86_64", 0x7ffce34ad500) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/tls/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/tls", 0x7ffce34ad500)    = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/haswell/x86_64/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/haswell/x86_64", 0x7ffce34ad500) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/haswell/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/haswell", 0x7ffce34ad500) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/x86_64", 0x7ffce34ad500) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/libnss_mymachines.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
munmap(0x7fd2b4c56000, 87818)           = 0
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 5
fstat(5, {st_mode=S_IFREG|0644, st_size=87818, ...}) = 0
mmap(NULL, 87818, PROT_READ, MAP_PRIVATE, 5, 0) = 0x7fd2b4c56000
close(5)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libnss_mdns4_minimal.so.2", O_RDONLY|O_CLOEXEC) = 5
read(5, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P\v\0\0\0\0\0\0"..., 832) = 832
fstat(5, {st_mode=S_IFREG|0644, st_size=10160, ...}) = 0
mmap(NULL, 2105360, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 5, 0) = 0x7fd2b3553000
mprotect(0x7fd2b3555000, 2093056, PROT_NONE) = 0
mmap(0x7fd2b3754000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 5, 0x1000) = 0x7fd2b3754000
close(5)                                = 0
mprotect(0x7fd2b3754000, 4096, PROT_READ) = 0
munmap(0x7fd2b4c56000, 87818)           = 0
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 5
fstat(5, {st_mode=S_IFREG|0644, st_size=87818, ...}) = 0
mmap(NULL, 87818, PROT_READ, MAP_PRIVATE, 5, 0) = 0x7fd2b4c56000
close(5)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libnss_resolve.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libnss_resolve.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/libnss_resolve.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/libnss_resolve.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
munmap(0x7fd2b4c56000, 87818)           = 0
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 5
fstat(5, {st_mode=S_IFREG|0644, st_size=87818, ...}) = 0
mmap(NULL, 87818, PROT_READ, MAP_PRIVATE, 5, 0) = 0x7fd2b4c56000
close(5)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libnss_dns.so.2", O_RDONLY|O_CLOEXEC) = 5
read(5, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\200\17\0\0\0\0\0\0"..., 832) = 832
fstat(5, {st_mode=S_IFREG|0644, st_size=26936, ...}) = 0
mmap(NULL, 2121952, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 5, 0) = 0x7fd2b334c000
mprotect(0x7fd2b3351000, 2097152, PROT_NONE) = 0
mmap(0x7fd2b3551000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 5, 0x5000) = 0x7fd2b3551000
close(5)                                = 0
mprotect(0x7fd2b3551000, 4096, PROT_READ) = 0
munmap(0x7fd2b4c56000, 87818)           = 0
socket(AF_INET, SOCK_DGRAM|SOCK_CLOEXEC|SOCK_NONBLOCK, IPPROTO_IP) = 5
connect(5, {sa_family=AF_INET, sin_port=htons(53), sin_addr=inet_addr("1.1.1.1")}, 16) = 0
poll([{fd=5, events=POLLOUT}], 1, 0)    = 1 ([{fd=5, revents=POLLOUT}])
sendmmsg(5, [{msg_hdr={msg_name=NULL, msg_namelen=0, msg_iov=[{iov_base="\340\322\1\0\0\1\0\0\0\0\0\0\3www\6ubuntu\3com\0\0\1\0\1", iov_len=32}], msg_iovlen=1, msg_controllen=0, msg_flags=MSG_OOB|MSG_PEEK|MSG_DONTWAIT|MSG_EOR|MSG_WAITALL|MSG_FIN|MSG_SYN|MSG_WAITFORONE|MSG_FASTOPEN|MSG_CMSG_CLOEXEC|0x834a0010}, msg_len=32}, {msg_hdr={msg_name=NULL, msg_namelen=0, msg_iov=[{iov_base="\264\353\1\0\0\1\0\0\0\0\0\0\3www\6ubuntu\3com\0\0\34\0\1", iov_len=32}], msg_iovlen=1, msg_controllen=0, msg_flags=0}, msg_len=32}], 2, MSG_NOSIGNAL) = 2
poll([{fd=5, events=POLLIN}], 1, 5000)  = 0 (Timeout)
socket(AF_INET, SOCK_DGRAM|SOCK_CLOEXEC|SOCK_NONBLOCK, IPPROTO_IP) = 6
connect(6, {sa_family=AF_INET, sin_port=htons(53), sin_addr=inet_addr("127.0.0.53")}, 16) = 0
poll([{fd=6, events=POLLOUT}], 1, 0)    = 1 ([{fd=6, revents=POLLOUT}])
sendmmsg(6, [{msg_hdr={msg_name=NULL, msg_namelen=0, msg_iov=[{iov_base="\340\322\1\0\0\1\0\0\0\0\0\0\3www\6ubuntu\3com\0\0\1\0\1", iov_len=32}], msg_iovlen=1, msg_controllen=0, msg_flags=MSG_OOB|MSG_PEEK|MSG_DONTWAIT|MSG_EOR|MSG_WAITALL|MSG_FIN|MSG_SYN|MSG_WAITFORONE|MSG_FASTOPEN|MSG_CMSG_CLOEXEC|0x834a0010}, msg_len=32}, {msg_hdr={msg_name=NULL, msg_namelen=0, msg_iov=[{iov_base="\264\353\1\0\0\1\0\0\0\0\0\0\3www\6ubuntu\3com\0\0\34\0\1", iov_len=32}], msg_iovlen=1, msg_controllen=0, msg_flags=0}, msg_len=32}], 2, MSG_NOSIGNAL) = 2
poll([{fd=6, events=POLLIN}], 1, 5000)  = 0 (Timeout)
poll([{fd=5, events=POLLOUT}], 1, 0)    = 1 ([{fd=5, revents=POLLOUT}])
sendmmsg(5, [{msg_hdr={msg_name=NULL, msg_namelen=0, msg_iov=[{iov_base="\340\322\1\0\0\1\0\0\0\0\0\0\3www\6ubuntu\3com\0\0\1\0\1", iov_len=32}], msg_iovlen=1, msg_controllen=0, msg_flags=MSG_OOB|MSG_PEEK|MSG_DONTWAIT|MSG_EOR|MSG_WAITALL|MSG_FIN|MSG_SYN|MSG_WAITFORONE|MSG_FASTOPEN|MSG_CMSG_CLOEXEC|0x834a0010}, msg_len=32}, {msg_hdr={msg_name=NULL, msg_namelen=0, msg_iov=[{iov_base="\264\353\1\0\0\1\0\0\0\0\0\0\3www\6ubuntu\3com\0\0\34\0\1", iov_len=32}], msg_iovlen=1, msg_controllen=0, msg_flags=0}, msg_len=32}], 2, MSG_NOSIGNAL) = 2
poll([{fd=5, events=POLLIN}], 1, 5000)  = 0 (Timeout)
poll([{fd=6, events=POLLOUT}], 1, 0)    = 1 ([{fd=6, revents=POLLOUT}])
sendmmsg(6, [{msg_hdr={msg_name=NULL, msg_namelen=0, msg_iov=[{iov_base="\340\322\1\0\0\1\0\0\0\0\0\0\3www\6ubuntu\3com\0\0\1\0\1", iov_len=32}], msg_iovlen=1, msg_controllen=0, msg_flags=MSG_OOB|MSG_PEEK|MSG_DONTWAIT|MSG_EOR|MSG_WAITALL|MSG_FIN|MSG_SYN|MSG_WAITFORONE|MSG_FASTOPEN|MSG_CMSG_CLOEXEC|0x834a0010}, msg_len=32}, {msg_hdr={msg_name=NULL, msg_namelen=0, msg_iov=[{iov_base="\264\353\1\0\0\1\0\0\0\0\0\0\3www\6ubuntu\3com\0\0\34\0\1", iov_len=32}], msg_iovlen=1, msg_controllen=0, msg_flags=0}, msg_len=32}], 2, MSG_NOSIGNAL) = 2
poll([{fd=6, events=POLLIN}], 1, 5000)  = 0 (Timeout)
close(5)                                = 0
close(6)                                = 0
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 5
fstat(5, {st_mode=S_IFREG|0644, st_size=87818, ...}) = 0
mmap(NULL, 87818, PROT_READ, MAP_PRIVATE, 5, 0) = 0x7fd2b4c56000
close(5)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libnss_myhostname.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libnss_myhostname.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/libnss_myhostname.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/libnss_myhostname.so.2", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
munmap(0x7fd2b4c56000, 87818)           = 0
openat(AT_FDCWD, "/usr/share/locale/locale.alias", O_RDONLY|O_CLOEXEC) = 5
fstat(5, {st_mode=S_IFREG|0644, st_size=2995, ...}) = 0
read(5, "# Locale name alias data base.\n#"..., 4096) = 2995
read(5, "", 4096)                       = 0
close(5)                                = 0
openat(AT_FDCWD, "/usr/share/locale/en_US.UTF-8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale/en_US.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale/en_US/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale/en.UTF-8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale/en.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale-langpack/en_US.UTF-8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale-langpack/en_US.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale-langpack/en_US/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale-langpack/en.UTF-8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale-langpack/en.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale-langpack/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
write(2, "ping: [www.ubuntu.com:]("http://www.ubuntu.com:") System err"..., 35ping: [www.ubuntu.com:]("http://www.ubuntu.com:") System error
) = 35
exit_group(2)                           = ?
+++ exited with 2 +++
```

---

### Post by chili555 on 2019-08-02
If you are running systemd, which is the default in Ubuntu 18.04, then your resolv.conf is incorrect. Let's correct it:

```
sudo rm -f /etc/resolv.conf
ln -s /run/systemd/resolve/stub-resolv.conf  /etc/resolv.conf
```I am mystified by the system error when trying to ping. Let's have a look at:```
cat /etc/hosts
cat /etc/hostname
```Finally, I'm not sure the strace result is significant. Although I can resolve, ping, surf the web, etc., perfectly, I get a very similar result.```
<snip>
openat(AT_FDCWD, "/usr/share/locale-langpack/en_US.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale-langpack/en_US/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale-langpack/en.UTF-8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale-langpack/en.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale-langpack/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
write(2, "ping: socket: Operation not perm"..., 38ping: socket: Operation not permitted
) = 38
exit_group(2)                           = ?
+++ exited with 2 +++


```I can ping [www.ubuntu.com](www.ubuntu.com) correctly, however:```

$ ping -c1 www.ubuntu.com
PING www.ubuntu.com (91.189.89.110) 56(84) bytes of data.
64 bytes from www-ubuntu-com.nuno.canonical.com (91.189.89.110): icmp_seq=1 ttl=46 time=93.4 ms

--- www.ubuntu.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 93.419/93.419/93.419/0.000 ms


```Is there any improvement after you make the resolv.conf change?

---

### Post by daddad62 on 2019-08-02
Pardon the amount of entires in the hosts file, I had to do something to make me able to install and update certain things.

```
&#9584;&#9472;# cat /etc/hosts   
### Hetzner Online GmbH installimage
# nameserver config
# IPv4
127.0.0.1 localhost localhost.localdomain
127.0.0.1 mail
95.100.155.104 ocsp.int-x3.letsencrypt.org
91.189.88.149 archive.ubuntu.com
13.74.252.37 packages.microsoft.com
91.189.95.83 ppa.launchpad.net
62.210.92.35 nginx.org
91.189.88.31 security.ubuntu.com
91.189.92.150 archive.canonical.com
192.95.20.194 packages.inverse.ca
143.204.247.63 download.docker.com
143.204.243.39 repo.mongodb.org
129.143.116.113 mirror2.hs-esslingen.de
143.204.247.18 deb.nodesource.com
143.204.247.32 download.onlyoffice.com
34.202.101.58 docker.io
176.9.117.41 repo.ombi.turd.me
#
# IPv6
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
2a01:4f9:2b:1ace::2  mail.poro.dk mail
&#9581;&#9472;root@mail ~ 
&#9584;&#9472;# cat /etc/hostname
mail
&#9581;&#9472;root@mail ~ 
&#9584;&#9472;# ping google.com
^C
&#9581;&#9472;root@mail ~ 
&#9584;&#9472;# ping www.ubuntu.com                                                                                                                                                               130 &#8629;
ping: www.ubuntu.com: System error

```

Sadly not resolved yet.

I attempted a tcpdump while I tried to dig @8.8.8.8 [www.google.com]("http://www.google.com")

```
&#9584;&#9472;# sudo tcpdump -n -i eth0 |grep 8.8.8.8.53                                                                                                                                            1 &#8629;
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes
17:22:54.524859 IP 95.216.117.49.41621 > 8.8.8.8.53: 42166+ [1au] A? www.google.com. (55)
17:22:59.524929 IP 95.216.117.49.41621 > 8.8.8.8.53: 42166+ [1au] A? www.google.com. (55)
17:23:04.525244 IP 95.216.117.49.41621 > 8.8.8.8.53: 42166+ [1au] A? www.google.com. (55)
17:25:21.710467 IP 95.216.117.49.46197 > 8.8.8.8.53: 22183+ [1au] A? www.google.com. (55)
17:25:26.710598 IP 95.216.117.49.46197 > 8.8.8.8.53: 22183+ [1au] A? www.google.com. (55)
17:25:31.710776 IP 95.216.117.49.46197 > 8.8.8.8.53: 22183+ [1au] A? www.google.com. (55)

```

I've removed and re-added port 53 several times on both UDP and UDP/TCP on the management site of Hetzner, the place I have this server.

---

### Post by chili555 on 2019-08-02
> # cat /etc/hosts   
### Hetzner Online GmbH installimage
# nameserver config
# IPv4
127.0.0.1 localhost localhost.localdomain
[COLOR="#FF0000"]127.0.0.1 [/COLOR]mail
95.100.155.104 ocsp.int-x3.letsencrypt.org
91.189.88.149 archive.ubuntu.comI believe this should be:```
127.0.1.1 mail
```Please change it.

I'm still note quite sure what this means or what to suggest to remedy it.> ping: [www.ubuntu.com:](www.ubuntu.com:) System errorMay we see:
```
cat /etc/nsswitch.conf
```

---

### Post by daddad62 on 2019-08-02
It has been changed. Issue acts slightly different. I couldn't do dig google.com, it resulted in the same error as dig @8.8.8.8 google.com. Now it actually gives the local server as point, the @8.8.8.8 still gives connection timed out, no servers reached.

nslookup actually looks it's churning some gears now.
It doesn't finish. but it does end up on the following:

```

&#9584;&#9472;# nslookup google.com
;; Got SERVFAIL reply from 127.0.0.53, trying next server

```



Here's the nsswitch.conf
```

&#9584;&#9472;# cat /etc/nsswitch.conf
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat systemd
group:          compat systemd
shadow:         compat
gshadow:        files

hosts:          files mymachines mdns4_minimal [NOTFOUND=return] resolve [!UNAVAIL=return] dns mdns4 myhostname
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

---

### Post by daddad62 on 2019-08-02
After the changes you suggested I still can't resolve, here's some more outputs for you.

```

&#9584;&#9472;# systemd-resolve --status
Global
          DNSSEC NTA: 10.in-addr.arpa
                      16.172.in-addr.arpa
                      168.192.in-addr.arpa
                      17.172.in-addr.arpa
                      18.172.in-addr.arpa
                      19.172.in-addr.arpa
                      20.172.in-addr.arpa
                      21.172.in-addr.arpa
                      22.172.in-addr.arpa
                      23.172.in-addr.arpa
                      24.172.in-addr.arpa
                      25.172.in-addr.arpa
                      26.172.in-addr.arpa
                      27.172.in-addr.arpa
                      28.172.in-addr.arpa
                      29.172.in-addr.arpa
                      30.172.in-addr.arpa
                      31.172.in-addr.arpa
                      corp
                      d.f.ip6.arpa
                      home
                      internal
                      intranet
                      lan
                      local
                      private
                      test

Link 7 (vethe857148)
      Current Scopes: none
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: no
    DNSSEC supported: no

Link 5 (vethd1613b4)
      Current Scopes: none
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: no
    DNSSEC supported: no

Link 3 (docker0)
      Current Scopes: none
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: no
    DNSSEC supported: no

Link 2 (eth0)
      Current Scopes: none
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: no
    DNSSEC supported: no

```
```

&#9584;&#9472;# systemd-resolve google.com
google.com: resolve call failed: No appropriate name servers or networks for name found

```

---

### Post by chili555 on 2019-08-02
We see no DNS nameservers here. Where, exactly, is/are they declared?

systemd-resolve --status should report something like this:

```
Link 3 (wlp3s0)
      Current Scopes: DNS
DefaultRoute setting: yes
       LLMNR setting: yes
MulticastDNS setting: no
  DNSOverTLS setting: no
      DNSSEC setting: no
    DNSSEC supported: no
  Current DNS Server: 8.8.8.8
         [COLOR="#FF0000"]DNS Servers: 8.8.8.8
                      8.8.4.4[/COLOR]
          DNS Domain: ~.
```


I notice this:  > cat /etc/netplan/*.yaml
zsh: no matches found: /etc/netplan/*.yamlDid you remove netplan, which is the default for networking in Ubuntu Server 18.04 et seq? With what did you replace it?

I am starting to be very concerned that you've undertaken quite a few changes that we now have to discover and undo.

---

### Post by jbruyet on 2019-11-26
I was in here looking for an answer to my DNS problem and this fixed it for me

```
sudo rm -f /etc/resolv.conf
ln -s /run/systemd/resolve/stub-resolv.conf  /etc/resolv.conf
```

Thanks Chili555! 

Thanks, 

Joe B

---

