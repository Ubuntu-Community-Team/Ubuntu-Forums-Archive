---
title: "Road Runner Lite and Ubuntu don't Mix?"
date: 2008-08-01
forum: Networking &amp; Wireless
---

### Post by redvamp128 on 2008-08-01
I decided to try the latest release.I now have Road Runner Lite...it has me stumpped 

I can't get online with Ubuntu.


I even put in the numbers for the connection I am on now - Static the connection and still it sends but does not recieve. The network card works.... machine it is installed on is a dual boot....Win2k and Ubuntu 8.

I even tried the auto dhcp... no luck after leaving it connected for 15min.

I tried the Ipv4ll .... as well as the roaming...

Anyone have any suggestions....

I even tried the term- ifup

ifconfig gives what I take as an internal number. but nothing close- I even tried adding the sc.rr.com to my dns- but it won't even let me type the S of the sc.rr.com in dns. I also put the number in as well... Still no luck.
Ping says not connected... It says I have 3 connections...

Loopback- Eth0:lo Eth0:avihi


Any suggestions- I even tried it on Live Cd... and also tried Puppy linux(live) and still no luck. But normally I use this computer I am typing on to connect using MSVP2007...

Any suggestions... Now it will take me time to reply back. Because I have to switch between computers.(the Cat 5-cable) in the back of the modem.

Funny thing though is that DSL gets online.

What is strange is that I booted up DSL linux (live) and it found the internet and worked very well. Just thought the latest Ubuntu release would have worked just as well.

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

?? Would love to get the other Computer online??

---

### Post by redvamp128 on 2008-08-03
I would love to get this computer online and before someone says it... I should not have to buy a router since I am not on that computer on a daily basis- More like weekly... and possibly more if I can get it online.


Thanks in advance.

---

### Post by mrbannerman on 2008-08-03
I'm not sure if I am going to be of much help. However, here it is. RR, at least in Texas, needs a login script. Dialling in with username and password doesn't connect. I have googled in the past and found vague descriptions of how it can be set up. Try googling login.scp Linux road runner and see what comes up.
Here's one that looks helpful -
[http://www.belikoff.net/rr-dialup-in-linux](http://www.belikoff.net/rr-dialup-in-linux)
Good Luck,
MRB:)

---

### Post by redvamp128 on 2008-08-03
I do not have to dial into it- It is attached by Cat-5 cable To the Arris Modem. No Password Required. With Windows It picks up an Ip address and goes online.  With Ubuntu it just sits there- No matter how many configs I do.

I even tried putting in the numbers I was using on this computer I am typing on. And Still no luck.

---

### Post by dmizer on 2008-08-04
Try disabling NetworkManager.  After doing this, you will no longer have the network applet in the system tray (by the clock), but you can still configure your network by going to: system > administration > networking

Here's how to disable NetworkManager:

Open a terminal, and copy/paset the following commands into the terminal:
```
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo touch /etc/default/NetworkManager&& sudo echo exit > /etc/default/NetworkManager
sudo touch /etc/default/NetworkManagerDispatcher&& sudo echo exit > /etc/default/NetworkManagerDispatcher
```

Then go to: System > Administration > Networking and configure your network for DHCP

---

### Post by redvamp128 on 2008-08-16
Little Update-

It seems as if the issue is with the Cable Modem-
It seems as if it locks in the Mac(network card) Address of this machine I am typing on now.- I booted the Live Cd of Ubuntu in this machine and it ran and went online.

But when I connect it to the other machine which has a different Mac Address... I would have to take the battery out and unplug it. Then let it sit for a minute and replug it back in. Too Much Trouble.

Anyone Know if I use the  Ubuntu installer to resize XP and install would have issues with this config.

C:\ = 20.4gig Fat32 Windows Me (Location of the Boot.ini- NTLDR)
D:\ =17.7 gig NTFS Windows XP Pro
?


Was thinking of making Ubuntu take about 3gigs of the XP space.

I will be using the latest Heron Edition. 8.04 I believe.

---

### Post by dmizer on 2008-08-16
If the problem is with the modem, you could have fixed the problem by purchasing a router.  That way, Roadrunner only sees the mac address of your router, and you can connect any computer you like with any operating system you like.

---

