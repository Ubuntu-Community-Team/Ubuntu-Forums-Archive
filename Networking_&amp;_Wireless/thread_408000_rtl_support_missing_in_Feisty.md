---
title: "rtl support missing in Feisty?"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by king_arthur on 2007-04-12
As for subject.

Tonight I decided to give Feisty Beta a spin and was most impressed by the overall performance.
It installed like a charm, the new migration assistant is great however, at first glance I am missing the modules relevant to my rtl 8180L card hence, no WiFi.

It was working out of the box with dapper and edgy.

Ironically, it was also the first time I have seen the network manager working without any additional tinkering.

But obviously, you can't get it all... :D

/P

---

### Post by Tranquilo on 2007-04-14
I have the same problem. Seems to be blacklisted because of some bug.

---

### Post by dbott67 on 2007-04-14
You can view the status here:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78255](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78255) and
[https://launchpad.net/ubuntu/+source/module-init-tools/+bug/88430](https://launchpad.net/ubuntu/+source/module-init-tools/+bug/88430)

You could also try using ndiswrapper.

-Dave

---

### Post by Tranquilo on 2007-04-14
Thank you very much!
I have spent hours trying to figure out what was wrong. And now it works!
What a strange bug btw.

---

### Post by king_arthur on 2007-04-14
> **Tranquilo said:**
> Thank you very much!
I have spent hours trying to figure out what was wrong. And now it works!
What a strange bug btw.

What have you done to fix it?

If I force-load the module with **sudo modprobe r810x**, it does load but I still have difficulties in getting WiFi connection.

/P

---

### Post by king_arthur on 2007-04-14
> **dbott67 said:**
> You can view the status here:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78255](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78255) and
[https://launchpad.net/ubuntu/+source/module-init-tools/+bug/88430](https://launchpad.net/ubuntu/+source/module-init-tools/+bug/88430)

You could also try using ndiswrapper.

-Dave

Thank you for pointing this out and saving me wasting further time trying to solve the issue.

So is ndiswrapper the only answer at present?

Any chance this driver will be fixed any time soon? :D

/Pieter

**UPDATE:** no need for ndiswrapper. 
Adding a dummy char to the essid name as suggested in the bug report worked like a charm. :D

Waiting for the bugfix now

---

### Post by dbott67 on 2007-04-14
Glad it's working for you.

Just for those reading this in the future, the workaround is this:

Add an extra character to the ESSID in the /etc/network/interfaces file (or when entering it in your wifi manager).  If this is what the file would normally look like:
```
dbott@dapper:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid bott
wireless-key s:mysecretwepkey
```You would change it to this:
```
dbott@dapper:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid bott[COLOR=Blue]**x**[/COLOR]   [COLOR=Red]*<--- add a dummy character to the end of your ESSID*[/COLOR]
wireless-key s:mysecretwepkey[COLOR=Red][/COLOR]

```-Dave

---

### Post by king_arthur on 2007-04-15
> **dbott67 said:**
>  ```

wireless-essid bott
wireless-key s:mysecretwepkey[COLOR=Blue]**x**[/COLOR]   [COLOR=Red]*<--- add a dummy character to the end of your key*[/COLOR]

```-Dave

Sorry mate, but that is not the way it works (at least for me) :o
```
wireless-essid bott[COLOR=Blue]**x**[/COLOR]   [COLOR=Red]*<--- add a dummy character to the end of your ESSID*[/COLOR]
wireless-key s:mysecretwepkey

```Are you sure it works your way as well? :)

/P

---

### Post by dbott67 on 2007-04-15
Oooooooooooooooops!  

You're right. D'oh!  I don't have the problem and I was just following the instructions of adding the dummy character to the ESSID, but I added it to the WEP key. -10 points for not being able to read!

-Dave

---

