---
title: "Wireless problem, HP Stream"
date: 2016-03-07
forum: Networking &amp; Wireless
---

### Post by gackthugo on 2016-03-07
Hello to all in the community,

I have this same problem but in a HP Stream with the same wireless card.
The commands provided above >  echo "options rtl8723be swenc=1 fwlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8723be.confecho 'KERNEL=="wlan0", RUN+="/sbin/iwconfig wlan0 txpower 18"' | sudo tee -a /etc/udev/rules.d/75-wlan.rules will work in mint 17.3 or a new log is needed?

Thanks in advance.

---

### Post by Bucky Ball on 2016-03-07
*Post moved to own thread.*

Welcome. The issues are rarely the same. To begin, you are not using the same machine as the OP in the thread you originally posted on.

By all means, keep an eye on that thread and take and give where appropriate, but you'll have much better chance of support on your own thread (and it avoids the confusion of attempting to deal with two users issues on the same thread, among other reasons for not posting your issue on an already started thread.)

Please see the wirelessinfo link in my signature, run it, and post the output between code tags (link in my signature). Thanks.

---

### Post by gackthugo on 2016-03-08
Sorry for posting in the wrong thread, should have created a new one.
Anyway, the info you asked is in the attachment.

Thanks for the help.

---

### Post by gackthugo on 2016-03-10
Any help please?
Is the info in the attachment usefull?

Thanks

---

