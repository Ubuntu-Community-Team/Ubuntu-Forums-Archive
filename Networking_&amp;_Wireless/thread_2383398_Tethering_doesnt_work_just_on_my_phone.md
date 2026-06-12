---
title: "Tethering doesnt work just on my phone"
date: 2018-01-24
forum: Networking &amp; Wireless
---

### Post by rodrigoproton on 2018-01-24
Hi!

I was able to connect my pc on internet using tethering till yesterday, but it just stopped working. I tried my father and mother phones, both are working. Its just mine that doesnt work. Please help me, I really need the PC to study and cant always be using mom and dad's phone. Thank you.

---

### Post by Hadaka on 2018-01-24
Hi,First obviously,there is nothing wrong with Ubuntu as you
have no problem connecting when you use your parents cell phones.
The issue is with YOUR phone. Have you reset your cell phone ? Does
the cell phone connect to the internet when not tethered ? Have you 
deleted and added back in the wifi connection ? Have you altered or
downloaded any 3rd party apps. for tethering ? Has your cell phone
provider blocked your ability to tether for excessive or abusive use ?
What ever the reason or reasons..it's not Ubuntu and I suggest you mark
this thread solved and find a solution or cause for your problem on a cell phone forum.
Good Luck.

---

### Post by rodrigoproton on 2018-01-24
Hi, Hadaka. Thank you for answering.


Have you reset your cell phone ? 

A: yes

Does
the cell phone connect to the internet when not tethered ? 

A: yes

Have you deleted and added back in the wifi connection ? 

A: yes


Have you altered or
downloaded any 3rd party apps. for tethering ? 

A: after the problem happened, I tried to install tethering apps on android to connect on pc, but without result.
Has your cell phone
provider blocked your ability to tether for excessive or abusive use ?

A: no, Im not tethering the mobile, even because I dont have credits to access web. I am tethering wi-fi, the same my father and mom phones.

My friend told me to write in terminal 
sudo systemctl status NetworkManager. Here's the result:


```
sudo systemctl status NetworkManager
&#9679; NetworkManager.service - Network Manager
Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor p
Active: active (running) since qua 2018-01-24 13:59:00 BRST; 2h 59min ago
Docs: man:NetworkManager(8)
Main PID: 1042 (NetworkManager)
Tasks: 4 (limit: 4915)
CGroup: /system.slice/NetworkManager.service
&#9500;&#9472;1042 /usr/sbin/NetworkManager --no-daemon
&#9492;&#9472;2288 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts

jan 24 16:53:34 ubuntu NetworkManager[1042]: <info> [1516820014.3036] device (e
jan 24 16:56:57 ubuntu dhclient[5352]: receive_packet failed on enp0s29f7u8: Net
jan 24 16:56:58 ubuntu NetworkManager[1042]: <info> [1516820218.1245] device (e
jan 24 16:56:58 ubuntu NetworkManager[1042]: <info> [1516820218.5966] dhcp4 (en
jan 24 16:56:58 ubuntu NetworkManager[1042]: <info> [1516820218.5966] dhcp4 (en
jan 24 16:56:58 ubuntu NetworkManager[1042]: <info> [1516820218.5994] dns-mgr:
jan 24 16:56:58 ubuntu dnsmasq[2288]: setting upstream servers from DBus
jan 24 16:56:59 ubuntu NetworkManager[1042]: <error> [1516820219.2786] platform-
jan 24 16:56:59 ubuntu NetworkManager[1042]: <warn> [1516820219.2797] device (e
jan 24 16:56:59 ubuntu NetworkManager[1042]: <info> [1516820219.2803] devices r
lines 1-20/20 (END)...skipping...
&#9679; NetworkManager.service - Network Manager
Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor preset: enabled)
Active: active (running) since qua 2018-01-24 13:59:00 BRST; 2h 59min ago
Docs: man:NetworkManager(8)
Main PID: 1042 (NetworkManager)
Tasks: 4 (limit: 4915)
CGroup: /system.slice/NetworkManager.service
&#9500;&#9472;1042 /usr/sbin/NetworkManager --no-daemon
&#9492;&#9472;2288 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/var/run/NetworkMa

jan 24 16:53:34 ubuntu NetworkManager[1042]: <info> [1516820014.3036] device (enp0s29f7u8): Activation: successful, device act
jan 24 16:56:57 ubuntu dhclient[5352]: receive_packet failed on enp0s29f7u8: Network is down
jan 24 16:56:58 ubuntu NetworkManager[1042]: <info> [1516820218.1245] device (enp0s29f7u8): state change: activated -> unmanag
jan 24 16:56:58 ubuntu NetworkManager[1042]: <info> [1516820218.5966] dhcp4 (enp0s29f7u8): canceled DHCP transaction, DHCP cli
jan 24 16:56:58 ubuntu NetworkManager[1042]: <info> [1516820218.5966] dhcp4 (enp0s29f7u8): state changed bound -> done
jan 24 16:56:58 ubuntu NetworkManager[1042]: <info> [1516820218.5994] dns-mgr: Writing DNS information to /sbin/resolvconf
jan 24 16:56:58 ubuntu dnsmasq[2288]: setting upstream servers from DBus
jan 24 16:56:59 ubuntu NetworkManager[1042]: <error> [1516820219.2786] platform-linux: do-change-link[10]: failure changing lin
jan 24 16:56:59 ubuntu NetworkManager[1042]: <warn> [1516820219.2797] device (enp0s29f7u8): failed to disable userspace IPv6LL
jan 24 16:56:59 ubuntu NetworkManager[1042]: <info> [1516820219.2803] devices removed (path: /sys/devices/pci0000:00/0000:00:1
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
lines 1-20/20 (END)
```

---

### Post by Hadaka on 2018-01-24
Hi, please use code tags when you post output data. its the "#" symbol
second row..far right..on the response /reply page.
ok..is this correct ? PC >~~~Tether~~~Cell Phone >)))  ((((<WIFI Router/Modem >~~~~ INTERNET ?
Thanks

---

### Post by rodrigoproton on 2018-01-24
Hey, sorry that I did it wrong.

I did it again. Here's the result:

```
# &#9679; NetworkManager.service - Network Manager
# Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor p
# Active: active (running) since qua 2018-01-24 13:59:00 BRST; 5h 38min ago
# Docs: man:NetworkManager(8)
# Main PID: 1042 (NetworkManager)
# Tasks: 4 (limit: 4915)
# CGroup: /system.slice/NetworkManager.service
# &#9500;&#9472;1042 /usr/sbin/NetworkManager --no-daemon
# &#9492;&#9472;2288 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/var/run/NetworkManager/dnsmasq.pid --listen-address=127.0.1.1 --cache-size=0 --conf-file=/dev/null --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq --conf-dir=/etc/NetworkManager/dnsmasq.d
# jan 24 19:30:19 ubuntu NetworkManager[1042]: <info>  [1516829419.2291] device (enp0s29f7u8): Activation: successful, device activated.
# jan 24 19:37:04 ubuntu dhclient[7235]: receive_packet failed on enp0s29f7u8: Net
# jan 24 19:37:04 ubuntu dhclient[7235]: receive_packet failed on enp0s29f7u8: Network is down
# jan 24 19:37:07 ubuntu NetworkManager[1042]: <info>  [1516829827.0821] devices removed (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/net/enp0s29f7u8, iface: enp0s29f7u8)
# jan 24 19:37:08 ubuntu NetworkManager[1042]: <info>  [1516829828.4962] device (enp0s29f7u8): state change: activated -> unmanaged (reason 'removed') [100 10 36]
# jan 24 19:37:08 ubuntu NetworkManager[1042]: <info>  [1516829828.7909] dhcp4 (enp0s29f7u8): canceled DHCP transaction, DHCP client pid 7235
# jan 24 19:37:08 ubuntu NetworkManager[1042]: <info>  [1516829828.7910] dhcp4 (enp0s29f7u8): state changed bound -> done
# jan 24 19:37:09 ubuntu NetworkManager[1042]: <info>  [1516829829.0718] dns-mgr: Writing DNS information to /sbin/resolvconf
# jan 24 19:37:09 ubuntu dnsmasq[2288]: setting upstream servers from DBus
# jan 24 19:37:10 ubuntu NetworkManager[1042]: <error> [1516829830.5534] platform-linux: do-change-link[13]: failure changing link: failure 19 (No such device)
# jan 24 19:37:10 ubuntu NetworkManager[1042]: <warn>  [1516829830.5543] device (enp0s29f7u8): failed to disable userspace IPv6LL address handling
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
lines 1-20/20 (END)
```


Thank you in advance.

---

### Post by Hadaka on 2018-01-24
Hi please see the attached on CODE TAGS
and please answer the question I posted in post #4
```
is this correct ? PC >~~~Tether~~~Cell Phone >))) ((((<WIFI Router/Modem >~~~~ INTERNET ?
```
*Note this question is inside code tags.

[ATTACH=CONFIG]278314[/ATTACH]

---

