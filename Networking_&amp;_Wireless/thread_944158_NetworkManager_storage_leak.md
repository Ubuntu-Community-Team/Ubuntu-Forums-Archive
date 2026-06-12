---
title: "NetworkManager storage leak?"
date: 2008-10-11
forum: Networking &amp; Wireless
---

### Post by gribnick on 2008-10-11
My configuration is that I have a wireless (edimax) connection to my satellite internet and a wired connection to a hub of other local computers. My computer stays up for days at a time. Oddly enough, I am NOT having any connection problems. My problem is that NetworkManger is a storage pig and keeps growing.

Shortly after a reboot, NM (as reported by top) has about 9MB virt and the same resident. After 4 days, it has about 70MB virt and 46MB resident. After 10 days, it has 350MB virtual and 160MB resident. I used to do as much as several months between reboots but with this being a smaller system, I can no longer do that as NetworkManager takes over.. :confused:

I do not see this happening in other wired-only systems. One other piece of info is that there are TWO wireless networks in the immediate vicinity. A box sitting right next to this one is talking to a different network. Could interference be causing some issues?

---

