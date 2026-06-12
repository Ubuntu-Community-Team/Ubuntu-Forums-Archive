---
title: "Reaching secondary IP via eth0 from within docker fails"
date: 2020-10-27
forum: Networking &amp; Wireless
---

### Post by tbressers on 2020-10-27
[COLOR=#445D6E][FONT=&amp]After trying for days I hope someone can help me out over here. 

I would like to connect a docker to the secondary IP on my virtual host, where the applications in the docker use eth0.
[/FONT][/COLOR]
[COLOR=#445D6E][FONT=&amp]The good news is that a ping outside my docker to the secondary IP works (&#8216;ping -I 107.233.216.241 [www.google.com]("http://www.google.com/")&#8217;).
[/FONT][/COLOR]
[COLOR=#445D6E][FONT=&amp]I&#8217;ve setup a user network (macvlan) as well using:[/FONT][/COLOR]
[COLOR=#445D6E][FONT=&amp]docker network create -d macvlan --subnet=107.233.216.241/24 --gateway=107.233.216.254 my-macvlan-net[/FONT][/COLOR]
[COLOR=#445D6E][FONT=&amp]
PS: I&#8217;m not completely sure about the gateway, but I used extension 254 because my main IP uses the same gateway, and if I ommit this parameter it is set to extension 1, which doesn&#8217;t work either.[/FONT][/COLOR]
[COLOR=#445D6E][FONT=&amp]
Then I connected via:[/FONT][/COLOR]
[COLOR=#445D6E][FONT=&amp]docker run --rm -dit --network my-macvlan-net --name my-macvlan-alpine --ip 107.233.216.241 alpine:latest ash[/FONT][/COLOR]
[COLOR=#445D6E][FONT=&amp]
Now a ping to Google from within the docker yields:
[SIZE=3][FONT=system]ping: bad address &#8216;[www.google.com]("http://www.google.com/")&#8217;[/FONT][/SIZE][/FONT][/COLOR][SIZE=3][FONT=system]
[/FONT][/SIZE][COLOR=#445D6E][FONT=&amp]
(note that a ping to an existing IP just doesn&#8217;t give data back)[/FONT][/COLOR]
[COLOR=#445D6E][FONT=&amp]
An &#8216;ip a&#8217; from within the docker gives:
[/FONT][/COLOR]
[SIZE=3][FONT=system][COLOR=#445D6E]1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN qlen 1000
link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
inet 127.0.0.1/8 scope host lo
valid_lft forever preferred_lft forever
117: eth0@if116: <BROADCAST,MULTICAST,UP,LOWER_UP,M-DOWN> mtu 1500 qdisc noqueue state UP
link/ether 02:42:6d:ed:d8:f0 brd ff:ff:ff:ff:ff:ff
inet 107.233.216.241/24 brd 107.233.216.255 scope global eth0
valid_lft forever preferred_lft forever[/COLOR]
[COLOR=#445D6E]And an &#8216;ip route&#8217; from within the docker gives:[/COLOR]
[COLOR=#445D6E]default via 107.233.216.254 dev eth0
107.233.216.0/24 dev eth0 scope link src 107.233.216.241[/COLOR]
[/FONT][/SIZE][COLOR=#445D6E][FONT=&amp]
Any tips to help me out?[/FONT][/COLOR]

---

