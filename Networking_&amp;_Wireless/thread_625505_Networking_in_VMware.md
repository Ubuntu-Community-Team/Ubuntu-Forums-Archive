---
title: "Networking in VMware"
date: 2007-11-28
forum: Networking &amp; Wireless
---

### Post by JaggedOne on 2007-11-28
I just installed VMware and windows XP on top of it. How do I get networking set up? As of right now I have zero connectivity in my virtual machine. I am running ubuntu 7.10 and am connected over wifi.

Thanks.

---

### Post by mark-mlt on 2007-11-28
Hi, im new to ubuntu and to this forum aswell. I installed ubuntu on vmware workstation and im having problems regarding the internet connection. Any help pls on how to set a wired connection? 10x :)

---

### Post by veloce on 2007-11-28
> **JaggedOne said:**
> I just installed VMware and windows XP on top of it. How do I get networking set up? As of right now I have zero connectivity in my virtual machine. I am running ubuntu 7.10 and am connected over wifi.

Thanks.

You set up networking as you install vmware, what did you set up?

Be aware that vmware doesn't bridge wifi out of the box.  There is a work around - I saw it in this forum somewhere, try searching for vmware wifi network.

---

### Post by JaggedOne on 2007-11-28
I solved the problem myself. Perhaps my method can help mark as well. Go to the settings for your virtual install. Set the ethernet network connection to NAT. 

This sets up your virtual install to share the same IP address and internet connection with the host machine, so if the host is connected, the virtual install is also connected.

---

### Post by mark-mlt on 2007-11-29
yep i all ready tried NAT but it didnt work :/

---

