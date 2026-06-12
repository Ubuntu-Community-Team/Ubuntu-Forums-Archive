---
title: "Internet Access"
date: 2008-09-08
forum: Networking &amp; Wireless
---

### Post by sunilkumar on 2008-09-08
Hi I posted a topic in absolute Beginner Talk. It went to 5 pages without solving the problem.

I am newbie to linux. Please help me.

My post is [here]("http://ubuntuforums.org/showthread.php?t=909325&page=5")

the first page is here [http://ubuntuforums.org/showthread.php?t=909325](http://ubuntuforums.org/showthread.php?t=909325)

I am desparate now and want to solve or remove UBUNTU.

Anyway, you guys are very helpfull. A big THANKS for that.

Regards,
-S-

---

### Post by mips on 2008-09-08
In Windows XP click on "Start", click on "Run Command", enter 'cmd' and enter 'ipconfig /all' in the dos box and paste the output here.

Edit: Who's is your ISP and post a link to their website please.

---

### Post by sunilkumar on 2008-09-08
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\sunil>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : four-927e7a5b90
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Realtek RTL8168C(P)/8111C(P) PCI-E G
igabit Ethernet NIC
        Physical Address. . . . . . . . . : 00-1D-7D-74-6E-5B
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.101
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 84.235.126.138
        

This is the out put of ipconfig /all command in Win XP.
My ISP is [http://www.stc.com.sa](http://www.stc.com.sa)

Regards,
-S-

---

### Post by mips on 2008-09-08
First try and configure ubuntu for Static IP address settings instead of dhcp. Just to see if it works or not. Just do it via the GUI under preferences (sorry don't know the exact location as I have not used gnome in ages.

Use the above addresses you posted

IP Address. . . . . . . . . . . . : 192.168.1.101
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Default Gateway . . . . . . . . . : 192.168.1.1
DHCP Server . . . . . . . . . . . : 192.168.1.1
DNS Servers . . . . . . . . . . . : 84.235.126.138

---

### Post by sunilkumar on 2008-09-08
Thanks for ALL. I tried the static IP address. Try to ping 82.211.81.158 and 216.239.57.83 I got 0% success rate. Then I gave following commands from my previous posts, again:

ifconfig

lspci

ifconfig

iwconfig



All these to check the status and to give you the report. Then I tried the command

sudo pppoe-start


echo "127.0.1.1 sunil-Desktop" | sudo tee -a /etc/hosts

(to free the DNS?)

sudo dhclient -r

sunil@sunil-desktop:~$ sudo dhclient -r

Internet Systems Consortium DHCP Client V3.0.6

Copyright 2004-2007 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



Listening on LPF/eth0/00:1d:7d:74:6e:5b

Sending on   LPF/eth0/00:1d:7d:74:6e:5b

Sending on   Socket/fallback

DHCPRELEASE on eth0 to 192.168.1.1 port 67

send_packet: Network is unreachable

send_packet: please consult README file regarding broadcast address.

sunil@sunil-desktop:~$ sudo dhclient

There is already a pid file /var/run/dhclient.pid with pid 134519072

Internet Systems Consortium DHCP Client V3.0.6

Copyright 2004-2007 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



Listening on LPF/eth0/00:1d:7d:74:6e:5b

Sending on   LPF/eth0/00:1d:7d:74:6e:5b

Sending on   Socket/fallback

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3

DHCPOFFER of 192.168.1.101 from 192.168.1.1

DHCPREQUEST of 192.168.1.101 on eth0 to 255.255.255.255 port 67

DHCPACK of 192.168.1.101 from 192.168.1.1

bound to 192.168.1.101 -- renewal in 38203 seconds.

sunil@sunil-desktop:~$ sudo /etc/init.d/network restart

sudo: /etc/init.d/network: command not found

sunil@sunil-desktop:~$ 


This was the last part :):):) Blind man driving his car. AlaS! Just tried with Firefox and the net was available! I am typing this from UBUNTU.

But,
Still I am not able to ping. Why?
Cant surf with my laptop (wireless Win XP again). What is the problem? Or is it related to this?
If I re-started the system, what will happen? The connection will go? In that case what should I do?

THANK YOU FOR ALL.

Regards,
-S-

---

### Post by jimv on 2008-09-08
Not all sites/ip addresses respond to PING requests.  That would be funny if that was the case.

---

### Post by sunilkumar on 2008-09-08
If I restarted the computer what will happen?
What was the problem? What was the meaning of the commands I gave?
How it worked?
Can you please explain?

Thanks for All.

Regards,
-S-

---

### Post by sunilkumar on 2008-09-08
I tried after restarting, but the connection was gone!
Then I gave the command **sudo dhclient**
After this it was working!

Why configuration is not saved? How can I save the configuration? Waht to do?

Lots of questions:):):) Learning curve...

Regards,
-S-

---

### Post by jimv on 2008-09-10
make sure your /etc/network/interfaces file contains these lines:

```
auto eth0
iface eth0 inet dhcp
```

Make sure that these are the only two lines that contain eth0.

---

### Post by Bucky Ball on 2008-09-10
Hi sunilkumar. Don't change your file, follow jimv's instructions. He is more on top of this than I and am just posting this in case it gives him any ideas. :)


jimv - just wondering if this would help in the /etc/network/interfaces file at boot considering 'sudo ppp0 start' seems to be working later:

auto ppp0

That was in the original /etc/network/interfaces file. The original file, before any changes, was this:

```

auto lo
iface lo inet loopback

iface ppp0 inet ppp
provider ppp0

auto ppp0

iface eth0 inet ipv4ll

auto eth0
```Thought that might give you some ideas. I was helping sunilkumar in the other forum. You are having much better luck, though! Good one.

---

