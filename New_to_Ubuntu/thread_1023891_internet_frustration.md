---
title: "internet frustration"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by olliey on 2008-12-28
hi! 

I've had a dell P4 laptop (rebuilt) that runs ubuntu since october, bought from my local freegeek. it has a d-link wireless card, and using that and wired net has been no problem until the last few days, when it has stopped connecting at all!! this am, it picked up a wireless signal for about five mins and then kicked it again--i've also tried plugging it in to a cable modem and it wont connect to that either.

i've gone through all the official documentation and followed all the steps for setting it up, but nothing is working--plus, it work fine for three mths and now it won't at all!

i know this is totally n00b but i need help! 

thanks thanks thanks!!

---

### Post by linux_tech on 2008-12-28
what is output of (post)
In terminal type:
```
sudo lshw -C network
ifconfig
cat /etc/resolv.conf
netstat -l -np -p
netstat -rn
cat /etc/network/interfaces

```
Is it dsl?
Did you try rebooting everything? if not try this first
Are you getting green lights on pc netwk card, router?
Did you try pinging internet by name, ip addr
also ping loopback- 127.0.0.1
try to ping gateway ip addr

---

### Post by olliey on 2008-12-28
it says "1shw: command not found"

my lights are all good, and i've rebooted a whole bunch of times. 

pinging loopback-- it says "64 bytes from 127.0.0.1: icmp_seq=233 ttl=64 time=0.057 ms", given that the seq and time values are different.

---

### Post by newbee70 on 2008-12-28
> **olliey said:**
> it says "1shw: command not found"

my lights are all good, and i've rebooted a whole bunch of times. 

pinging loopback-- it says "64 bytes from 127.0.0.1: icmp_seq=233 ttl=64 time=0.057 ms", given that the seq and time values are different.

olliey the command should be: 

small "L" not 1 in the lshw command.

---

### Post by linux_tech on 2008-12-28
yup can't help with no info ... now how about

sudo lshw -C network
ifconfig
cat /etc/resolv.conf
netstat -l -np -p
netstat -rn
cat /etc/network/interfaces

---

### Post by olliey on 2008-12-28
okay...duh :P

so i got a whole pile of text....is there a specific part i need to know or do i have to type the whole pile out? 

i wish i had my thumb drive right about now!

---

### Post by linux_tech on 2008-12-28
You can highlight the test using your mouse curser in the terminal screen. Left click and at the same time, drag the mouse curser over the text to highlight it.  After text is highlighted, press ctrl + c keys at same time (this copies the highlighted text to the clipboard) so you can click reply then and paste it in the reply text box by pressing ctrl + v at same time.

If you do not want to use the shortcut keys, then you can also right click on the highlighted text and choose copy, then right click in the reply text box and choose paste.

---

