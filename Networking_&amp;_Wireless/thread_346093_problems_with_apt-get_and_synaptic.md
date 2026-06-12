---
title: "problems with apt-get and synaptic"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by pliumbum on 2007-01-25
hello,

finally i am posting this from my comp with ubuntu, and this is a huge leap forward for me. the problem is now another. now i am sure that my wireless card is supported, that i have configured my network about right.. but there is one bad thing.

the last thing i had to do was setting ipv6 off. i set it off on firefox and it started working suddenly!
so then i thought that the problem is about the same for the whole system. i logged in as root, went to etc/modprobe.d/aliases, made everything like that: 

alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
#alias net-pf-10 ipv6 

saved, rebooted, logged in normally, but i am unable to connect using synaptic or apt-get. i also tried connecting gaim, and failed. then i thought that only firefox was working. but a couple of minutes ago i decided to try downloading a torrent file. bittorrent connected and i am downloading!

i also tried turning ipv6 back on, nothing worked. the dns seems to be correct.. what could i do? i cant install anything!

here's what i get when trying to use apt-get:

donatas@donatas-laptop:~$ sudo apt-get update
Password:
0% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.

then nothing happens. it gets stuck.

the same about synaptic, trying to get updated list, or to install something, the progress bar just gets stuck at "downloading file 1 of 15", for example

---

### Post by pliumbum on 2007-01-25
nobody knows what to do? come on..

---

