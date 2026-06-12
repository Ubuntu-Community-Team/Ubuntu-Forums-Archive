---
title: "ndiswrapper version / driver version mismatch"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by czaleski on 2006-08-30
Greetings,

Was hoping for some advice. I have a fresh install of Ubuntu Dapper. The only thing I did was to update the kernel to 2.6.15-26-686 in order to have smp support. I followed an ndiswrapper install guide here [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper). It all worked fine & could see/use the wireless adapter (the Dell 1390, ie: broadcom 4311), until I rebooted... then ndiswrapper doesn't load properly any more.
I did indeed do both "sudo ndiswrapper -m", as well as add 'ndiswrapper' to the /etc/modules file.

The log from boot-time seems ok:
"ndiswrapper version 1.23 loaded (preempt=yes,smp=yes)"
this is repeated about 9 times

ndiswrapper -l reports:
bcmwl5 driver present, hardware present

...but it is not a running process. If I try to run it manually via "modprobe ndiswrapper" I get an error:
"FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-26-686/misc/ndiswrapper.ko): Operation not permitted"

This process also causes 2 log entries to be generated:
"ndiswrapper version 1.23 loaded (preempt=yes,smp=yes)"
"localhost loadndisdriver: loadndisdriver: main(638): version 1.7 doesn't match driver version 1.8"

I'm not sure what "driver version 1.8" refers to in this case. I checked carefully and I'm confident that I'm using the correct Windows driver - .inf & .sys files - for my adapter (although this error may be unrelated to that).

I understand that the version of ndiswrapper is the "1.7" part, but could someone please help/elaborate on the mismatch?

Any advice or input is appreciated
Thanks very much

---

### Post by czaleski on 2006-08-31
This is probably a bit obscure, so I hope no one minds if I bump it once or twice for a little extra face time...

---

