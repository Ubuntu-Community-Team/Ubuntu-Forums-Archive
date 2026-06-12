---
title: "Can't connect to wireless network"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by gnarkilljboy on 2008-05-03
I am trying to connect to my wireless network using ubuntu. I Installed ubuntu, but I can't figure out how to conect to my wireless network. It is installed on my laptop.

---

### Post by superprash2003 on 2008-05-04
on the top right corner.. you will find an internet icon(similar to the one in windows like a monitor).. click on it and you should see the available networks.. then click on the network and you should be connected

---

### Post by gnarkilljboy on 2008-05-04
The only one available is the wired network, no wireless. But it is a wireless laptop.

---

### Post by NIT006.5 on 2008-05-04
Have you checked to see if any restricted drivers need to be enabled? Under System->Administration->Restricted Drivers Manager.

If not, there might not be a Linux driver available for that adapter, in which case you will need to install ndiswrapper-common, ndiswrapper-utils and ndisgtk. You will then be able to use the windows driver.

---

### Post by gnarkilljboy on 2008-05-04
ok. How do I install those? do I have to use the terminal? I am new to ubuntu, not to familliar with the terminal.

---

### Post by NIT006.5 on 2008-05-04
No worries. The easiest is to do it through System->Administration->Synaptic Package Manager - if you search for "ndis" you should find those three packages listed.

Once done, you should be able to add the Windows drivers through System->Administration->Windows Wireless Drivers. You will obviously need the windows drivers on disc though - then you will just browse to them using that program. Browse to the INF file, and it should add the windows drivers. 

If that works ok, then you should now see a wireless connection in your network properties that you can configure.

---

### Post by gnarkilljboy on 2008-05-04
Ok, I can find the first 2, but not the one called ndisgtk.

---

### Post by NIT006.5 on 2008-05-05
Hi, sorry for the delay. I've checked and that's definitely the right package name.

It's possible that you need to enable universe software in your sources list since ndisgtk might not be supported by Canonical, so might not be present by default. You can do this under System->Administration->Software Sources. Check the option labelled "Community-maintained Open Source software (universe)". You might as well enable the restricted and multiverse options while you're at it. You will then need to update your package lists in Synaptic (click the Reload button) and search again.

Hope that helps.

---

### Post by gnarkilljboy on 2008-05-09
Thanks. I have it working now.

---

### Post by NIT006.5 on 2008-05-12
No problem, glad to be of assistance.

---

### Post by saikas on 2008-05-12
Hi, 
maybe you can help me too? I also cannot connect my WLAN card. and problem is that i cannot turn it on, becouse it go online by pressing on button, which need drivers and i looked in fujitsu siemens website, there is no drivers for linux  for my pc.
so maybe any thoughts

---

### Post by NIT006.5 on 2008-05-13
> **saikas said:**
> Hi, 
maybe you can help me too? I also cannot connect my WLAN card. and problem is that i cannot turn it on, becouse it go online by pressing on button, which need drivers and i looked in fujitsu siemens website, there is no drivers for linux  for my pc.
so maybe any thoughts

Which "on button" are you referring to? Is this something you see in Windows? If so, then it's not important - you won't see the same thing in Ubuntu.

If you can't find Linux drivers for your adapter, then you should be able to use the Windows drivers via ndiswrapper - as per my previous posts on this thread.

---

