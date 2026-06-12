---
title: "Yet another ltmodem problem"
date: 2005-06-12
forum: Networking &amp; Wireless
---

### Post by joe247 on 2005-06-12
Hi,
It's my second day with my first Linux system, Ubuntu Hoary 5.04 i386 (default Desktop installation). I'm trying to install my old Lucent 56k winmodem. I installed build-essentials and linux-headers and I've download and unpacked ltmodem-2.6-alk-7.tar.bz2. However when I try to make the ltmodem-2.6-alk-7 contents I get the error
make: *** /lib/modules/2.6.10-5.386/build : No such file or directory. Stop.
make: *** [module] Error 2

The file I downloaded was for kernel 2.6. Does anyone have a more up-to-date file or know how to edit the makefile?

Any help for a complete beginner would be very appreciated,
Thanks.

---

### Post by sapo on 2005-06-12
Ubuntu have a pre-compiled module for ltmodem i think..

Try:

```

sudo apt-get install linux-restricted-modules

```

---

### Post by joe247 on 2005-06-12
sapo: Thanks. I think linux-restricted-modules is already installed. What do I do then if I want to get my modem working?

---

### Post by joe247 on 2005-06-12
I did the following, and I think I have the drivers totally installed...

$ vi Makefile # and edit KERNEL_DIR to be /usr/src/linux-2.6.0
$ make
$ sudo mkdir /lib/modules/linux-headers-2.6.10-5.386/ltmodem-alk
$ sudo cp -a ltmodem.ko ltserial.ko /lib/modules/2.6.0/ltmodem-alk
$ sudo depmod -a

$ sudo cat > /etc/modprobe.d/ltmodem <<EOF
alias char-major-62 ltserial
alias /dev/tts/LT0 ltserial
alias /dev/LT-modem ltserial
EOF
$ sudo update-modules


Now, when I try and activate the connection, pp0, under Networking, the modem makes some sounds but nothing more.

Can anyone tell me what tools I need and places I can get a guide to finishing the connection?

Thanks again.

---

### Post by az on 2005-06-12
[http://test.wiki.ubuntu.com/forum/hardware/lucent](http://test.wiki.ubuntu.com/forum/hardware/lucent)

---

### Post by joe247 on 2005-06-12
When I try and connect with wvdial I get
pppd option error (exit code 2)


The following are inabled in /etc/ppp/options

asyncmap 0
auth
crtscts
lock
hide-password
modem
proxyyarp
lcp-echo-internal 3-
lcp-echo-fialure 4
noipx

Anyone know how can I can solve this?

Thanks

---

