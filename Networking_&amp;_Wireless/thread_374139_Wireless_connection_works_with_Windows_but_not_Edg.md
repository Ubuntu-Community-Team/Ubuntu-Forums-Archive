---
title: "Wireless connection works with Windows but not Edgy"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by Buster95 on 2007-03-02
I moved this message from another section (probably the wrong one) because I didn't get any responses.

Loaded Edgy 6.10 from a downloaded and tested boot disk, onto a laptop with XP on another partition. XP connects OK through wireless router to my ADSL connection. Not so with Ubuntu.
Searched the threads and tried a few things that seemed close to what I'm experiencing. 
Following suggestions on another thread, I interrogated for an IP address [sudo dhclient eth0] and got the message "No DHCPOFFERS received" Presumably that simply confirmed the bleeding obvious. Tried changing to a fixed IP - no result. This laptop came with a Via Ethernet adaptor card.
Would appreciate a starting tip.
Cheers

More:
Rebooted to Ubuntu, changed the IP address back to "automatically assigned by DHCP". Either way, when I reboot to XP, the wireless connects. It's a Realtek RTL 8187. Also tried Edgy on the Ethernet connection on my desktop - l nothing!

More:
Copied networking parameters from Windows to Edgy (Ethernet disconnected; Wireless DNS settings). Still no connection.

ifconfig returns the following:
laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:90:F5:57:BA:BB  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:50 Base address:0x4800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:98 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7220 (7.0 KiB)  TX bytes:7220 (7.0 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:15:AF:12:7D:B7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:7 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1504 (1.4 KiB)  TX bytes:0 (0.0 b)

---

### Post by chili555 on 2007-03-02
We would love to see the output of sudo iwconfig wlan0 as well as sudo iwlist wlan0 scanning. Are you using WEP or WPA? Obscure 2/3, but not all of any encryption keys that show up, so we can see if the structure (hex, ascii, passphrase, etc.) may be a problem.

---

### Post by FIONEX on 2007-03-02
Follow these instructions, but when you get to the end DONT RESTART, just do the "/init.rc/dbus restart" command. After you do that, run "nm-applet" and you're all good (make sure you have a system tray to see the applet).
[http://www.debianadmin.com/enable-wp...ntu-linux.html](http://www.debianadmin.com/enable-wp...ntu-linux.html)

---

### Post by Buster95 on 2007-03-02
xx@laptop:~$ sudo iwconfig wlan0
Password:
wlan0     802.11b/g  ESSID:"hka54541@primusdsl"  
          Mode:Managed  Channel=4  Access Point: Not-Associated   
          Bit Rate=11 Mb/s   Sensitivity=4/6  
          Retry:on   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

xx@laptop:~$ sudo iwlist lan0 scanning
lan0      Interface doesn't support scanning.

---

### Post by Buster95 on 2007-03-02
Fionex,
That link returned "no post matched your criteria".

Chilli555
I have no idea whether I'm using WEP or WPA. How do I find that out?

I appreciate all your help.

---

### Post by chili555 on 2007-03-02
sudo iwlist **w**lano scanning

Here is an example from my computer:

```
wlan0     Scan completed :
          Cell 01 - Address: 00:13:10:62:8D:F7
                    ESSID:"GBR1"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-67 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=1

```

It says, Encryption key: on. This means some kind of WEP or WPA encryption is in place.

Did you set up WEP or WPA on the router after you plugged it in, or did you just plug and pray?

I am suspicious about your essid: hka54541@primusdsl. Is that really the essid in the router? If you specify the essid you want to connect to, it won't readily connect to any other. Scanning will tell us what the essid the router is broadcasting and we can change to match in the computer. Please see, for example the essid in my scan: ```
ESSID:"GBR1"
``` So, in my case, my essid must be GBR1 in order to connect.
Try again: sudo iwlist **w**lan0 scanning

---

### Post by Buster95 on 2007-03-02
Thanks Chilli555,
xx@laptop:~$ sudo iwlist wlan0 scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:15:E9:03:F7:FE
                    ESSID:"default"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:73  Signal level:0  Noise level:37
                    Extra: Last beacon: 83ms ago

xx@laptop:~$

Regarding the ESSID:
When I loaded Edgy, it did not automatically find my wireless router. So, I interrogated my wireless router (with XP which is on another partition and finds the wireless router annoyingly well) and inserted the username that came up. Should I have used something else? Nothing else looks appropriate.
Cheers

---

### Post by chili555 on 2007-03-02
Well, user name is not the same as essid, for sure.

Let's go to System -> Administration -> Networking and highlight your wireless connection. Click Properties and change Network Name (ESSID) to default. (Even though it shows up in scanning as "default" we want the word without quotes: default.)  Click OK and it will probably connect right then. If not, restart networking with sudo /etc/init.d/networking restart. 

Let us know.

PS - I assume you posted a hypothetical user name, didn't you? Yes, you did.

---

### Post by Buster95 on 2007-03-02
Thanks Chili,
Went to System/administration/networking/wireless connection. Changed ESSID to default. Did not connect.
From a terminal, entered sudo /etc/init.d/networking restart. Got this:
xx@laptop:~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.wlan0.pid with pid 6186
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:15:af:12:7d:b7
Sending on   LPF/wlan0/00:15:af:12:7d:b7
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.0.1 port 67
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "admin".
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:15:af:12:7d:b7
Sending on   LPF/wlan0/00:15:af:12:7d:b7
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.0.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.171 -- renewal in 510569 seconds.
                                                                         [ ok ]
xx@laptop:~$ 

Still wont connect.
Cheers

---

### Post by chili555 on 2007-03-02
Uhhhh...what does this mean?
```
DHCPOFFER from 192.168.0.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.171 -- renewal in 510569 seconds.

```

I believe you *are* connected. Did you try to get a web page?

---

### Post by Buster95 on 2007-03-02
Tested it by trying to go to Google home page. It simply grinds away without getting there.

---

### Post by chili555 on 2007-03-02
Try ping -c3 64.233.161.99 This is Google's IP address, at least here in USA. If you get returns, you know you are connected and that you have a DNS problem. Please also post cat /etc/resolv.conf

You might also check if you can ping -c3 192.168.0.1  (which is your router)

---

### Post by Buster95 on 2007-03-02
Chili555,
You are close - very very close to cracking this conundrum.

xx@laptop:~$ ping -c3 64.233.161.99
PING 64.233.161.99 (64.233.161.99) 56(84) bytes of data.
64 bytes from 64.233.161.99: icmp_seq=1 ttl=240 time=263 ms
64 bytes from 64.233.161.99: icmp_seq=2 ttl=240 time=267 ms
64 bytes from 64.233.161.99: icmp_seq=3 ttl=240 time=260 ms

--- 64.233.161.99 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 260.361/263.609/267.442/2.920 ms
xx@laptop:~$ ping -c3 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=0.864 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.860 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=0.813 ms

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.813/0.845/0.864/0.040 ms
xx@laptop:~$

---

### Post by chili555 on 2007-03-02
When a router hands you an IP address, it is supposed to give you DNS server addresses, too. (DNS servers: another subject for the young Jedi to Google up.) Mostly they do, sometimes they won't.

We can work around this as follows: sudo gedit  /etc/resolv.conf

Type in:

nameserver 192.168.0.1

Save and close. Then ping -c3 [www.google.com](www.google.com). If it works, as I am confident it will, try Firefox and go look at Google. We have our fingers and toes crossed for you!

---

### Post by Buster95 on 2007-03-02
Thank you Master, but the force is not strong today. No luck!

xx@laptop:~$ ping -c3 64.233.161.99
PING 64.233.161.99 (64.233.161.99) 56(84) bytes of data.
64 bytes from 64.233.161.99: icmp_seq=1 ttl=240 time=263 ms
64 bytes from 64.233.161.99: icmp_seq=2 ttl=240 time=267 ms
64 bytes from 64.233.161.99: icmp_seq=3 ttl=240 time=260 ms

--- 64.233.161.99 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 260.361/263.609/267.442/2.920 ms
xx@laptop:~$ ping -c3 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=0.864 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.860 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=0.813 ms

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.813/0.845/0.864/0.040 ms
xx@laptop:~$ sudo gedit /etc/resolve.conf
Password:
dexter@laptop:~$ ping -c3www.google.com
Usage: ping [-LRUbdfnqrvVaA] [-c count] [-i interval] [-w deadline]
            [-p pattern] [-s packetsize] [-t ttl] [-I interface or address]
            [-M mtu discovery hint] [-S sndbuf]
            [ -T timestamp option ] [ -Q tos ] [hop1 ...] destination
xx@laptop:~$ 

You'd laugh if you saw how I'm migrating these terminal printouts to this page. I copy the laptop terminal output to a memory stick and carry it over to my PC to paste it here.

I'm starting to wonder if the issue is related to the modem, not the wireless router. The modem is a Netcomm NB5 ADSL2+ modem router. The wireless router is a D-Link DL-524.
My desktop PC running XP connects OK to the modem via Ethernet. My laptop in XP (using the modem and wireless togetheralso works well. But somehow, Edgy can't automatically do the necessary handshaking.

---

### Post by chili555 on 2007-03-02
```
ping -c3www.google.com
```

Hmmm. When a command kicks back Usage, it's saying, you missed something or, in this case, mis-typed something. Please try again: ping -c3 [www.google.com](www.google.com)

> You'd laugh if you saw how I'm migrating these terminal printouts to this page.  Laugh? We've all done it, and know it's a pain. 

We await your report with optimism.

---

### Post by Buster95 on 2007-03-02
It seems to me from this result that the damned machine is telling me that all is well and that my failure to connect is a curious figment of my fertile imagination.

xx@laptop:~$ ping -c3 [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (66.249.89.99) 56(84) bytes of data.
64 bytes from [www.google.com](www.google.com) (66.249.89.99): icmp_seq=1 ttl=240 time=158 ms
64 bytes from [www.google.com](www.google.com) (66.249.89.99): icmp_seq=2 ttl=240 time=158 ms
64 bytes from [www.google.com](www.google.com) (66.249.89.99): icmp_seq=3 ttl=240 time=158 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 158.323/158.524/158.893/0.261 ms
xx@laptop:~$

---

### Post by chili555 on 2007-03-02
After we hoist a tall, cool one, fire up Firefox and surf a bit. Also, now that you are connected, get the updates installed. System -> Administration -> Update Manager.

Have fun and welcome to the community!

---

### Post by Buster95 on 2007-03-02
The only problem is Chili555, I still can't connect!

---

### Post by chili555 on 2007-03-02
What did Firefox have to say? Did you back out whatever was in the address bar and type in [http://www.google.com](http://www.google.com) and press Enter? What happened then? You can summarize, no usbdrive.

---

### Post by Buster95 on 2007-03-02
I have set Google as my home page. I selected the home page icon and it just tries to connect until it times out. I also tried the update Ubuntu  selection and it failed also.

What's particularly galling is that I've just rebooted my laptop to XP and am using it to send this message, by wireless router and modem.

Is it possible that the driver of the laptop card is wrong for Edgy? The card in the laptop is a Realtek RTL 8187?

---

### Post by chili555 on 2007-03-02
It can't be wrong if you can successfully ping Google and your router. Ditto as to the suitability of the router and modem. Please reboot to Ubuntu, try ping -c3 [www.google.com](www.google.com) and, if successful, try Firefox again. If not successful, let us see sudo ifconfig wlan0.

This can't *not* work.

---

### Post by Buster95 on 2007-03-02
Rebooted to Edgy. Tried Firefox again - no luck; opened terminal;

xx@laptop:~$ ping -c3www.google.com
Usage: ping [-LRUbdfnqrvVaA] [-c count] [-i interval] [-w deadline]
            [-p pattern] [-s packetsize] [-t ttl] [-I interface or address]
            [-M mtu discovery hint] [-S sndbuf]
            [ -T timestamp option ] [ -Q tos ] [hop1 ...] destination
xx@laptop:~$ ping -c3www.google.com
Usage: ping [-LRUbdfnqrvVaA] [-c count] [-i interval] [-w deadline]
            [-p pattern] [-s packetsize] [-t ttl] [-I interface or address]
            [-M mtu discovery hint] [-S sndbuf]
            [ -T timestamp option ] [ -Q tos ] [hop1 ...] destination

Tried Firefox again - no luck

xx@laptop:~$ sudo ifconfig wlan0
Password:
wlan0     Link encap:Ethernet  HWaddr 00:15:AF:12:7D:B7  
          inet addr:192.168.0.171  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fe12:7db7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:55 errors:0 dropped:60 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9268 (9.0 KiB)  TX bytes:5550 (5.4 KiB)

xx@laptop:~$

Are we having fun yet?

---

### Post by chili555 on 2007-03-02
> xx@laptop:~$ ping -c3www.google.com
Usage: ping [-LRUbdfnqrvVaA] [-c count] [-i interval] [-w deadline]

> When a command kicks back Usage, it's saying, you missed something or, in this case, mis-typed something. Please try again: ping -c3 [www.google.com](www.google.com)


> Are we having fun yet? No.

```
inet addr:192.168.0.171
``` You have an IP address. You are connected.

It's beddy time here in the states, see you later.

---

### Post by Buster95 on 2007-03-02
Thanks for your patience. I'm sure I'll still be struggling with this for the next few days.
Maybe you can look me up again. I appreciate the help.
Cheers

---

### Post by zhtx on 2007-03-02
hey guys,
I'm new but I've been trying to get my wifi to work. the thing is I have a BCM4306 which is known to be pain in the *** but I have installed the card properly. the wireless connection worked until I restarted the system. now to switch it on i have to type:
sudo modprobe bcm43xx
but still I can see it in system > administration > networking, I don't know how to turn it on. also, NetworkManager Applet shows only wired connection and no other choice. I'm sure the card is working, it scans and finds the wireless networks. could you just tell me how to turn it on? I'm just not sure what to search for because everybody has problems with installing the drivers and firmware and I believe I'm done with that.
thanks in advance,
zhtx

---

### Post by Buster95 on 2007-03-03
[but still I can see it in system > administration > networking,]

What do you see in properties?

---

### Post by Buster95 on 2007-03-03
Still struggling with making this connection. In summary, I seem to ping OK but can't raise a website. It just grind away until it times out.
I know that the software is OK because XP works well on the other partition.
Any help would be gratefully accepted by a pathetically puzzled Buster95.
Cheers

---

### Post by chili555 on 2007-03-03
Good evening. Please open a terminal and type carefully:

firefox [http://www.yahoo.com](http://www.yahoo.com)

Let us know what happens and what, if any errors pop out on the terminal.

Check your typing, spaces, spelling, etc. carefully.

---

### Post by Buster95 on 2007-03-03
Hello again Chili555,
Appreciate your persistence.
Did it twice. Same result both times. It launches Firefox. "Connecting to www.yahoo..." appears at the bottom of the screen. It grinds on until it times out.
Cheers

---

### Post by bukwirm on 2007-03-03
Sounds suspiciously like a DNS problem. What is the output of this command: 

cat /etc/resolv.conf

---

### Post by chili555 on 2007-03-03
Getting late in USA and early in Oz?

When you go to Firefox, Edit -> Preferences -> Advanced -> Network, click Settings and how does it say you connect to the Internet? I believe in your situation, Direct is to be preferred. 

Close, click Home and let us know.

---

### Post by Buster95 on 2007-03-03
Thanks for your help

xx@laptop:~$ cat /etc/resolve.config
nameserver 192.168.0.1
xx@laptop:~$

---

### Post by chili555 on 2007-03-03
I hope you meant /etc/resolv.conf without the e and conf, not config!

Please see post #14. No wonder we are having trouble!!!

sudo gedit /etc/resolv.conf

Add the line:

nameserver 192.168.0.1

Save and quit.

Open up Firefox and pull a web page.

---

### Post by Buster95 on 2007-03-03
Hello Chili555,
Some delay in getting your message and responding. My desktop PC is not available to me right now, so I'm forced to keep swapping between XP and Edgy partitions to follow your instructions and communicate.
It's around 3:30pm in Sysney right now; it's sunny and around 30C. Why, why, why am I sitting here praying over this bloody machine???
To answer your question, Firefox advanced/ connection details/ propreties tells me that automatic connection is made. No other boxes or fields are populated.

Cheers

---

### Post by bukwirm on 2007-03-03
Your resolv.conf file generally needs to have the IP addresses of your ISP's DNS servers.
Can you connect to your modem directly, ie, not though your router (Edit: probably with a cable)? If you can, do so, then reboot. Look at the resolv.conf file and write down the IP addresses listed.
Then, go to your router's configuration. Somewhere, there should be a section labeled something like "Domain Name Server (DNS) Address". Choose the "Use these DNS servers" option and enter the addresses from resolv.conf
Reboot and try the wireless again - what does "cat /etc/resolv.conf" output?

---

### Post by Buster95 on 2007-03-03
> **chili555 said:**
> I hope you meant /etc/resolv.conf without the e and conf, not config!

Please see post #14. No wonder we are having trouble!!!

sudo gedit /etc/resolv.conf

Add the line:

nameserver 192.168.0.1

Save and quit.

Open up Firefox and pull a web page.

Hello Chili555,
Rechecked post #14. I did follow that instruction.
However, I repeated sudo gedit /etc/resolv.conf; cut-and-pasted "nameserver 192.168.0.1" (just in case I'd dislexified it) over the existing entry which looked identical to me, but I didn't want to risk it.  That screen now appears as: 
nameserver 192.168.0.1
nameserver 192.168.1.1

Firefox still doesn't pull up a website.

Reviewed some earlier posts. Comparing the output of sudo iwlist wlan0 scanning on your mahine to that of mine, I notice that yours has a signal level of -67dBm. Mine has zero. Tried it again a few minutes ago and it's the same. 
What i that telling me?
Cheers

---

### Post by bukwirm on 2007-03-04
If you connect to your router with a cable, can you get any web pages?

Also, did you try the stuff in my last post?

---

### Post by Buster95 on 2007-03-04
Hello Bukwirm
Sorry about the delay. I'm using the same laptop to communicate (XP) and check (Edgy). Lots of jumping back and forth.
Output of cat /etc/resolv.conf (cut-and-pasted)
xx@laptop:~$ cat /etc/resolv.conf
nameserver 192.168.1.1
nameserver 192.168.0.1
xx@laptop:~$ 

I tried hard connect using the ethernet line from modem to wireless router. No luck.
Then I tried the line from the modem to my desktop. No luck.
I then tried the line from modem to desktop only this time plugged into my laptop.
Booted up on Edgy. No luck. Rebooted on XP and that's what I'm using right now.

Cheers

ps forgot to mention I checked that the 2 addressed returned above are also shown in the DNS servers box
also,
in XP the IP address is given as 192.168.0.100. Is that the same as 192.168.1.1 as shown above from Edgy?

---

### Post by bukwirm on 2007-03-04
Hmm.... Extremely peculiar...

All right, you have a desktop connected to the router with a wired connection, correct? If the desktop is running linux, what does it's resolv.conf file look like?
What does the laptop's resov.conf look like if you connect it directly to the modem (then reboot, of course)?

Edit: I'm going to bed now, since its 1:30 am here, but I'll check back tomorrow.

---

### Post by Buster95 on 2007-03-04
I may have confused you there Bukwirm.
I have a desktop running XP linked to a Netcomm NB5 modem by ethernet. Also connected to the modem is a D-Link DL 524 wireless router. Everybody else in the family and the dog are connected to that.

I also have a laptop running XP and Edgy. The laptop is configured for ethernet or wireless connection. Both work with XP. Neither work with Edgy.

Eureka - just had a brain explosion......... thought I'd follow up some earlier threads relating to connectivity and ipv6. Disabled ipv6 using instructions from someone else on this forum AND IT WORKED! Sorry - was I shouting? I must have got a bit excited there.

I'm just posting this in case some other tragic has been following this thread. Mind you, I'm still on the ethernet link with my laptop and haven't yet tried the wireless link, But, I am pathetically and pathologically optimistic. I still have other challenges regarding making the audio and on-board webcam work, but that's for another thread.

Thanks to Chili555 and Bukwirm for staying up so late to help me.
Cheers

---

### Post by bukwirm on 2007-03-04
Gah! Why didn't I think of that!?

> **Buster95 said:**
> 
Thanks to Chili555 and Bukwirm for staying up so late to help me.
Cheers

You're welcome :)

---

### Post by justinux on 2007-03-06
Hi all,

I am experiencing a similar problem, and have tried a lot of the suggestions (including disabling ipv6), but still can not connect.  Here is my situation:

I have a DSL modem connected to a wireless router's uplink connection (acting as a switch).

In windows, I can connect to both the modem (192.168.1.0) and the router (192.168.1.1), the DNS/gateway is 192.168.1.0 and everything connects fine.

In ubuntu, on the same laptop, I can only connect to the router, it never makes it to the modem.  It seems like ubuntu doesn't see the router as a switch and does not even try to find the modem.  The DNS, however, is set to the modem (192.168.1.0).

How does windows know to move on to the modem and how can I get ubuntu to do the same?

Any ideas?
Thanks
-Justin

---

### Post by chili555 on 2007-03-06
Justin-

You will have better luck if you start your own new thread. Please post your ifconfig and cat /etc/resolv.conf along with this description of your problem.

---

