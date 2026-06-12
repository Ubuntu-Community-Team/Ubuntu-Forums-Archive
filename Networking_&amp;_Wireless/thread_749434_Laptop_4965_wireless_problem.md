---
title: "Laptop 4965 wireless problem"
date: 2008-04-08
forum: Networking &amp; Wireless
---

### Post by johny007 on 2008-04-08
I've got an asus s96s latop with an intel 4965 (agn) wireless card. I've been having problems with this wireless for a while (e.g. it didn't work 'out of the box', I had to install drivers through ndsiwrapper, but at least the NetworkManager  finally managed to find my network).
Here comes the problem.
The NetworkManager managed to connect to some not protected network, which was found, but it cannot connect to my network, which has a WEP personal password. I'm 100% sure that the password I give is correct etc., because it works on windows vista. 

When I try to connect this icon goes round and round but doesn't connect, but it also says 'attempting to get a network key for network 'my_ntw_name'' or sth like that.

Can anyone help?

---

### Post by nixscripter on 2008-04-08
Under the applet, try using "Connect to Other Wireless Network," and enter the key and name manually. Make sure that if you use a hexidecimal key to select that type.

Assuming that doesn't work, then while the icon is going around, check on the status of the wireless by opening the terminal and typing ```
iwconfig
``` to check the signal level and whether it is associating or not.

---

