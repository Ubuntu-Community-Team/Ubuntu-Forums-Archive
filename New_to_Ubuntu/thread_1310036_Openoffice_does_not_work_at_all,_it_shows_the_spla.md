---
title: "Openoffice does not work at all, it shows the splash and nothing further"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by legolas_w on 2009-11-01
Hello everyone.

I can not use openoffice in my ubuntu 9.10. I tried running oowriter in the console to see what kind of problems it faces which prevent it from opening but it just showd the splash screen and crashed without any error in the console.

If I double click on a word document I see the splash screen opening and getting invisible without showing any error message or the open office writer.
Is there any way that I can use to see what is wrong with the open office?

I tried removeing and installing it again with no luck.


Thanks

---

### Post by Hagar Delest on 2009-11-01
First try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

If no change, try the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by legolas_w on 2009-11-03
> **Hagar de l'Est said:**
> First try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

If no change, try the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

I tried reseting the user profile and it had no effect.
I purged and reinstalled the opneoffice from repository and it had no effect either.

Is there anyway to see what is happening to openoffice which cause this problem? some log files, etc...

---

### Post by Hagar Delest on 2009-11-03
> **legolas_w said:**
> I purged and reinstalled the opneoffice from repository and it had no effect either.
Have you tried the Sun version???

---

### Post by Unchqua on 2009-11-03
> **legolas_w said:**
> Is there anyway to see what is happening to openoffice which cause this problem? some log files, etc...
Are you willing to try strace? Output will be huge but it will tell everything in details.

---

### Post by legolas_w on 2009-11-03
> **Unchqua said:**
> Are you willing to try strace? Output will be huge but it will tell everything in details.

Sure, let me know how to do that and I will try to understand what is wrong. if I was unable to do so, I will post the result here.

Thanks

---

### Post by Unchqua on 2009-11-04
Just run
```
strace oowriter >output
```and after oowriter crashes (if any) look through output text file for any suspicious messages. You're looking for any complains about program not finding anything vital for it to run.

---

### Post by linux6994 on 2009-11-04
Have you tried to reinstall it sudo apt-get install openoffice.org-writer?

Do you have java installed?

---

### Post by legolas_w on 2009-11-05
I purged the installation and installed it again several time. I have java installed and when I type java it works.

I am going to try the targz installation method and finally I will go to sun to buy staroffice.

Thanks.

---

### Post by legolas_w on 2009-11-07
Hi
I installed OpenOffice from the tar.gz archive and it acts the same way that repository OpenOffice acts. I used strace and I get the following output. I can not find anything which indicates that something is wrong. Can you please help me with interpreting the strace log?

```

strace openoffice.org3 -writer %U
execve("/usr/bin/openoffice.org3", ["openoffice.org3", "-writer", "%U"], [/* 48 vars */]) = 0
brk(0)                                  = 0x9568000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x4001e000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=91208, ...}) = 0
mmap2(NULL, 91208, PROT_READ, MAP_PRIVATE, 3, 0) = 0x40020000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260l\1\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1319364, ...}) = 0
mmap2(NULL, 1325416, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x40037000
mmap2(0x40175000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13e) = 0x40175000
mmap2(0x40178000, 10600, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x40178000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x4017b000
set_thread_area({entry_number:-1 -> 6, base_addr:0x4017b8d0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0x40175000, 8192, PROT_READ)   = 0
mprotect(0x805e000, 4096, PROT_READ)    = 0
mprotect(0x4001b000, 4096, PROT_READ)   = 0
munmap(0x40020000, 91208)               = 0
getpid()                                = 5478
rt_sigaction(SIGCHLD, {SIG_DFL, [CHLD], SA_RESTART}, {SIG_DFL, [], 0}, 8) = 0
geteuid32()                             = 1000
brk(0)                                  = 0x9568000
brk(0x9589000)                          = 0x9589000
getppid()                               = 5477
stat64("/opt/openoffice.org/basis3.1/program", {st_mode=S_IFDIR|0755, st_size=16384, ...}) = 0
stat64(".", {st_mode=S_IFDIR|0755, st_size=16384, ...}) = 0
open("/usr/bin/openoffice.org3", O_RDONLY) = 3
fcntl64(3, F_DUPFD, 10)                 = 10
close(3)                                = 0
fcntl64(10, F_SETFD, FD_CLOEXEC)        = 0
rt_sigaction(SIGINT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGINT, {0x804f5fb, ~[RTMIN RT_1], 0}, NULL, 8) = 0
rt_sigaction(SIGQUIT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGQUIT, {SIG_DFL, ~[RTMIN RT_1], 0}, NULL, 8) = 0
rt_sigaction(SIGTERM, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGTERM, {SIG_DFL, ~[RTMIN RT_1], 0}, NULL, 8) = 0
read(10, "#!/bin/sh\nexec /opt/openoffice.o"..., 8192) = 57
execve("/opt/openoffice.org3/program/soffice", ["/opt/openoffice.org3/program/sof"..., "-writer", "%U"], [/* 48 vars */]) = 0
brk(0)                                  = 0x9063000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x4001e000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=91208, ...}) = 0
mmap2(NULL, 91208, PROT_READ, MAP_PRIVATE, 3, 0) = 0x40020000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260l\1\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1319364, ...}) = 0
mmap2(NULL, 1325416, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x40037000
mmap2(0x40175000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13e) = 0x40175000
mmap2(0x40178000, 10600, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x40178000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x4017b000
set_thread_area({entry_number:-1 -> 6, base_addr:0x4017b8d0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0x40175000, 8192, PROT_READ)   = 0
mprotect(0x805e000, 4096, PROT_READ)    = 0
mprotect(0x4001b000, 4096, PROT_READ)   = 0
munmap(0x40020000, 91208)               = 0
getpid()                                = 5478
rt_sigaction(SIGCHLD, {SIG_DFL, [CHLD], SA_RESTART}, {SIG_DFL, [], 0}, 8) = 0
geteuid32()                             = 1000
brk(0)                                  = 0x9063000
brk(0x9084000)                          = 0x9084000
getppid()                               = 5477
stat64("/opt/openoffice.org/basis3.1/program", {st_mode=S_IFDIR|0755, st_size=16384, ...}) = 0
stat64(".", {st_mode=S_IFDIR|0755, st_size=16384, ...}) = 0
open("/opt/openoffice.org3/program/soffice", O_RDONLY) = 3
fcntl64(3, F_DUPFD, 10)                 = 10
close(3)                                = 0
fcntl64(10, F_SETFD, FD_CLOEXEC)        = 0
rt_sigaction(SIGINT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGINT, {0x804f5fb, ~[RTMIN RT_1], 0}, NULL, 8) = 0
rt_sigaction(SIGQUIT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGQUIT, {SIG_DFL, ~[RTMIN RT_1], 0}, NULL, 8) = 0
rt_sigaction(SIGTERM, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGTERM, {SIG_DFL, ~[RTMIN RT_1], 0}, NULL, 8) = 0
read(10, "#!/bin/sh\n#*********************"..., 8192) = 3960
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x4017b938) = 5479
close(4)                                = 0
read(3, "Linux\n", 128)                 = 6
--- SIGCHLD (Child exited) @ 0 (0) ---
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 5479
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x4017b938) = 5480
--- SIGCHLD (Child exited) @ 0 (0) ---
close(4)                                = 0
read(3, "i686\n", 128)                  = 5
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 5480
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x4017b938) = 5481
--- SIGCHLD (Child exited) @ 0 (0) ---
close(4)                                = 0
read(3, "/opt/openoffice.org/basis3.1/pro"..., 128) = 37
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 5481
lstat64("/opt/openoffice.org3/program/soffice", {st_mode=S_IFREG|0555, st_size=3960, ...}) = 0
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x4017b938) = 5482
close(4)                                = 0
read(3, "/opt/openoffice.org3/program\n", 128) = 29
read(3, "", 128)                        = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 5482
chdir("/opt/openoffice.org3/program")   = 0
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x4017b938) = 5483
--- SIGCHLD (Child exited) @ 0 (0) ---
close(4)                                = 0
read(3, "/opt/openoffice.org3/program\n", 128) = 29
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 5483
chdir("/opt/openoffice.org/basis3.1/program") = 0
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x4017b938) = 5484
--- SIGCHLD (Child exited) @ 0 (0) ---
close(4)                                = 0
read(3, "soffice\n", 128)               = 8
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 5484
stat64("/opt/openoffice.org3/program/../basis-link/ure-link/bin/javaldx", {st_mode=S_IFREG|0555, st_size=10912, ...}) = 0
geteuid32()                             = 1000
getgid32()                              = 1000
getegid32()                             = 1000
getgroups32(0, NULL)                    = 18
getgroups32(18, [4, 20, 21, 24, 26, 29, 30, 44, 46, 100, 104, 106, 112, 121, 122, 124, 1000, 1002]) = 18
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x4017b938) = 5485
--- SIGCHLD (Child exited) @ 0 (0) ---
close(4)                                = 0
read(3, "/usr/lib/jvm/java-6-sun-1.6.0.16"..., 128) = 128
read(3, "ava-6-sun-1.6.0.16/jre/lib/i386\n", 128) = 32
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 5485
stat64("/etc/adabasrc", 0xbfd20200)     = -1 ENOENT (No such file or directory)
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x4017b938) = 5487
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 5487
--- SIGCHLD (Child exited) @ 0 (0) ---
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x4017b938) = 5488
rt_sigaction(SIGTERM, {0x804f5fb, ~[RTMIN RT_1], 0}, NULL, 8) = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 78}], 0, NULL) = 5488
--- SIGCHLD (Child exited) @ 0 (0) ---
exit_group(0)       

``` 

Thanks.

---

### Post by Unchqua on 2009-11-07
From strace log it seems that you have Sun JDK 1.6.0b16 installed and OOoWriter tries to access its jre/lib/i386 directory. What's your OS architecture? Where did you get JDK distribution from? Please provide output from command
```
$JAVA_HOME/bin/java -version
```

---

### Post by legolas_w on 2009-11-07
output for the command is:

```
java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) Server VM (build 14.0-b16, mixed mode)

```

My system is 32 bit with the PAE kernel to use all 4 gigs of ram.

inside the  **usr/lib/jvm/** there is a link and a folder as follow:

```
java-6-sun  java-6-sun-1.6.0.16
```


The default JVM (which is in the path) is installed manually (I got the JDK from Sun website and install it for my development tasks) but the one in the **usr/lib/jvm/** is installed automatically and I am not aware which software did that.

---

### Post by Unchqua on 2009-11-07
What if you remove that unknownsource /usr/lib/jre/ JRE either manually (may be not remove but rename .../jre to .../jre~) or by finding out which package did that? I see that OpenOffice installation is also done manually since it lies in /opt directory, right?
I guess the problem boils down to javaldx (OO's binary responsible to dealing with Java business during OO startup) for some reason not able to cope with that /usr/lib/jre.
For example, I have Ubuntu 8.04 with OO 2.4 installed from standard repository and JDK 6 installed manually. JDK's bin directory is in the PATH; JAVA_HOME not set by default. No matter if JAVA_HOME is set or not, pointing either to JDK or JRE bin directory, and no matter if PATH contains right bin directory or not, javaldx says it can't find Java Runtime Envoronment. But at least OO works.

---

### Post by legolas_w on 2009-11-09
hi,


After countless install, purge, remove, ...  I found the problem by running 

strace /usr/lib/openoffice/program/soffice.bin

There was a culprit font in /home/legolas/.fonts which was causing a segmentation fault in the system.the font name was aquabase_spanish

Thanks everyone who looked into my problem. Now I have two problem before making Karmic a beloved release for myself.

Thanks.

---

### Post by AlexDudko on 2009-11-09
Same problem here. Changing java version and disabling it in openoffice completely didn't make any difference. I also tried various documents, created in previous version of openoffice and couldn't find any cause of the crashes depending on font, style, language usage in a document. After rebooting it opens a document and can create a new one, but it constantly crashes both while saving or editing a document. So, writer crashes also with documents, created with this version of word processor. Installing Sun's version had the same result. Though in development release of Fedora (F12), which has the same version of OOO these crashes don't occur. The problem can be caused by a bug in some Ubuntu libraries which OOO depends on.

---

### Post by DanFoxDavies on 2009-11-09
I get the same sort of problem (OpenOffice just vanishing with no warning) but only after I scroll down a document I've opened. I'm using a fresh 9.10 on a 64bit Intel system with Ubuntu-restricted-extras installed (therefore including java). I have no .fonts folder in my home folder, this includes after I 'Show Hidden Files'. There is a .fontconfig full of files with unreadable names, but that's all.

---

### Post by legolas_w on 2009-11-09
I suggest you use:


```
strace /usr/lib/openoffice/program/soffice.bin
```

and see what is the output after word processor crashed. this way you will be able to find the cause and therefore the cure.

---

### Post by AlexDudko on 2009-11-09
The last message in output is:
> lstat64("/home/me/.openoffice.org/3/.lock", 0xbfb92710) = -1 ENOENT (No such file or directory)
exit_group(79)                          = ?

But starting writer with the command
> strace /usr/lib/openoffice/program/soffice.bin
from time to time appear alert messages with this content:
> error loding BASIC of document
file:///home/me/.openoffice.org/3/user/basic/script.xlc/:
General Error.
General input/output error.
and
> error loding BASIC of document
file:///home/me/.openoffice.org/3/user/basic/script.xli/:
General Error.
General input/output error.

---

### Post by legolas_w on 2009-11-09
> **AlexDudko said:**
> The last message in output is:

But starting writer with the command

from time to time appear alert messages with this content:

and

I suggest you rename **.openoffice.org** to something else and let the openoffice create it from scratch. I hope it resolve the problem because I am unable to understand what is wrong with your installation.

---

### Post by ssdt on 2009-11-09
I think you have to uninstall it first and reinstall it back again.

---

### Post by AlexDudko on 2009-11-09
I **have** already tried to reinstall and use both karmic and Sun's versions of OpenOffice. And also I tried to remove .openoffice.org directory. Nothing helped yet. But... I use karmic for about a month (from the development stage) and from the very installation it worked just fine. Crashes started about two weeks ago. Unfortunately, I don't remember which updates I accepted then.

---

### Post by Hagar Delest on 2009-11-09
See: [[Solved] script.xlb and dialog.xlb general error](http://user.services.openoffice.org/en/forum/viewtopic.php?f=6&t=16588).

---

