---
title: "Windows XP in VirtualBox - Security Considerations"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by JBA2337 on 2009-07-09
I recently installed VirtualBox into Ubuntu, and I am running Windows XP in the VirtualBox. Since I am runing Windows XP inside of Ubuntu, does Windows XP still have the usual security problems, i.e. virus vulnerability, adware & spyware threats, activex exploitation,etc.; or, does being inside Ubuntu give extra protection to Windows XP? Should I still run the usual scans for viruses, adware, and spyware in Windows XP. Should I install a software firewall in Windows XP?

JBA2337

---

### Post by XCan on 2009-07-09
Windows will have its usual security problems. Unless you use Ubuntu to block it from the internet, for example, Ubuntu won't give any extra protection.

---

### Post by evermooingcow on 2009-07-09
You probably don't need a software firewall if you run it in a NAT. You could rely on the firewall of the host OS.

Usual security measures are recommended if the virtual OS is important to you. If VirtualBox has a snapshot or similar feature you could alternatively have the install always revert back to its fresh state everytime you boot up. You could save all settings that you want to keep to a shared folder on the host OS.

---

### Post by niteshifter on 2009-07-09
Hi,

It depends. What will the XP Guest be used for? If it's going be like a regular XP install: handling email, IM, surfing the web, etc. - then yes, it needs all the patchwork (antivirus). If XP's networking setup is NAT with Vbox you could probably skip the firewall, as that NAT is hiding the XP machines IP address. If the setup is Host Networking then a firewall is needed.

If XP's there just for some particular software with no or minimal Internet exposure (no email, IM, minimal surfing) - then no, it doesn't need all the patchwork.

One can use the "snapshot" feature of Virtualbox to keep a clean copy or you can just copy the .vdi file out of ~/.VirtualBox/HardDisks after setting it up. Refresh the copy / make another after Windows updates.

---

### Post by superprash2003 on 2009-07-09
its better to have a firewall+antivirus installed

---

### Post by donkyhotay on 2009-07-09
Depending on what you use it for you can just set it up the way you want and create a snapshot so that if it ever gets infected you can just revert it back to the working point. Everything stored on it after the snapshot is lost of course but if you don't store anything important on the windows side it's not a problem.

---

