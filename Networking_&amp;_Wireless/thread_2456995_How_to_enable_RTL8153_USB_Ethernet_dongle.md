---
title: "How to enable RTL8153 USB Ethernet dongle?"
date: 2021-01-23
forum: Networking &amp; Wireless
---

### Post by ryan170 on 2021-01-23
I'm running Ubuntu Server 20.04.1 on an Intel NUC 10i5. I've found that the ethernet port on the NUC is very iffy - just barely touching/nudging the ethernet cable makes me lose connection. So I bought a USB 3.0-Ethernet adapter. (I could RMA, but I don't want to spend the time doing it right now).

lsusb:
```
Bus 002 Device 002: ID 0bda:8153 Realtek Semiconductor Corp. RTL8153 Gigabit Ethernet Adapter
```

lsmod | grep -e cdc -e r8152 (I know the 8153-8152 discrepancy, but 8153 doesn't turn up anything; this looks to be the same adapter)
```
cdc_ether              20480  0
usbnet                 45056  1 cdc_ether
r8152                  69632  0
mii                    20480  2 usbnet,r8152
```

I can't get ip addr show to show any connection for it however. How do I enable the use of this USB Ethernet dongle to replace eno1 (the current port)? Thanks!

---

### Post by ryan170 on 2021-01-23
I've been following this tutorial: [https://www.pcsuggest.com/install-rtl8153-driver-linux/](https://www.pcsuggest.com/install-rtl8153-driver-linux/)

Everything goes well, until I get to sudo make install, then I run into an error:
```
<me>@nuc10i5:~/r8152-2.14.0$ make
make -C /lib/modules/5.4.0-64-generic/build M=/home/<me>/r8152-2.14.0 modules
make[1]: Entering directory '/usr/src/linux-headers-5.4.0-64-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory '/usr/src/linux-headers-5.4.0-64-generic'
<me>@nuc10i5:~/r8152-2.14.0$ sudo make install
make -C /lib/modules/5.4.0-64-generic/build M=/home/<me>/r8152-2.14.0 INSTALL_MOD_DIR=kernel/drivers/net/usb modules_install
make[1]: Entering directory '/usr/src/linux-headers-5.4.0-64-generic'
  INSTALL /home/<me>/r8152-2.14.0/r8152.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: ../crypto/bio/bss_file.c:69
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: ../crypto/bio/bss_file.c:76
sign-file: certs/signing_key.pem: No such file or directory
  DEPMOD  5.4.0-64-generic
Warning: modules_install: missing 'System.map' file. Skipping depmod.
make[1]: Leaving directory '/usr/src/linux-headers-5.4.0-64-generic'
modprobe r8152
modprobe: ERROR: could not insert 'r8152': Operation not permitted
make: *** [Makefile:42: install] Error 1
```

It seems like the module is unsigned, and Ubuntu 20 won't allow me to install unsigned drivers. Would turning Secure Boot off help with this, or is there a better way to install this module? Thanks.

---

### Post by CelticWarrior on 2021-01-24
Yes, Secure Boot should be disabled for convenience.

---

### Post by ryan170 on 2021-01-25
> **CelticWarrior said:**
> Yes, Secure Boot should be disabled for convenience.

I've disabled secure boot, and finished the tutorial. It didn't show any errors, but I still have no output for the USB Ethernet adapter in ip addr show.

```
<me>@nuc10i5:~/r8152-2.14.0$ sudo make install
rmmod r8152
make -C /lib/modules/5.4.0-64-generic/build M=/home/<me>/r8152-2.14.0 INSTALL_MOD_DIR=kernel/drivers/net/usb modules_install
make[1]: Entering directory '/usr/src/linux-headers-5.4.0-64-generic'
  INSTALL /home/<me>/r8152-2.14.0/r8152.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: ../crypto/bio/bss_file.c:69
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: ../crypto/bio/bss_file.c:76
sign-file: certs/signing_key.pem: No such file or directory
  DEPMOD  5.4.0-64-generic
Warning: modules_install: missing 'System.map' file. Skipping depmod.
make[1]: Leaving directory '/usr/src/linux-headers-5.4.0-64-generic'
modprobe r8152
<me>@nuc10i5:~/r8152-2.14.0$ sudo depmod -a
<me>@nuc10i5:~/r8152-2.14.0$ ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 1c:69:7a:6b:c2:0a brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.100/24 brd 192.168.1.255 scope global eno1
       valid_lft forever preferred_lft forever
    inet6 fe80::1e69:7aff:fe6b:c20a/64 scope link
       valid_lft forever preferred_lft forever
4: wlp0s20f3: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 3c:58:c2:d7:7f:80 brd ff:ff:ff:ff:ff:ff
5: br-94b3f458b8a2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default
    link/ether 02:42:34:ea:00:e3 brd ff:ff:ff:ff:ff:ff
    inet 172.18.0.1/16 brd 172.18.255.255 scope global br-94b3f458b8a2
       valid_lft forever preferred_lft forever
    inet6 fe80::42:34ff:feea:e3/64 scope link
       valid_lft forever preferred_lft forever
6: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default
    link/ether 02:42:50:c6:dd:ef brd ff:ff:ff:ff:ff:ff
    inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
       valid_lft forever preferred_lft forever
8: vetha289795@if7: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-94b3f458b8a2 state UP group default
    link/ether 4a:34:02:0a:d2:9e brd ff:ff:ff:ff:ff:ff link-netnsid 2
    inet6 fe80::4834:2ff:fe0a:d29e/64 scope link
       valid_lft forever preferred_lft forever
10: vethae0bbfd@if9: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-94b3f458b8a2 state UP group default
    link/ether e6:22:a3:10:b3:8e brd ff:ff:ff:ff:ff:ff link-netnsid 1
    inet6 fe80::e422:a3ff:fe10:b38e/64 scope link
       valid_lft forever preferred_lft forever
12: veth49e271e@if11: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-94b3f458b8a2 state UP group default
    link/ether 3a:1b:5b:c3:55:97 brd ff:ff:ff:ff:ff:ff link-netnsid 0
    inet6 fe80::381b:5bff:fec3:5597/64 scope link
       valid_lft forever preferred_lft forever
14: veth699abb9@if13: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-94b3f458b8a2 state UP group default
    link/ether 9a:d5:c4:89:36:ee brd ff:ff:ff:ff:ff:ff link-netnsid 4
    inet6 fe80::98d5:c4ff:fe89:36ee/64 scope link
       valid_lft forever preferred_lft forever
16: veth560c528@if15: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-94b3f458b8a2 state UP group default
    link/ether f6:48:37:21:93:1f brd ff:ff:ff:ff:ff:ff link-netnsid 3
    inet6 fe80::f448:37ff:fe21:931f/64 scope link
       valid_lft forever preferred_lft forever
18: veth2c0a8a2@if17: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-94b3f458b8a2 state UP group default
    link/ether 06:4e:db:0a:1a:fa brd ff:ff:ff:ff:ff:ff link-netnsid 5
    inet6 fe80::44e:dbff:fe0a:1afa/64 scope link
       valid_lft forever preferred_lft forever
21: enx00e04d715e72: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 00:e0:4d:71:5e:72 brd ff:ff:ff:ff:ff:ff
```

What else can I do to get this working? Thanks.

---

### Post by mastablasta on 2021-01-27
wouldn't the OS have to be installed with secure boot turned off to be able to patch the kernel?

also i would claim the NUC if it is still under warranty. it is not functioning as expected.

---

### Post by slickymaster on 2021-01-27
*Thread moved to **Networking & Wireless**.*

---

### Post by chili555 on 2021-01-27
Why do you want to use a USB adapter in favor of your internal device which seems to be working well?

What steps did you take at the Network Manager icon at the upper right to turn off the internal and turn on the USB? Since the internal has an IP address, I can only assume that the ethernet cable is attached to the internal device only Are you, for some reason, using two ethernet cables?

---

