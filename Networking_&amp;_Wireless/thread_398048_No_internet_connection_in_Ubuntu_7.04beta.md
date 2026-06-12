---
title: "No internet connection in Ubuntu 7.04beta"
date: 2007-03-31
forum: Networking &amp; Wireless
---

### Post by gztomas on 2007-03-31
Hello, I have just installed Ubuntu 7.04beta in my pc
I have a speedtouch330 adsl usb modem. I have read the article in this forum about installing the modem, and the one in [www.linux-usb.org](www.linux-usb.org) (which is nearly the same). I have done everything exactly as it is said there. However, i can´t connect to the internet.
It seems that the firmware loads ok, and it's the right one. It seems the modem connects, but when i go to my mozilla browser i can't navigate. Also, i see that the icon in the top right of my screen says there is no connection.
I know you need information in order to help me, so i copied some things i consider interesting from the syslog:

Mar 31 14:11:02 gonzalez-desktop kernel: [   41.211803] usb 1-2: reset full speed USB device using uhci_hcd and address 4
Mar 31 14:11:02 gonzalez-desktop kernel: [   41.378963] usbcore: registered new interface driver speedtch
Mar 31 14:11:02 gonzalez-desktop kernel: [   41.498275] speedtch 1-2:1.0: found stage 1 firmware speedtch-1.bin
Mar 31 14:11:02 gonzalez-desktop kernel: [   41.847133] speedtch 1-2:1.0: found stage 2 firmware speedtch-2.bin
Mar 31 14:11:02 gonzalez-desktop kernel: [   46.520502] ATM dev 0: ADSL line is synchronising
Mar 31 14:11:02 gonzalez-desktop kernel: [   57.141422] NTFS driver 2.1.28 [Flags: R/O MODULE].
Mar 31 14:11:02 gonzalez-desktop kernel: [   57.198502] NTFS volume version 3.1.
Mar 31 14:11:02 gonzalez-desktop kernel: [   59.230523] NET: Registered protocol family 17
Mar 31 14:11:02 gonzalez-desktop kernel: [   61.517620] ATM dev 0: ADSL line is up (608 kb/s down | 128 kb/s up)
Mar 31 14:11:07 gonzalez-desktop kernel: [   70.328280] eth0: link down
Mar 31 14:11:07 gonzalez-desktop avahi-daemon[4776]: Successfully called chroot().
Mar 31 14:11:07 gonzalez-desktop avahi-daemon[4777]: chroot.c: open() failed: No such file or directory
Mar 31 14:11:07 gonzalez-desktop avahi-daemon[4776]: Failed to open /etc/resolv.conf: Invalid argument
Mar 31 14:11:07 gonzalez-desktop NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth0'. 
Mar 31 14:11:07 gonzalez-desktop NetworkManager: <information>^IDeactivating device eth0. 
Mar 31 14:11:18 gonzalez-desktop kernel: [   82.054290] PPP generic driver version 2.4.2
Mar 31 14:11:32 gonzalez-desktop pppd[5187]: Plugin rp-pppoe.so loaded.
Mar 31 14:11:32 gonzalez-desktop pppd[5187]: In file /etc/ppp/peers/speedtch: unrecognized option 'nas0'
Mar 31 14:11:57 gonzalez-desktop kernel: [  121.104617] ADDRCONF(NETDEV_UP): eth0: link is not ready

If you need more info to help me, please ask.:confused: 

Please, cosider that i am a complete beginner in linux, so i beg you to be specific.

Thanks a lot!:) 

PD: Sorry for my bad english, it is not my native language.

---

### Post by johnc4510 on 2007-03-31
Try going to:

System>Administration>Networking   in the drop down menus

Make sure your dsl connection is enabled

---

### Post by gztomas on 2007-03-31
I have gone there and it seems it is active. Any other suggestion? :(

---

### Post by Mutahir on 2007-04-10
If you are using ADSL broadband type this in the terminal:

sudo pppoeconf

type your password and then a wizard will take you through to the process, make sure when it asks for username, 'omit' the username field and type your username and then it will ask for your password.

hope it helps, otherwise post your $ifconfig results and we will try to work it out.

Regards

Mutahr

---

### Post by motorbreath on 2007-04-10
What kernel are you using. 

I'm currently using 2.6.20-14-386 but if I use 2.6.20-14-generic, internt doesn't work. 

Try booting using another kernel

Generally one of the first things I do if something goes pear shaped is try another kernel.

---

