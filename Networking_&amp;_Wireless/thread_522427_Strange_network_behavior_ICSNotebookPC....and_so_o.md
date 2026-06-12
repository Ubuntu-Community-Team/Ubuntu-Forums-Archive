---
title: "Strange network behavior ICS/Notebook/PC....and so on (7.04)"
date: 2007-08-10
forum: Networking &amp; Wireless
---

### Post by gargl on 2007-08-10
Hello.
I've read many forum posts/wikis/google...and so on but I have no idea left, please help me.

So I figured it out myself, but it was so fckng hard... that I think and hope that
many people who got the same strange behavior of their network could find help here.
In advance, sorry for the bad english, I still hope that everybody understands what Im going to say.


First a brief description of the problem:

My Network:

Notebook(NB).....<->.....DesktopPC(PC)....<->......Router(Internet)
ubunut 7.04..................ubuntu 7.04
..................................eth0 192.168.100.6<---->192.168.100.1
eth0<----------------->eth1 192.168.100.77
eth1 WLan

(Textual: My Notebook is connected via a cross-over cable from eth0 to the
eth1 nic in my Desktop PC. And my Desktop PC is connected via a cable to a Router, which
is connected to the Internet (broadband/DSL))


What didnt work (Problems):
I wasnt able ping my PC from my NB and vice versa!
No MATTER WHAT I tried.
Neither could I use my PC as a router for my NB wich was my original intention before it get stucked.

Tried:	DHCP (configuring PC with dnsmasq and ipmasq)
	manual settings, IP, Gateway, DNS ....

Logical I couldn't set up a Router!



What worked:
At home, I was able to connect my NB directly to a WLan Router, using the Internet.
Also very strange, if I turned on "Roaming Mode" I could ping ONE(!) NIC @ my PC from my NB.
But NO other configuration allowed me to do that, except after my solution.





I've read a lot around, recognizing that there are also hardware issues.

But something was all the time strange:
my 'ifconfig'@NB showed up some NIC's among eth0 and eth1 
eth:avah

As far as I know avah is in some way correlated with the programm [http://avahi.org/](http://avahi.org/)
which should enable people to get an easy access to different networks.

...MUCH TIME IN BETWEEN MY RECOGNITION OF THAT FACT AND...




Well whatsoever, to make a long story short, my solution:
If you take a close look to POINT 9 of the FAQ's  [http://avahi.org/wiki/Avah4users#Troubleshooting](http://avahi.org/wiki/Avah4users#Troubleshooting)
> 
I want to bridge two networks that are connected via a VPN regarding mDNS. Avahi doesn't let me!
By default Avahi will not consider a Point-To-Point link (such as a VPN link) for mDNS traffic.
[...]
If you still want to use Avahi with P-t-P links, you can enable the allow-point-to-point= option in Avahi's configuration file.


On my system:
	/etc/avahi/avahi-daemon.conf
(make backup as always before trying stuff!)

search for  allow-point-to-point= and change the value from "no" to "yes".

No that was my solution after it, I could ping, using my PC as router, using internet with my NB and 
all that stuff.



Now some comments on that, first admins here.
If Im right MANY people got problems regarding this issue, so maybe you could make an Wiki out of it?
If my idea is wrong and worked only for me simple ignore my suggestion.

In general:
I REALLY like the approach to make things working out of the box and making them easier.
But please, please, if you implement new functions that cause such a severe change in the way an OS or parts of it 
behaves it would be nice to mention it.
Well to be honest I think it is mentioned anywhere and I didnt read it?
But it take me so much work to figure that out, and if there were a read "sign" saying, "The whole network issues
regarding Ubuntu Feisty Fawn is basically managed by avahi, if any problems aside hardware issues appear,
check out the FAQ of...".
This would have helped me so much.

By the way I still know about the trade-off of making things working out of the box and "controlling them".

But I wont bleat to much, its just...narf, never mind.
Instead of bothering, I would like to thank all developers, forum members and all
the people working at ubuntu realising such a cool project.

Thanks, and may my solution help you, before you spent a day on it ;-)

Bye,
gargl :-)

---

