---
title: "Jammy constantly roaming between APs and loosing sessions"
date: 2023-09-30
forum: Networking &amp; Wireless
---

### Post by jensk on 2023-09-30
I have a 22.04 Jammy that have problems with my wifi network. The problem is that within 1 - 2 minutes it roams to the other AP on my network. This even though the existing wifi connection is better or equal to the new connection. This affects many things like ssh sessions that dies, lost connections in Jitzi meetings etc. very irritating. The Jamy pc is a Dell XPS. I have tried reinstaling Jammy, but the faulty roaming behavior is still there.

My network consists of two Unifi UAC AP pro connected to a Edgerouter lite router. Other devices phones or windows pc's on my network doesn't show this constant roaming behaviour.

I have tried to turn power management off but the problem persists.

How do i tell NetworkManager to only roam between APs when the existing connection to the present AP is bad?

---

### Post by praseodym on 2023-10-02
Add the MAC address of the AP you want to connect to into the "BSSID" field of the network manager profile. Check if WPA2 only is activated and no WPA/WPA2 mixed mode

---

### Post by jensk on 2023-10-09
I have found a solution - maybe the solution. Aparently my Jammy install constantly was trying to switch to IP v6. It had the effect that the Ip v4 connection was constantly renewed and that the dhcp server (my UBNT Edgerouter Lite) gave a new Ip adress each time the pc retuned to IP v4 after not getting any replies on IPv6 dhcp requests.
I set the network manager connection to my wifi to have IP v6 disabled and the problem disappeared.

---

### Post by jensk on 2023-10-09
.

---

