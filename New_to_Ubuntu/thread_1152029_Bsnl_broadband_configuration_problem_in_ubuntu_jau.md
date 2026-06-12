---
title: "Bsnl broadband configuration problem in ubuntu jaunty jackalope"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by t_k_majumdar on 2009-05-07
I recently installed ubuntu jaunty jackalope. Its a pleasure to install through both Desktop & Alternate CDs for i386 architecture. My experience in linux is only 3 months old but I had no problem installing it. However, configuring the BSNL Broadband via ADSL modem is giving some unexpected problem. 

I can configure internet connection by typing " sudo pppoeconf" in a terminal and accepting the defaults. It would go flawlessly and I could surf the net. After switching off the computer or terminating the connection with "sudo poff -a"; the reconnection can also be established via command " sudo pon dsl-provider". But, now, I can't surf the net and the plog command shows that there are some errors. This can be remedied by starting the whole process again by typing " sudo pppoeconf"!So, each time I want to connect to the net, I shall have to configure the connection from the fresh.

What is the solution? 

Another question : Is there any way in ubuntu 9.04 to continuously display the internet connection parameters or at least whether the connection is alive and working or not?

---

### Post by cariboo on 2009-05-07
Have tried setting up your connection using Network Manager? Right-click and select Edit Connections, then click the DSL tab.

---

### Post by t_k_majumdar on 2009-05-08
Thanks cariboo907 for your helping gesture. I tried it before sudo pppoeconf but it does not work.

---

### Post by golusweet on 2009-05-08
Configure your adsl modem, and supply username and password.

Adsl Modem will connect to the internet automatically when you turn it on.

No configuration needed in ubuntu.:)

Check settings of your modem, open using this address in browser, 

[http://192.168.1.1](http://192.168.1.1)

---

### Post by superprash2003 on 2009-05-08
also post output of **ifconfig** from the terminal

---

### Post by t_k_majumdar on 2009-05-09
First of all, I like to thank Prashanth and golusweet for taking interest in the problem.

Dear golusweet - I am sorry to say that I right-click the Network icon > Edit connection > DSL > Add > DSL Tab > suppy username & password > check connect automatically > close. This shows a DSL connection 1 .......Never. Right-clicking the network icon > enable connection does not connect  and connection information says "No valid active connections found!".
Connecting to [http://192.168.1.1](http://192.168.1.1) gave me many details of the modem, but I don't have the ability to understand or utilize them in any fruitful way.


Dear Prasanth - 

I downloaded your tutorial but must confess that I shall need some time to understand it. How setting up DHCP server will help this problem?

_This is the output of ifconf file after unsuccessful attempt to connect to net :_
ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:888 errors:0 dropped:0 overruns:0 frame:0
          TX packets:888 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:70776 (70.7 KB)  TX bytes:70776 (70.7 KB)

_..and the same after successful attempt to connect to net :_
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:a1:b0:10:85:c7  
          inet6 addr: fe80::2a1:b0ff:fe10:85c7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1161 (1.1 KB)  TX bytes:933 (933.0 B)
          Interrupt:11 Base address:0xdc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:592 (592.0 B)  TX bytes:592 (592.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:117.194.231.133  P-t-P:117.194.224.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1460  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:343 (343.0 B)  TX bytes:94 (94.0 B)

---

### Post by superprash2003 on 2009-05-10
the "check out my tutorials" is my signature.. just a link to my blog.. it has nothing to do with your problem.. you dont  need a dhcp server :) .. your eth0 isnt getting an ip address. thats probably why you are facing this issue. in your terminal type **sudo dhclient eth0** and post output.. this should hopefully give eth0 an ip address from your router.

---

### Post by t_k_majumdar on 2009-05-10
You are really helpful. Yes, I think you are right in diagnosing the cause of the problem.
_The output of "sudo dhclient eth0" without net connection :_

sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:a1:b0:10:85:c7
Sending on   LPF/eth0/00:a1:b0:10:85:c7
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.2 from 192.168.1.1
bound to 192.168.1.2 -- renewal in 19648 seconds.

[U]and while connected to the net : 
[/U]
sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:a1:b0:10:85:c7
Sending on   LPF/eth0/00:a1:b0:10:85:c7
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 192.168.1.2 from 192.168.1.1
DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.2 from 192.168.1.1
bound to 192.168.1.2 -- renewal in 18632 seconds.

---

### Post by superprash2003 on 2009-05-11
so when you didnt have the internet connection.. and when you type that command, did internet start working after that?? it should have , cause you got an ip 192.168.1.2 from your router..

---

### Post by t_k_majumdar on 2009-05-11
Yes, it works. 

So, the problem now narrows down to: how to configure settings so that the computer gets ip address automatically instead of opening terminal and typing the command "sudo dhclient etho" each time before connecting to the net?

---

### Post by superprash2003 on 2009-05-11
well.. it should pick up an ip actually.. you could use static ip otherwise.. [http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html](http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html)

---

### Post by jayaramk on 2009-05-12
well i too have the same problem... the problem started when i installed the nvidia graphics driver.. before to that everything was ok...

before installing the graphics driver i used to have a connection "auto eth0" in my network manager... but after that that connection was gone... even if i create it... its not getting saved... i also do not get the updates notified from the network manger like connection is established etc etc...

---

### Post by t_k_majumdar on 2009-05-13
The problem is solved. :)Thanks to you, Prasanth and others for helping me. 

Actually, I configured the /etc/interfaces via terminal and it now looks like :
-----------------------------------------------------
auto lo
iface lo inet loopback

iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1
-----------------------------------------------------
I then choosed Open DNS Servers as per the article "Speed Up Web Browsing by Caching DNS to Your Hard Drive in Ubuntu" at [http://ubuntulinuxhelp.com/speed-up-web-browsing-by-caching-dns-to-your-hard-drive-in-ubuntu/](http://ubuntulinuxhelp.com/speed-up-web-browsing-by-caching-dns-to-your-hard-drive-in-ubuntu/).
I changed these lines of /etc/pdnsd.conf file from :
	label = "root-servers";
	root_server=on;
to:
label = "OpenDNS";
	ip=208.67.220.220,208.67.222.222;
	root_server=off;
This worked.

However, following settings also works; probably better as per query time for the command Dig.ubuntu.com  in terminal:

------------------------------------------------------
auto lo
iface lo inet loopback


iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1
gateway 192.168.0.1
-----------------------------------------------------

Long-live ubuntu!

---

### Post by rohitfeb14 on 2009-06-27
I tried to connect via the network manager but failed.., Iv guess there is some problem either with authentication methods or some ip assigning problem...... Please help..:confused:

---

### Post by medya on 2009-10-30
Guys I have the same problem, 
I have to poff and also pppoeconf every time I start ubuntu .

what should I do ?


and [http://192.168.1.1](http://192.168.1.1) doesn't give me my modem's config panel .
how could I find my modem's panel's ip ?

---

