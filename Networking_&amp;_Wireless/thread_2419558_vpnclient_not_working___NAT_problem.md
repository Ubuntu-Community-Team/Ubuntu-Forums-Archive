---
title: "vpnclient not working  / NAT problem ?"
date: 2019-05-24
forum: Networking &amp; Wireless
---

### Post by sky59 on 2019-05-24
I have VPN server SoftEther running on Ubuntu and it is 99.9999999% working correct.
It encapsulates company network into VPN. It contains also access to internet.
There are computers in company network like [FONT=&amp]10.81.100.142, 10.81.10.2 (ten,two), 10.81.220.3 ...
[/FONT][COLOR=#333333][FONT=&amp]
The gateway IP is 10.81.100.1   (company router with DHCP server)

When I use windows PC with SoftEther client everything works 100% correct. I can browse also internet
over this VPN having avoided geopolitical restrictions when I am abroad.


I also need to run SoftEther client on Ubuntu PC and also on Android tablet. Here the problem starts.
Both behave in the same way so I describe for instance Android situation:

After spending already a lot of time I finished with this "ip route" table that seems to work correct:
(cache is flushed, of course)


[/FONT][/COLOR][COLOR=#333333][FONT=&amp]0.0.0.0/1 dev vpn_banovce scope link[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]default via 192.168.92.1 dev wlan0 [/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]default via 192.168.92.1 dev wlan0 metric 310[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]10.81.0.0/16 dev vpn_banovce proto kernel scope link src 10.81.100.105 [/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]128.0.0.0/1 dev vpn_banovce scope link [/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]192.168.92.0/24 dev wlan0 proto kernel scope link src 192.168.92.131 metric 310 [/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]192.168.92.1 dev wlan0 scope link

[/FONT][/COLOR][COLOR=#333333][FONT=&amp]
vpn_banovce  is  interface created by SoftEther client
IP [/FONT][/COLOR][COLOR=#333333][FONT=&amp] 10.81.100.105 is provided by company router DHCP
[/FONT][/COLOR][COLOR=#333333][FONT=&amp]GW is [/FONT][/COLOR][COLOR=#333333][FONT=&amp] 10.81.100.1[/FONT][/COLOR][COLOR=#333333][FONT=&amp]

wlan0 is internet connection for tablet IP [/FONT][/COLOR][COLOR=#333333][FONT=&amp]192.168.92.131   GW [/FONT][/COLOR][COLOR=#333333][FONT=&amp]192.168.92.1
also provided automatically by DHCP

In this situation I can ping computers on company network [/FONT][/COLOR][COLOR=#333333][FONT=&amp]10.81.100.142, 10.81.10.2 (ten,two), 10.81.220.3 ...

[/FONT][/COLOR][COLOR=#333333][FONT=&amp]but I can not ping 8.8.8.8 and also internet access is not working, so I added this:

[/FONT][/COLOR][COLOR=#333333][FONT=&amp]iptables -t nat -A OUTPUT -j DNAT --to-destination 10.81.100.1[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]iptables -t nat -A POSTROUTING -j MASQUERADE

[/FONT][/COLOR][COLOR=#333333][FONT=&amp]now I can ping everything even 8.8.8.8

but when I try to go on internet I get funny situation, I go into the company router instead to the internet, see screeshots below

I typed into the browser  [www.shmu.sk]("http://www.shmu.sk")    and   [www.dieselpower.cz/forum]("http://www.dieselpower.cz/forum") but response is very funny for me

What have I done wrong? How it should be correct? Thanx in advance for the help I am already desperate....

Does the SoftEther client need to know about the GW 10.81.100.1? The server knows it already....
[/FONT][/COLOR][COLOR=#333333][FONT=&amp]

[/FONT][/COLOR][ATTACH=CONFIG]283308[/ATTACH][ATTACH=CONFIG]283309[/ATTACH][COLOR=#333333][FONT=&amp]




[/FONT][/COLOR]

---

