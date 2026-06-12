---
title: "RDP or VNC"
date: 2023-03-09
forum: Networking &amp; Wireless
---

### Post by monike on 2023-03-09
Hello, I'm trying to choose a way to connect to a remote computer. I need access to Windows from Linux. 
I'm not very good at this topic, which method is better for me RDP or VNC? 
I would be grateful for your help.

---

### Post by TheFu on 2023-03-09
> **monike said:**
> Hello, I'm trying to choose a way to connect to a remote computer. I need access to Windows from Linux. 
I'm not very good at this topic, which method is better for me RDP or VNC? 
I would be grateful for your help.

It depends.  But lacking any information, assuming you have a high-enough level of Win11 to have RDP built-in, then RDP with all the security possible would be better.  I don't know if the Linux RDP client can connect.

I'd never use either if going over the internet.  They are both very commonly cracked methods to gain access not just to the other system, but to the entire LAN.

Now, if you are running Windows under a libvirt/KVM virtual machine, then there are other, better, options thanks to SPICE over SSH and SSL, but you didn't mention that.

---

### Post by kattrin on 2023-03-10
Hi! In your case, you can choose any of these methods. VNC is platform agnostic and will run across all typical operating systems and the limitation on RDP is that the server software is only compatible with the Windows operating system but clients can be run on all common operating systems. 
But they have a different principle of data transfer, so a lot depends on how you want to use and what you want to do on the remote desktop. I would advise you to read this article [https://www.helpwire.app/blog/vnc-vs-rdp-protocol/](https://www.helpwire.app/blog/vnc-vs-rdp-protocol/) where the differences and scenarios for using each option are described in great detail.

---

### Post by DuckHook on 2023-03-10
*Thread moved to **Networking & Wireless** as the more appropriate forum.*

When posting, please use standard styles and fonts. Nonstandard formatting is hard to read on small screens or for those with vision restrictions.

---

### Post by securitydad on 2023-03-13
Great resource that explains the difference with RDP and VNC.  KNow that TeamViewer is a VNC user is what I needed to know.

---

### Post by naufrsb on 2023-03-16
hey!

If you are primarily accessing a Windows machine from a Linux computer then RDP will be much better. But if you need to access different systems and platforms, VNC (being platform-agnostic) will be the more versatile option for you.

I hope that helps!

---

