---
title: "Error in compiling e1000 latest driver"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by psylance on 2008-08-28
```
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home//Desktop/e1000-7.5.5.1/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home//Desktop/e1000-7.5.5.1/src/e1000_main.o
  CC [M]  /home//Desktop/e1000-7.5.5.1/src/e1000_82540.o
  CC [M]  /home//Desktop/e1000-7.5.5.1/src/e1000_82542.o
  CC [M]  /home//Desktop/e1000-7.5.5.1/src/e1000_82571.o
  CC [M]  /home//Desktop/e1000-7.5.5.1/src/e1000_82541.o
  CC [M]  /home//Desktop/e1000-7.5.5.1/src/e1000_82543.o
  CC [M]  /home//Desktop/e1000-7.5.5.1/src/e1000_ich8lan.o
  CC [M]  /home//Desktop/e1000-7.5.5.1/src/e1000_80003es2lan.o
  CC [M]  /home//Desktop/e1000-7.5.5.1/src/e1000_mac.o
  CC [M]  /home//Desktop/e1000-7.5.5.1/src/e1000_nvm.o
  CC [M]  /home//Desktop/e1000-7.5.5.1/src/e1000_phy.o
  CC [M]  /home//Desktop/e1000-7.5.5.1/src/e1000_manage.o
  CC [M]  /home//Desktop/e1000-7.5.5.1/src/e1000_param.o
  CC [M]  /home//Desktop/e1000-7.5.5.1/src/e1000_ethtool.o
  CC [M]  /home//Desktop/e1000-7.5.5.1/src/kcompat.o
  CC [M]  /home//Desktop/e1000-7.5.5.1/src/e1000_api.o
  LD [M]  /home//Desktop/e1000-7.5.5.1/src/e1000.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home//Desktop/e1000-7.5.5.1/src/e1000.mod.o
  LD [M]  /home//Desktop/e1000-7.5.5.1/src/e1000.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
gzip -c ../e1000.7 > e1000.7.gz
# remove all old versions of the driver
find /lib/modules/2.6.20-15-generic -name e1000.ko -exec rm -f {} \; || true
find /lib/modules/2.6.20-15-generic -name e1000.ko.gz -exec rm -f {} \; || true
install -D -m 644 e1000.ko /lib/modules/2.6.20-15-generic/kernel/drivers/net/e1000/e1000.ko
/sbin/depmod -a || true
install -D -m 644 e1000.7.gz /usr/share/man/man7/e1000.7.gz
man -c -P'cat > /dev/null' e1000 || true
man: 
cannot write to /var/cache/man/cat7/e1000.7.gz in catman mode
e1000.
```

Had this error. Tried many methods but can't work. The machine is a Debian4r3 machine. I think it's because the machine is using gcc4.3 instead of gcc3.4.

How can i make it use gcc3.4 instead?

---

### Post by cariboo on 2008-08-29
Wouldn't be a little easier to upgrade to a newer kernel and use the builtin modules for your network card?

Jim

---

