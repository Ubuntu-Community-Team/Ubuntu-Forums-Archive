---
title: "Is Auto detect Nework possible?"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by kantan on 2007-05-30
I'm a new user to linux and am use to working with WinXP.  I have broadband from two ISPs at home.  When I installed Edubuntu it gave me an option to detect and configure my internet connection, which it then did.  Now because of the numerous updates I need to temporarily move it to my faster broadband connection.  When I move it, it fails to connect to the internet.  Is there an auto detect option for Ubuntu like there is for Windows XP?  I tried copying over the information about default gateway, static IP, and DNS servers from my WinXP machine which auto detects the network connection, but Edubuntu still fails.  Not only does it not auto detect the new broadband connection, it fails when I feed it the information I get from my WinXp machine.  The only thing I don't do is put in a domain name and the hosts file entry 127.0.1.1 because I don't know what those should be.  Also, i unplug the cable from my winXP machine and put it in the Edubuntu machine after getting network information so I'm not using both at the same time.

---

### Post by reckless2k2 on 2007-05-30
Please give more details as to the internet providers. The reason I ask is because highspeed is very different from dialup and comcast is different than dsl.

---

### Post by kantan on 2007-05-30
The slow one is TDS so for that one it has a domain of tds.net and in the host file it has 127.0.1.1 somethingsomething.tds.net.  TDS is through the phone line and Edubuntu receives its connection through a netgear router.  The faster one is Charter and its cable, Edubuntu receives its connection directly through their cable modem.

---

### Post by reckless2k2 on 2007-05-30
It should be plug and play but it sounds like it's not. I'm not sure which version you are running but you can plug it in and restart networking which is a pain. 

sudo /etc/init.d/networking restart

or you can put a line in /etc/network/interface (i think that's the path). Forgive me it's been a little bit since i touched that file and put auto in the network interfaces. There should be something documented around about it or someone might chime in.

---

### Post by kantan on 2007-05-30
Thanks that worked.  When I first tried it, it didn't work, but atleast it told me that it wasn't receiving any DHCP responses.  I figured I would have to unplug the cable modem and start it again.  I tried the command again and it worked nicely.  Thanks again.

---

### Post by reckless2k2 on 2007-05-31
OHHHHH...well then that's your issue. Part of understanding your environment was getting to understand how things were plugged in. If you are going STRAIGHT from cable modem to NIC, then you'll have to power cycle the cable modem each time you switch between NICs. The cable modem is mapped to the last NIC that was plugged in. So you will have to power cycle it each time. When you go from cable modem > router > PC, you don't have to power cycle the cable modem then because the router is recognized by the cable modem. 

I hope you understand what I mean. If you are going cable modem > PC then the cable modem holds the MAC address of the last NIC plugged in. 

If the "auto" line is in the interfaces file, then the cable modem reset should then cause the PC to query for a new address again. If not you can do it manually.

---

### Post by Robsteranium on 2007-06-02
I was hoping to detect my ethernet card from using this procedure but couldn't.  When I run > ```
sudo /etc/init.d/networking restart
``` I receive this respose:
```
eth0: ERROR while getting interface flags: No such device
```

Iknow that there** is** an ethernet card, and that the physical connection is ok because the XP machine at the other end of the wire recognizes the LAN at the appropriate speed.

No joy with
```
modprobe 8139too
```
either.

Xubuntu 7.04
2.6.20-15-generic kernel
Realtek 8139 (if my memory serves correctly)

Any ideas?

Ta in adv

---

### Post by Robsteranium on 2008-01-09
The answer was:
```
modprobe ne
```

---

