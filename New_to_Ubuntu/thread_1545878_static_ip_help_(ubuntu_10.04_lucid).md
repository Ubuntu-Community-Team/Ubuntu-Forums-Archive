---
title: "static ip help (ubuntu 10.04 lucid)"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by Austischke on 2010-08-04
i'm trying to set up a static ip address for my laptop, but i don't know how. Instructions please? And i'm BRAND new to computers. so elaborate, or just keep it simple

---

### Post by NoBugs! on 2010-08-04
Right click the network-manager panel icon, go to "Edit Connections" and select the one you want to change. Click Edit, and under the IP Settings tab you'll see it's set to Automatic(DHCP). Change that to Manual and you can set the address.

---

### Post by ubudog on 2010-08-04
Right click on the wireless icon.  Click on "Edit Connections".   Then click on the "Wireless" tab.  Choose your network and click the Edit button.  Click on the ipv4 tab.  Change the drop down list from DHCP to Manual.  In the settings, change the Address section to your desired ip address, the netmask to 255.255.255.0, the gateway to 192.168.1.1 (that is the most common gateway, but could be different).  Change your DNS servers to whatever you want.  I prefer [OpenDNS.]("http://www.opendns.com/")  Then reboot, and everything you should have a static ip address.

---

### Post by Austischke on 2010-08-04
sorry, but new problem, I've no idea about what to do with the netmask or the gateway, this absence of knowledge includes what they are, where to find them, what to do with them, and what to type in. Please help, my dad says to look at the info provided from the router to the pc, through the dhcpz ????!!!!!

---

### Post by joereith on 2010-08-04
edit the wired connection.Open terminal and type ifconfig. Look for the ipv4 address for eth0 interface. Click the add button next to where it says addresses and if your ip is 192.168.1.* for eth0 make one up for address like 192.168.1.201 subnet is 255.255.255.0 and gateway would be 192.168.1.1.

---

### Post by Austischke on 2010-08-04
sorry for changing this so much, but I've found and set IP, mask, and gateway, so now i just need to know what to do with the DNS server section. where and how do i find it?

---

### Post by joereith on 2010-08-04
lookup opendns and copy the server addresses. I think that they are 208.67.222.222 and 208.67.220.220

---

### Post by Austischke on 2010-08-04
are you required to have to dns addresses? cuz i have a dns address and everything else filled out, but it won't let me apply the IP address.

---

### Post by oldfred on 2010-08-04
My dns server in Ubuntu is 192.168.1.1 or the router. The actual DNS addresses are set up in the router and it is using DHCP to connect to comcast and auto finds the dns addresses.

---

### Post by Clever_Username on 2010-08-05
Opendns primary and secondary IP's are:

[LIST]
[*]208.67.222.222
[*]208.67.220.220
[/LIST]

---

### Post by Clever_Username on 2010-08-05
> **oldfred said:**
> My dns server in Ubuntu is 192.168.1.1 or the router. The actual DNS addresses are set up in the router and it is using DHCP to connect to comcast and auto finds the dns addresses.


Sorry, I just read your last post. I believe it should say that for your DNS servers if your on a router. I know my connection does.I wouldn't think you would need to change those settings though. I mean most times one DNS server is as good as another. 
But you might consider waiting for a more experienced person to back my statement up. I'm still pretty new.

---

