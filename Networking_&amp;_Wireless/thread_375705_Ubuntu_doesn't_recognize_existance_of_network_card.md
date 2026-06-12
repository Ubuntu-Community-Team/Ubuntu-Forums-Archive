---
title: "Ubuntu doesn't recognize existance of network card"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by Eschatokyrios on 2007-03-04
Dell Inspiron 5150 with ubuntu 6.06.

When I go into wireless assistant, it returns an error that no usable devices were found. iwconfig just lists lo and eth0, which naturally have no wireless extentions. ifconfig doesn't even list the existance of wlan0, and when I do ifup wlan0 it also doesn't recognize that the device exists. It works perfectly fine when I boot into windows on the same computer, so it's not a hardware problem. Anyone know what's going on?

---

### Post by teaker1s on 2007-03-04
Ubuntu hasn't got a driver loaded for it.
In terminal
try
```
lspci
lsusb
```
see if you can see the makers chip id or post results so we can see

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=wireless&titlesearch=Titles]("https://help.ubuntu.com/community/?action=fullsearch&context=180&value=wireless&titlesearch=Titles")

---

### Post by Eschatokyrios on 2007-03-04
I do have a driver for it though, set up with ndiswrapper. Ndiswrapper -l returns "driver installed, device present"

---

### Post by Eschatokyrios on 2007-03-05
I ran dmesg for an unrelated reason, and I found these ndiswrapper related error messages that didn't used to be there. Perhaps they're the reason my network card isn't working?
```

laptop:~$ sudo dmesg | grep ndiswrapper
Password:
[17179608.276000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179608.296000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179608.296000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed
[17179608.316000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179608.320000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179608.320000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed
[17179608.712000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179608.716000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179608.716000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed
[17179609.040000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179609.040000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179609.040000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed
[17179609.064000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179609.068000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179609.068000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed
[17179609.092000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179609.092000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179609.096000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed


```

I don't think I need the lspci entry, because I used it before to get the right driver for ndiswrapper and it definately did work for a time. I don't want to retype it from the laptop's screen if I don't need to :)

---

### Post by teaker1s on 2007-03-06
one of the recent kernels breaks wifi and secondly have you got ndiswrapper-utils 1.8 installed as it's sometimes required

---

### Post by Eschatokyrios on 2007-03-06
I didn't change the kernel at all, though. I don't have ndiswrapper-utils, but I never had it, so that can't be the problem either. I didn't make any major changes to the system before ndiswrapper stopped working.

---

