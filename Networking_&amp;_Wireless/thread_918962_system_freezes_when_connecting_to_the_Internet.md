---
title: "system freezes when connecting to the Internet"
date: 2008-09-13
forum: Networking &amp; Wireless
---

### Post by hnw555 on 2008-09-13
Hello all,

I am new to ubuntu and linux so this has been a real challenge for me.

I have installed Ubunto hardy on emachines T4200.  The install went fine but I had lots of problems getting the wireless adapter to work.   I an using a dlink dwl-120.  I used ndiswrapper to install the drivers from the original windows install disk from dlink. I think I finally got it going as I could successfully ping an outside url from the terminal window. However, anytime I try to connect to the internet, either with Firefox or doing a system update, the system freezes and I have to do a hard reboot.

Any help would be greatly appreciated.

---

### Post by pytheas22 on 2008-09-13
That sounds like a major problem with ndiswrapper--perhaps it would help to use a different Windows driver.  Please post the output of:
```

lsusb
lspci -nn
```

and we can look up a good driver to use.

Also, does the computer freeze when you type these commands:
```

ping google.com
host google.com
wget google.com
sudo apt-get update
```

---

### Post by hnw555 on 2008-09-13
I solved the issue by purchasing a wireless adapter that actually works with ubuntu.  I purchased a Belkin f5d7050 which worked immediately upon plug in.  It was only $30 at best buy.

---

