---
title: "network sniffing tool"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by Tex-Twil on 2007-05-04
Hello,
I'm looking for a sniffer with **GUI ** for linux that can  sniff http, pop3, imap, ... traffic and capture passwords.

i.g. :
[http://www.nirsoft.net/utils/password_sniffer.html](http://www.nirsoft.net/utils/password_sniffer.html)
[http://www.effetech.com/sniffer/](http://www.effetech.com/sniffer/)


thanks you.

---

### Post by tcarradine on 2007-05-04
try Ethereal


Tim

---

### Post by jrusso2 on 2007-05-04
Whats wrong with wireshark?

---

### Post by Tex-Twil on 2007-05-04
yes I know ethereal (wireshark) but what I want is a more easy to use interface. For example for the chat sniffing a tool that capture only chat protocols.

---

### Post by ohioboy757 on 2007-05-04
dsniff does not have a GUI and has more uses other than just sniffing password/protocols but it can be used for this.  But it sounds like you want the most gain for the least effort and this may require effort.

---

### Post by Tex-Twil on 2007-05-05
Hi,
yes I also found dsniff. It's seems pretty powerfull but I cannot make it work properly: I have a open wifi network but  dsniff detects only traffic going to **my** pc. Not traffic going from my other PC to the internet. It seems like it is **not** working in primiscuous mode. Wireshar running in the same time detects other traffic properly.

---

### Post by ohioboy757 on 2007-05-05
I have only used dsniff on a wired network.  I am not sure if dsniff works properly with wireless.  A workaround is to use some of the other features in dsniff implements to spoof the gateway MAC address to redirect all traffic to your system and use IP forwarding from your system to the original gateway.

---

### Post by ohioboy757 on 2007-05-05
Another option is to save the traffic with Wireshark than run the capture file thru dsniff offline.

---

### Post by Tex-Twil on 2007-05-05
Well, capturing with wireshark and then reading a file is a possibility but it's a kind of "offline" sniffing.

ARP poisoning would also be a solution but it is too noisy :) Wireless network is like a hub so it should be simple.

Maybe are threr other tools ?

---

