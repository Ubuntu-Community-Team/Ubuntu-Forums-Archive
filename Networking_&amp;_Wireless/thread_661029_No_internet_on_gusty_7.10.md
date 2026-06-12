---
title: "No internet on gusty 7.10"
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by loera on 2008-01-07
ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:40:45:25:A8:48  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:45ff:fe25:a848/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2249 (2.1 KB)  TX bytes:3938 (3.8 KB)
          Interrupt:11 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

I have not been able to get internet access since edgy. I am trying gusty now. When I tried to set things like edgy, removing network manager and setting network to DCHP, my system would freeze. Now I have somehow managed to get it set to DCHP, and it seems to be connected but firefox just sits there trying to connect with no results. Any help is appreciated.

---

### Post by eluzi on 2008-01-07
In a terminal, do this:

cat /etc/resolv.conf

This file holds the DNS servers, they translate things like [www.google.com](www.google.com) in an ip address. If something is configured, then try:

ping [www.google.com](www.google.com)

If this is OK, then u should check your firefox LAN settings, about Proxy (the machines that redirect your requests to the internet and pass the answers back to you). 

Good luck :)

---

### Post by loera on 2008-01-07
Thanks for your response, this is what I get:

loera@loera-laptop:~$ cat /etc/resolv.conf
nameserver 69.20.128.5
nameserver 69.20.129.5
nameserver 24.116.212.232
loera@loera-laptop:~$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
loera@loera-laptop:~$ 

Nothing so far....

---

### Post by eluzi on 2008-01-07
Try this:

```
 route -n 
```

And post the output, u should have a default gateway set, and u should be able to ping it...

Example:

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.21.16.0      0.0.0.0         255.255.240.0   U     0      0        0 eth0
0.0.0.0         10.21.16.1      0.0.0.0         UG    0      0        0 eth0

```
ping 10.21.16.1
```

---

### Post by loera on 2008-01-07
Here are the results, I canceled the operation when it got to "seq=54". (whatever that means)

loera@loera-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
loera@loera-laptop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.103 icmp_seq=1 Destination Host Unreachable
From 192.168.1.103 icmp_seq=2 Destination Host Unreachable
From 192.168.1.103 icmp_seq=3 Destination Host Unreachable
.
.
.
From 192.168.1.103 icmp_seq=54 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
56 packets transmitted, 0 received, +54 errors, 100% packet loss, time 55154ms
, pipe 3
loera@loera-laptop:~$ ping 192.168.1.0
Do you want to ping broadcast? Then -b
loera@loera-laptop:~$ 

Thank you.
Sorry it takes a while for a response, I have to put the info on a jump drive and paste.

---

### Post by eluzi on 2008-01-07
Let me explain to u what's happening, the gateway is your mean of communication with the outside world, and the ping command tests connectivity. Seems like u are not even connected to the gateway... So u won't be able to get to the internet...

What's your internet connection ? 
In the machine with Ubuntu u also have windows ? 
And the machine u're writing from, is in the same network ? Its gateway is the same ?

Trying to figure out if the problem is really under Ubuntu or elsewhere...

---

### Post by loera on 2008-01-07
My laptop is the one having the problem, yes I am dual booting with windows.

I have a desktop that I dual boot as well, I am running 7.10 right now to write this and this is the 
route -n from this computer:

both computers are connected to linksys router

loera@loera-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

---

### Post by eluzi on 2008-01-07
Hummm got it... 

With the laptop, under Windows u can connect normally ? 
Can u navigate in both (laptop and desktop) at the same time, if under Win the connection is working ?

---

### Post by loera on 2008-01-07
I am now writing to you with my laptop running windows. .
When I first started, I was:
Ubuntu laptop = no internet
Windows desktop = internet

Then I switched:
Ubuntu Laptop = no internet
Ubuntu desktop =  internet

Now I'm:
Windows laptop =  internet
Windows desktop =  internet.

The goal is to go wireless with the laptop. it has a built in card. but if I can't even get wired, i don't think I have a chance with wireless.

Does this answer your question?

---

### Post by anti-loop on 2008-01-09
I hope you get your problem solved. I am in a similar situation. At least you got a person replying to your post.

---

### Post by kazib on 2008-01-09
This worked on my laptop just now.

Go to /boot/grub/  and open the file menu.lst

sudo gedit menu.lst      or     sudo emacs menu.lst

Scroll down to the blocks after the line "## ## End Default Options ##"

Your first menu item should look like this:

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic ...
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

At the end of the 'kernel ...' line  add:  acpi=noirq

Do this for only the first menu item.  Go back up to the top and find the line that begins with "timeout".  If the number after "timeout" is about 2 or 3,  set it a little higher to around 10.

And then, a little lower there is a line:  "hiddenmenu".  Place a "#" in front if there's not one already there.



Now reboot your computer and test out your connection like before.  If it works then 'hooray' and manually place "acpi=noirq" on the rest of the linux entries in menu.lst.


If this causes your computer to not boot at all, then boot into safe mode or the second entry on the grub menu and undo the changes to menu.lst


  Hope this helps.  Good Luck.

---

