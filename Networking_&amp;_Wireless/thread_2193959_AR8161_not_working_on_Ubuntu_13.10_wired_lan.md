---
title: "AR8161 not working on Ubuntu 13.10 wired lan"
date: 2013-12-15
forum: Networking &amp; Wireless
---

### Post by Windows_Apple_Linux on 2013-12-15
Hello!
I recently installed Ubuntu 13.10 and complety wiped my hard drive, the installation went smooth but once completed i cant go on the internet since it doesn't recognize my LAN. 
I followed all the possible tutorials online but none of them work. Here is that I have done so far:

Downloaded Compat-drivers-2013-03-04-u 
Extracted home folder
Open terminal
CD /home/GUI/...long file name
./scripts/driver-select alx
Make
Now this is where things goes ugly.. I receive few lines of erros: CC1: some warning being treated as erros make [4] ... And so on.

I also tryed on using compact-wireless-3.5.4-snpc but same error.

Since I can't use the internet with my PC, I have to downloads stuff from my cell phone then transfer it over, so I have no way of using  sudo apt-get command lines..

Kernel: 3.11.0-12-generic (using commend line: uname -r)
Uname -m : x86_64
CPU: AMD fax 4300 4 gb of ram
Lspci: Qualcomm Atheros AR8161 gigabit Ethernet (rev 10)
Motherboard: Asus m5 a78lm-m lx3

Any help would be much appreciated!

---

