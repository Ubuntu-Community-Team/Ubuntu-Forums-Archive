---
title: "Firestarter Problem"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by Aiello on 2008-02-10
I have just installed Firestarter and I am seeming to have some problems with it. I am using a desktop computer connected my wireless network, (the type of wireless card is a RangeMax Wireless PCI Adapter WPN311 if that helps at all). When I start Firestarted I get this error message: Failed to start the firewall. The device wifi0 is not ready. Please check your network device setting and make sure your Internet connection is active. Any suggestions on what to do? 

-Thanks!

---

### Post by pvrsnarayana on 2008-02-10
Firestarter shows settings only for the connected Network device in Preferences->Firewall->Network settings.  Select the appropriate interface in firestarter preferences and try.

---

### Post by Aiello on 2008-02-10
The only options I can select are Ethernet device (eth0), Unknown device (wifi0), and Uknown device (ath0). Which one of these should I select? Sorry if these questions are kind of basic, but I litterally just started using Ubuntu and Linux.

---

### Post by pvrsnarayana on 2008-02-10
Select the interface which connects to your wireless network.  you can check that using ifconfig

---

### Post by Aiello on 2008-02-10
After running ifconfig in the terminal, how do I know which one I am using?

---

### Post by Aiello on 2008-02-10
Well, I have switched my preferences to ath0. When the firewall starts, it says there is an error, but it starts anyways. It says : An unknown error occurred. Please check your network device setting and make sure your Internet connection is active. Even though it appears that the firewall starts, is it actually protecting my computer?

---

### Post by pvrsnarayana on 2008-02-11
You can check for the interface which has a valid ip address and the tx and rx packet counts.  firestarter is just a gui for the iptables to configure it, so even though it does not show up it is actually protecting your computer.

---

