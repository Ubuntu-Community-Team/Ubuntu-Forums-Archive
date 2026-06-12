---
title: "Slow network experience"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by PietKiwi on 2007-10-22
I'm experiencing a slower than normal network connection. I run Ubuntu 7.10 and I have a gbit NIC. Connected to a gbit netgear and also connected to this netgear a gbit NAS. When I start an FTP session with filezilla I get around 5 MB/s. When I copy a file from one folder to another it takes up to 20 minutes to copy 4 GB (ISO). This is about 3.5 MB/s. I think this is slow and I would expect more of it.

I googled around and turned off IPV6 in my /etc/modprobe.d/aliases but that didn't make a difference. 

Everything is connected at 1000mb full duplex and I don't see any errors.

Does anyone have any idea?

Thanks in advance...

---

### Post by PietKiwi on 2007-10-24
I guess there is no linux network guru that can help me tweak my network?

---

### Post by slowcoach on 2007-10-24
This is an ongoing problem, there is no answer yet. 
Gigabit LAN on Debian is many times faster than Feisty and Gutsy for some reason.

---

### Post by lapsey on 2007-10-25
No kidding: I have the same specs as the OP and I'm getting **10-Mbit** speeds, never mind Gbit or 100-mbit.

Seriously, 2 Gb took about 7 hours to transfer over this interface!

i feel sorry if you have Gigabit ethernet and have to buy a 10/100 card (I have several to use until this is fixed so thank goodness)

---

### Post by PietKiwi on 2007-10-26
I am glad that it's a known issue!

Any idea how I can keep track of a bugfix? I am relatively new to ubuntu...

I forced my gbit card into 1000mbit with ethtool but it just sucked bigtime. I now plugged back to my 1st NIC, a 10/100 onboard NIC and I think I need to reboot because it keeps crashing when I connect to my NAS... :(

---

### Post by PietKiwi on 2007-10-26
I think the reboot helped. My speed is still 20 minutes for a dvd iso but at least now I know that I am connect at 100mbit :)

---

