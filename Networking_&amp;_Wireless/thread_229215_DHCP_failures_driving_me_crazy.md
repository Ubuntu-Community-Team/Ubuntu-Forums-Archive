---
title: "DHCP failures driving me crazy"
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by brallan on 2006-08-04
I would like some help diagnosing this problem.

Around the time my ISP (a nice local linux wireless collective) updated my router firmware (They need to have their own firmware on the linksys) I also updated to dapper, and I began to have problems with the LAN. The techie insists that my constant failure of the router to correctly assign IPs to the daper machines via DHCP is due to my misconfiguration of the network. I find this hard to believe as all I have are a few switches and all of the dapper machines are set to recieve an IP via DHCP. 

The network is a router on the roof receiving a wireless signal which then connects to switches and individual machines, 4 with dapper and others with windows. When I boot up dapper machines, any of several things can happen:

1) The entire network can crash, the router freezes up, even trying to call up the router's IP in firefox fails from any machine, including the machine with XP.
2) The router freezes from ubuntu machines, but not from windows machines.
3) Everything works, but machines are missing on the router DHCP table, even ones that have internet.
4) Everything works fine.

this is rather frustrating, since it seems rather random, and above all since the only reliable solution I have found if to go up to the roof, unplug the router & switches, and plug in each switch on the network one by one, waiting 10 secs between each, often several times a day.

I guess I could just assign a static IP to each dapper machine, but I don't know how.

Any help would be greatly appreciated.

---

### Post by OpsVentus on 2006-08-04
First off I blame your ISP's firmware.
But you could try to put in static ip's.
You can do this in the network manager.
There you put an ip-adres in the range of your router. The gateway is the ip-adres of your router, the first dns-server is also the ip-adres of your router.

If you need more help, tell me the configuration of your network.

Cheers,
Bart.

---

### Post by brallan on 2006-08-04
i would like to blame the firmware too, but there are lots of people using it without problems, many using linux. Since I saw that dapper has some kind of [bug about assigning hostnames]("http://www.ubuntuforums.org/showthread.php?t=55564") with a linksys wrt54g (they appear blank in the DHCP clienttable), I figured the problem was probably with dapper.

At first I thought it must have been a switch problem, but when i changed switches, I still had problems. I wondered about the cables, too, but I never got around to changing cables, since many of them are over 10 m.

I'd like to assign static IPs. Do I need to change anything within the router itself? Can I assign a static IP within the range of the DHCP set (up to 50 starting at ...100) or does it need to be outside this range? I tried to set one static IP within this range and it erased the DHCP client table (though everything else still seemed to work except that particular machine.)

From the router (internal IP: 10.35.230.1), the LAN tree looks like this:  I have a switch (with open lines for laptops) which connects to an AP (a trust) and another switch with a linksys pap2 (voip) and four desktops- one XP box and three dapper boxes, and a final switch connecting one more dapper box.

---

### Post by eXisor on 2006-08-04
First off, I use a wrt54g and have no problems getting a dhcp ip from the router in dapper.

Second, when setting a static ip (you should probably do this in /etc/network/interfaces) you need to choose an ip in the lan subnet but NOT within the routers dhcp allocating range.

Do you have the router's usersname and password? Does it have a browser reachable gui frontend? 
Can you telnet in to look at the config?
Or ssh?

I'm inclined to agree with OpsVentus. It sounds like the router setup is flaky, but you need some way of proving this, hence my questions about whether you can see the router config.

---

### Post by brallan on 2006-08-04
yeah, probably the only thing with the linksys & dapper is that the hostnames don't appear in the dhcp clienttable. I'm not the only one who had this issue:

[http://www.ubuntuforums.org/showthread.php?t=55564](http://www.ubuntuforums.org/showthread.php?t=55564)

I access the router via firefox and I do have the password. I can save it as html as well. while setting static IPs is not the ideal solution, but it will have to do for the moment.

thanks for the advice, I will set the static IPs outside the dhcp range.

---

### Post by eXisor on 2006-08-04
My hostnames appear fine with a dapper/wrt54g setup. 
Are you all on the same domain/workgroup? The only machine I have that doesn't show a hostname is on a different domain.

---

