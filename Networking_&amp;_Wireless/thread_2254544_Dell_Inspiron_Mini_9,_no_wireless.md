---
title: "Dell Inspiron Mini 9, no wireless"
date: 2014-11-27
forum: Networking &amp; Wireless
---

### Post by Gary100 on 2014-11-27
I have a dell Inspiron Mini 9 Netbook, and I've happily been running ubuntu 12.04 for some time. I made some kind of major screw-up, and I thought the easiest thing to do would be to reinstall completely from USB, which I did. Now, while I can connect to internet via ethernet plugin cable, I can't connect via wifi. When I hit the networking icon, there is the usual "check" next to "Enable Networking"

Can anyone help me get back wifi?

Gary

---

### Post by Bucky Ball on 2014-11-27
While online with a cable, do an update and then check 'Additional Drivers' (maybe Hardware Drivers in your Ubuntu). Anything there?

---

### Post by Gary100 on 2014-11-28
I let it take me through the whole "update process." There was no mention of "additional divers", but there was a message about drivers, not free, from a third party. The offer now seems to have vanished. At first, it appeared as an icon next to the "mail" icon. The update also updated my hardware profile. Where can I find that driver offer again? Can it be that the supplier of my computer installed some drivers I need to pay for?

---

### Post by Bucky Ball on 2014-11-28
'Additional Drivers' is in the Settings menu. I'm unfamiliar with Unity, but if you do a search for it in the dash (that is the way to do it?) you will find it. If it made the offer of available drivers, that is where you will probably find the option.

You could also log out and back in or restart and see if it is offered again, but it's looking good so far.

---

### Post by Hadaka on 2014-11-28
Hi, please show us the output of..
```
lspci -nn | egrep '0200|0280'
lsmod | egrep 'wl|b43'
rfkill list all
```
thanks.

---

### Post by Gary100 on 2014-11-28
@Buckyball
I panicked, so I'm not sure what my actual steps were, but I stumbled on an option to install something like - Broadcom STA Wireless Driver - and that seems to have done the trick, wireless is back. You set me on the right path, so THANKS!

@Hadaka
I think I'm going to quit while I'm ahead! But thanks to you, too for your input

You two made my day, so thanks again, both

---

### Post by Bucky Ball on 2014-11-28
Great news! Please mark thread as solved (you can follow the second link in my signature for how) to help others. Good luck and enjoy. ;)

---

