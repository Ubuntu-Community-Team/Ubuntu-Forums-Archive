---
title: "Wireless Connection Gutsy"
date: 2008-01-27
forum: Networking &amp; Wireless
---

### Post by jaywalker13 on 2008-01-27
My wireless seems to be turned off.

Product: PRO/Wireless 2200BG Network Connection from Intel.

Since installing Gutsy it has not been possible to turn it on with the usual Fn F2 combination on the Dell Inspiron 9300 keyboard.

I also have Windows XP installed on this laptop and I can still turn on the wireless in Windows and connect OK so the hardware is OK.

I did sudo lshw -C network in Terminal and it says "wireless=radio off".

I previously had Feisty on this computer and wireless worked fine.

Is there any way I can get the wireless to turn on or is something else wrong altogether?

Thanks

Jay

---

### Post by jaywalker13 on 2008-01-31
Well I had yet another look at old posts and found a solution to this problem. And who wrote the previous post? I did! "Thanks Jay. You could have told me this without going to the forum." "That's OK Jay, always happy to help.")

In case it helps anyone else, this is from my earlier post:

"My setup does not like it when eth0 (wired) and eth1 (wireless) are both enabled. From a textbook, got this:

sudo ifconfig eth0 down

Also had to untick eth0 in manual configuration

Also used the following to set up eth1:

sudo ifconfig eth1 192.168.1.11 netmask 255.255.255.0 up"



The sudo lshw -C network command now includes the statement "wireless=IEEE 802.11g".

So it's solved, but I'd be interested if anyone can guide me to understand that a bit more.

Cheers

Jay

---

