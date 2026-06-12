---
title: "How do I install ndiswrapper without an internet connection in Ubuntu?"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by JHQ_623 on 2008-09-29
Ok i'm sharing my neabors internet via wifi & can't get ubuntu on the net now everybody's saying i'll need to download ndiswrapper, windows wireless driver, wifi radar & so on but how can i acomplished that when i can't get on the internet through ubuntu to download the requried software i tired downloading from xp & burning ndiswrapper & installing it from there but it dosn't work. If anyone could help please let me know what to do before i throwaway the software & cd.

---

### Post by aladinonl on 2008-09-30
if u r really sharing internet with him, go over his house and plug cable in for a moment. If u r using HIS internet WITHOUT HIS acknowledgement, go somewhere else, like a cybercafe.

---

### Post by superprash2003 on 2008-09-30
in your terminal type lshw -C network and post output

---

### Post by NE Key on 2008-09-30
The answer is here;

[http://ubuntuforums.org/showthread.php?t=563547](http://ubuntuforums.org/showthread.php?t=563547)

Install "ndiswrapper" package without working internet connection (from your ubuntu installation cd)

sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9

---

