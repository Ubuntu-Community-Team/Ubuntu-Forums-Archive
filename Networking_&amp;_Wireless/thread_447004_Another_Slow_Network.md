---
title: "Another Slow Network"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by Khashul on 2007-05-17
We have a network with a few Windows PCs, one Fedora PC and this Ubuntu PC. All file transfers between PCs work except for to the Ubuntu machine which is ridiculously slow.

It has a US Robotics Gigabit Network card -> [Here]("http://www.usr-emea.com/products/p-wired-product.asp?prod=net-7902a&loc=unkg")

I've done a lot of searching on the internet and I've come to conclusion that its a driver problem from all the similar issues people are having. So I was wondering if anyone could help me solve this I would much appreciate it.

I'm quite a new user to Linux so if you need any more info don't hesitate to ask!

Martin

---

### Post by tgm4883 on 2007-05-17
Is the gigabyte NIC hooked up to a gigabyte swich/router or a 10/100 switch/router?

---

### Post by Khashul on 2007-05-17
Its connected to a Gigabyte switch, we had it working with other distros but we decided to move to Ubuntu for media purposes so just trying to sort it on this machine.

---

### Post by Khashul on 2007-05-18
Can anyone else help?

---

### Post by Khashul on 2007-05-20
Bump

---

### Post by galileux on 2007-08-17
Hi
I've been experiencing the exact same problem, and still haven't been able to come up with a solution. I did a lot of testing to track down the culprit but with no definite results yet.

I have a small network made up by:

- A file server running Edgy-Server with Samba on a Sempron CPU, Asus M2n-E board, Nvidia Giganet NIC card onboard, no X.

- A windows client represented by a Dell Inspiron laptop running Windows XP, Intel motherboard, inbuilt 10/100 NIC.

- A Feisty desktop client, running Feisty amd64 on a Intel Core2 Duo E6600 hosted by an Asus P5B motherboard, with Realtek Gigalan on-board.

Same problem: from the moment the feisty got into the network the transfer speeds to and from the server have been ridiculous: talking about 5 MB/s server-to-client and 1.5 MB/s client-to-server.

Initially, I could not even save files to the Samba shares from the Feisty, transfers failed systematically. The ability to write to the shares was established only after disabling the onboard Realtek, disabling it from BIOS and slipping an old Realtek 10/100 in a PCI slot, But speed was still slow (values above).

We then proceeded as follows:
- Checked Samba, seems OK (normal speeds from the windows client).
- Booted feisty32 LiveCD on the Dell Laptop... surprise: normal transfer speeds! (using "scp -r" for the tests).

This is the stage we're at now: there can only be 2 reasons left:

- Problem is caused by the hardware (namely, the Asus P5B board, which has already given problems with the onboard NIC).

- Problem is caused by the 64-bit architecture. This could not be tested because the Dell laptop's processor does not support 64-bit.

Only thing left to do: try to replace the motherboard and see what happens. Maybe I'll post the results back.

Khashul et al, could you possibly post some details here about your hardware/software configuration (e.g. version of Ubuntu, hardware details, etc)?

Regards
Galileux

---

### Post by punkrokk on 2007-08-17
I'd gtry it with 32 bit if you have a 32 bit board. I think alot of the drivers for 64 bit are newer and less stable.

---

### Post by galileux on 2007-08-17
Punkrokk: Yes, sorry, I forgot to mention: I also booted the Coreduo nto a Feisty 32-bit LiveCD and got no improvement on the uploads to the server.

---

### Post by touser on 2007-10-09
I'm having the same problem on my dfi lanparty nforce 4 board with both the onboard marvel controller and then onboard nvidia CK804 card. The network transfer rate over gigabit is maxing out at 8MB/s with samba, 1-2MB/s over scp, 4-5MB/s over nfs. The problem is not with the rest of the network and not with the onboard hardware because when i reboot into windows xp transfer rates go right back to 46MB/s. If anyone has any clue how to speed things up for nforce 4 boards i'd greatly appreciate the help!

---

