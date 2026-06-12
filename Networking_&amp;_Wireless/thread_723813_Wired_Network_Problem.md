---
title: "Wired Network Problem"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by DarkMartyr on 2008-03-13
I have a Compaq Presario f755 and have just installed Ubuntu to try it out on here. I have used it on my desktop and love it. Only trouble is my ethernet card on my laptop isn't connecting to the internet. I left it on it's default (roaming mode) and it shows the two monitors but not lit up or any animation. Firefox cannot connect to websites and i can't ping [www.google.com](www.google.com). I enabled the restricted driver for my wireless (Atheros 5007eg) but it didn't add anything to the networking connection list. I'm on the vista partition right now and obviously the wired/wireless connections work fine.
Do I just need a driver for my ethernet card?
I didn't need to download one on my desktop, but obviously every computer is slightly different.
Any help would be great, I'm semi-newbie when it comes to Linux so if you need more info just tell me the commands I need. Thanks

---

### Post by DarkMartyr on 2008-03-13
Also, I've tried a few things I've seen on the forums here.

ifconfig output:

```

eth3            link encap:Ethernet Hwaddr 00:00:6C:13:F1:31
                   inet6 addr: fe80: :200:6cff:fe13:f131/64   Scope:Link
                   UP BROADCAST RUNNING MULTICAST   MTU:1500 Metric:1
                   RX packets:6430 errors:0 dropped:0 overruns:0 frame:0
                   TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
                   collisions:0  txqueuelen:1000
                   RX bytes:388068  (378.9 KB)    TX bytes:6075  (5.8 KB)
                   Interrupt:17  Base address:0x8000
  

```

---

### Post by alphaniner on 2008-03-13
Your ifconfig output suggests you have 3 other ethernet interfaces eth0, eth1, and eth2.  Can you run ```
ifconfig -a
``` please?  Also, do you know if you use DHCP (get an IP address automatically) or static IP (enter numbers manually) in windows?

---

### Post by DarkMartyr on 2008-03-13
This is kind of odd. I restarted my laptop and it did it's little "requesting network address" (something like that) and the monitors icon changes to those two dots and the swirling line (hope that makes sense). I right-clicked and opened the Connection Information and it now says eth4 and has all 0's for the addresses.


here is the new ifconfig -a

```
eth4      Link encap:Ethernet  HWaddr 00:00:6C:7F:B2:CB  
          inet6 addr: fe80::200:6cff:fe7f:b2cb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:449 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26940 (26.3 KB)  TX bytes:5124 (5.0 KB)
          Interrupt:18 Base address:0x4000 

eth4:avah Link encap:Ethernet  HWaddr 00:00:6C:7F:B2:CB  
          inet addr:169.254.9.21  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)


```
I didn't enter a static ip for windows so I assume it has to be DHCP

---

### Post by alphaniner on 2008-03-13
That is a problem.  For whatever reason, Ubuntu thinks your adapter is a new one eash time you boot.  Unfortunately, that is beyond my area of expertise.  I may still be able to help you get online, but you'd probably have to redo it each time you reboot as it involves editing config files.  For starters, make a backup copy of your interfaces file by typing

```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```

then open the file with

```
sudo nano /etc/network/interfaces
```.  For DHCP, the file should look something like this:

```
auto lo
iface lo inet loopback

auto eth*
iface eth* inet dhcp
```

the * in eth* being whatever it is showing up as in ifconfig.  So right now it would be eth4.

Then save the file by pressing 'CTRL+X', then 'y', then ENTER.

Now, run

```
sudo /etc/init.d/networking restart
```

at the end of a bunch of output, if all is well, you should see a message saying you were assigned an IP address, which should then show up in *ifconfig*.  If so, give google a ping.

I don't use the Network Manager at all (in fact I usually uninstall it) so I don't know what is going on with the icon as you mentioned.  Give this a try and if it works, you will at least have internet until someone fixes the bigger problem of your Phoenix-like ethernet adapter.

---

### Post by DarkMartyr on 2008-03-13
ok here is what happens when I do the network restart.

after a bunch of output it says

```

Listening on LPF/eth4/00:00:6c:7f:b2:cb
Sending on   LPF/eth4/00:00:6c:7f:b2:cb
Sending on   Socket/fallback
DHCPDISCOVER on eth4 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth4 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth4 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth4 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth4 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth4 to 255.255.255.255 port 67 interval 1
no DHCPOFFERS received.
No working leases in the persistent database - sleeping.
grep: etc/resolv.conf: no such file or directory
                                                                                                  [OK]

```


I might also mention I am not using a router I'm plugged right into my modem.

---

### Post by alphaniner on 2008-03-14
Well the fact that you saw

```
DHCPDISCOVER on eth4 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth4 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth4 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth4 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth4 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth4 to 255.255.255.255 port 67 interval 1
```

seems to imply that your card is working... try a couple more things for me if you would.

In Windows, open the command prompt and type

```
ipconfig /all
```

that's i**p**config not ifconfig.  Copy down the IP address, Subnet Mask, Default gateway, and DNS servers somewhere you can reach them in ubuntu.

In Ubuntu, type

```
sudo nano /etc/resolv.conf
```

The file doesn't exist yet, so type something, then delete it, then hopefully it will save the blank file when you save/quit like you did the last time.  Run ifconfig to see what your ethernet card is calling itself this time, and if it changed, update the interfaces file accordingly.  Then run /etc/init.d/networking restart again and let me know what happens.  If you get the message "grep: etc/resolv.conf: no such file or directory" then you will have to open the file again, type something and save it, then open it again and delete what you typed and save again.  There is an easier way to do this through the command line but I don't know what it is.  Then run the networking restart command again.

I should warn you that I may be completely wasting your time so please don't get too upset if this doesn't work out.  I have one more thing you can try and it involves entering all the information you acquired from the Windows but it is probably just a shot in the dark.

---

### Post by DarkMartyr on 2008-03-14
Okay, I think it is time to move onto the your last guess. In advance I appreciate all your help.

I did all that you said, had to modify the interfaces again to eth5 this time. Restarted the network and it gave less output, only tried 3 times for the DHCPDISCOVER and had no DHCPOFFERS again. This time however it didn't say it couldn't find the resolv.conf file.

---

### Post by alphaniner on 2008-03-14
Ok, I really doubt this is going to work but it is worth a shot.  Again, sorry for wasting your time, I really thought the first attmpt would fix things.  Anyhoo, open the interfaces file and make the following modifications:

```
auto lo
iface lo inet loopback

auto eth*
iface eth* inet **static**
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1 (may not have gotten one, if so just omit this entire line)
```

But replace those numbers with the ones you got from windows.

Now open the resolv.conf file and add a line for **each** of the DNS servers you got from windows in the following manner:

```
nameserver 12.34.56.78
nameserver 12.34.56.79
```

Then do a networking restart and see what happens.

---

### Post by DarkMartyr on 2008-03-14
I tried a network restart and got:

 * Reconfiguring network interfaces...
SIOCDELRT: no such process
 [ok]
 

I went ahead and tried pinging google.com as well as going to google.com in firefox

firefox just searches for google forever and ping times out says unkown host google.com

pinging my gateway (69.246.190.1) but it was hanging so i ctrl+c and it said 100% loss time 21009ms

---

### Post by DarkMartyr on 2008-03-14
Anyone else have any ideas? I would love to get my laptop up and running. -opens Solitaire while he waits-

---

### Post by alphaniner on 2008-03-14
I'm sorry I couldn't help you.  I did do some searching between posts (I searched for 'eth changing') about your increasing eth#.  Apparently you are not the only one who has had this problem.  There are unfortunately several different supposed solutions, though, so I still don't have an answer for you.

I did find out *why* your eth numbers are changing, however.  Look at the first ifconfig output you posted:

```
eth3            link encap:Ethernet Hwaddr **00:00:6C:13:F1:31**
```

and the second:

```
eth4      Link encap:Ethernet  HWaddr **00:00:6C:7F:B2:CB**
```

Notice the HWaddr is changing?  That's your network card's MAC address,and it should **not** be changing.  So when Ubuntu sees a different MAC address, it thinks it is a different card.  I started a post about the issue at [ifconfig hwaddr]("http://ubuntuforums.org/showthread.php?t=723917") it would probably be a good idea to jump in there and post the output of a few more *ifconfig*s.  Again, sorry for wasting so much of your time.  I gotta hit the sack soon but if you haven't figured things out by tomorrow afternoon I'll try to help some more (assuming you want any more of my 'help' ](*,) )

---

### Post by DarkMartyr on 2008-03-14
I'll hop on that other thread. Thanks for all the help

---

