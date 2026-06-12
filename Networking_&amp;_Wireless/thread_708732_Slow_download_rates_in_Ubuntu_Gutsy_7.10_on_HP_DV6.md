---
title: "Slow download rates in Ubuntu Gutsy 7.10 on HP DV6775US"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by Ken2527 on 2008-02-26
Hi All and thanks in advance for any help extended to me.  I am somewhat of a Linux Noobie, but I am learning more and more each day.  I have a brand new HP Pavilion DV6775US laptop with the following specs: Intel Core 2 duo, 3 Gigs ram, Nvidia graphics card.  I have a cable broadband connection that allows for 6Mb connection using Vista.  I have a dual partition with Gutsy and have been able to install everything in Ubuntu without a hitch.  My only problem is the extremely slow download rates that I am experiencing.  This laptop has an Intel Pro wireless 4965AGN card.  I have read and followed all of the forums for slow internet connectivity that I could find in these forums and nothing is working.  Below are the steps I have taken:

1. Disabled IPV6 both in about:config in Firefox and by editing /etc/modprobe.d/aliases with alias net-pf-10 off

2. Updated DNS with Open DNS entries in Network Manager; 208.67.222.222, 208.67.220.220

3. Updated libc6

4. Tried using ndiswrapper with windows driver instead of iwl4965

Also as a side note I also tested connection with a LAN cable and the internet and downloads still performed very poorly.  In Vista I normally download files at around 500Kb/s - In Gutsy my download rate is topping out at 30Kb/s.  I am really at a loss for what to try next - Any help from the experts in these forums would be greatly appreciated. I am quickly becoming a Linux fan and fixing this issue would help me immensely.

---

### Post by fedex1993 on 2008-02-27
are you talking about like updates are slow downloading. ONe reason why the downloads might be slow is the mirror that your on. It could be there are alot of users on the mirror or a bandwith restruction on the mirror it self

---

### Post by Ken2527 on 2008-02-27
No it isn't just downloads from the download repositories it is downloads from anywhere. I downloaded the same file in both Vista and Gutsy to compare download rates - In Vista I downloaded at 550Kb/s in Gutsy it downloaded at 25Kb/s.

---

