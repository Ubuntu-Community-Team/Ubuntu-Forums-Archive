---
title: "Intel Centrino Wireless N-1000 hard-blocked"
date: 2018-05-26
forum: Networking &amp; Wireless
---

### Post by xawery87 on 2018-05-26
I've just installed Ubuntu 18.04 LTS on my Lenovo Ideapad Z570. Sadly, WiFi isn't working, even though it did during installation. My Intel Centrino Wireless N-1000 card seems to be hard-blocked, despite the hardware switch being set to "on". I've run dmesg, lsmod, lspci and rfkill and pasted the outputs here: [https://pastebin.com/S4JWxb4H](https://pastebin.com/S4JWxb4H) 

EDIT:
On the LiveCD everything is working fine. The output of lspci is the same as expected. Rfkill doesnt show any hard-blocks. I've pasted the output of dmesg and lsmod [here]("https://pastebin.com/x17KZUTk"). The modules: dm_mirror, dm_region_hash, dm_log, isofs, nls_utf8, overlay, uas and usb_storage are loaded on the LiveCD, but not on the installed system.
Any ideas, why wireless networking isn't working on the installed system?

---

### Post by jeremy31 on 2018-05-27
*Thread moved to **Networking & Wireless**.*

---

### Post by praseodym on 2018-05-27
Please run
```

echo "blacklist ideapad_laptop" | sudo tee /etc/modprobe.d/blacklist-ideapad.conf
```
and reboot

---

### Post by xawery87 on 2018-05-27
Thanks for replying, praseodym. Unfortunately blacklisting the ideapad_laptop module did not help. Here's the [dmesg]("https://pastebin.com/Hf79e4pg"), just in case. I've also tried blacklisting the acer_wmi module before (did not work) and restoring BIOS default configuration (it has worked for some people on the forums, but not for me).

---

### Post by jeremy31 on 2018-05-27
Does the switch position change the results of rfkill list?

---

### Post by xawery87 on 2018-05-27
The WiFi card is hard-blocked, but not soft-blocked, regardless of the switch's position

---

### Post by jeremy31 on 2018-05-27
I think the switch might be broken and you should see [https://www.youtube.com/watch?v=yzAKcmlaH1M](https://www.youtube.com/watch?v=yzAKcmlaH1M)
It shows how to unblock wifi using a piece of tape

---

### Post by xawery87 on 2018-05-28
I am not really convinced, that it's a hardware issue. Here's why:
1) WiFi is working out of the box on the LiveCD. I'm sorry for not stressing that properly. That's in fact, how I posted on this forum before I found an Ethernet cable.
2) I've found an USB network adapter which also was turned off according to GNOME (no hardblock however).
3) The adapter suddenly started working after I unloaded iwlwifi.
Therefore I think it's the software causing the problem (conflicting kernel modules or something?). What do you think? I am grateful for the "Pin #20" advice, but I think of opening my computer and tinkering with it as a measure of last resort.

---

