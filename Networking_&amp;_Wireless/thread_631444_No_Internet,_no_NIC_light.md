---
title: "No Internet, no NIC light"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by btwbtw on 2007-12-04
I have a dual boot PC on which I mostly run Windows but booted into Feisty last night to run the updater. No Internet. I notice that the OEM Realtek NIC light is off too. Everything works normally under Win and that's where I'm writing this. I also cannot figure out how to post the results of ifconfig, lspci, lshw, etc. I have a read-only USB hard drive where I write my Windows backups, but I cannot write to it while in Ubuntu so I can't figure out how to move files from Ubuntu to Windows to post here  :(

I ran ethtool -i eth0 and got driver and version information.

I'm not very knowledgeable about networking -can someone tell me how to jumpstart the NIC?

---

### Post by btwbtw on 2007-12-04
When I run ifconfig, in addition to the loopback(?) entry there are two others. One is "eth0" and one is "eth0:avah"

When I run ifconfig -s, there is one line for "eth0" and one line for "eth0:"

---

### Post by btwbtw on 2007-12-04
Removing power from the computer for a while seems to have solved the problem.

---

### Post by btwbtw on 2007-12-04
The next time I rebooted the computer, the NIC was deactivated again. I wonder why this is happening now - I never had this problem when I was using Ubuntu frequently.

---

