---
title: "Connecting two computers without a LAN"
date: 2006-12-10
forum: Networking &amp; Wireless
---

### Post by amd-64 on 2006-12-10
I have two computers with NICs and a wired hub. There is no network (LAN) in this location, but I still would like to connect the two computers through the hub.

Any ideas. Is there a howto somewhere. 

Also Will file transfers be any faster than transferring through a busy LAN. 

Looking forward to your ideas.

---

### Post by skwillz on 2006-12-10
IANANA, but typically, you will want to statically assign IPs to each machine. Your hub configuration should let you know all the variables for doing this and you can setup each machine in the respective network configuration dialogs.

As far as speed goes, you are basically limited to whether or not you are on a 10/100/1000 network and other factors like read/write speeds on each machine, line noise, whatever.

---

### Post by lloyd_b on 2006-12-10
I'm assuming that your "hub" is simply that - a basic dumb ethernet hub.

First, pick a network to use.  I'd recommend 192.168.0.x, as this is a standard "non-routable" network, which means that if you add an internet gateway at some point in the future you won't have any conflict.  You can safely use anything in the 192.168.x.x range, or anything in the 10.x.x.x range.

Note: for editing files, you'll need to do "sudo nano {file}" (or "sudo vim {file}" if you're familiar with the vi/vim editor).  These files are "owned" by root, so "sudo" is required to edit them.

On machine 1, edit the file "/etc/network/interfaces", changing:

```
auto eth0
iface eth0 inet dhcp
```

To

```
auto eth0
iface eth0 inet static
     address 192.168.0.10
     netmask 255.255.255.0
     broadcast 192.168.0.255

```

After making this change, type:
```
sudo /etc/init.d/networking restart
```
to apply the changes.

On machine 2, do exactly the same, except for "address", use "192.168.0.11"

At this point, you should have a network connection between the two machines, but you will have to reference them by IP address.  To add names for the machine, edit the file "/etc/hosts", adding a line as follows:

```
192.168.0.11  Machine2
```
on machine 1, and 

```
192.168.0.10  Machine1
```
on machine 2

(You can name the machines whatever you want - I'm using "Machine1" and "Machine2" to make it easy).

Once you've done that, you can reference the other machine by that name.

As far as performance, yes, you should get better performance than on a typical LAN, as there will be little or no contention for the wire.  How much a difference that will make will depend on the LAN against which you're comparing it.

Lloyd B.

---

### Post by amd-64 on 2006-12-14
This howto worked flawlessly. Unfortunately, I only had 10baseT hub so transfer rates maxed at 900kb/s. On the lan, the switches are gigabit and I typically get 6Mb/s.

---

### Post by lloyd_b on 2006-12-14
> **amd-64 said:**
> This howto worked flawlessly. Unfortunately, I only had 10baseT hub so transfer rates maxed at 900kb/s. On the lan, the switches are gigabit and I typically get 6Mb/s.

With only two computers involved, you don't necessarily need a hub.  If you can lay your hands on a "crossover cable" (A cable with the transmit/receive pairs switched on one end) you can use it to directly connect the two computers.  

You can buy such a cable at any *good* computer store.  Or if you've got the tools you can [[COLOR="Red"]make your own[/COLOR]]("http://www.makeitsimple.com/how-to/dyi_crossover.htm").

Lloyd B.

---

### Post by porsher_puddles on 2006-12-31
i have read your guide but i'm having abit of trouble, i have 2 machines connected via a crossover cable, both running win xp pro, one is running ubuntu breezy the other dapper. machine 1(dapper) is on the internet and i can share the connection in windows, which is basically what i would like to do with ubuntu so i can use it and learn.
i have got so far and now i'm stuck, when one machine is on windows and the other is on ubuntu, the ubuntu one can see the windows machine.

i think i know why the ubuntu machines can't see each other is because i haven't referenced them, but i'm having problems doing this, i can't seem to edit my /etc/hosts it comes up as read only

---

### Post by koenn on 2006-12-31
if you've read the thread, no doubt you saw the part where it says
> Note: for editing files, you'll need to do "sudo nano {file}" (or "sudo vim {file}" if you're familiar with the vi/vim editor). These files are "owned" by root, so "sudo" is required to edit them.
?

---

