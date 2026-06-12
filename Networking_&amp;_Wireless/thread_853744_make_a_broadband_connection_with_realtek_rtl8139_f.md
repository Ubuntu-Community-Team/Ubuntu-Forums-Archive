---
title: "make a broadband connection with realtek rtl8139 family pci fast ethernet NIC"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by Bipin on 2008-07-08
i couldnt connect to the internet 
first i downloaded ndiswrapper-1.53 as my friend told me 
but i couldnt install 
as i type the command <make install> inside ndiswrapper directory
it shows error code 2 or something like that 
and when ui type <install> again it shows error #2 or somthin
so m not able to install ndiswrapper 
can anybody help me to get internet connection



my PC Requirement are
intel(R) pentium 4
CPU 1.80Ghz
512 MB RAM

with microsoft windows XP Service Pack 2
can anybody help me on this

---

### Post by pytheas22 on 2008-07-08
ndiswrapper is only for wireless cards, so it's not going to help you with ethernet.

First, please give these commands a shot and let me know if they help:
```

sudo rmmod 8139too
sudo modprobe 8139cp
sudo ifconfig eth0 up
```

If you don't get any errors, wait a few seconds and see if you can connect to the Internet.  If you do get errors, try this:
```

sudo rmmod 8139cp
sudo modprobe 8139too
sudo ifconfig eth0 up
```

And again, if you haven't gotten any errors, wait a couple seconds and try to connect.

If the above doesn't help, please post the output of these commands (if necessary, copy-and-paste them into a text file and transfer it using a USB drive to another computer) so that we can figure out what's going on:
```

lshw -C Network
lspci
```

---

