---
title: "Cant always access Ubuntu 14 from local network"
date: 2015-05-14
forum: Networking &amp; Wireless
---

### Post by Andrew_Welham on 2015-05-14
Got a really strange issue. I'm running Ubuntu server 14.04 as a Virtualbox VM, which is hosted on windows 7.
I've got no issues connecting to devices on the network or on the internet, but I do have issues connecting to the server from the clients, on any port.
Yes its sound like a firewall issue, but its not as if I ping the client from the ubuntu server I can then connect to the server from the device (in most cases) on any port(which is open) currently 22, 80,443
So I have ruled out firewall issues and have been looking at ARP  / routing issues, all looks ok. I have also moved the VM from server to another and this has caused the MAC to change. Looking on the clients they all appear to have the correct arp entries. Up until yesterday I could access from the internet, but this appears to have stopped now from some devices.

Any ideas where to start?

Thanks

---

### Post by Andrew_Welham on 2015-05-14
Got a little further,
The reason is the arp broadcasts don't appear to be working , if pinging the client works  then the arp table is updated at both ends, or if the entries are added to the arp tables  manually on ubuntu server then it also works ok.
Any idea why the arp cache (which i have cleared down and refreshed) is not being updated properly

---

