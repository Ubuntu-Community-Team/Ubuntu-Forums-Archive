---
title: "System Monitor, Firestarter, Network History"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by chris winter on 2010-05-22
Fairly new to Ubuntu, Paranoid ex-Windows user.
Ubuntu 9.10, Fiirefox 3.6.3
Before I get online, I start System Monitor & Firestarter. Firestarter is set as root, which makes me nervous.
Watching the Network History in the Sys Mon window, I'm receiving & sending info,
but the Firestarter active connections doesn't tell me who is sending & receiving.
Just want to know what's coming & going, and where it's going to & coming from.
Is there any way to do this???
:confused:

I switched to Ubuntu after 3 frustrating months of going back & forth with Windows techs.
2 rootkits, 5 reoccurring trojans, numerous malware removed, &  having my business & home computer hacked in 1998 & my identity stolen. ($30,000 on 2 credit cards taken out in my name, w/another $30,000 in interest.) 
Paranoid?  You betcha!
I'm a K.I.S.S. kinda guy, (Keep It Simple, Stupid.), & Linux Ubuntu is that & more.

---

### Post by cariboo on 2010-05-23
Firestarter is no longer recommended, as it hasn't been updated since 2005. The preferred utility to set set iptables rules is ufw for the command line or gfuw for a gui. Ufw installed by default and gufw is in the repositories. If you have a default installation and you haven't installed any services there are no ports listening, so you have nothing to worry about.

I would suggest removing firestarter completely using the following command:

```
sudo apt-get -purge firestarter
```

as it will conflict with ufw.

To check your firewall, enable the iptables rules by opening a terminal and typing:

```
sudo ufw enable
```

then go [here]("http://nmap-online.com/") to check your firewall.

---

### Post by Brackenn on 2010-05-23
Hey, I have Ufw enabled, and I have an application that is running in wine, and it checks back with the home office. I want to block it. I know it checks with somewhere on the Internet, because if I unplug my network cable, the application works fine. but if I try to run it with the network cable plugged in, it tells me it's an 'invalid version'. how do I identify the ip address that it is going to?

---

