---
title: "SSH refusing connections"
date: 2014-05-23
forum: Networking &amp; Wireless
---

### Post by mckinnonryall on 2014-05-23
I'm writing a script that uses  SSH. I ran "arp" and got these results:
```
/$ arp
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.1.2              ether   28:be:9b:1a:de:3e   C                     wlan0
192.168.1.5              ether   00:1c:c3:9e:b8:55   C                     wlan0
192.168.1.4              ether   00:19:df:d3:5e:4b   C                     wlan0
192.168.1.3                      (incomplete)                              wlan0
192.168.1.1              ether   20:4e:7f:3f:f4:1c   C                     wlan0
192.168.1.104                    (incomplete)                              wlan0
192.168.1.250                    (incomplete)                              wlan0
192.168.1.31             ether   e0:46:9a:7a:25:2a   C                     wlan0
192.168.1.25             ether   60:6c:66:62:57:cd   C                     wlan0
```
When I type "ssh (ip)", If the HWaddress was "(incomplete)", It returns this:
```
/$ ssh 192.168.1.104
ssh: connect to host 192.168.1.104 port 22: No route to host
```

If I tried to SSH into the others, either this:
```
/$ ssh 192.168.1.31
ssh: connect to host 192.168.1.31 port 22: Connection refused
```
or this:
```
/$ ssh 192.168.1.2



```
happened. I think the latter result (doing nothing) is from trying to connect to an iPhone. The "Connection refused" result is what happens when I try to connect to my other Ubuntu laptop. What am I doing wrong? Do I need to change the port I use? How can I do that? Is the other computer even listening on any other ports? I need this to work on computers that I don't have direct access to, so how can I make sure that it will log in without having to enable SSH - if this is what I need to do - on the target computer.

---

### Post by The Cog on 2014-05-23
Connection refused almost certainly means that the target is not running an SSH server and therefore not listening for connections. Try this command on one of the Ubuntu boxes:
```
sudo apt-get install openssh-server
```
but make sure all its passwords are strong ones.

The incomplete arp entries are attempts to connect to addresses that don't exist on the network - they are not answering arp requests.

You will not be able to ssh into any machines unless they are running an SSH server, so I don't really understand what you are trying to do.

---

### Post by mckinnonryall on 2014-05-23
> **The Cog said:**
> ...means that the target is not running an SSH server.
Ah. I didn't quite understand how SSH works. I can't find a good overview of what SSH does. I'm not sure why the secondary laptop wasn't running a server. My main laptop and secondary laptop were both had Ubuntu installed from the same flash drive, with the same "download extras" settings, and the main one had a server running. They've both only had Ubuntu for a few days.

---

