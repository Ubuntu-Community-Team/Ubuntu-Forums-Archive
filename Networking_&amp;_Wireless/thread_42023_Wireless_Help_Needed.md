---
title: "Wireless Help Needed"
date: 2005-06-15
forum: Networking &amp; Wireless
---

### Post by AGilley007 on 2005-06-15
I have a Simmens SpeedStream Wireless USB and I have used the guide to install it and everything went find till I did the "ndiswrapper -l" I got the following,

root@ubuntu:~#ndiswrapper -l
ssusbnds          invalid driver

I don't know what to do that is the only file on that cd that has a ending of .inf

---

### Post by rachii on 2005-06-15
when i did mine, and apparently other people had to do this as well...i had to copy all the files that were in teh same folder as the driver (a .cat and .sys file) along with the .INF    i moved them all to a folder then```
ndiswrapper -i filename.inf
``` 

but it didnt work for me until i copied all the other files

---

### Post by AGilley007 on 2005-06-15
Ok thanks that worked and I rebooted but I still can't get on a web site is their somthing else I have to do?

---

### Post by rachii on 2005-06-16
if you go to "system - administration - networking" on the gnome menu...enter password...  do you see the wireless card listed?  is it selected as the "default gateway device"?  is it activated and configured in here?

when i was using FC3 and ndiswrapper, i ended up having to write a script to run at startup so that it would scan for access points and connect....but when i installed ubuntu on that computer it was all automatically working through "system-admin-network"   so maybe you can get your going through there? let me know

---

### Post by ssck on 2005-06-16
[QUOTE=AGilley007]Ok thanks that worked and I rebooted but I still can't get on a web site is their somthing else I have to do?[/QUOTE]


in the terminal console, type the following :
ifconfig and see what you get 

and then iwconfig and see what you get

---

### Post by AGilley007 on 2005-06-16
I filled in all the stuff for the interned under the sys-admin-net but and clicked activate and that took a minute or two and then i clicked ok, that took a little bit to then I restarted but now when I go their it does not show up. So I did the ifconfing and the iwconfig and this is what I got.


alan@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:878 errors:0 dropped:0 overruns:0 frame:0
          TX packets:878 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:78048 (76.2 KiB)  TX bytes:78048 (76.2 KiB)

wlan0     Link encap:IPv6-in-IPv4
          inet6 addr: ::127.0.0.1/96 Scope:Unknown
          UP RUNNING NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:7 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

alan@ubuntu:~$ iwconfig
lo        no wireless extensions.

wlan0     no wireless extensions.

wlan1     no wireless extensions.

alan@ubuntu:~$


Then i went back and did the ndiswrapper -l and it said that is was present.

---

### Post by AGilley007 on 2005-06-16
Ok I rebooted into it again and it showed up but it still won't show web pages and wont get on the internet here is the ifconfig and the iwconfig now.

alan@ubuntu:~$ sudo -s
root@ubuntu:~# ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4822 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4822 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:427971 (417.9 KiB)  TX bytes:427971 (417.9 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:02:DD:31:E1:A5
          inet6 addr: fe80::202:ddff:fe31:e1a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

root@ubuntu:~# iwconnnnnnnnnnnnnnnnnnfig
bash: iwconnnnnnnnnnnnnnnnnnfig: command not found
root@ubuntu:~# iwconfig
lo        no wireless extensions.

Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wlan0     IEEE 802.11FH  ESSID:off/any
          Channel:0  Access Point: 00:00:00:00:00:00   Bit Rate:0 kb/s
          Tx-Power:46 dBm
          RTS thr:35619 B   Fragment thr:35621 B
          Encryption key:off
          Power Management max timeout:0us  mode:All packets received
          Link Quality:100  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

root@ubuntu:~#


Here is a screenshots of the other thing.

---

### Post by AGilley007 on 2005-06-16
bump

---

### Post by ssck on 2005-06-17
[QUOTE=AGilley007]Ok I rebooted into it again and it showed up but it still won't show web pages and wont get on the internet here is the ifconfig and the iwconfig now.

alan@ubuntu:~$ sudo -s
root@ubuntu:~# ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4822 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4822 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:427971 (417.9 KiB)  TX bytes:427971 (417.9 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:02:DD:31:E1:A5
          inet6 addr: fe80::202:ddff:fe31:e1a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

root@ubuntu:~# iwconnnnnnnnnnnnnnnnnnfig
bash: iwconnnnnnnnnnnnnnnnnnfig: command not found
root@ubuntu:~# iwconfig
lo        no wireless extensions.

Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wlan0     IEEE 802.11FH  ESSID:off/any
          Channel:0  Access Point: 00:00:00:00:00:00   Bit Rate:0 kb/s
          Tx-Power:46 dBm
          RTS thr:35619 B   Fragment thr:35621 B
          Encryption key:off
          Power Management max timeout:0us  mode:All packets received
          Link Quality:100  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

root@ubuntu:~#


Here is a screenshots of the other thing.[/QUOTE]


what do u get when you type iwlist wlan0 scan ? can you also show what is in your /etc/network/interfaces file ?

you could also install gtkwifi.it will help you to detect your ap.

---

