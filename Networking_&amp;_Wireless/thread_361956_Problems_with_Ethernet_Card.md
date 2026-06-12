---
title: "Problems with Ethernet Card"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by Platinum J on 2007-02-15
Hello everyone, 

First thank you for all your help and support. Now heres the deal: My girlfriend has a Dell Inspiron 600m and when she was running Windows it was not working well with the ethernet card. So then I tried the Ubuntu Edgy Live CD and surprise it recognized it and seemed to work. Then upon installation it worked as first, but then edgy had trouble recognizing it. Now, its up to luck. Additionally, the whole system seems to have become more unstable and I have a feeling its related some how to the wireless or the ethernet card. I'm a little lost as to what to do. I've also tried the Kubuntu Edgy and Dapper live Cds but to no avail. Is it possible the ethernet card is broken? The lights in the back turn on however. How would I replace it? The Ethernet card is a Broadcom. 

Thanks, 

- Platinum One

---

### Post by gradedcheese on 2007-02-15
what happens when it "breaks"?  ie: no network connection but the card still appears as an interface?  Or the interface is also gone?  Do you know how to use the usual tools (ifconfig, lspci, dhclient) or would you like some troubleshooting suggestions with them?

---

### Post by amo-ej1 on 2007-02-15
I'd suggest pasting the output of the 'lspci' command (just type it in in a terminal) to give us an idea of what is in the laptop. Also the last few lines of the 'dmesg' command (which contains the kernel errors, if any and messages)

---

