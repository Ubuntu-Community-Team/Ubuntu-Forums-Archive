---
title: "How to compile e1000 latest drivers?"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by hdotcom on 2007-05-25
Hi..

I've been having problems trying to compile the latest version of e1000 drivers (7.5). The error message can been seen below.

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

What does the error message "cannot write to /var/cache/man/cat7/e1000.7.gz in catman mode
e1000." refer to? How can i fix it? Thanks.

Rgds,

H.

---

### Post by hdotcom on 2007-05-26
Can anyone help please? Thanks.

H.

---

### Post by chili555 on 2007-05-26
I might try *sudo make.*

---

