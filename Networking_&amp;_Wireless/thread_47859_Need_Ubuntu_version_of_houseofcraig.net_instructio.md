---
title: "Need Ubuntu version of houseofcraig.net instructions"
date: 2005-07-10
forum: Networking &amp; Wireless
---

### Post by mxreader on 2005-07-10
Help me (newbie) please,

I have a DWL-G520+ WIreless and was not able to get Ubuntu connecting to the Access Point with WEP, I came across several threads explaining that this is not supported by the acx111 driver in Hoary, but pointing to a clue in [http://www.houseofcraig.net/acx100_howto.php](http://www.houseofcraig.net/acx100_howto.php) it looked worth a try and so after going step by step and after moving the original acx driver as instructed with 

find /lib/modules/`uname -r` -name "*acx*" -exec mv {} /root \;
(note: I see that an acx folder (presumably my "old" driver) is created in the root folder)

but when the instructions asked to verify the presence of the correct version of the kernel source, by typing: ls /lib/modules/`uname -r`/build/include/linux/version.h 
I got a response "ls: /lib/modules/2.6.10-5-386/build/include/linux/version.h: No such file or directory" so I am now up the creek with little knowledge i dont know how to undo or re-install the acx drivers.  Damn, the instructions must be backwards.

I tried downloading through synaptic what looked like a source kernel 2.6.10 but afterwards typing the ls command still doesnt get the right response so I guess the files must be located elsewhere in Ubuntu.

Q. How can I get back and reinstall the driver? so I can undo this bad decision?

I should have chosen the safer route of using ndiswrapper (the instructions look a whole lot easier).

---

### Post by mxreader on 2005-07-12
](*,)

---

