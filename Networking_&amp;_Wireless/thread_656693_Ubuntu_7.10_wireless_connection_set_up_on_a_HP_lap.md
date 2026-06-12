---
title: "Ubuntu 7.10 wireless connection set up on a HP laptop"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by kailasht1 on 2008-01-02
I am trying to set up a wireless connection in ubuntu 7.10 gutsy  on my HP Pavillion laptop.I got a thread and followed that but still I could not get it worked.I would like to tell yo what I did so far.
I started with....
:~$lspci
I could see the line 
Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

then I installed ndiswrapper through aptitude:
:~$sudo aptitude install ndiswrapper-utils-1.9

later, I carried out following commands successfully.
:~$wget [http://ftp.us.dell.com/network/R151517.EXE](http://ftp.us.dell.com/network/R151517.EXE)
:~$mkdir driver
:~$unzip -a R151517.EXE -d driver/
:~$cd driver/DRIVER/
:~$sudo ndiswrapper -i bcmwl5.inf
:~$sudo ndiswrapper -l
:~$sudo ndiswrapper -m
:~$sudo modprobe ndiswrapper

Then I rebooted but alas! I didn't see wireless connection icon on the top. Can anyone please tell me what did I miss? or was anything wrong? apart from corrections if you have got any new method then please let me know.

Thanks in advance

---

### Post by befrying on 2008-05-24
do you have another link to download [http://ftp.us.dell.com/network/R151517.EXE](http://ftp.us.dell.com/network/R151517.EXE) ive searched to download it but keeps saying that its a bad file

---

