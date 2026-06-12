---
title: "Public wifi causing disconnection for reason=4 Disassociated due to inactivity"
date: 2019-09-30
forum: Networking &amp; Wireless
---

### Post by p5music on 2019-09-30
Hello,
I am experiencing frequent disconnections when using a public wi-fi network. Many other users experience the same.
The reason is that the network at some point (very soon, very often) stop transmitting data. So the main reason for disconnections is just reason=4 Disassociated due to inactivity - Client session timeout exceeded.
Note that there is no constant behavior. It happens that at certain times in the late afternoon the system has better performances. In rare times it has no issues for long times.
Sometimes buffered videso suffer less of this issue because buffering can benefit from intermittent data flow. But usually data do not come back after disconnection.
My equipment works well in other environments. Wi-fi signal is not weak because all this happens also when being in the room with the wi-fi antenna on the wall.
I would like to assess what's going on.
I read on the internet that old wi-fi equipment can have issues and disconnect users for whatever reason.
The wi-fi provider do not collaborate, so they neither acknowledge the problem, nor perform any sort of on-site technical test.
I would like to know if any tool exists to assess that their equipment is doing bad.
Thanks in advance

```

pc@pc:~$ journalctl --since="2019-10-01 11:54:00" --until="2019-10-01 11:57:00"
-- Logs begin at Thu 2019-08-29 18:20:32 CEST, end at Tue 2019-10-01 12:20:52 CEST. --
ott 01 11:54:06 pc wpa_supplicant[935]: wlp2s0: CTRL-EVENT-DISCONNECTED bssid=6c:3b:6b:11:e2:0f reason=4 locally_generated=1
ott 01 11:54:07 pc wpa_supplicant[935]: wlp2s0: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
ott 01 11:54:06 pc NetworkManager[934]: <warn>  [1569923646.9611] sup-iface[0x556a6debc130,wlp2s0]: connection disconnected (reason -4)

```

---

### Post by jimmyrus on 2019-10-03
> **p5music said:**
> Hello,
I am experiencing frequent disconnections when using a public wi-fi network. Many other users experience the same.
The reason is that the network at some point (very soon, very often) stop transmitting data. So the main reason for disconnections is just reason=4 Disassociated due to inactivity - Client session timeout exceeded.
Note that there is no constant behavior. It happens that at certain times in the late afternoon the system has better performances. In rare times it has no issues for long times.
Sometimes buffered videso suffer less of this issue because buffering can benefit from intermittent data flow. But usually data do not come back after disconnection.
My equipment works well in other environments. Wi-fi signal is not weak because all this happens also when being in the room with the wi-fi antenna on the wall.
I would like to assess what's going on.
I read on the internet that old wi-fi equipment can have issues and disconnect users for whatever reason.
The wi-fi provider do not collaborate, so they neither acknowledge the problem, nor perform any sort of on-site technical test.
I would like to know if any tool exists to assess that their equipment is doing bad.
Thanks in advance

```

pc@pc:~$ journalctl --since="2019-10-01 11:54:00" --until="2019-10-01 11:57:00"
-- Logs begin at Thu 2019-08-29 18:20:32 CEST, end at Tue 2019-10-01 12:20:52 CEST. --
ott 01 11:54:06 pc wpa_supplicant[935]: wlp2s0: CTRL-EVENT-DISCONNECTED bssid=6c:3b:6b:11:e2:0f reason=4 locally_generated=1
ott 01 11:54:07 pc wpa_supplicant[935]: wlp2s0: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
ott 01 11:54:06 pc NetworkManager[934]: <warn>  [1569923646.9611] sup-iface[0x556a6debc130,wlp2s0]: connection disconnected (reason -4)

```
How would we know? You haven't given us information that would give anyone any clues. What kind of wifi hardware do you have and what version of ubuntu? Who is the wifi provider and have you tried a different wifi adapter? Get a cheap usb dongle for $20 or so just to see if the problem goes away, or follows your system. What kind of wifi access point do you have? If its provided by your isp, they will usually change it for free if it keeps dropping you.

---

### Post by p5music on 2019-10-05
@[**[COLOR=#000000]jimmyrus[/COLOR]**]("https://ubuntuforums.org/member.php?u=2133269")

My system is ASUS S300CA with this OS                    [URL="https://ubuntuforums.org/member.php?u=2133269"][B][COLOR=#000000]

```

Operating System: Kubuntu 19.04
KDE Plasma Version: 5.15.4
KDE Frameworks Version: 5.56.0
Qt Version: 5.12.2
Kernel Version: 5.0.0-29-generic
OS Type: 64-bit
Processors: 4 × Intel® Core&#8482; i5-3317U CPU @ 1.70GHz
Memory: 3,7 GiB of RAM


```[/COLOR][/B][/URL]

but the issue does not depend on which operating system is installed. Indeed it is experienced also with Windows and Android.

All this OSes have the same issue with the public network I amtalking about, while do not have any disconnection with other networks, like phone tethering and different wifi home routers or public hotspots.
Disconnections are so much frequent that the network is not useable.
The disconnection does not appear in the Network Manager because it still seems to be connected. It is just a data disruption, it is like the user is dropped.

In fact there are two parallel networks based on the same infrastructure.
I am using a special script to switch between the two networks when one of them disconnects. It mitigates the problem. Also reconnecting the same network works but it is a random thing so the switching script is more suitable for me as I have found, and I can to use the internet somehow in the place served by those two wifi access points.
The fact is that it's not a matter of temporary failure, indeed the network is still working.

I am interested in discovering what is happening at the moment of disconnection. I think that the system has a special weakness that drops the user when it has to connect someone else, but it is not acceptable, and the connection is up for very short time. It is also possible that some awkward expedient is being used to show that many users are served, while it is not so, not even at a basic web-navigation level. This is a public service, very expensive for the public institution that pays for it.

I would like to have some tools to run, to discover the technical event that happens so to officially protest. They do not acknowledge the issue, they do not collaborate.

---

### Post by jimmyrus on 2019-10-06
> **p5music said:**
> @[**[COLOR=#000000]jimmyrus[/COLOR]**]("https://ubuntuforums.org/member.php?u=2133269")

My system is ASUS S300CA with this OS                    [URL="https://ubuntuforums.org/member.php?u=2133269"][B][COLOR=#000000]

```

Operating System: Kubuntu 19.04
KDE Plasma Version: 5.15.4
KDE Frameworks Version: 5.56.0
Qt Version: 5.12.2
Kernel Version: 5.0.0-29-generic
OS Type: 64-bit
Processors: 4 × Intel® Core™ i5-3317U CPU @ 1.70GHz
Memory: 3,7 GiB of RAM


```[/COLOR][/B][/URL]

but the issue does not depend on which operating system is installed. Indeed it is experienced also with Windows and Android.

All this OSes have the same issue with the public network I amtalking about, while do not have any disconnection with other networks, like phone tethering and different wifi home routers or public hotspots.
Disconnections are so much frequent that the network is not useable.
The disconnection does not appear in the Network Manager because it still seems to be connected. It is just a data disruption, it is like the user is dropped.

In fact there are two parallel networks based on the same infrastructure.
I am using a special script to switch between the two networks when one of them disconnects. It mitigates the problem. Also reconnecting the same network works but it is a random thing so the switching script is more suitable for me as I have found, and I can to use the internet somehow in the place served by those two wifi access points.
The fact is that it's not a matter of temporary failure, indeed the network is still working.

I am interested in discovering what is happening at the moment of disconnection. I think that the system has a special weakness that drops the user when it has to connect someone else, but it is not acceptable, and the connection is up for very short time. It is also possible that some awkward expedient is being used to show that many users are served, while it is not so, not even at a basic web-navigation level. This is a public service, very expensive for the public institution that pays for it.

I would like to have some tools to run, to discover the technical event that happens so to officially protest. They do not acknowledge the issue, they do not collaborate.
You haven't said what you're connecting to. If this wifi is provided by your ISP, then tell them you need a new router because the one you have is junk. If this is public wifi then don't complain. They have tons of users and I'm certain they have tons of people whining about how bad things are, whether they are or not, and they're probably not. Most user complaints about free services are caused by what users do or the problems don't exist anywhere outside their own minds. Public wifi can limit or drop if you do things they dont like, like bittorrent, videos, or junk like that. Typically there for basic web and email. If you have no problems with tethering, then use it since that seems to be a simple solution to the not-at-all-linux-related problem your having. You need to see network logs to find out why the remote network is dropping you so unless you have them theres nothing your going to see on your system that doesn't just say "disconnected".  

Very good chance its either your "special script" or what your doing on the network that's causing your problem. If you don't like what your getting for free then don't use it.

---

