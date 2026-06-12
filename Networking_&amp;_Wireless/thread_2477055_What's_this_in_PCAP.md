---
title: "What's this in PCAP?"
date: 2022-07-13
forum: Networking &amp; Wireless
---

### Post by xisom on 2022-07-13
I've bought a Bluetooth Chinese keyboard recently. I sort of feel like my computer has been acting funny since I started using the keyboard. It may very well be nothing but I want to make sure that's not the case for the heck of it. I performed a PCAP via Wireshark and I came across this:

[IMG]https://i.imgur.com/AYYYsvq.png[/IMG]

Sorry but I'm not tech savvy. What does this mean?

---

### Post by &amp;KyT$0P# on 2022-07-13
All that screenshot shows is that those were the 21st and 22nd packets captured, that they were captured 11.26... seconds after starting the Wireshark capture, and the first part of the MAC address involved for each packet.  And that background color, and the use of MAC addresses instead of IPs, suggest those might be ARP packets, maybe?  But all that is not enough information to be sure what those packets mean.

Could you please share the full lines? (You might want to obscure the last portion of MAC addresses, and any potentially-identifying parts of IP addresses if you know what devices the IP addresses belong to.)

---

