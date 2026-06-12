---
title: "Does not turn on Wirless switch"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by komatsu100 on 2009-01-12
Loaded Ubuntu 8.10 on my Acer Aspire laptop and when I open the Ubuntu it does not turn my wireless swithch on, so I have not internet connection.

---

### Post by pytheas22 on 2009-01-13
Please be more specific.  What do you mean when you say Ubuntu 'does not turn the wireless switch on?'  Do you mean that when you press the button to enable your wireless, nothing happens?  Or do you just mean that you have no wireless connectivity?

Please also post the output of these commands:
```

lspci -nn
lsusb
lshw -C Network
dmesg | grep -i radio
sudo iwlist scan
```

---

### Post by komatsu100 on 2009-01-14
When I open Ubuntu my wireless switch turnes off and I can't turn it back on.  Log off Ubuntu and open windows and the swithch automaticly turns on.

---

### Post by Michael.Godawski on 2009-01-14
hi,
pytheas22 is right we need some more input to help you.

First let's make sure Ubuntu has recognized your wlan card and installed the drivers correctly. Please post the output of the commands posted above.

---

### Post by komatsu100 on 2009-01-16
lspci -nn
00.0b.0 Network Controller [0280] Broadcom Corporation BCM 4318 [Airforce one 54g] 802.119 Wireless Lan Controller [14e4:4318] (rev 02)
lsusb
Bus 002 Device 002: ID046d:c50e Logitech Inc. MX-1000 Cordless Mouse Rec. 
Bus 002 Device 001: ID1d6b:0001:Linux Foundation 1.1 root hub
Bus 001 Device 001: ID1d6b:0001:
Bus 003 Device 004: ID413c:5008: Dell Computer Corp.
Bus 003 Device 002: ID 05e3:0608 Genesys Logic,Inc. USB-2.04-port HUB
Bus 003 Device 001: ID 1d6b:002 Linux Foundation 2.0 root hub
lshw -C Network
Network 0 Disabled
description wireless Interface
Physical id:1
logical Name Wlan0
Serial: 00:14:a4:4a:f2:a3
capabilities:ethernet physical wireless
Configuration:broadcast=yes multicast=yes wreless=IEEE 802;11bg
Network 1 Disabled
description:Ethernet interface
physical id:2
logical name:  pan0
serial:a284:da:ad:00:d1
capabilities:ethernet physical
configuration:broadban=yesdrivers=bridge 
drivers version=2.3
firmware N/A
dmesg | grep -i radio
dmesg invalid option---i
sudo iwlist scan
[sudo] Password for username: 
Then it would not allow me to inter a password our move the curser in any direction with anything.  I am new to Linux and if you can give me any information in any way I will appricate it.  Thanks.

---

### Post by komatsu100 on 2009-01-16
I don't know how that smiley face appears on the logical name:  pan0

---

### Post by pytheas22 on 2009-01-16
Thanks for the information.  You have a Broadcom 4318 card, which should work well, although you may need to enable it first.

First, go to System>Administration>Hardware Drivers.  There should be a box for enabling your wireless card.  Check yes, then follow the instructions.

If that doesn't work, please plug your computer into the Internet using an ethernet (wired) cable and run these commands to enable your wireless card manually:
```

sudo apt-get update
sudo apt-get install b43-fwcutter
```

(If you have no way of getting a wired connection, let me know and we can work around it.)
> 
[sudo] Password for username:
Then it would not allow me to inter a password our move the curser in any direction with anything. I am new to Linux and if you can give me any information in any way I will appricate it. Thanks.

Yes, you don't see anything on the screen while you're typing your password; this is for security reasons.  But the computer is still accepting input.  Just type your password and press enter.

---

### Post by komatsu100 on 2009-01-17
Thanks Pytheas22 I appreiacate any help, even with my spelling.  Ha!

---

### Post by pytheas22 on 2009-01-18
Did this solve the problem for you?

---

