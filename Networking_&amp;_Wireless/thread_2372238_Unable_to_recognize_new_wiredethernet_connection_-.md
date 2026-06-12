---
title: "Unable to recognize new wired/ethernet connection - xubuntu 16.04"
date: 2017-09-22
forum: Networking &amp; Wireless
---

### Post by zarkon32 on 2017-09-22
Hello, all. Fairly new ubuntu user here, decide to stuff the entirety of windows, haven't looked back.

I've recently gotten hooked up with a new connection with the ISP I'm working for at the moment. I don't have the correct kind of router (mine's DSL i.e. not for a cabled connection), so I'm using my other, old connection via an old router to access the internet.

For whatever reason, despite all cables being plugged in correctly and no damage to any of the cables whatsoever, xubuntu's not recognizing the new dish/connection. To clarify, I'm trying to connect to the new unit outside via cable (via the PoE box) straight from the dish outside. The ethernet port on my laptop normally lights up white when it recognizes an ethernet connection (like when I plug an ethernet cable from my old router into my laptop), but is not doing so in this case.

[http://paste.ubuntu.com/25594240/](http://paste.ubuntu.com/25594240/)

I've tried creating a new ethernet connection in Network < Edit Connections, using the mac address supplied with outside unit -  it's (the outside unit/connection) also configured to automatically provide dhcp settings. 

Any ideas where to start?

---

### Post by SeijiSensei on 2017-09-22
First, run the command "lspci" so we can see what adapters are recognized by the system.  On my system, I get (among others)
```

00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-V (rev 05)

```

---

### Post by zarkon32 on 2017-09-23
Output of lspci, specific to ethernet: 
```
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 07)
```

---

### Post by SeijiSensei on 2017-09-23
A Google search indicates that lots of people seem to be having trouble with that device.  The final post in this thread suggests a solution, but it's complicated.

[https://askubuntu.com/questions/770368/realtek-ethernet-driver-error-ubuntu-16-04](https://askubuntu.com/questions/770368/realtek-ethernet-driver-error-ubuntu-16-04)

---

### Post by zarkon32 on 2017-09-23
The answer to that has been very helpful. I've managed to get the new drivers installed, and rebooted my laptop after that. The (new) ethernet connection still did not show up in network manager

I've now encountered a new problem, wherein ifconfig no longer shows enp3s0, which I've now learned is my ethernet NIC. Trying to add either a random MAC address or the actual MAC address of my outside unit/dish gives me SIOCSIFADDR: No such device.

After reading a similar article to the one Seiji posted ([https://unixblogger.com/2016/08/11/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/](https://unixblogger.com/2016/08/11/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/)), I'm going to reboot again and see if ifconfig shows me my NIC.

Edit: No luck, have tried adding it in /etc/network/interfaces, still does not show up in ifconfig.. looking on how to get it back

---

