---
title: "Wireless network always disconnected with d-link n150 pico usb adapter"
date: 2013-09-20
forum: Networking &amp; Wireless
---

### Post by Ming_Dong on 2013-09-20
Hi, I am meeting a very annoying problem.
Just installed ubuntu 13.04 on my desktop(dell t3400), and I use the d-link n150 pico usb adapter to connect to the internet.
After boot into the system, it can connect to my home wireless network(the signal is very good), but after just around 30 secs, it will be disconnected. after that, I can't even find my wireless ssid in the list. This can be reproduced 100%.

I searched the web, somebody said I should use wpa2 only security mode for my router, I changed that, didn't help.

could someone help me please?

thanks in advance.

---

### Post by Hadaka on 2013-09-20
Hi,please post the output of..
```
lspci -nnk | grep -iA3 net
lsmod
lsusb
rfkill list
```
As a temp test please also do..
```
sudo modprobe -r rtl8192cu
sudo modprobe rtl8192cu swenc=1
```
I'm not sure yet if this is your driver, ,it will only
survive for one boot anyway...so not to worry.
thanks.

---

### Post by Ming_Dong on 2013-09-20
will do it this evening.

---

### Post by Ming_Dong on 2013-09-20
Start my computer, connect to the wireless network, disconnected, everything like before.
so I begin to input your commands, after the third command, magic thing happened, my network reconnected!!! and it never disconnects even after restarting.
I don't know what happened, seems your commands only list some information?
or what I need is just waiting some time after it disconnected?

any way, thanks, very happy.

---

### Post by varunendra on 2013-09-21
> **Ming_Dong said:**
> so I begin to input your commands, after the third command, magic thing happened, my network reconnected!!! and it never disconnects even after restarting.

By "third command", do you mean "lsusb"? Then yes, all the four commands, including this one in the first set are only informative. They don't do anything other than spitting out some info that we are interested in.

I suggest you post the outputs of all four anyway, so we can see if you have one of those cards/drivers which have any known issues, with known fixes possibly.

---

