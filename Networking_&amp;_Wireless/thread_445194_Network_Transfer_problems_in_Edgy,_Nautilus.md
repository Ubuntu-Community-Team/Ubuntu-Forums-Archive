---
title: "Network Transfer problems in Edgy, Nautilus ?"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by decker on 2007-05-15
Ok, so here's the situation. 

Problem: I have bandwidth issues when trasnfering data between my Edgy laptop an other devices.

Scenario 1: Edgy SMB Server, i browse to it with my Edgy Laptop and transfer data. The data will burst as seen in the image and create horrible throughput issues. If i use my windows laptop, i can stream stuff, no problem.
   Symptoms: Nautilus starts hitting 40-50% utilization

Scenario 2: Same setup as S1, but i use SCP/SFTP/FTP, no problem, throughput is perfect. As long as it's not through nautilus

Scenario 3: I transfer from my Dlink NAS drive (SMB+FTP) to my Edgy Laptop OR Edgy Server and i get same issues with throughput.

Notes:
  - No iptables rules, everything is clean.
  - I have a Linksys SRW2008MP gigabit switch (changing switches makes no difference)
  - No errors on either network interface or any of the switch ports (managed)

Hardware:
  - Server: P4, 2GBram, intel 10/100 NIC 
  - Client: IBM T42p P4-1.5GBram and Dell P4m 1GB

My Guess:
  - Not a server issue since the windows client works fine
  - looks like there may be some issue with Nautilus throttling the data transfer somehow, can this be fixed?

[IMG]http://i46.photobucket.com/albums/f131/nicks2k/transfer.jpg[/IMG]

---

