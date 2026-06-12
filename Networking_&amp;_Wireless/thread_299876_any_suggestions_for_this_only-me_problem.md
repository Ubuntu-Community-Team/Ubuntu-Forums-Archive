---
title: "any suggestions for this only-me problem?"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by redsax on 2006-11-14
Problems: after installed ubuntu/edgy, could not connect to internet. my ethernet card is Marvell Yukon 88E8056, 
needing sk98lin driver.

1. when boot, no either sk98lin or skge/etc is loaded, which,
along with other results from lspci/ifconfig/lshw, suggests
the card is not identified by any driver.
e.g., see: [http://ubuntuforums.org/showthread.php?t=296361](http://ubuntuforums.org/showthread.php?t=296361)

2. So after googling and narrowing possibilities, the problem
is in old sky2.c, id of 88E8056, i.e. 4364, is not listed.
One hack is to directly add this id in sky2.c and recompile the driver.

3. Alternatively, a new sk98lin can be downloaded 
from :[http://www.marvell.com](http://www.marvell.com). Lots of people reported 
their good news after re-installing the updated driver. 
So I went to dl'ed it, but when I ran the installation, my computer always died during "checking the driver". 

4. Since I could produce a patch by using the downloaded 
install.sh, I tried to recompile my kernel. However, ubuntu, which relies so much on getting any packages from servers, 
is really not convenient when internet is not connected 
(I need to install qt/libncurses).

5. Finally since I understand sh file, I figured out
install.sh actually compiled the new driver, but when it ran
insmod to install the compiled ko, the problem happened. 
So I skipped the step in install.sh, then found out sk98lin
can identify the ethernet card now when booting, but at 
the same time makes my computer die (freeze) after loading
sk98lin. Something must be in conflict with that the ethernet
card is run by sk98lin?

My question is whether this problem only depends on linux
distributions? So I may try another linux?
On the other hand, since I have spent so much time on 
ubuntu, kind of feel I should keep it. 

Any suggestions for this problem? now when my computer boots,
after loads sk98lin and prints out Marvell 88E8056 ..., it
dies immediately. I have to reset the power in order to
start the computer. Now I am using windows instead (dual boot).
](*,) ](*,) ](*,)

---

