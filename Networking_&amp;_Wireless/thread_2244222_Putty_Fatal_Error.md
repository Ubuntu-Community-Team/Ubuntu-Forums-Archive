---
title: "Putty Fatal Error"
date: 2014-09-14
forum: Networking &amp; Wireless
---

### Post by mahmoud_moosa2 on 2014-09-14
Hello everybody,

My OS is ubuntu 12.04 desktop 32-bit.
i am connecting the pc directly to cisco switch using serial console cable.

my problem is i am unable to connect using putty as shown in the screenshot below.
eventhough i can connect using minimcom with the same serial.

i tried but no luck.

i appreciate any comment and thank you very much.

respectfully,

ubuntu moses

[ATTACH=CONFIG]256453[/ATTACH][ATTACH=CONFIG]256454[/ATTACH][ATTACH=CONFIG]256455[/ATTACH]

---

### Post by TheFu on 2014-09-15
I've used putty for ssh connections - never for serial connections. Does it support serial?
Ethernet is the standard network connection - I suppose you have a good reason to want serial?

---

### Post by mahmoud_moosa2 on 2014-09-25
> **TheFu said:**
> I've used putty for ssh connections - never for serial connections. Does it support serial?
Ethernet is the standard network connection - I suppose you have a good reason to want serial?

Hello and welcome,

yes it does and thank you for your reply.

i found the reason, it is the permission and here is the solution i would like to share it to help ubuntu lovers::guitar:

login as root
chmod 666 /dev/ttyUSB0

in my case i am using serial to USB convertor and the concept applys to other connectors. :-)

now it's perfectly working and i want to mark it as solved.


respectfully,

ubuntu moses

---

### Post by TheFu on 2014-09-25
Allowing "other" to write to a USB device may not be the best, secure, solution. Could you place your userid into the group for that file/device?  Not good for bin/root, but if the group is specialized for USB devices - might be better than 666 perms.

---

