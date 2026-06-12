---
title: "ess modem driver error"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by CateranLlama on 2009-03-23
Hi.  I'm a beginner, more or less.  And I've been going round and round and round with this modem driver for a month now.  I really would like to have it, there's no way to get on the internet here other than dial-up.  And I'm tired of using other people's  machines to get online.  

Anyway, the make.log looks like this, after my error.  

  LD	binary.a
make -C /lib/modules/2.6.27-7-generic/build M=/home/llama/ess_2.6-v0.5
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  LD      /home/llama/ess_2.6-v0.5/built-in.o
  CC [M]  /home/llama/ess_2.6-v0.5/essserial-2.6.o
  CC [M]  /home/llama/ess_2.6-v0.5/essserial_pci.o
  CC [M]  /home/llama/ess_2.6-v0.5/essserial_hw.o
  CC [M]  /home/llama/ess_2.6-v0.5/linmodem-2.6.o
  LD [M]  /home/llama/ess_2.6-v0.5/linmodem.o
  LD [M]  /home/llama/ess_2.6-v0.5/esscom.o
  LD [M]  /home/llama/ess_2.6-v0.5/esscom_hw.o
  Building modules, stage 2.
  MODPOST 3 modules
WARNING: could not find /home/llama/ess_2.6-v0.5/.binary.a.cmd for /home/llama/ess_2.6-v0.5/binary.a
  CC      /home/llama/ess_2.6-v0.5/esscom.mod.o
  LD [M]  /home/llama/ess_2.6-v0.5/esscom.ko
  CC      /home/llama/ess_2.6-v0.5/esscom_hw.mod.o
  LD [M]  /home/llama/ess_2.6-v0.5/esscom_hw.ko
  CC      /home/llama/ess_2.6-v0.5/linmodem.mod.o
  LD [M]  /home/llama/ess_2.6-v0.5/linmodem.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
rm -f /dev/ttyS_ESS0
echo "KERNEL==\"ttyS_ESS0\", SYMLINK=\"modem\"" > /etc/udev/rules.d/70-ess.rules
/bin/sh: cannot create /etc/udev/rules.d/70-ess.rules: Permission denied
make: *** [install] Error 2

---

### Post by mrbiggbrain on 2009-03-23
> **CateranLlama said:**
> Hi.  I'm a beginner, more or less.  And I've been going round and round and round with this modem driver for a month now.  I really would like to have it, there's no way to get on the internet here other than dial-up.  And I'm tired of using other people's  machines to get online.  

Anyway, the make.log looks like this, after my error.  

  LD	binary.a
make -C /lib/modules/2.6.27-7-generic/build M=/home/llama/ess_2.6-v0.5
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  LD      /home/llama/ess_2.6-v0.5/built-in.o
  CC [M]  /home/llama/ess_2.6-v0.5/essserial-2.6.o
  CC [M]  /home/llama/ess_2.6-v0.5/essserial_pci.o
  CC [M]  /home/llama/ess_2.6-v0.5/essserial_hw.o
  CC [M]  /home/llama/ess_2.6-v0.5/linmodem-2.6.o
  LD [M]  /home/llama/ess_2.6-v0.5/linmodem.o
  LD [M]  /home/llama/ess_2.6-v0.5/esscom.o
  LD [M]  /home/llama/ess_2.6-v0.5/esscom_hw.o
  Building modules, stage 2.
  MODPOST 3 modules
WARNING: could not find /home/llama/ess_2.6-v0.5/.binary.a.cmd for /home/llama/ess_2.6-v0.5/binary.a
  CC      /home/llama/ess_2.6-v0.5/esscom.mod.o
  LD [M]  /home/llama/ess_2.6-v0.5/esscom.ko
  CC      /home/llama/ess_2.6-v0.5/esscom_hw.mod.o
  LD [M]  /home/llama/ess_2.6-v0.5/esscom_hw.ko
  CC      /home/llama/ess_2.6-v0.5/linmodem.mod.o
  LD [M]  /home/llama/ess_2.6-v0.5/linmodem.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
rm -f /dev/ttyS_ESS0
echo "KERNEL==\"ttyS_ESS0\", SYMLINK=\"modem\"" > /etc/udev/rules.d/70-ess.rules
/bin/sh: cannot create /etc/udev/rules.d/70-ess.rules: **Permission denied**
make: *** [install] Error 2

are you running this as root by useing sudo? compileing anything thats not going in, and useing just your home directory usualy requires root privlages. 

try 

```
sudo make
```

or whatever make variant your useing (makegui, makethis, makethat)

---

### Post by CateranLlama on 2009-03-23
Well.  I got a different batch of ... it at least ends with an error ... I think...

The sad thing is, I had this part working before I updated Ubuntu.  I just can't remember what it took to get it there...

make -C /lib/modules/2.6.27-7-generic/build M=
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/kconfig/conf.o
scripts/kconfig/conf.c: In function ‚Äòconf_askvalue‚Äô:
scripts/kconfig/conf.c:104: warning: ignoring return value of ‚Äòfgets‚Äô, declared with attribute warn_unused_result
scripts/kconfig/conf.c: In function ‚Äòconf_choice‚Äô:
scripts/kconfig/conf.c:306: warning: ignoring return value of ‚Äòfgets‚Äô, declared with attribute warn_unused_result
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/zconf.tab.o
In file included from scripts/kconfig/zconf.tab.c:2486:
scripts/kconfig/confdata.c: In function ‚Äòconf_write‚Äô:
scripts/kconfig/confdata.c:501: warning: ignoring return value of ‚Äòfwrite‚Äô, declared with attribute warn_unused_result
scripts/kconfig/confdata.c: In function ‚Äòconf_write_autoconf‚Äô:
scripts/kconfig/confdata.c:739: warning: ignoring return value of ‚Äòfwrite‚Äô, declared with attribute warn_unused_result
scripts/kconfig/confdata.c:740: warning: ignoring return value of ‚Äòfwrite‚Äô, declared with attribute warn_unused_result
In file included from scripts/kconfig/zconf.tab.c:2487:
scripts/kconfig/expr.c: In function ‚Äòexpr_print_file_helper‚Äô:
scripts/kconfig/expr.c:1090: warning: ignoring return value of ‚Äòfwrite‚Äô, declared with attribute warn_unused_result
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf -s arch/x86/Kconfig
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  UPD     include/linux/utsrelease.h
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [all] Error 2
llama@llama-desktop:~/ess_2.6-v0.5$

---

