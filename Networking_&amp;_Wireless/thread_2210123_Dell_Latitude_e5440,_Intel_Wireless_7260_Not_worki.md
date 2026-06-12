---
title: "Dell Latitude e5440, Intel Wireless 7260: Not working on ubuntu 12.04"
date: 2014-03-09
forum: Networking &amp; Wireless
---

### Post by quilby2 on 2014-03-09
I have ubuntu 12.04, the wireless works on windows but not on my ubuntu.

I ran this command that I found 

wget -N -t 5 -T 10  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x  wireless_script && ./wireless_script


and got this:

[http://pastebin.com/9MVaDHRC](http://pastebin.com/9MVaDHRC)



Thanks for your help

---

### Post by Hadaka on 2014-03-09
hi, please post the output of..
```
uname -mr
lspci -nnk | grep -iA2 net 
dmesg | grep iwl
```

also you have loaded the b43 wireless driver
that is for broadcom devices,you have an Intel wireless
card. Lets remove that non working b43 driver.
please do..
```

sudo apt-get remove --purge  b43-fwcutter firmware-b43-installer
```
thanks.

---

### Post by quilby2 on 2014-03-09
You are correct, I just ran some commands I found in similar threads.
I removed the drivers like you said, and this is the output of the first command :

uname -mr
3.8.0-37-generic x86_64

lspci -nnk | grep -iA2 net 
00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I218-LM [8086:155a] (rev 04)
    Subsystem: Dell Device [1028:05de]
    Kernel driver in use: e1000e
--
02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4470]


dmesg | grep iwl
no output

---

### Post by Hadaka on 2014-03-09
hi, thanks for removing that. This link is EXACTLY
what you need to do to get this going. if you need
help with it..let me know.Read the entire post,follow the
commands...end of post...and all should be fine.
[http://askubuntu.com/questions/331667/no-wireless-for-intel-corporation-7260-version-63](http://askubuntu.com/questions/331667/no-wireless-for-intel-corporation-7260-version-63)

---

### Post by quilby2 on 2014-03-10
Thanks a lot, this worked after a restart. :P

---

### Post by mörgæs on 2014-03-10
Good, then please mark the thread 'solved'.

---

