---
title: "Lost in a tutorial..."
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by Gorromog on 2008-07-15
I recently downloaded Wubi to see how my computer will handle Ubuntu. The install went smooth and so far all I have been trying to do is to get me wireless card(WG311v3) working. I followed a tutorial on the Ubuntu hardware support site, and it seems to be incomplete. 

Tutorial I used
[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

Me being a complete noob to Linux, also have another problem. The "sudo modprobe ndiswrapper" line just asks for my password to proceed, and then nothing happens. Just typing in "modprobe ndiswrapper" or "ndiswrapper -m"(I guess that is not the same thing, but it gave me pretty much the same error message) tells me that I don't have permission to add it as a module to load (which is what I think that line is trying to get at)

If anybody needs more information to help me, please tell me. 

Thank you.

---

### Post by Gorromog on 2008-07-16
bump

---

### Post by dmizer on 2008-07-16
> **Gorromog said:**
> I recently downloaded Wubi to see how my computer will handle Ubuntu. The install went smooth and so far all I have been trying to do is to get me wireless card(WG311v3) working. I followed a tutorial on the Ubuntu hardware support site, and it seems to be incomplete. 

Tutorial I used
[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

Me being a complete noob to Linux, also have another problem. The "sudo modprobe ndiswrapper" line just asks for my password to proceed, and then nothing happens. Just typing in "modprobe ndiswrapper" or "ndiswrapper -m"(I guess that is not the same thing, but it gave me pretty much the same error message) tells me that I don't have permission to add it as a module to load (which is what I think that line is trying to get at)

If anybody needs more information to help me, please tell me. 

Thank you.

first of all, you would have been better off simply posting in the howto thread rather than creating your own.  that way, the people viewing the post have experience with the howto and are more likely to be able to help you.

in this case, the command "sudo modprobe ndiswrapper" should have no output. it's simply loading the module into the kernel so you can use it.  if you received no error message when performing this command, then it was performed successfully.  please continue to the next step in the howto.

edit:
if you're curious, you can confirm that the module was loaded into the system by looking at the output of the following command:
```
dmesg | tail
```

---

### Post by thegodfaza on 2008-07-16
From my experience ndiswrapper on ubuntu doesn't like to load at boot. So go ```
sudo nano /etc/modules
``` and add ndiswrapper to the list.

---

