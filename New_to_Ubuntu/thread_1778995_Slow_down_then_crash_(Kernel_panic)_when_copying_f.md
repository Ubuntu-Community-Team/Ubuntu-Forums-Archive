---
title: "Slow down then crash (Kernel panic) when copying files from usb in 11.04"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by findlad on 2011-06-09
Hello all,
I have a toshiba NB555D, and have had no end of bother getting it working with Ubuntu. As it stands i have 11.04 installed and most major problems under control except that when transferring large files from usb, the mouse slows after a gig or so before freezing completely often with a flashing caps lock key. It would be nice to be able to get some music etc onto this bad boy. Any ideas?

---

### Post by jtarin on 2011-06-09
Unmount the device safely and then unplug. Plug it back in and start your file transfer then when it freezes issue this command in the terminal and post the last 20 lines here.```
cat /var/log/syslog
```

---

### Post by findlad on 2011-06-10
Id love to, but the entire computer jams up, then i get the flashing caps lock of death. I dont get the opportunity to ctrl alt t my way to a terminal window, it just dosent respond.

---

### Post by jtarin on 2011-06-10
> **findlad said:**
> Id love to, but the entire computer jams up, then i get the flashing caps lock of death. I dont get the opportunity to ctrl alt t my way to a terminal window, it just dosent respond.
When your system freezes what do you do to regain control?
Try this...Open your terminal type and enter the command just after starting the transfer then.

---

### Post by findlad on 2011-06-13
Sorry for the delay, was away for the weekend. The transfer itself dosent freeze, the whole computer does, and i cant get it working again. It involves a hard shutdown and restart. Dont get much from the syslog, but here it is after the restart if it helps


Jun 13 18:54:54 duncan-TOSHIBA-NB555D kernel: [   43.212224] wlan0: RX AssocResp from 00:22:6b:52:ac:04 (capab=0x411 status=0 aid=3)
Jun 13 18:54:54 duncan-TOSHIBA-NB555D kernel: [   43.212233] wlan0: associated
Jun 13 18:54:54 duncan-TOSHIBA-NB555D kernel: [   43.212899] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun 13 18:54:54 duncan-TOSHIBA-NB555D NetworkManager[456]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Jun 13 18:54:54 duncan-TOSHIBA-NB555D kernel: [   43.272115] Intel AES-NI instructions are not detected.
Jun 13 18:54:54 duncan-TOSHIBA-NB555D kernel: [   43.280915] padlock_aes: VIA PadLock not detected.
Jun 13 18:54:54 duncan-TOSHIBA-NB555D NetworkManager[456]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Jun 13 18:54:54 duncan-TOSHIBA-NB555D wpa_supplicant[485]: WPA: Key negotiation completed with 00:22:6b:52:ac:04 [PTK=CCMP GTK=TKIP]
Jun 13 18:54:54 duncan-TOSHIBA-NB555D wpa_supplicant[485]: CTRL-EVENT-CONNECTED - Connection to 00:22:6b:52:ac:04 completed (auth) [id=0 id_str=]
Jun 13 18:54:54 duncan-TOSHIBA-NB555D NetworkManager[456]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Jun 13 18:54:54 duncan-TOSHIBA-NB555D NetworkManager[456]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'sgcommand'.
Jun 13 18:54:54 duncan-TOSHIBA-NB555D NetworkManager[456]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 13 18:54:54 duncan-TOSHIBA-NB555D NetworkManager[456]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jun 13 18:54:54 duncan-TOSHIBA-NB555D NetworkManager[456]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Jun 13 18:54:54 duncan-TOSHIBA-NB555D NetworkManager[456]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun 13 18:54:54 duncan-TOSHIBA-NB555D NetworkManager[456]: <info> dhclient started with pid 1432
Jun 13 18:54:54 duncan-TOSHIBA-NB555D NetworkManager[456]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun 13 18:54:54 duncan-TOSHIBA-NB555D dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Jun 13 18:54:54 duncan-TOSHIBA-NB555D dhclient: Copyright 2004-2010 Internet Systems Consortium.
Jun 13 18:54:54 duncan-TOSHIBA-NB555D dhclient: All rights reserved.
Jun 13 18:54:54 duncan-TOSHIBA-NB555D dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jun 13 18:54:54 duncan-TOSHIBA-NB555D dhclient: 
Jun 13 18:54:54 duncan-TOSHIBA-NB555D dhclient: Listening on LPF/wlan0/7c:4f:b5:14:3e:05
Jun 13 18:54:54 duncan-TOSHIBA-NB555D dhclient: Sending on   LPF/wlan0/7c:4f:b5:14:3e:05
Jun 13 18:54:54 duncan-TOSHIBA-NB555D dhclient: Sending on   Socket/fallback
Jun 13 18:54:54 duncan-TOSHIBA-NB555D dhclient: DHCPREQUEST of 192.168.1.100 on wlan0 to 255.255.255.255 port 67
Jun 13 18:54:54 duncan-TOSHIBA-NB555D NetworkManager[456]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jun 13 18:54:54 duncan-TOSHIBA-NB555D dhclient: DHCPACK of 192.168.1.100 from 192.168.1.1
Jun 13 18:54:54 duncan-TOSHIBA-NB555D dhclient: bound to 192.168.1.100 -- renewal in 39636 seconds.
Jun 13 18:54:54 duncan-TOSHIBA-NB555D NetworkManager[456]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jun 13 18:54:54 duncan-TOSHIBA-NB555D NetworkManager[456]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jun 13 18:54:54 duncan-TOSHIBA-NB555D NetworkManager[456]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Jun 13 18:54:54 duncan-TOSHIBA-NB555D NetworkManager[456]: <info>   address 192.168.1.100
Jun 13 18:54:54 duncan-TOSHIBA-NB555D NetworkManager[456]: <info>   prefix 24 (255.255.255.0)
Jun 13 18:54:54 duncan-TOSHIBA-NB555D NetworkManager[456]: <info>   gateway 192.168.1.1
Jun 13 18:54:54 duncan-TOSHIBA-NB555D NetworkManager[456]: <info>   hostname 'duncan-TOSHIBA-NB555D'
Jun 13 18:54:54 duncan-TOSHIBA-NB555D NetworkManager[456]: <info>   nameserver '192.168.1.1'
Jun 13 18:54:54 duncan-TOSHIBA-NB555D NetworkManager[456]: <info>   domain name 'cg.shawcable.net'
Jun 13 18:54:54 duncan-TOSHIBA-NB555D NetworkManager[456]: <info> Scheduling stage 5
Jun 13 18:54:54 duncan-TOSHIBA-NB555D NetworkManager[456]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jun 13 18:54:54 duncan-TOSHIBA-NB555D NetworkManager[456]: <info> Done scheduling stage 5
Jun 13 18:54:54 duncan-TOSHIBA-NB555D NetworkManager[456]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Jun 13 18:54:54 duncan-TOSHIBA-NB555D NetworkManager[456]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jun 13 18:54:54 duncan-TOSHIBA-NB555D avahi-daemon[452]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.100.
Jun 13 18:54:54 duncan-TOSHIBA-NB555D avahi-daemon[452]: New relevant interface wlan0.IPv4 for mDNS.
Jun 13 18:54:54 duncan-TOSHIBA-NB555D avahi-daemon[452]: Registering new address record for 192.168.1.100 on wlan0.IPv4.
Jun 13 18:54:55 duncan-TOSHIBA-NB555D avahi-daemon[452]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::7e4f:b5ff:fe14:3e05.
Jun 13 18:54:55 duncan-TOSHIBA-NB555D avahi-daemon[452]: New relevant interface wlan0.IPv6 for mDNS.
Jun 13 18:54:55 duncan-TOSHIBA-NB555D avahi-daemon[452]: Registering new address record for fe80::7e4f:b5ff:fe14:3e05 on wlan0.*.
Jun 13 18:54:55 duncan-TOSHIBA-NB555D NetworkManager[456]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Jun 13 18:54:55 duncan-TOSHIBA-NB555D NetworkManager[456]: <info> Policy set 'Auto sgcommand' (wlan0) as default for IPv4 routing and DNS.
Jun 13 18:54:55 duncan-TOSHIBA-NB555D NetworkManager[456]: <info> Activation (wlan0) successful, device activated.
Jun 13 18:54:55 duncan-TOSHIBA-NB555D NetworkManager[456]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jun 13 18:55:04 duncan-TOSHIBA-NB555D kernel: [   53.328034] wlan0: no IPv6 routers present
Jun 13 18:55:45 duncan-TOSHIBA-NB555D ntpdate[1620]: step time server 91.189.94.4 offset 11.615387 sec

---

### Post by findlad on 2011-06-23
So, bit more of an update, then hopefully someone has some good ideas. The slow down and eventual freeze occurs when copying a large quantity (1gb ish) to the hard drive. I don't think it is a reading issue as i can play music for ages with little issue, even though banshee wont even open any more. And i can not get the system back when it freezes, i have to do a hard reset. The first symptom is the mouse becoming so sluggish it is unusable, and in any case clicking does not seem to work.
I think this might be the same root problem reported in a previous post detailing issues installing 11.04 in the first place on the toshiba nb555d, as that crash happened when copying files to the hard drive. Those work arounds were to get 11.04 installed in the first place. I don't think it fixes the fundamental problem.
What do you think? Buffer issue of some kind? I/O software? Driver issue?
I am new to ubuntu, and i don't really have much knowledge of the command line (not since my amiga 1200 anyway).
Any help would be apreciated.

---

### Post by jtarin on 2011-06-23
Before you start your transfer......in a terminal issue the command  ```
tail -f /var/log/messages
```....leave the terminal open and start your transfer and see if the message output gives you any error messages or indications.

---

### Post by findlad on 2011-06-30
Tried that, got

tail: cannot open `/var/log/messages' for reading: No such file or directory

when i navigated to this location, the contents are:

alternatives.log    dist-upgrade    kern.log		syslog
alternatives.log.1  dmesg	    kern.log.1		syslog.1
apparmor	    dmesg.0	    kern.log.2.gz	syslog.2.gz
apt		    dmesg.1.gz	    kern.log.3.gz	syslog.3.gz
auth.log	    dmesg.2.gz	    kern.log.4.gz	syslog.4.gz
auth.log.1	    dmesg.3.gz	    lastlog		syslog.5.gz
auth.log.2.gz	    dmesg.4.gz	    mail.err		udev
auth.log.3.gz	    dpkg.log	    mail.log		ufw.log
auth.log.4.gz	    dpkg.log.1	    news		unattended-upgrades
boot		    faillog	    pm-powersave.log	wtmp
boot.log	    fontconfig.log  pm-powersave.log.1	wtmp.1.gz
bootstrap.log	    fsck	    pm-suspend.log	Xorg.0.log
btmp		    gdm		    pm-suspend.log.1	Xorg.0.log.old
btmp.1.gz	    installer	    pycentral.log
ConsoleKit	    jockey.log	    samba
cups		    jockey.log.1    speech-dispatcher

Not sure what to do now. What does tail do? 
I appreciate your help by the way, don't think i have been too forthcoming with the appreciation :)

---

### Post by jtarin on 2011-06-30
> **findlad said:**
> 
Not sure what to do now. What does tail do? 

To see what "tail" is issue the command ```
man tail
```. press "q" to quit the screen.
Now let's try the same thing with```
tail -f /var/log/syslog
```....now start your transfer.

---

