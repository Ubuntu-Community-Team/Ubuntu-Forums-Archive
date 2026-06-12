---
title: "Wireless Network Idle"
date: 2005-09-01
forum: Networking &amp; Wireless
---

### Post by ContinuumXLS on 2005-09-01
Hey, 

I installed ubantu on my laptop yesterday (now a dual boot with windows xp pro) (hp pavilian 17'' widecreen), and everything seemed to go fine. This morning when I started up the computer, it would not connect to the internet. I opened up the network admin, re-checked all of the settings, and looked at the connection status - It jumps back and fourth between idle and Sending/Recieving...The thing is, I can still get onto the internet when I log onto windows. I have a wireless router, and I did configure the settings correctly seeing as it worked lastnight...Is there anything I can do to fix it?

(if you need more info just let me know - I am also a new linux user, so if you need me to do anything, could you please explain how to do it? thanks!)

---

### Post by phen on 2005-09-01
if your laptop is a centrino system, you could try an update of ipw2200 firmware and module.

i dont remember the link, but you can find it by:  go to the ubuntu.com wiki, check for hp laptop support, find hp nc6120. there's a link provided. (the thread about updating the driver is not hp specific, but it was needed for this laptop, too)

if your pc is not using a centrino chipset, you should open a terminal (right click the desktop) and type:

```

lspci
iwconfig
ipconfig

```

post the wireless specific output of all three tools. maybe a "lsmod" could help as well..

---

### Post by ContinuumXLS on 2005-09-01
Thanks for the help!

The laptop is a centrino, so I will go and download the patch and post the results here! Thanks!

---

