---
title: "ubuntu server and Vbox"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by andyux on 2010-07-14
I need to install server LAMP to run an application for a client. Since i wont use this much but would need to start it quickly when the client calls, i thought it would be nice to have it virtualbox (on my vista laptop),. Would a LAMP configuration work ok on Vritualbox? Just for testing purposes to run locally, i dont need to "serve" anything online on that system.
Thanks

---

### Post by bodhi.zazen on 2010-07-14
> **andyux said:**
> I need to install server LAMP to run an application for a client. Since i wont use this much but would need to start it quickly when the client calls, i thought it would be nice to have it virtualbox (on my vista laptop),. Would a LAMP configuration work ok on Vritualbox? Just for testing purposes to run locally, i dont need to "serve" anything online on that system.
Thanks


yes you can do this easily with VBox (or KVM or VMWare).

---

### Post by Hanzerik on 2010-07-14
I have used VMWare and VBox. Currently only using VirtualBox as it fits my needs. I don't run a "Server" VM, but do use it for a Debian Desktop that I keep some Apps running on 24/7. But the same principle applies to a VM Server. My "Server" is a slow machine in todays standards so I use it to serve natively instead of having multiple VMs running.

I use it on a headless server, and run the VM in VRDP (Headless) mode. I can either ssh into the VM or use RDP to connect to the desktop.

I love Virtualization for the flexibility of it all. Have one machine hosting anything from Linux/Windows Desktops, to Domain controller, exchange/email server, webservers. Or even a firewall/proxy for your network. The possibilities are endless.

---

### Post by Old_Grey_Wolf on 2010-07-14
Virtualbox OSE is licensed under GPL; however, it has some limitations. You may be able to do your work with the limitations. You need to find out what they are, and how they may affect you. Virtualbox PUEL is better; however, it is for personal use. It seems you would be wanting to use it for a business. You can pay for Virtualbox as well. 

Here is a link to their licensing FAQ...[http://www.virtualbox.org/wiki/Licensing_FAQ](http://www.virtualbox.org/wiki/Licensing_FAQ)

---

### Post by JKyleOKC on 2010-07-15
Here's a clip directly from question 6 of that license FAQ link (emphasis added by me):

"Personal use is when you install the product on one or more PCs yourself and you make use of it (or even your friend, sister and grandmother). **It doesn't matter whether you just use it for fun or run your multi-million euro business with it.** Also, if you install it on your work PC at some large company, this is still personal use. However, if you are an administrator and want to deploy it to the 500 desktops in your company, this would no longer qualify as personal use."

This is one of the most impressive things, to me, about VBox. I've never seen such an explicit explanation of "personal use" in any other license!

---

### Post by andyux on 2010-07-20
Thanks all for your time and replies-

---

