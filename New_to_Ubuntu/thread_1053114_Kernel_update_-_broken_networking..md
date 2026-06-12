---
title: "Kernel update - broken networking."
date: 2009-01-28
forum: New to Ubuntu
---

### Post by celticbhoy on 2009-01-28
I have just run update manager & it installed kernel version 2.6.27-11 among a bunch of other updates, and now I can no longer connect to my network with an ethernet cable. If i boot into 27-9 everything still works fine. I am using an acer aspire one with intrepid.

---

### Post by green69 on 2009-01-30
> **celticbhoy said:**
> I have just run update manager & it installed kernel version 2.6.27-11 among a bunch of other updates, and now I can no longer connect to my network with an ethernet cable. If i boot into 27-9 everything still works fine. I am using an acer aspire one with intrepid.

I was having the same problem (aspire one - Intrepid - 2.6.27.11) but with the wifi connection.
A solved the problem going to wifi driver dir and compiling again:

cd madwifi-hal-0.10.5.6*/
make
sudo make install
modprobe ath_pci


I don't have experience but to me it works. You can get a try!

---

