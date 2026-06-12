---
title: "wireless problem and network analysis"
date: 2007-05-27
forum: Networking &amp; Wireless
---

### Post by AlexenderReez on 2007-05-27
i'm using belkin usb adapter,which is as for whole of guide in internet state...i should be using wlan wireless connection,after install its windows wireless driver by using  ndiswarpper  ....but strangely ...after fresh install feisty on my computer...my wireless work perfectly....using eth1 connection....i wonder why...and why it is happen like that(even without install its driver...so i decided don't want to install driver).....i have test my belkin wireless adapter on a computer that install ubuntu ultimate edition ....as all we know ubuntu ultimate edition comes with complete install important and useful sotware by default..it is including ndiswarpper ...and strangely after install its windows driver on that particular computer....it detect wlan connection ....do i need to care whether i'm using **wlan** or **eth1** connection....?i hope to get help and explaination about this situation...


as i'm using wireless that doesn't provided with encryption or any kind of security ...which is mean perfectly understood it using parent control over what user access . . .i need to log in my username and password to access webpage/ or log in page before access other website .....this is look great but ofcouse it bring a lot of problem than good conclusion. . .most of the time when i insert my username and password.....it will take me to same place after i enter/log in,which is mean i can't login....it is also mean its parent control having problem with that...(if it is not having problem then i can straight away access to other website.....)...when i click to other website address ...it will bring me to log in page....and this stupid thing will keep happen untill server restart or i having blackout then electricity on again(which also perfectly understood , server restart )...but the problem is , i'm not the one who manage when the server will restart...i have ask to company that provide this wireless connection ...and  keep getting same answer ...they will restart the server....it will take 2 or 3 days or more times for them to do that....(i don't why)...and this problem keep happen and pissing me off after that....i keep complaining this problem...and explain the situation but same...them will keep reasoning the same answer...they can't do much except to restart the server....

my question is....is there any network hacking(NOT cracking) to solve this problem....to get rid from log in page or to settle problem when i click log in enter...it will proceed to next website...please ....


as i'm writing as posting to this forum..it is perfectly understood that i'm using normal connection right now.....and i can't do any wireless testing to show to anybody...but as i mention above .....it is more than enough information and all infrmation that i can give from wireless testing.....i expect help and explaination

---

### Post by AlexenderReez on 2007-05-27
this is few sceenshoot that i have took incase my explaination is not clear....


> reez@aLeXeNdeRreEz:~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth1.pid with pid 17155
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:11:50:b4:14:11
Sending on   LPF/eth1/00:11:50:b4:14:11
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 10.0.11.254 port 67
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:11:50:b4:14:11
Sending on   LPF/eth1/00:11:50:b4:14:11
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                         [ OK ]


---

### Post by ruy_lopez on 2007-05-27
You don't need to worry about your Wireless settings. I wish I could help you. That page is hidden from the outside world.

You can try some of these:

[http://www.3proxy.com](http://www.3proxy.com)
[http://www.alienproxy.com/](http://www.alienproxy.com/)
[http://www.cleverproxy.com/](http://www.cleverproxy.com/)
[http://www.freetoview.net/](http://www.freetoview.net/)
[http://www.ibypass.com/](http://www.ibypass.com/)

I don't know if this is what you are looking for.

---

### Post by AlexenderReez on 2007-05-27
> **ruy_lopez said:**
> You don't need to worry about your Wireless settings. I wish I could help you. That page is hidden from the outside world.

You can try some of these:

[http://www.3proxy.com](http://www.3proxy.com)
[http://www.alienproxy.com/](http://www.alienproxy.com/)
[http://www.cleverproxy.com/](http://www.cleverproxy.com/)
[http://www.freetoview.net/](http://www.freetoview.net/)
[http://www.ibypass.com/](http://www.ibypass.com/)

I don't know if this is what you are looking for.

thanks for concern....i will check those web lists...at least i 'm sure i will learn something new.....and i love learning...thanks....:KS

---

### Post by AlexenderReez on 2007-05-27
do you know how to integrate those all thing to synaptic...i need it to upgrade my software.....actually i have other alternative but.....i want to try this...i really appreciate any help....

---

