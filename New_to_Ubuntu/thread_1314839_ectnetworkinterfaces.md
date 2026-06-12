---
title: "/ect/network/interfaces ?"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by garyed on 2009-11-04
I have a wireless laptop using 8.04 & my connection works fine most of the time. Sometimes though when I boot up the connection shows full bars but just doesn't work. I try to run ifup -a & ifdown -a when that happens with no success. In the man files it says that ifup -a will only work on whatever is listed in the interfaces file.
This is it now:
> $ cat /etc/network/interfaces
auto lo
iface lo inet loopback

this is my ifconfig :
> gary@t2-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:39:b2:15:dd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:12:f0:99:41:0a  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe99:410a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:359 errors:0 dropped:0 overruns:0 frame:0
          TX packets:336 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:298669 (291.6 KB)  TX bytes:50082 (48.9 KB)
          Interrupt:11 Base address:0x4000 Memory:fce00000-fce00fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1300 (1.2 KB)  TX bytes:1300 (1.2 KB)



I also would like to be able to plug an ethernet cord & not go wireless
on certain occasions. 
I'm a little unsure what to add but rebooting always solves my problem.

---

### Post by iansane on 2009-11-04
I'm a little confused by not seeing wlan0 since you have wireless but I'm using Ubuntu Hardy and my settings are a result of using the GUI network configuration so I really don't know much about this.

```

auto lo
iface lo inet loopback




iface wlan0 inet dhcp
wireless-key xxxxxxxxxxxxxxxxxxxxxxxx
wireless-essid lotusNet

auto wlan0

```

There is my network interfaces file.
I x'd out the wireless key and it's only for 128 bit wep encryption so it might be different for you.

I think your wired connection should be something like

iface eth0 inet dhcp
auto eth0

But it seems like something is missing there.

I'm also confused by seeing eth0 and eth1 in you ifconfig.

Looks like something is different in xubuntu so I hope this little bit of info helps some.

---

### Post by garyed on 2009-11-04
I also have an old copy of Ubuntu Feisty on the same laptop so I'll check that config too.
I think eth0 is my wired connection but its not in my interfaces either.

---

### Post by Barriehie on 2009-11-04
My connection seems to 'get stuck' every now and then so I added a crontab entry so that every 20 minutes it runs 'dhclient' and since adding that I've had no issues.

Barrie

---

### Post by Iowan on 2009-11-04
My laptop (Jaunty) also uses eth1 for the wireless card.  You can check **lshw -C network** to see which interface does what.
Seems like Hardy's NM was a bit tricky. I have several links, but dunno if the problems they help resolve got fixed somewhere along the way.

---

### Post by garyed on 2009-11-04
I checked my Feisty interfaces file & it has a reference to eth2 & there's no eth2 at all on my laptop but everything still works O.K.
I found that plugging in a cable works fine also without any other setup.
I never lose my wifi connnection once I get it but its just every once in a while at startup it doesn't connect even though it shows a good connection on the tool bar. I'm just trying to find another way besides rebooting to get back online.

---

