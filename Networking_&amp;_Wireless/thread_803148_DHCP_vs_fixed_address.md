---
title: "DHCP vs fixed address"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by tonymoloney on 2008-05-22
I live in a retirement village in Perth, Western Australia where I am president of the computer club.
Due to limitations on our PABX and cabling within the village, our broadband service comes in via two dedicated phone lines and is then distributed around the village by wireless.
Each home in  the village that is connected has an aerial in the roof space feeding a wireless access point, which then goes via cable to the RJ45 port in the computer.
At present most (but not all) of the systems are set up as DHCP, but our network administrator wants to change them all to fixed addresses for some reason that I don't follow.
Has anyone got a comment on this?

---

### Post by Peter09 on 2008-05-22
DHCP is a better way of handling IP addressing, however unless we have more details as to why your admin whats to go that way its difficult to comment.

PC

---

### Post by tonymoloney on 2008-05-22
As I said, I don't really understand what he's talking about, but next time I see him, I'll try to get him to explain in words of one syllable:)

---

### Post by Iowan on 2008-05-22
Maybe he thinks it's better security if IP addresses are "registered"? My opinion (for what it's worth) is that DHCP would be easier to manage, and no less secure.

---

### Post by Peter09 on 2008-05-22
Hi Iowan,
yes this did cross my mind, I wondered whether he was is getting strangers camping onto the wireless network. Most probably the security of the encryption keys are not good (people talk).

PC

---

### Post by hyper_ch on 2008-05-22
dedicated IPs make it simpler to tune services and limits for specific machines and identify them.

Furthermore from a point of liability you also might want to know who everyone is at a given time.

---

### Post by rickyjones on 2008-05-22
> **hyper_ch said:**
> dedicated IPs make it simpler to tune services and limits for specific machines and identify them.

Furthermore from a point of liability you also might want to know who everyone is at a given time.

That would be my purpose for assigning static IPs but I wouldn't do that manually. DHCP has a lot of great uses. I'd create DHCP reservations for each system so I can track usage and keep everything simple.

-Richard

---

### Post by Iowan on 2008-05-22
IIRC, DHCP allows assigning "static" leases based on MAC address (still not impossible to spoof, but neither are IP addresses).

---

