---
title: "Access internet via phone using Bluetooth PAN: 'modprobe bnep' has no effect?"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by cyberco on 2007-09-27
Using Ubunty Feisty I want to access the internet via my 3G phone using bluetooth. I've been struggling with this issue for quite  a while now and would like to get it working so I don't have to switch to Windows when I'm on the road. :)

Here are the steps I've taken:

- pair the laptop and phone (windows mobile 5)
- phone: turn on 'internet sharing' 
- For the laptop I follow the steps as described here:
[http://ubuntuforums.org/showthread.php?t=400864&highlight=bluetooth+pand](http://ubuntuforums.org/showthread.php?t=400864&highlight=bluetooth+pand)
- 'hcitool scan' works fine and shows list of BT devices
- Edit '/etc/bluetooth/hcid.conf' and set:
autoinit yes
security auto
pairing multi
passkey "0000"
- But then: 'sudo modprobe bnep' gives no output. As if nothing happens.
-- 'iwconfig' shows no bnep0, 
-- so doing 'sudo ifconfig bnep0' throws an error saying 'bnep0: error fetching interface information: Device not found'
- What I've also tried:
-- set 'PAND_ENABLED=1' in '/etc/init.d/bluetooth'
-- What's discussed here (second half): [http://news.softpedia.com/news/Connect-to-the-Internet-from-Anywhere-Using-a-GPRS-Connection-50670.shtml](http://news.softpedia.com/news/Connect-to-the-Internet-from-Anywhere-Using-a-GPRS-Connection-50670.shtml)

I'm at a loss, I have no idea what I'm doing wrong and where I should be looking for a solution.

Some relevant links that I found but didn't solve my issue:

Other way around (laptop/desktop as internet proxy for phone)
[http://ubuntuforums.org/showthread.php?t=173016&highlight=bluetooth+pand](http://ubuntuforums.org/showthread.php?t=173016&highlight=bluetooth+pand)

General:
[http://bluez.sourceforge.net/contrib/HOWTO-PAN](http://bluez.sourceforge.net/contrib/HOWTO-PAN)

In Gentoo:
[http://gentoo-wiki.com/HOWTO_The_host-to-host_Bluetooth](http://gentoo-wiki.com/HOWTO_The_host-to-host_Bluetooth)

Dialup networking:
[http://www.howtoforge.com/bluetooth_pand_debian_etch](http://www.howtoforge.com/bluetooth_pand_debian_etch)

---

### Post by evuraan on 2007-09-30
Try calling pand manually, and see if bnep0 is created:

```

# pand --listen -c <macid> --role=NAP -n --persist
pand[11406]: Bluetooth PAN daemon version 3.9
pand[11406]: Connecting to <macid>
pand[11406]: bnep0 connected



```

---

### Post by cyberco on 2007-09-30
> **evuraan said:**
> Try calling pand manually, and see if bnep0 is created:

```

# pand --listen -c <macid> --role=NAP -n --persist
pand[11406]: Bluetooth PAN daemon version 3.9
pand[11406]: Connecting to <macid>
pand[11406]: bnep0 connected



```

That solved my problem! Thank you very much!

So the steps I now take are:

```

sudo pand --listen -c 00:17:83:11:AB:F9 --role=NAP -n --persist

```

Then in another terminal:

```

sudo ifconfig bnep0
sudo ifup bnep0

```

One small question I still have is how I can put this all in one script (which launches 'pand' in a seperate process/thread).

---

### Post by evuraan on 2007-09-30
Just evoke pand without -n and --persist, you won't need to spawn another terminal. 

pand man page:


```


       --nodetach -n
              Do not become a daemon

       --persist -p[interval]
              Persist mode


```

---

### Post by tech0007 on 2007-11-17
> **evuraan said:**
> Try calling pand manually, and see if bnep0 is created:

```

# pand --listen -c <macid> --role=NAP -n --persist
pand[11406]: Bluetooth PAN daemon version 3.9
pand[11406]: Connecting to <macid>
pand[11406]: bnep0 connected



```
I get this error why I do 'pand --listen -c <macid> --role=NAP -n --persist'

SIOCSIFADDR: No such device
bnep0: unknown interface: No such device
SIOCSIFNETMASK: No such device

I would appreciate any help.

---

### Post by cyberco on 2007-11-17
> **tech0007 said:**
> I get this error why I do 'pand --listen -c <macid> --role=NAP -n --persist'

SIOCSIFADDR: No such device
bnep0: unknown interface: No such device
SIOCSIFNETMASK: No such device

I would appreciate any help.

According to:

[http://www.ibm.com/developerworks/library/wi-enable.html#2]("http://www.ibm.com/developerworks/library/wi-enable.html#2")

it looks as if your 'BNEP (Bluetooth Network Encapsulation Protocol)' doesn't 'register itself with the Linux networking layer as an Ethernet device'. It should show up when issuing 'ifconfig'.

I'm sorry I can't help you any further than that, but I hope it helps.

---

### Post by ivaylo on 2008-05-14
Hi,

Can anyone explain me what can be the cause for 

pand[3947]: Connecting to <macid>
pand[3947]: Connect to <macid> failed. Connection refused(111)

I want to note, also that I have pan0 device and I can assign an IP on it. I don't really know where this device came from :?

I hope that someone will help me with this :)

---

### Post by 3gun on 2008-06-28
> **evuraan said:**
> Try calling pand manually, and see if bnep0 is created:
```

# pand --listen -c <macid> --role=NAP -n --persist
pand[11406]: Bluetooth PAN daemon version 3.9
pand[11406]: Connecting to <macid>
pand[11406]: bnep0 connected

```

that didn't solve my problem :(
```
modprobe bnep
pand --listen --role GN
ifconfig bnep0 10.0.0.1
```
DID work for some time. but after i tried to make it a script and put it in **/etc/init.d** and **update-rc.d myscript defaults** device became unfindable by others. even after removing script with **update-rc.d -f myscript remove** and **rm /etc/init.d/myscript**. there are outputs of some commands:
```

# pand --listen -c 00:09:D0:50:0F:44 --role NAP -n
pand[6521]: Bluetooth PAN daemon version 3.19
pand[6521]: Connecting to 00:09:D0:50:0F:44
pand[6521]: Connect to 00:09:D0:50:0F:44 failed. No route to host(113)
```
```
# pand --listen --role NAP -n
pand[6518]: Bluetooth PAN daemon version 3.19
// now it hangs...

```
also tried all of this after calling **/etc/init.d/bluetooth restart**. didn't help too.
there are no bnep0 in output of ifconfig.
PS: trouble came after Vista connected to Ubuntu, any ideas? :)

---

### Post by flytripper on 2008-06-28
may i ask why? are you rich? have you any idea how much phone companies charge for that kind of connection? i am in england and on o2 if i acces the internet on my pc through my mobile its like 5 quid a MB. the guy in the shop looked horrified when i inquired as to the tarrif for that kind of thing..

---

### Post by 3gun on 2008-06-28
actually, i don't need an internet via phone )) my point is to connect my PC with my notebook with PAN, but i have a same problem as posted in #1 :)

P.S. sometimes it's useful to have inet via phone. f.e. when u're on study

---

