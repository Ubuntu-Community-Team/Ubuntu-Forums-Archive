---
title: "Compiling help"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by trj021782 on 2010-09-30
I am trying to compile some software,

The tutorial from the site I got it from said I should unpack the software and navigate to that directory then login as root and use the command:

make

and after that was done use the command:

make install 

I did all of these things but it errors out during the first process, I tried "make install" just in case but it was to no avail. 

Here is the screen print out of what happened during the first step

root@joe-ps3-ubuntu:/usr/local/src/xor# sudo make
make -e PWD=/kmod -C kmod
make[1]: Entering directory `/usr/local/src/xor/kmod'
make -C /lib/modules/2.6.31-22-powerpc64-smp/build M=/kmod modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-22-powerpc64-smp'
scripts/Makefile.build:44: /kmod/Makefile: No such file or directory
make[3]: *** No rule to make target `/kmod/Makefile'.  Stop.
make[2]: *** [_module_/kmod] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-22-powerpc64-smp'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/local/src/xor/kmod'
make: *** [all] Error 2
root@joe-ps3-ubuntu:/usr/local/src/xor# 

What am I doing wrong?

---

### Post by robsoles on 2010-09-30
Not sure you are doing anything wrong but you say the instructions say to login as root and you are not logging in as root but instead executing the make command as root - not a huge difference but at least a slight one.

```
sudo bash
```

is my preferred way to become root if everything I need to do for the next few commands would otherwise be prefixed with sudo.

Try:
```
sudo bash
cd /usr/lib/src/xor
make
exit
```
The 'exit' on the end there is to close the session that was opened for root when 'sudo bash' was executed.

If it still bombs (has errors and won't compile) then it is something else, please repost the output if it has errors and isn't the same as above.

---

### Post by trj021782 on 2010-10-01
> **robsoles said:**
> Not sure you are doing anything wrong but you say the instructions say to login as root and you are not logging in as root but instead executing the make command as root - not a huge difference but at least a slight one.

```
sudo bash
```is my preferred way to become root if everything I need to do for the next few commands would otherwise be prefixed with sudo.

Try:
```
sudo bash
cd /usr/lib/src/xor
make
exit
```The 'exit' on the end there is to close the session that was opened for root when 'sudo bash' was executed.

If it still bombs (has errors and won't compile) then it is something else, please repost the output if it has errors and isn't the same as above.

Thnaks for the help, It worked

---

