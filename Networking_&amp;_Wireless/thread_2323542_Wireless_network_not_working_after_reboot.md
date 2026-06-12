---
title: "Wireless network not working after reboot"
date: 2016-05-06
forum: Networking &amp; Wireless
---

### Post by Catherine_Kerr on 2016-05-06
I have been using Ubuntu 14.04 on a Lenovo Idea-pad flex 15 laptop for the last two years (but I'm no expert). In the last few days, the laptop hung so I switched off and on again. Now I have three serious problems (in order of importance)

1. The laptop no longer connects to the network.
2. If I shut the lid and then open again, the laptop doesn't wake up and I have to turn off an on again.
3. My USB mouse no longer works.

I really need to solve the first problem, but I included the others as they may be related. When I click on the network icon, it says "No network devices available". If I try to restart the network manager, I get message "Disconnected - you are now offline"

I ran the wireless trouble-shooting script and output is [here]("http://paste.ubuntu.com/16253215/").
Any suggestions?
Thanks

---

### Post by jeremy31 on 2016-05-06
Welcome to the forums.  The kernel modules aren't loading, what happens if you try loading the wireless module manually using ```
sudo modprobe -v ath9k
```

A workaround for the 3 issues may be to boot to an older kernel.  When booting press SHIFT until the Grub menu appears, scroll down to Previous Linux Versions or Advanced Options, then pick an older kernel to boot to

---

### Post by Catherine_Kerr on 2016-05-06
Thanks very much for prompt response. On modprobe, I get "FATAL: Module ath9k not found"

Your suggested workaround worked though :D Even the mouse is working :cool:
I reverted to Ubuntu, with Linux 3.13.0-79-generic, rather than 0-83 which was the latest version installed.
Does this mean that there is a bug in 0-83 and will it be fixed in later version?

Thank you SO much for solving this for me. 
CK

---

### Post by jeremy31 on 2016-05-06
I think something got corrupted when it hung

---

