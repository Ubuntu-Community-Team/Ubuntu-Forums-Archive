---
title: "wireless help"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by tyler1175 on 2007-02-10
ok, so I am completely new to linux and iv'e been trying to get my wireless usb adapter zd1211 working for hours i got it working once and when i restarted it didn't work again. So now it recognizes it and when i use iwconfig it says the mac address of the AP and that its connected at 11mb/s , but when i use dmesg the last thing it says is no ipv6 routers present i'm not sure if thats whats making it mess up though im prety sure the problem is i'm not getting an ip address and i have dhcp enabled. any ideas on what to do?

---

### Post by shane634 on 2007-02-10
What version of ubuntu are you using??

If edgy try this:

[http://www.ubuntuforums.org/showthread.php?t=354212&highlight=zd1211](http://www.ubuntuforums.org/showthread.php?t=354212&highlight=zd1211)

 If dapper try this:

[http://www.ubuntuforums.org/showthread.php?t=188654&highlight=zd1211](http://www.ubuntuforums.org/showthread.php?t=188654&highlight=zd1211)

  Good luck and let us know if you resolve it.

---

### Post by tyler1175 on 2007-02-10
im using edgy and I already got the driver working it's just i cant get an ip address from my router i think.

---

### Post by morozj on 2007-02-10
To get it working try using a static IP address. Not sure why but I have never had much success with DHCP so I always use static in my simple environment.

---

### Post by trippinnik on 2007-02-10
i've gotten it working with dhcp.  but sometimes i've had to type dhclient and the command line to connect.  if you're adventurous you might want to try to get the kernel zd1211rw driver to work in the latest kernel.  you can follow these instructions, it's what i've been doing.  Network Manager detect the device and can auto switch between wireless and ethernet.  it also allows WPA without extra configuration.

---

