---
title: "USR5610C Modem not detected?"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by Odd_sam on 2009-01-20
I am trying to move from windows to linux. I am fairly experienced with XP but I don't know a thing about linux. From what I have found my modem is one of the few hardware modems made by USR. The official Ubuntu help guide doesn't give any support for the USR chipsets. I've looked on USR's website for drivers and there was an .rpm file which apparently is for redhat distros only. I have/am using Ubuntu 8.10 and I am stuck on dialup. I can use winxp as an internet connection, but I cannot access the internet with linux. So downloading stuff through sudo get-apt doesn't work for me. I've looked and the cases where the modem caused trouble was after detection. So I need a noob's guide for detecting the modem. I did use scanmodem and it did find and spit out some text files. If you need me to copy paste those I can.

Also I don't know if the problem is with the modem or with my hardware setup. I don't know the official terms for the hardware but the modem is not connected directly to the mobo. There is a bridge like expansion that connects the PCI modem to the motherboard. If a picture would be better than my fail attempt to describe it let me know and I'll post one. 

Thanks for helps.

---

### Post by cariboo on 2009-01-20
Could  you open an Applications-->Accessories-->Terminal and type:

```
sudo lshw -C network
```

and paste the output in you next post. The above command (code is a misnomer) lists all the network hardware attached to your computer.

Jim

---

### Post by Odd_sam on 2009-01-21
Here's what I got.
>   *-network               
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth0
       version: 02
       serial: 00:0b:db:68:25:aa
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k3-NAPI firmware=N/A latency=64 link=no mingnt=255 module=e1000 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: b6:75:07:e3:81:41
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by ModelM on 2009-01-21
Your USR5610 should appear in the result of typing the command

lspci

into a terminal. This is a hardware modem - no drivers are required.

After you see your modem listed in the result of the above command, in a terminal type:

sudo wvdialconf

and wait for it to finish. This will create a basic configuration file for wvdial. In the same terminal:

sudo gedit /etc/wvdial.conf

will bring the config file up in an editor where you can edit your login name & password. Save the file after editing, then in the same terminal type:

sudo wvdial

and, I hope, it should dial & connect to your ISP.

---

### Post by ieee488 on 2009-01-21
I have this modem, and as ModelM says, Ubuntu recognizes it.

Follow the instructions given, and you'll be good to go.

---

### Post by Odd_sam on 2009-01-21
Thanks all. It works. But as a side note when I ran the command cariboo907 gave me the modem did not come up in the terminal. But when I ran the command ModelM posted, the modem showed up. Either way I have successfully connected with wvdial. Thanks.

---

