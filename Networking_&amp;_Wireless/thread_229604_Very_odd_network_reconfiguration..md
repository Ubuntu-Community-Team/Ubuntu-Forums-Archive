---
title: "Very odd network reconfiguration."
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by edrosten on 2006-08-04
Has anyone here experienced a problem along these lines?

I few days ago, a computer I administer started to behave oddly with regards to its modem. The first problem was that it started autodialling on boot. I checked /etc and sure enough  /etc/network/interfaces was modified on the day that the problem was first reported (the line "auto ppp0" was present) . 

The second problem was that the connection was running very slowly. stty --file=/dev/ttyS0 revealed that the serial connection to the modem was operating at 9600 baud, and the problem was fixed by changing it to 115200.

The odd thing is that I can not figure out how these changes occured. The only user of the computer is not aware of how to bring up an editor as root and modify file in /etc. Further, I had a very thorough hunt through the administrative GUI, and there appears to be no way of setting either of those two options described.

I can fix the problems (though I don't know the `proper' place to put stty --file=/dev/ttS0 speed 115200), but it disturbs me that the changes happened.

Has anyone any idea what might have caused them. I've had a dig around, but I haven't found anything yet.

---

### Post by cantormath on 2006-08-04
I just dont know how people are still using dialup

---

