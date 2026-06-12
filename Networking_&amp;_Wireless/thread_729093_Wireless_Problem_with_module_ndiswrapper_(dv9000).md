---
title: "Wireless Problem with module ndiswrapper (dv9000)"
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by vicanbas on 2008-03-19
Hey guys! I have an HP dv9000 laptop. I managed to install my wireless nic with the working device drivers. I was able to connect to my WEP encrypted router without any problems. Once i rebooted it seems that the module did not load up so i had to use modprobe ndiswrapper everytime I rebooted. Then I solved this by adding the module "ndiswrapper" under the etc/modules file. Everything worked fine when I rebooted like two or three more times. When I rebooted again nothing showed up under iwconfig:

xxx@xxx:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

I rebooted again and the wireless card WAS detected and it DID WORKED. I rebooted again and it did not work. Rebooted again and it WORKED and so forth. Whenever the card works, I run modprobe ndiswrapper and it just stops without getting or displaying any results.
The module is loaded. I know this because:

xxx@xxx:~$ lsmod | grep ndiswrapper
ndiswrapper           233826  1 
usbcore               161584  7 ndiswrapper,usbhid,uvcvideo,hci_usb,ohci_hcd,ehci_hcd

I sense that (im sorry if I am totally wrong....linux newbie) the module is not terminating correctly everytime I turn off my computer and therefore it doesn't work when I restart; working the second time I restart

Any help on this would be greatly appreciated. Thanks in advanced!

---

