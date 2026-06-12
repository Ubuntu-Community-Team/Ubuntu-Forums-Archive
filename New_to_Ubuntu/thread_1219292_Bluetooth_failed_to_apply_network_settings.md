---
title: "Bluetooth failed to apply network settings"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-07-21
Twice, but several days apart, I have received a Bluetooth error message. See attached screenshot.

1 - How serious is this?

2 - Is there a fix?

---

### Post by Mark_in_Hollywood on 2009-10-13
After a few reboots (the next day), this problem resolved itself.

---

### Post by sourav_b4u on 2009-10-14
Hi ,

I have newly installed ubuntu 9.04 in my sony vaio FZ25GN laptop. 
My bluetooth is not functioning.

sourav@sourav:~$ hciconfig -a
hci0:    Type: USB
    BD Address: 00:1B:FB:8D:15:57 ACL MTU: 1021:6 SCO MTU: 64:1
    UP RUNNING 
    RX bytes:169 acl:0 sco:0 events:20 errors:0
    TX bytes:327 acl:0 sco:0 commands:20 errors:0
    Features: 0xff 0xff 0x8f 0xfe 0x9b 0xff 0x79 0x83
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: 
    Link mode: SLAVE ACCEPT 
Can't read local name on hci0: Input/output error (5)
sourav@sourav:~$ hcitool scan
Scanning ...
Inquiry failed: Connection timed out
sourav@sourav:~$ uname -r
2.6.28-15-generic

Any help is appreciated.

Thanks in Advance.

Regards

Sourav

---

### Post by Mark_in_Hollywood on 2009-10-14
sourav_b4u

Please make a NEW post about this problem. The way we work at the forums is to treat each persons problem separately. I know this may not appear in the threads, but I cannot help you. AND I have marked my post as solved. 

Sorry for the inconvenience.

---

