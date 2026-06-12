---
title: "Ubuntu 16.04 No Internet Connection After Update"
date: 2018-11-13
forum: Networking &amp; Wireless
---

### Post by jdmtimemachine on 2018-11-13
Hello to all Ubuntu users.

I run an MSI GP62 Leopard Pro laptop.

Its dual boot with Windows10 and Ubuntu 16.04.

I LOVE Ubuntu and i rarely use W10.

Ubuntu is my main OS..so when i totally lost internet connectivity i was dumbfounded..i mean the internet has all but gone. I can't update..nothing.

I have read so many posts, tried to connect with an ethernet cable and simply cannot connect. I've tried to restore to an earlier back up and still no luck.

Windows10 works perfectly which is how I'm writing this now.

When it comes to editing commands with Gedit, etc I'm not very confident but i have tried.

I'm very close to a re-install and have backed up all my data and files, but would rather try and fix this problem in the case this happens again.

In regards to the update.it was a weird one for the update gave no details of what was going to be updated, it was a blank window and only showed the file size which was very small. I ignored it the first time but when it showed itself again i agreed to the update and then after that my internet was gone.

Device manager shows i am still connected, restarting that didn't work.

Has anyone had this happen to them recently?
It happened 3 days ago..for 3 days i have tried what i can but still no luck which has brought me here.

Any help would be greatly appreciated thank you. :)

EDIT-Just wanted to add i can't ping google which I've tried, i get no responses back.
If anyone wants any data from terminal please let me know, i will have to log into Ubuntu and copy and paste any terminal read outs  and then log back into windows and then here to reply. :P

---

### Post by mitesh.agrwl on 2018-11-13
Hi,

> In regards to the update.it was a weird one for the update gave no  details of what was going to be updated, it was a blank window and only  showed the file size which was very small. I ignored it the first time  but when it showed itself again i agreed to the update and then after  that my internet was gone.


This is weird, normally any Ubuntu/Linux user should ignore such updates but i feel it became to irritating to ignore.

please paste the output of **ping 8.8.8.8  **and  **ping [www.google.com](www.google.com) **

---

### Post by Autodave on 2018-11-13
*I'm very close to a re-install and have backed up all my data and files,  but would rather try and fix this problem in the case this happens  again.*

I have been running some form of Ubuntu for the past 10+ years.  The one thing that I learned long time ago (and again several times since) is that upgrading from one release to another rarely works well, if at all.  I just do clean installs.  Doing that saves me time and lots of headaches.

---

### Post by slickymaster on 2018-11-13
Thread moved to **Networking & Wireless** for a better fit

---

### Post by jdmtimemachine on 2018-11-14
> **mitesh.agrwl said:**
> Hi,



This is weird, normally any Ubuntu/Linux user should ignore such updates but i feel it became to irritating to ignore.

please paste the output of **ping 8.8.8.8  **and  **ping [www.google.com]("http://www.google.com") **

Hi thanks for your reply.

Here is the output of first command-
```
keanu@keanu-GP62-6QF:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=120 time=40.3 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=120 time=38.2 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=120 time=39.0 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=120 time=39.9 ms
64 bytes from 8.8.8.8: icmp_seq=5 ttl=120 time=38.4 ms
64 bytes from 8.8.8.8: icmp_seq=6 ttl=120 time=38.1 ms
64 bytes from 8.8.8.8: icmp_seq=7 ttl=120 time=39.1 ms
64 bytes from 8.8.8.8: icmp_seq=8 ttl=120 time=38.5 ms
64 bytes from 8.8.8.8: icmp_seq=9 ttl=120 time=37.9 ms
64 bytes from 8.8.8.8: icmp_seq=10 ttl=120 time=38.3 ms
64 bytes from 8.8.8.8: icmp_seq=11 ttl=120 time=37.9 ms
64 bytes from 8.8.8.8: icmp_seq=12 ttl=120 time=37.7 ms
64 bytes from 8.8.8.8: icmp_seq=13 ttl=120 time=37.5 ms
64 bytes from 8.8.8.8: icmp_seq=14 ttl=120 time=38.1 ms
64 bytes from 8.8.8.8: icmp_seq=15 ttl=120 time=37.2 ms
64 bytes from 8.8.8.8: icmp_seq=16 ttl=120 time=37.2 ms
64 bytes from 8.8.8.8: icmp_seq=17 ttl=120 time=37.2 ms
64 bytes from 8.8.8.8: icmp_seq=18 ttl=120 time=38.3 ms
64 bytes from 8.8.8.8: icmp_seq=19 ttl=120 time=38.9 ms
64 bytes from 8.8.8.8: icmp_seq=20 ttl=120 time=38.1 ms
64 bytes from 8.8.8.8: icmp_seq=21 ttl=120 time=37.1 ms
64 bytes from 8.8.8.8: icmp_seq=22 ttl=120 time=38.0 ms
64 bytes from 8.8.8.8: icmp_seq=23 ttl=120 time=37.3 ms
64 bytes from 8.8.8.8: icmp_seq=24 ttl=120 time=37.4 ms
64 bytes from 8.8.8.8: icmp_seq=25 ttl=120 time=38.0 ms
64 bytes from 8.8.8.8: icmp_seq=26 ttl=120 time=38.2 ms
64 bytes from 8.8.8.8: icmp_seq=27 ttl=120 time=37.2 ms
64 bytes from 8.8.8.8: icmp_seq=28 ttl=120 time=36.9 ms
64 bytes from 8.8.8.8: icmp_seq=29 ttl=120 time=37.1 ms
64 bytes from 8.8.8.8: icmp_seq=30 ttl=120 time=37.5 ms
64 bytes from 8.8.8.8: icmp_seq=31 ttl=120 time=37.8 ms
64 bytes from 8.8.8.8: icmp_seq=32 ttl=120 time=37.7 ms
64 bytes from 8.8.8.8: icmp_seq=33 ttl=120 time=41.4 m
```

Here is the output of second command, but it resulted in saying "Unknown Host"

```
keanu@keanu-GP62-6QF:~$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
```

> **Autodave said:**
> *I'm very close to a re-install and have backed up all my data and files,  but would rather try and fix this problem in the case this happens  again.*

I have been running some form of Ubuntu for the past 10+ years.  The one thing that I learned long time ago (and again several times since) is that upgrading from one release to another rarely works well, if at all.  I just do clean installs.  Doing that saves me time and lots of headaches.

Yep same here also.

16.04 is my third Ubuntu install, always a fresh clean install.
:)

EDIT-I'm in Australia so apologies for my late replies. 
Thanks again. :)

---

### Post by mitesh.agrwl on 2018-11-14
```
keanu@keanu-GP62-6QF:~$ ping [www.google.com]("http://www.google.com")
ping: unknown host [www.google.com]("http://www.google.com")
```

The output from first command shows that internet connection is good, you are able to access the internet but the problem is with DNS resolution. 

Please paste the output of the following command  ```
nmcli device show <interfacename> | grep IP4.DNS
```

---

### Post by jdmtimemachine on 2018-11-15
> **mitesh.agrwl said:**
> The output from first command shows that internet connection is good, you are able to access the internet but the problem is with DNS resolution. 

Please paste the output of the following command **nmcli device show <interfacename> | grep IP4.DNS**

Will do thank you...back soon! :)

Hi here is the output..doesn't look good I'm afraid...:(

```
keanu@keanu-GP62-6QF:~$ nmcli device show <interfacename> | grep IP4.DNS
[COLOR=#ff0000]bash: syntax error near unexpected token `|'
```

I tried a few more things on my end which gave no result..here are the 3 different commands i entered and the outputs that followed-

```
keanu@keanu-GP62-6QF:~$ sudo gedit /etc/resolvconf/resolv.conf.d/tail

(gedit:2838): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-spell-enabled not supported

** (gedit:2838): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-encoding not supported
```

COMMAND#2
```
sudo mkdir -p /run/resolvconf/interface
sudo resolvconf -u
sudo service resolvconf restart

keanu@keanu-GP62-6QF:~$ sudo mkdir -p /run/resolvconf/interface
keanu@keanu-GP62-6QF:~$ sudo resolvconf -u
/etc/resolvconf/update.d/libc: Warning: /etc/resolv.conf is not a symbolic link to /run/resolvconf/resolv.conf
keanu@keanu-GP62-6QF:~$ sudo service resolvconf restart
keanu@keanu-GP62-6QF:~$
```

COMMAND#3

```
/etc/NetworkManager/NetworkManager.conf
Delete (or comment out with a hash #) the line that reads dns=dnsmasq.
Restart NetworkManager via sudo service NetworkManager restart

keanu@keanu-GP62-6QF:~$ sudo gedit /etc/NetworkManager/NetworkManager.conf
[sudo] password for keanu: 

(gedit:2726): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (gedit:2726): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-spell-enabled not supported

** (gedit:2726): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-encoding not supported

```
Everything i try seems to hit a wall.

Has something been damaged to the point where i will need to do a complete re-install?

Or is there still an option for me to have this problem fixed?

I hope there is..looking forward to your reply tomorrow! :)

---

### Post by mitesh.agrwl on 2018-11-15
> Hi here is the output..doesn't look good I'm afraid...:sad:

```
keanu@keanu-GP62-6QF:~$ nmcli device show <interfacename> | grep IP4.DNS
bash: syntax error near unexpected token `|'
```

The **<interface>** in the command above hsould have been replaced by the 'name of network interface interface'. If you are not sure about it, then do the following:

```
Command : ifconfig

enp3s0    Link encap:Ethernet  HWaddr 88:ae:1d:d5:40:04  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:7939 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7939 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:986272 (986.2 KB)  TX bytes:986272 (986.2 KB)

wlp2s0b1  Link encap:Ethernet  HWaddr 00:26:82:da:ee:50  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:82ff:feda:ee50/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:437880 errors:0 dropped:0 overruns:0 frame:0
          TX packets:285973 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:583226427 (583.2 MB)  TX bytes:39348181 (39.3 MB)


```
In above example the interface card used is *wlp2s0b1*. Hence, will replace *<interfacename>* with **wlp2s0b1**.

> **jdmtimemachine said:**
> I tried a few more things on my end which gave no result..here are the 3 different commands i entered and the outputs that followed-

keanu@keanu-GP62-6QF:~$ sudo gedit /etc/resolvconf/resolv.conf.d/tail

OUTPUT-
(gedit:2838): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-spell-enabled not supported

** (gedit:2838): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-encoding not supported

COMMAND#2
sudo mkdir -p /run/resolvconf/interface
sudo resolvconf -u
sudo service resolvconf restart

OUTPUT-
keanu@keanu-GP62-6QF:~$ sudo mkdir -p /run/resolvconf/interface
keanu@keanu-GP62-6QF:~$ sudo resolvconf -u
/etc/resolvconf/update.d/libc: Warning: /etc/resolv.conf is not a symbolic link to /run/resolvconf/resolv.conf
keanu@keanu-GP62-6QF:~$ sudo service resolvconf restart
keanu@keanu-GP62-6QF:~$

COMMAND#3

/etc/NetworkManager/NetworkManager.conf
Delete (or comment out with a hash #) the line that reads dns=dnsmasq.
Restart NetworkManager via sudo service NetworkManager restart
RESULT-
keanu@keanu-GP62-6QF:~$ sudo gedit /etc/NetworkManager/NetworkManager.conf
[sudo] password for keanu: 

(gedit:2726): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (gedit:2726): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-spell-enabled not supported

** (gedit:2726): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-encoding not supported

Everything i try seems to hit a wall.

Has something been damaged to the point where i will need to do a complete re-install?

Or is there still an option for me to have this problem fixed?

I hope there is..looking forward to your reply tomorrow! :)

Hopefully there was no damage done by first and third command (s set), if no editing was done in gedit or gedit did not responded. The second command set has updated the *resolvconf**. *Please paste the reference link which mentioned the solution. Also paste the outputs of following command, run each command individually.

```
$ ls /etc/resolvconf/
$ ls /etc/resolvconf/interfaces
```

---

### Post by slickymaster on 2018-11-15
_@jdmtimemachine @mitesh.agrwl_:

I've already edited several posts in this thread due to an improper posting of output. Please take in consideration that output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. Please [always use code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") when doing it

---

### Post by mitesh.agrwl on 2018-11-15
@slickymaster:

Thanks for the correction and information.

---

### Post by jdmtimemachine on 2018-11-15
Hi and thanks again for your help.

Im sure ive done this wrong again in regards to the code you posted-
nmcli device show <interfacename> | grep IP4.DNS

I added wlp2s0b1 to where interfacename was but resulted in this output-
nmcli device show <wlp2s0b1> | grep IP4.DNS
keanu@keanu-GP62-6QF:~$ nmcli device show <wlp2s0b1> | grep IP4.DNS
bash: syntax error near unexpected token `|'

I ran the other commands and this is the output-
OUTPUTS OF EACH COMMAND-
keanu@keanu-GP62-6QF:~$ nmcli device show <wlp2s0b1> | grep IP4.DNS
bash: syntax error near unexpected token `|'
keanu@keanu-GP62-6QF:~$ ls /etc/resolvconf/
interface-order  resolv.conf.d  update.d  update-libc.d

keanu@keanu-GP62-6QF:~$ ls /etc/resolvconf/interfaces
ls: cannot access '/etc/resolvconf/interfaces': No such file or directory
keanu@keanu-GP62-6QF:~$

Its 5am here and i need to hurry off to work, so not the best time for me to wrap my head around these commands so i apologize for this, when i arrive home i will try to make more sense of it but greatly appreciate your help thanks so much.

There was no damage done that i know of when i ran the other commands.

I'm not very good at this but hopefully i can get it working today before the weekend.

> **slickymaster said:**
> _@jdmtimemachine @mitesh.agrwl_:

I've already edited several posts in this thread due to an improper posting of output. Please take in consideration that output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. Please [always use code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") when doing it

I apologize for that, but i simply have no idea how to use post tags...is there a beginner section where i can post my problems to instead of here?

---

### Post by QIII on 2018-11-15
This question is in the correct place.  There is no need to put it elsewhere.  Code tags should be used everywhere, including the "New to Ubuntu" area.  slickymaster included a link with instructions for using code tags, but let me give you the condensed version.

There are two ways to use code tags:

1.  Click on the # button above the text entry box, place your cursor between the code tags that appear and type or paste your text.  Alternatively, paste or type your text, highlight it and then click the # button.

2.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after your text.  The square brackets are required.

---

### Post by jdmtimemachine on 2018-11-15
Thanks [**[COLOR=#990303][B]QIII :)**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=628170")

---

### Post by jdmtimemachine on 2018-11-15
> **mitesh.agrwl said:**
> Please paste the reference link which mentioned the solution.

[https://ubuntuforums.org/showthread.php?t=2358660](https://ubuntuforums.org/showthread.php?t=2358660)

---

### Post by jdmtimemachine on 2018-11-15
> **mitesh.agrwl said:**
> The **<interface>** in the command above hsould have been replaced by the 'name of network interface interface'. If you are not sure about it, then do the following:

```
Command : ifconfig

enp3s0    Link encap:Ethernet  HWaddr 88:ae:1d:d5:40:04  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:7939 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7939 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:986272 (986.2 KB)  TX bytes:986272 (986.2 KB)

wlp2s0b1  Link encap:Ethernet  HWaddr 00:26:82:da:ee:50  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:82ff:feda:ee50/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:437880 errors:0 dropped:0 overruns:0 frame:0
          TX packets:285973 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:583226427 (583.2 MB)  TX bytes:39348181 (39.3 MB)


```
In above example the interface card used is *wlp2s0b1*. Hence, will replace *<interfacename>* with **wlp2s0b1**.

Hi again, my interface card is wlp2s0, so i entered that to replace <interfacename> which resulted in the following output-
```
[keanu@keanu-GP62-6QF:~$ nmcli device show <wlp2s0> | grep IP4.DNS
bash: syntax error near unexpected token `|'
```

The output from 2nd solution to which i posted the reference link to is as follows-
[https://ubuntuforums.org/showthread.php?t=2358660](https://ubuntuforums.org/showthread.php?t=2358660)
```
keanu@keanu-GP62-6QF:~$ sudo gedit /etc/systemd/resolved.conf
[sudo] password for keanu:
** (gedit:2725): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
** (gedit:2725): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-spell-enabled not supported
** (gedit:2725): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-encoding not supported
** (gedit:2725): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported
```

---

### Post by jdmtimemachine on 2018-11-16
Hi everyone i managed to get my internet back, thanks for the help [**[COLOR=#000000]mitesh.agrwl[/COLOR]**]("https://ubuntuforums.org/member.php?u=2111225")!

Because you mentioned DNS that allowed to me to do a much better search and in the end resulted in me fixing the problem.

I found the command-[code] sudo dpkg-reconfigure resolvconf [code]
 
Then did a reboot, after that i was able to ping google and my internet was back up and running. :)

---

