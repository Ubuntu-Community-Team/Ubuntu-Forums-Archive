---
title: "[SOLVED] Network stopped working. No default route. How to debug?"
date: 2014-06-06
forum: Networking &amp; Wireless
---

### Post by pierre_masci on 2014-06-06
Hi there, 

The network on my newly (3 days) installed Lubuntu (14.04, amd64) worked perfectly,
until today the network crashed on the router (other people were also affected), and then it came back up for everyone but me.
I'm following [this guide]("http://www.davidpashley.com/articles/network-troubleshooting/") to troubleshoot the issue. 

I know that my network card is detected and my cable is well plugged, because:
```
$** ip link**
eth 0: [...]
eth1: [...]
$ **sudo mii-tool**
eth0: no link
eth1: [...],** link ok**
```
So, I'm dealing with **eth1** here (I have two network cards, one of which I don't use).

I check that I have an IP address, with:
```
$ [B]ip addr show dev eth1
[/B]eth1: [...][SIZE=2][FONT=arial]
[COLOR=#000000]inet 192.168.0.2/24 brd 192.168.0.255 scope global eth1
[/COLOR][...][/FONT][/SIZE]
```[SIZE=2][FONT=arial]

Then I did 
```
$ [B]ip route
[/B][...] docker0 [...]     // I have a docker server running locally, I'm guessing it doesn't interfere. It has not been a problem so far.
192.168.0.0/24 dev **eth1**  proto kernel  scoope link 192.168.0.2 metric 1
```
and realized that **I don't have a default route**. If I had one it would be indicated by "default via" (according the the troubleshooting guide I'm following).

After that I didn't really know what to do: the troubleshooting guide didn't tell what to do in this case.
I looked in several places online, and probably **did a few things** I shouldn't have done:
[LIST]
[*]I did
[/LIST]
```
$ sudo dhclient eth1
```
which wouldn't work ("File exists"), so I forced it with 
```
$ sudo dhclient eth1 -r; sudo dhclient eth1
```
[/FONT][/SIZE]
[LIST]
[*]I modified /etc/resolv.conf manually.
[/LIST]
[SIZE=2][FONT=arial]
[LIST]
[*]I did
[/LIST]
```
$ route add default gw 192.168.0.2 eth1
```
after having deleted the previous route (which was 192.168.0.0/24).

[LIST]
[*]I modified /etc/udev/rules.d/70-persistent-net.rules manually (it caused me trouble on this machine in a previous installation, because I have two network cards).
[/LIST]
But it didn't work, so I deleted both the eth0 and eth1 lines, so they could be re-created a reboot.
[/FONT][/SIZE]
[LIST]
[*]I rebooted the computer a few times, tried to do the operations above in various orders a few times.
[/LIST]

[FONT=arial]The command results that I have copied above, are the ones that I get** now**.[/FONT][SIZE=2][FONT=arial]
I remark that the route is back to 192.168.0.0/24, which is vaguely reassuring. But there is still no default route.

I don't know** what I should do now** to assess the problem and get back to normal.
Any help would be very welcome.

PS: [/FONT][/SIZE][FONT=arial]Because I'm using Lubuntu, I don't have network-manager. It's "play with the command line :D"[/FONT]

---

### Post by pierre_masci on 2014-06-06
Well, after more than an hour of struggle without any result, it's suddenly working again.
I can go on internet.
I have no idea why...
And 'ip route' still does not indicate 'default via'... so apparently it was not necessary.

Ah! I realized that I seem to have network-manager installed:
```
$ dpkg- S network-manager
```
...but i can't use it!
```
$ network-manager
network-manager not found
```
I don't understand.

I'm not marking the matter as solved yet. The exact same thing might happen again any time, I need to understand what happened.
Some of my work online is critical, I cannot afford to have internet stop for an hour all of a sudden.

Any idea what might have happened?

---

### Post by varunendra on 2014-06-06
"network-manager" is a background service, not a command that you can use like that. What you use to manage that service is "nm-tool" applet, which doesn't load by default in the latest version of Lubuntu due to a [bug]("https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/1308348"). Workaround is here : [http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html](http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html)

---

### Post by pierre_masci on 2014-06-06
Thanks a lot varunendra! That's very good help :)

I read a bit more about it Lubuntu, and found out that one of its weak spots is wireless networking. 
Good to know in the future.

---

### Post by varunendra on 2014-06-06
You're welcome!

Please mark the thread as [SOLVED] if you are satisfied and have no more questions. :)

---

