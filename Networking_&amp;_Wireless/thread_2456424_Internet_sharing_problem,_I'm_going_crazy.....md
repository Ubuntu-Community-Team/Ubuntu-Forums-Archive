---
title: "Internet sharing problem, I'm going crazy...."
date: 2021-01-11
forum: Networking &amp; Wireless
---

### Post by MaxVio on 2021-01-11
Hello everyone, I expose the problem that grips me;
I have a mini PC with Ubuntu 20.04 x86/64 Desktop installed, on this mini PC with an integrated Gigabit network card I added a second Gigabit card on USB3 that I use to connect the computer to the main router of the ISP in DHCP.
The integrated card is connected to a gigabit switch and is set in a different subnet obviously from the router, in practice the USB3 is the WAN while the integrated one is the LAN, I also set the DHCP on this card and set all the rules IPTable so as to make it practically a router.
Apparently everything works perfectly because when I connect a second PC in DHCP on the switch it regularly takes the IP, gateway and DNS and I can safely surf.
If I do a speedtest on Ookla from the PC connected to the switch I get about 500 Mbit/s which is the same speed I get if I do the same test directly from the mini PC/router.
The problem is when I try to download something....
If for example I try to download Ubuntu (with direct download not with torrent), from the mini PC/router I get easily 25-30 MB/s while if I try from the PC connected on the switch I do not get more than 1.2 MB/s, that is, there is a dramatic drop in performance I dare say ...
Can anyone help me or point me in the right direction to solve this problem? I've tried the impossible on the Internet but I couldn't figure it out ...
Help!!!!!
Thanks in advance for those who want to help me [-o

---

### Post by TheFu on 2021-01-11
Storage performance matters. what's different?
This isn't just a network test.  Also, the remote server capacity can fluctuate. One run is not sufficient for comparison.

---

### Post by MaxVio on 2021-01-11
Well i made this post because i did several tests and nothing, if i download directly from the mini PC i get all the speed, from any device attached to the switch i get the poor download speed, i made the Ubuntu example but it's for all direct downloads...

---

### Post by TheFu on 2021-01-11
> **MaxVio said:**
> Well i made this post because i did several tests and nothing, if i download directly from the mini PC i get all the speed, from any device attached to the switch i get the poor download speed, i made the Ubuntu example but it's for all direct downloads...

And writing files is slow. It will slow down the networking.  What is different?
First, the USB-NIC adapter is added. Could that be it?

Run some tests for the other devices just on the LAN. Are those slow too or not?  Real numbers. Real tests that can be reproduced, please.  Post the setup, numbers, what's involved hardware and software from end-to-end, and the actual commands used, please.

I ask these things since all of them are important.  We aren't going to solve this - you are. You are there. We are not.
Questions, 
[LIST]
[*]how fast can your LAN support? - don't bring any storage into that.  use **iperf3**. Hopefully, no surprises with this, but we don't know until you check.
[*]how fast is the storage? - don't bring any networking into that.  use **bonnie++**. I bet there are surprises with this. People never think there storage is slow, but it often is much slower than the box claimed.
[*]how fast on the LAN are file transfers.  Use the same protocol for all tests. Read from the same source system and write to the different clients. Use HTTP, scp, sftp, rsync and CIFS (no GUI). time the xfer commands - use **time** and lynx/wget/curl and scp, and sftp, and rsync, and smbclient to do the transfers. It would be best if the router isn't involved.
[/LIST]

I bet you'll learn specific things about each client doing these tests. Perhaps the switch is the issue?  We don't know, until you test.

---

### Post by MaxVio on 2021-01-11
I will do all those tests, thank you for the support, for now i j[COLOR=#242729][FONT=Arial]ust finished a test now, i started two downloads at the same time, i mean two ubuntu downloads, same version, same site, everithing the same, one from the mini PC and the other from the PC on the switch, the first was downloading at 30 MB/s the other at 1.4 MB/s , if i do the same test 100 times the result is the same always...
All NICs and the switch are 1Gb each, and if i connect the pc that is on the switch direct to the router i have back those 30 MB/s so, for sure it have to be something on the switch or on the mini PC...
The storage on the PC is an SSD and when i tranfer file inside the lan they go fast, 900 and more Mbit[/FONT][/COLOR]

---

### Post by MaxVio on 2021-01-11
Alttttt Update, (in some ways the problem is thicken), the machine from which I'm doing the tests is in dual boot, win10/64 and Ubuntu 20.04 LTS; for accuracy and not to leave any stone unturned, I tried from the Ubuntu GUI, well, from Ubuntu works perfectly so the problem is on Windows ... but what the heck is???? Why only on downloads?What is it, do I have a poltergeist in the PC?

---

### Post by MaxVio on 2021-01-12
Update!
So, gripped by doubts I asked my brother to run the same tests from his line, everything exactly as I did, including the download sources that for Ubuntu are the official site ITA (I state that the same thing happens with other downloads that are not Ubuntu and other sources); i premise that he has done the tests directly connected to the ISP router and therefore not sharing the connection,he lives in another city and has a different ISP from mine (I have Fastweb he has Tim), his line is a 100/20 FTTC mine is a 1000/200 FTTH, here are his results with Windows 10-64 , MacOS and Ubuntu 20. 04 LTS:

[[IMG]https://i.ibb.co/JKt7sJ7/Tests.jpg[/IMG]]("https://ibb.co/bPmBK9B")

At this point I ask you users (if you want) to run the same tests and report the results, if my doubts are confirmed, I do not have a poltergeist in the PC but it is a nice BUG of Windows, at least in the version 10/64 in Italy...

---

### Post by MaxVio on 2021-01-12
Solved!!!
In practice some Windows update must have changed for the worse some parameters....
The solution is to open a command prompt with administrator privileges and run this command:

[COLOR=#000000][FONT=Ubuntu]netsh int tcp set global autotuninglevel=normal

[/FONT][/COLOR]Mission accomplished :-)

---

