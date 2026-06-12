---
title: "Browser problem"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by ICUR2Ys on 2007-03-04
Hi
I am brand new to linux.  I have installed 6.1 on my desktop.  I get notices for software updates and I am able to download them without a problem.  However, firefox times out and cannot connect most of the time.  sometimes it will connect.  I have an actiontec gt701-wg DSL modem, and a linksys wireless -G router connected with cable.  This worked fine with windows xp on both of my computers.  Now my windows computer still works and I am using firefox on it.  I am not very technical in this area.  I would appreciate any help that you folks can provide.  Thank You.

---

### Post by chili555 on 2007-03-04
You might try this: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by ICUR2Ys on 2007-03-05
Thank you Chilli555.  I followed the instructions and disabled v6 but nothing changed.  It is interesting that I installed Xchat and that also works fine.  I just can't use a browser.

---

### Post by ICUR2Ys on 2007-03-10
I also installed Pan and it doesn't work.  Msg in log says  handshake failure.

---

### Post by chili555 on 2007-03-11
May we see the output of cat /etc/resolv.conf please?

---

### Post by ICUR2Ys on 2007-03-11
Please excuse my ignorance, I didn't know what you asked so I opened a terminal and entered it there.  I did get a response:  search domain.actdsltmp
                                         Nameserver 192.168.8.1
                                         Nameserver 198.6.1.3
If this is not right please tell me what to do.

Thank You very much

Tom

---

### Post by chili555 on 2007-03-11
You did perfectly.

Open that same terminal and type route -n. You should get something like this: ```
chili@LAPTOP:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
```
The Gateway is the IP address of your router and I am suspicious that it is not 192.168.8.1 as resolv.conf thinks it is.

Let's try the quick and easy fix. Open a terminal and type sudo gedit /etc/resolv.conf. Give your password. A text editor will pop up with the file you posted. We want to comment out the 192.x line, thus: ```
search domain.actdsltmp
**#**nameserver 192.168.8.1
nameserver 198.6.1.3
```

Save and close gedit. Then try surfing the web again and tell us if it improved.

---

### Post by ICUR2Ys on 2007-03-11
Thank You

One step at a time.  I entered route -n and had the identical output that you sent me except that at the end of each line under Iface I had eth0.

Now I will try and do the second part of your msg.

---

### Post by ICUR2Ys on 2007-03-11
I am sorry I am screwing up.  I misread the small font.  Ityped nameserver 192.168.8.1 and it should have been 192.168.0.1.  My apologies.

---

### Post by ICUR2Ys on 2007-03-11
My Dear Chili555,

Thank you very much.  My browser is now working fine.  You are a genius and I am very thankful that you were so kind to take the time to help me.

I am so happy.

---

