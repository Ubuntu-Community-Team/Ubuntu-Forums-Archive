---
title: "can't connect to wifi"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by Czubek on 2008-05-16
Hi.
I have laptop Dell Latitude **D620** with
```
Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
``` and Ubuntu 8.04 installed on it.

When I log in and click network manager applet icon I have list of wireless networks. When I select one of them nm-applet changes icon to two balls and blue turning around thing. After some time balls should be green and I should have be connected to network. In my case in about 90% nothing happens - I'm not connected to network. I can't connect to public network or wep2 encrypted network.
When I used Ubuntu 7.10 I had the same problem but proportions of connection fail were inverted.

I don't have any idea what's wrong and where start to fix it.

Laptop spec:
- intel core duo 1,66 ghz
- 1 gb ram
- intel mobile 945gm/gms video card

Thanks

---

### Post by chili555 on 2008-05-16
Please check my post #2 here: [http://ubuntuforums.org/showthread.php?t=796389](http://ubuntuforums.org/showthread.php?t=796389)

---

### Post by chili555 on 2008-05-16
I understand you cannot connect. What have you tried so far?

---

### Post by Czubek on 2008-05-17
I tried Wicd instead of Network Manager. The same problem. As I noticed in 7.10 when I try to connect NM was trying to connect for about 2-3 minutes and fail. In 8.04 it trying to connect all time, without stop.

---

### Post by chili555 on 2008-05-17
Do you have a running ethernet connection? Before you try to start wireless, detach the wire and:```
sudo ifdown eth0
```Have you tried the manual way?```
sudo iwconfig eth1 essid <ur_essid>
sudo iwconfig eth1 key <any_encryption_here?>
sudo dhclient eth1
```Substitute your details.

---

### Post by fh_scott on 2008-05-17
i'm having similar issues.  initially after installing 8.04 the status light wouldn't come on regardless of connection status.

i installed the backport drivers and that remedied that, but still at a minimum i need to 'sudo ifup eth1' when i power up the machine or return it from stand by to get the wifi to come up.  and that's assuming i am connecting to the same ap that i connected to immediately previously.

if i have moved networks, then there's a fair amount of restarting the networking service and re-connecting to the ap, despite saved settings before i can get an ip.

---

### Post by Czubek on 2008-05-22
I have noticed that I can connet to public acess point but I cant connect to my home wep2 protected network.

My syslog: [http://wklej.org/id/8e2979d5a1](http://wklej.org/id/8e2979d5a1)

---

### Post by psychoxfreak on 2008-12-29
i have a hp pavilion dv9000 i cant get my wireless internet to work on ubuntu but i can get the wired connection just fine only problem is i dont have access to the wired connection anymore i need help setting up my wifi please someone help me i dont know how to do this and this is my only os on my computer since i got it.  thanks

---

