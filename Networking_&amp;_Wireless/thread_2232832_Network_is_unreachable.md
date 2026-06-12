---
title: "Network is unreachable"
date: 2014-07-04
forum: Networking &amp; Wireless
---

### Post by wagner3 on 2014-07-04
Hi,

First, I'm completely new to Ubuntu and Linux at all, so I'm sorry if this is a basic question. I did tried to search for similar issues but couldn't find anything helpful.

I'm trying to setup a Proxy Server with Ubuntu 12.04 Server + Squid. I just installed Ubuntu 12.04 server and now I'm trying to setup the network connections.

I'm follow a step by step document to do that. What I have done until now is the following:

used nano to change interfaces to:

```
auto l0, eht0
iface lo inet loopback
iface eth0 inet static
adress 10.68.xx.xx
netmask 255.255.xxx.x
gateway 10.68.xx.x
dns-nameservers 10.68.xx.xx 10.58.xx.xx
```

After this, I used "service networking start" but got the message "service networking stop/waiting.

I also can't ping stuff, got the message "network is unreachable".

Utp cable works fine (tried on other computer)

Again, I'm a complete begginer at this, so any help will be highly appreciated.

Thank you!

Wagner

---

### Post by slickymaster on 2014-07-04
Moved to the **Networking & Wireless** sub-forum.

Hi wagner3 welcome to the forums. I've moved your thread to a suitable sub-forum as it address a networking issue and edit it, [adding code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") to it, because output code posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand.

---

### Post by chili555 on 2014-07-04
May I assume that the typographical errors above are corrected in the actual file?```
auto [COLOR="#FF0000"]l0, eht0[/COLOR]
iface lo inet loopback
iface eth0 inet static
[COLOR="#FF0000"]adress [/COLOR]10.68.xx.xx
netmask 255.255.xxx.x
gateway 10.68.xx.x
dns-nameservers 10.68.xx.xx 10.58.xx.xx
```Linux is a funny thing, if you've made a mistake, it won't whisper to itself "oh, I know what you mean", fix the error and move on; it just quits. 

I suggest:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.68.xx.xx
netmask 255.255.xxx.x
gateway 10.68.xx.x
dns-nameservers 10.68.xx.xx 10.58.xx.xx 
```Then see what interesting messages appear:```
sudo ifdown eth0 && sudo ifup -v eth0
```

---

### Post by wagner3 on 2014-07-04
Hey Chilli, thank you so much for the answer!

Well, actually I'm feeling a little dumb right now. I actually had "adress" instead of "address" on the file. (English is not my first language).

I can ping stuff just fine now! Thanks again!

---

### Post by chili555 on 2014-07-04
No worries; I've made errors like that myself. Some even today! Glad it's working.

Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

