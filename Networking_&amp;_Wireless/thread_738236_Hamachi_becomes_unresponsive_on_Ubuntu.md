---
title: "Hamachi becomes unresponsive on Ubuntu"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by ubuntogenius on 2008-03-28
I have come across this a few times now. Some of my installations work, where others ... well...
Take a fresh Ubuntu 7 Server install. Add Hamachi. Do the make install etc routine. Called tuncfg. Then when I run hamachi-init ... Nothing. Other servers I get to go on to hamachi start, join networks, login etc.

Any suggestion as to why some installs behave so very different? (Hardware differences aside, its the same standardised, and I don't install anything before I try the Hamachi install)

---

### Post by zeronothing on 2008-03-28
try this: 

on the pc having trouble running hamachi, download this package from the repository called upx-ucl-beta

sudo apt-get install upx-ucl-beta

next kill the tuncfg process so we can start fresh. remember to kill that process you have to have admin rights. next do the following instructions:

1.) cd /usr/bin

2.) sudo upx-ucl-beta -d hamachi

3.) sudo /sbin/tuncfg

4.)hamachi-init

5.)hamachi

hopefully you will be back in business. if you have anymore problems don't hesitate to ask....

---

