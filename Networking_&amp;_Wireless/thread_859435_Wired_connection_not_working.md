---
title: "Wired connection not working"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by jacoblyles on 2008-07-14
I spent some time trying to get my WUSB54G wireless USB adapter to work with encryption in Ubuntu. I finally gave up and decided to run a wire to the router, but now my wired network connection does not work either. I am not sure which steps I followed, but I know I installed a few kernel modules. 

I know the hardware is good because I am dual booting into Windows XP and everything works fine. 

Can anybody help? Being without my Ubuntu half is very frustrating. Thanks.

---

### Post by dca on 2008-07-14
Go into your 'System -> Administration -> Network' settings and see if 'Roaming mode' is enabled.  If it is, see if disabling that helps (but be sure to leave it set to DHCP if that's how your router is set)...

---

### Post by jacoblyles on 2008-07-14
> **dca said:**
> Go into your 'System -> Administration -> Network' settings and see if 'Roaming mode' is enabled.  If it is, see if disabling that helps (but be sure to leave it set to DHCP if that's how your router is set)...

Tried roaming and DHCP, neither works.

---

### Post by freetree on 2008-07-14
Can you ping your router? Try setup a static IP and try.

---

### Post by prshah on 2008-07-14
> **jacoblyles said:**
> 
 I am dual booting into Windows XP and everything works fine. 


Can you post more information about your network? Boot into Windows, then click Start-Run and give the command ```
cmd
```, press enter, then give the command ```
ipconfig /all
``` and post back whatever it spits out. 

Using this information, someone can easily guide you to setup the connection in Ubuntu.

---

### Post by jacoblyles on 2008-07-14
> **freetree said:**
> Can you ping your router? Try setup a static IP and try.

Sorry, I don't know how to do this.

---

### Post by jacoblyles on 2008-07-14
> **prshah said:**
> Can you post more information about your network? Boot into Windows, then click Start-Run and give the command ```
cmd
```, press enter, then give the command ```
ipconfig /all
``` and post back whatever it spits out. 

Using this information, someone can easily guide you to setup the connection in Ubuntu.

Here we go:

Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\User>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : user-b50709e9fb
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : RAWR

Ethernet adapter Local Area Connection 2:

        Connection-specific DNS Suffix  . : RAWR
        Description . . . . . . . . . . . : Attansic L1 Gigabit Ethernet 10/100/
1000Base-T Controller
        Physical Address. . . . . . . . . : 00-1B-FC-CA-68-43
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.107
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 192.168.0.1
        Lease Obtained. . . . . . . . . . : Monday, July 14, 2008 12:53:33 PM
        Lease Expires . . . . . . . . . . : Tuesday, July 15, 2008 12:53:33 PM

C:\Documents and Settings\User>

---

### Post by jacoblyles on 2008-07-14
Is it okay if I bump on this forum if my topic falls off the front page?

---

### Post by tastashkan on 2008-07-14
i have a similare problem i have an acer extensa 5420 and it doesnt run internet wireless nor ethernet plz tell me if u are able to fix your internet problem thxs

---

### Post by jacoblyles on 2008-07-14
I found out that I get an IP address in Ubuntu when I type "lshw -C network" at a terminal prompt, 198.162.1.107 I believe. However, I still get an "address not found" error every time I open up a browser and try to find a webpage. Can anyone help?

---

### Post by prshah on 2008-07-15
> **jacoblyles said:**
> Ethernet adapter Local Area Connection 2:

        Connection-specific DNS Suffix  . : RAWR
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.107
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 192.168.0.1


Fine, now, assuming your ethernet interface in ubuntu is eth0; post the output of the following commands```
sudo mii-tool eth0
sudo dhclient eth0
ping 192.168.1.1
ping www.google.com
ifconfig eth0

```

If you get no errors, try using Internet, otherwise please post back all the above output.

Remember to replace eth0 with the actual name of your interface; give the command ```
ifconfig
``` to list all interfaces, and then choose that which seems most obvious (_not_ lo, usually eth0)

---

