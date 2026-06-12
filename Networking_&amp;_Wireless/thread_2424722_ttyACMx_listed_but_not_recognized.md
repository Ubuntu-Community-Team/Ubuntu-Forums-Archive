---
title: "ttyACMx listed but not recognized"
date: 2019-08-13
forum: Networking &amp; Wireless
---

### Post by baqwas on 2019-08-13
Hello,

Under 19.04:
```
Linux BeUlta 5.0.0-23-generic #24-Ubuntu SMP Mon Jul 29 15:36:44 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
```

I can list the ACMx devices:
```
$ ls /dev/ttyACM*
/dev/ttyACM0  /dev/ttyACM1

```

but when I use Arduino IDE to upload code through one of these ports, i see the following message in the Output window of the IDE:
```
Sketch uses 275740 bytes (28%) of program storage space. Maximum is 983040 bytes.
Global variables use 1664 bytes (0%) of dynamic memory, leaving 260480 bytes for local variables. Maximum is 262144 bytes.
No device found on ttyACM0
An error occurred while uploading the sketch
```

The user running these commands is a member of the **dialout** group.

I am looking for advice along any one of the following tracks:
[LIST=1]
[*]Why would a port, /dev/ttyACM0 (for example), become undetectable suddenly?
[*]Is there some standard utility to test /dev/ttyACMx ports?
[/LIST]

Thanks for the guidance.

---

