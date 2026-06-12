---
title: "how to configure my ip address in ubuntu 10.04"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by jakkamgirish on 2010-05-24
hello,
        i am girish, i am exremely new 2 linux, i want to know how do we configure lan network ip address in ubuntu 10.04 , we have 2 dns servers in windows and i have a doubt regarding them also , its like should we enter 2 dns servers in the same block or ...?? is ther any other thing ??...:P..plz tel me how to configure ip address in linux ....and my ethernet card is not in built i have kept a another 1 in the mother board slots wil it e detected !!???!!??:confused:

---

### Post by hasanujjaman on 2010-05-24
Generally ethernet is automatically connected via DHCP.Network-manager applet shows "auto eth0" wired connection is connected.If u want to manually configure the IP then right click on the network-manager applet (notification area on top pannel) and click on "edit connection".Then under "wired" tab select "auto eth0" and press "Edit" button.After that under "IPv4" tab enter your configuration manually.

---

### Post by mikewhatever on 2010-05-24
The basics are the same as in Windows. There are two dns fields, primary and secondary, but only one is required. To access the configuration interface, open System->Preferences->Network-Preferences, select your connection and click 'Edit'. If you need more help, please elaborate on what exactly is the difficulty.

---

### Post by 3rdalbum on 2010-05-24
There's actually ONE field for DNS in Network Manager, but you can specify two DNSes; just put two into the field, with a comma between them.

---

### Post by Detonate on 2010-05-24
If you are using DHCP, the DNS servers listed in your router will be used.  If you are using a static IP, then your DNS servers will be the ones in the /etc/resolv.conf file.  You can edit this file as root and enter your DNS servers there.  However, if you use DHCP anything you enter will be overwritten.  See man resolv.conf.  If you wish to use DHCP with a DNS server other than the one provided by your ISP, you can go to your router (or modem if directly connected) set up page and enter the desired DNS there.

---

### Post by alfl on 2010-06-08
I setup, as mentioned by GUI, my eth0 connection with a manual ip adres. However if i check the /etc/networks/interfaces the new ip settings are not there. also after a reboot my eth0 is not operational and the /etc/networks/interfaces shows only the localhost setting :-?

I am using ubuntu 10.04.

Is this a bug or do i something wrong ??

---

### Post by Detonate on 2010-06-08
See post #7 in this thread.  You can spend hours figuring out why network manager is screwing up, or follow my simple instructions and be up and running in a few minutes.

[http://ubuntuforums.org/showthread.php?t=1494628](http://ubuntuforums.org/showthread.php?t=1494628)

---

