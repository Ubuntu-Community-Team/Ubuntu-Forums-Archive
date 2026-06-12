---
title: "[SOLVED] Atheros AR5418 Not Working in hardy"
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by Nxion on 2008-08-09
Hey,

I received my new wireless card in the mail and was anxious to install it. So after I installed it and booted my laptop. It does not seem that Ubuntu sees. If I do a iwconfig there is nothing there for wireless. NetworkManager does not see it as well. if I do a lspci it shows this:

> 0c:00.0 Network controller: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)

So Ubuntu is seeing it but I just cant use it. Also I opened up the Restricter drivers page in System > Administration > Hardware Drivers and it does not show up at all in there either.

Any help will be greatly appreciated.

Thanks,
Nx

---

### Post by Nxion on 2008-08-09
Im really hoping some one can help me here. Im dead in the water if I cant get mylaptop fixed :( Also does it make a differance how I attached the three wires? I have a gray, white and a black wire.

on antenna 1 i attached the White wire, atenna 2 is gray and 3 is the black. pretty much I just attaced it based on how my old intel card was layed out.

---

### Post by Nxion on 2008-08-13
Never mind I guess. I was able to get it working with Madwifi. Thanks anyway.

---

### Post by Nxion on 2008-08-18
This is what I used to get the card working.

```
sudo apt-get install build-essential
sudo apt-get install linux-headers-X-generic (run uname to find correct version and replace X)
sudo apt-get install subversion
sudo svn checkout [http://svn.madwifi.org/madwifi/trunk/](http://svn.madwifi.org/madwifi/trunk/) madwifi-ng
cd madwifi-ng
make 
make install
sudo gedit /etc/modules

You will need to add a line at the very end of the file:
ath_pci 			 		
```

A friend of mine gave it to me.
Cheers!

---

