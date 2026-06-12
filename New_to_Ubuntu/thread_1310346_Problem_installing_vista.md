---
title: "Problem installing vista"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by deanmilanov on 2009-11-01
Hi all!
Three days ago I downloaded and installed Ubuntu 9.10 on my PC, which had no other operational system working on it, as Win XP has crashed and I removed it completely. So, now I only have Ubuntu, and here's the problem: I have a PCI WiFi card that worked just fine with XP, but now I can't make it work. I tried to install XP back, but it can't find drive to be installed on (seems like it doesn't have SCSI drivers). So I tried Vista, but my drive is not NTFS therefore can't be installed. I don't have Internet connection to download some kind of partitioner for Ubuntu. What should I do?

---

### Post by Little Girl on 2009-11-02
Before you do anything, back up everything you care about. Windows doesn't play nice with Linux. :( Do you still have the partition Windows was on before, or did you repartition the drive before installing Ubuntu and give the entire drive to Ubuntu? If you used a Live CD to install Ubuntu, the CD comes with a partitioning program.

Here are some links that might be useful:

[LIST]
[*][http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm")
[*][http://www.dedoimedo.com/computers/dual_boot.html]("http://www.dedoimedo.com/computers/dual_boot.html")
[*][http://video.google.co.uk/videoplay?docid=-2369893842637434537#]("http://video.google.co.uk/videoplay?docid=-2369893842637434537#")
[*][http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")
[/LIST]

Good luck. :p

---

### Post by Windows Nerd on 2009-11-02
Format a partition back to NFTS with GParted. Just boot your ubuntu LiveCD, and find GParted in System>Administration. Then install vista on that partition. I believe there are some very useful tools which tell you how to dual boot Windows and Ubuntu.

Scott

---

### Post by deanmilanov on 2009-11-03
thank you, your posts were useful :) all the problems are solved now!

---

### Post by Little Girl on 2009-11-04
Glad to hear it! If there are any more happy endings today, they'll have to declare today Happy Ending Day. :popcorn:

---

