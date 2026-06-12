---
title: "Internet not working after update. PLEASE HELP"
date: 2016-02-10
forum: Networking &amp; Wireless
---

### Post by prem_kumari on 2016-02-10
After update my ubuntu 14.04 the wireless connection is not showing and on Settings>Network says the system is not campatible.
I really don't have a clue of what to do, I know nothing about codes. I've tried many codes I founded on different forums but nothing worked.
I'm using a ASUS SonicMaster, and I'm new on the linux world.
I need a paciente soul to help me, PLEASE [-o

---

### Post by ajgreeny on 2016-02-10
Go to [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336) and read the first two sticky posts at the top which will help you give the info needed to those who can help, which unfortunately does not really include me as I don't often use wifi.

---

### Post by prem_kumari on 2016-02-10
Thank you so much for your prompt answer and instruction. 
I tried what is said on the sticky posts and had no results... Maybe you can indicate me an expert in wireless connection, please? 
My knowledgement here is really poor, but I'm very good on following instructions. :KS

---

### Post by prem_kumari on 2016-02-10
***WIRED INTERNET CONNECTION is also not working.

---

### Post by Hadaka on 2016-02-10
Hi please open a terminal ctrl/alt/t then COPY and paste..
```
lspci -n | awk '/280/{print$3}'
```
post the output.

then do..
```
sudo apt-get remove --purge bcmwl-kernel-source
```
thanks.

---

