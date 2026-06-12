---
title: "Issue on INTERNET"
date: 2006-08-12
forum: Networking &amp; Wireless
---

### Post by ese on 2006-08-12
[B]Well as i see there seems some problem on the internet things.
 like mine has happened to me, the thing is that i have a fresh ubuntu 6.06 installed on my pc and what i observed is that i can browse my shared FOLDERS on my server and even can enter in REMOTE desktop on my other pc. and PING to my server with a result of positive and there is a good packets RECIEVE and SEND response with my IP address displayed.
   The thing is that i couldn't connect to the internet whenever i try to connect with FireFox.
  Please help on this issue for i am new to migrate to LINUX things.[/B]

---

### Post by steve.horsley on 2006-08-12
Can you try these commands and post the responses?
[B]route
cat /etc/resolv.conf
ping 82.211.81.186
ping [www.ubuntuforums.org](www.ubuntuforums.org)[/B]

---

### Post by ese on 2006-08-12
Oh thanks for your help i am glad you are here to rescue me well i dont know how to open the command line

---

### Post by dmglouis on 2006-08-12
To open Terminal (command line), Applications > Accessories > Terminal

---

### Post by drtvasudevan on 2006-08-12
also try this
in the firefox address bar type about:config 
and in the filter bar type ipv6 
and change from false to true= just double click it 
shutdown firefox
restart firefox.

---

### Post by slakkie on 2006-08-12
> **steve.horsley said:**
> 
route


Use 'route -n' in stead of 'route' (name resolving off).

---

### Post by ese on 2006-08-13
TO steve.horsley
 Here are the results for the command you told me to type.
ese@compaq:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.145.0   *               255.255.255.0   U     0      0        0 eth0
default         192.168.145.254 0.0.0.0         UG    0      0        0 eth0
ese@compaq:~$ cat/etc/resolv.conf
bash: cat/etc/resolv.conf: No such file or directory
ese@compaq:~$ ping 82.211.81.186
PING 82.211.81.186 (82.211.81.186) 56(84) bytes of data.
64 bytes from 82.211.81.186: icmp_seq=1 ttl=42 time=551 ms
64 bytes from 82.211.81.186: icmp_seq=2 ttl=42 time=558 ms
64 bytes from 82.211.81.186: icmp_seq=3 ttl=42 time=564 ms
64 bytes from 82.211.81.186: icmp_seq=4 ttl=42 time=549 ms
64 bytes from 82.211.81.186: icmp_seq=5 ttl=42 time=562 ms
64 bytes from 82.211.81.186: icmp_seq=6 ttl=42 time=552 ms
64 bytes from 82.211.81.186: icmp_seq=7 ttl=42 time=561 ms
64 bytes from 82.211.81.186: icmp_seq=8 ttl=42 time=567 ms

  and for the last one here it is:

ese@compaq:~$ ping [www.ubuntuforums.org](www.ubuntuforums.org)
ping: unknown host [www.ubuntuforums.org](www.ubuntuforums.org)
ese@compaq:~$

---

### Post by ese on 2006-08-13
well i have changed the ipv6 to TRUE in the FireFox browser and also i can connect to google with the "http://72.14.207.99" ip address and i can see google's homepage but when i click on any of the links it returns SERVER CAN NOT BE FOUD.
  just tell em what info do you need from me.

---

### Post by NetworkGuy on 2006-08-13
Hi ese,

I think you mistyped a command that steve.horsley wanted.  It will probably explain what is going on

From the terminal type 
cat (space) /etc/resolv.conf

---

### Post by ese on 2006-08-15
well thanks for the correction friends 
      here is the second one based on what you had told me,
 also about the ipv6 i have changed it to TRUE and restart mozilla, but doesn't work i can only enter google using the IP address then the result is i can see google's HOMEPAGE but couldnt't continue whenever i click a link.
  This is the result i get in the Terminal command.
ese@compaq:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.145.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.145.254 0.0.0.0         UG    0      0        0 eth0
ese@compaq:~$ cat /etc.resolv.conf
cat: /etc.resolv.conf: No such file or directory
ese@compaq:~$ ping 82.211.81.186
PING 82.211.81.186 (82.211.81.186) 56(84) bytes of data.
64 bytes from 82.211.81.186: icmp_seq=2 ttl=42 time=556 ms
64 bytes from 82.211.81.186: icmp_seq=3 ttl=42 time=556 ms
64 bytes from 82.211.81.186: icmp_seq=5 ttl=42 time=555 ms
64 bytes from 82.211.81.186: icmp_seq=8 ttl=42 time=556 ms
64 bytes from 82.211.81.186: icmp_seq=9 ttl=42 time=556 ms
64 bytes from 82.211.81.186: icmp_seq=10 ttl=42 time=548 ms
64 bytes from 82.211.81.186: icmp_seq=12 ttl=42 time=547 ms
64 bytes from 82.211.81.186: icmp_seq=13 ttl=42 time=553 ms
64 bytes from 82.211.81.186: icmp_seq=14 ttl=42 time=567 ms
    And for the last command here it is:
ese@compaq:~$ ping [www.ubuntuforums.org](www.ubuntuforums.org)
ping: unknown host [www.ubuntuforums.org](www.ubuntuforums.org)
ese@compaq:~$

---

### Post by NetworkGuy on 2006-08-15
ese, we still haven't gotten a good resolv.conf file from you.   Type this in exactly as you see it. 


```
sudo cat /etc/resolv.conf
```

Please post the results of that command.

Thanks

---

### Post by drtvasudevan on 2006-08-16
note in ese's mail 
ese@compaq:~$ cat /etc.resolv.conf
cat: /etc.resolv.conf: No such file or directory

---

### Post by drtvasudevan on 2006-08-16
ese copy the command from networkguy's post and paste in terminal
ther is a typo in your command.
(you need to pullldown edit from menu and choose paste
control v wont work, right?)

---

### Post by NetworkGuy on 2006-08-16
Inbetween etc and resolv needs to be a / instead of a .

---

### Post by ese on 2006-08-17
Well i think i dont miss it now i just copied it and past, here are the results:
 Also i reinstalled Ubuntu and check for internet b/c i found that the internet worked just ok using the Live CD but after i install Ubuntu it worked for just 20 mnts and never after that while the update installation is still running.
ese@compaq:~$ sudo cat /etc/resolv.conf
Password:
nameserver 192.168.141.1
nameserver 196.200.96.1
nameserver 196.200.102.1
ese@compaq:~$

   As i observed in the Terminal output there seems no IP of my server just the IP the DHCP server used for referencing but i dont find the third one (196.200.102.1) its not in the Server TCP/IP -properties list that the server used to refer to the IP address. while the two are for Prefered and Alternate IP address that the Server used to refer.
  I guse i give you the info you need .
 Thanks for all your help friend i hope this would be resolved at last.

---

### Post by NetworkGuy on 2006-08-18
Are you setting up this install in your house or at a business?  

If it is at a house, I'm wondering if you are using a home firewall/router between you and the Internet? (Linksys, Belkin or D-Link for example)  Because if you were, the IP address you get for DNS would be the internal address for the router unless you actually changed the configuration of the router.

If you are setting this up at a business, you may need to get your IT staff involved, if possible.  As I don't want to tell you to do something that has repercussions on somebody else network.

>   As i observed in the Terminal output there seems no IP of my server just the IP the DHCP server used for referencing but i dont find the third one (196.200.102.1) its not in the Server TCP/IP -properties list that the server used to refer to the IP address. while the two are for Prefered and Alternate IP address that the Server used to refer.
 

Do you manage the DNS server we are trying to communicate with? :-?  

Before we go any farther, I need to know the following

[LIST]
[*]Home network or Business network?
[INDENT][*] If Home Network - Are you using a home firewall/router?[/INDENT]
[*]Are you managing a DNS server and/or a DHCP server (not on a home router)?
[*]When things seem to break, can you still open a terminal and  ```
ping 82.211.81.186
``` and ```
ping 192.168.141.1
```
[/LIST]

To be honest, I'm more confused now with your last statement about the primary and secondary addresses of the "server"  Sorry, but more information is required before we can fix this one.  Unless somebody is seeing something I am missing.  (That is very possible)

We will get to the bottom of this one.

---

### Post by ese on 2006-08-19
Thanks Mr. Networkguy for all your nonstop help.
 
  well here are things that i need to clear for you :
  about the q?s  u asked
 
1.its a buisness network and i manage the DHCP server.
2.ok the server address is 192.168.145.2
3.The server is installed with  Windows 2000servr OS only 
4.the server gives IP address to the Pcs connected to it (all are Windows XP OS installed) with IP address from 192.168.145.10 upto 192.168.145.200.
5.exept my pc all the windos based Pcs get their IP address immediately when i connect to the line that connects with the server B/c it is a DHCP server.
6.the server uses prefferd DNS server 192.168.141.1 to connect to the net (outside world) and also uses 196.200.96.1 as an alternate DNS server ( if 192.168.141.1 fails).....i found this when i click on the properties ..of the TCP/IP configuration of the server. (**i think you told me this is  what confuses you well i think i explain more now**)

Now i normally find 192.168.145.25 IP address on the Pc i am using with windows XP and can connect to the internet normaly as usual but when i restart the pc and start with Ubuntu i get 
192.168.141.1 , 196.200.96.1 and 196.200.102.1 on the system-Administration-Networking-then on the DNS tab.   (normaly I only find these address on the SERVER TCP/IP properties as i told you )
....inever find these IP address on any windows based pc that i connect to the server they just get a DHCP IP address from the server from 192.168.145.10 upto 192.168.145.200.

 Now the other thing is that, on Ubuntu i can type an IP address of google on the Firefox address like this [http://72.14.207.99](http://72.14.207.99) and it comes with the hompage  but couldn't continue when i click a link form it or when  i type [www.google.com](www.google.com)  at the address.
 I have set IPV6 to true in Firefox.
 ... one thing i have read a thread says about totally changing IPV6 from Ubuntu (not only from Firefox) but i dont know how do that i thought may be i should try that.
 B/c the main thing seems Ubuntu doesn't get an IP address from the DHCP server (192.168.145.2) mainly b/c of some misunderstand between the server and the PC with Ubuntu either  in settings or protocol or somthings like IPV6 things like that.....
  And i dont think the server is set to Firwall b/c it is win2000.

  i gues i clear something so i will be waiting for your answer i hope i  answered what you ask or things you wanted to know. if still remain something i will ....

Also here is below what you told me to type on Terminal command.
  Thanks a lot for all your help.
   ese


ese@compaq:~$ ping 82.211.81.186
PING 82.211.81.186 (82.211.81.186) 56(84) bytes o f data.
64 bytes from 82.211.81.186: icmp_seq=1 ttl=42 ti me=574 ms
64 bytes from 82.211.81.186: icmp_seq=2 ttl=42 ti me=587 ms
64 bytes from 82.211.81.186: icmp_seq=3 ttl=42 ti me=564 ms
64 bytes from 82.211.81.186: icmp_seq=4 ttl=42 ti me=602 ms
64 bytes from 82.211.81.186: icmp_seq=5 ttl=42 ti me=601 ms
64 bytes from 82.211.81.186: icmp_seq=6 ttl=42 ti me=570 ms
64 bytes from 82.211.81.186: icmp_seq=8 ttl=42 time=555 ms
64 bytes from 82.211.81.186: icmp_seq=9 ttl=42 time=577 ms

and here is for the second one:
ese@compaq:~$ ping 192.168.141.1
PING 192.168.141.1 (192.168.141.1) 56(84) bytes of data.
64 bytes from 192.168.141.1: icmp_seq=1 ttl=61 time=17.1 ms
64 bytes from 192.168.141.1: icmp_seq=2 ttl=61 time=12.3 ms
64 bytes from 192.168.141.1: icmp_seq=3 ttl=61 time=13.1 ms
64 bytes from 192.168.141.1: icmp_seq=4 ttl=61 time=6.65 ms
64 bytes from 192.168.141.1: icmp_seq=5 ttl=61 time=58.6 ms
64 bytes from 192.168.141.1: icmp_seq=6 ttl=61 time=12.6 ms
64 bytes from 192.168.141.1: icmp_seq=7 ttl=61 time=17.5 ms
64 bytes from 192.168.141.1: icmp_seq=8 ttl=61 time=11.0 ms
64 bytes from 192.168.141.1: icmp_seq=9 ttl=61 time=17.3 ms
64 bytes from 192.168.141.1: icmp_seq=10 ttl=61 time=11.1 ms
64 bytes from 192.168.141.1: icmp_seq=11 ttl=61 time=17.3 ms
64 bytes from 192.168.141.1: icmp_seq=12 ttl=61 time=19.4 ms
64 bytes from 192.168.141.1: icmp_seq=13 ttl=61 time=41.1 ms
64 bytes from 192.168.141.1: icmp_seq=14 ttl=61 time=6.68 ms
64 bytes from 192.168.141.1: icmp_seq=15 ttl=61 time=19.2 ms
64 bytes from 192.168.141.1: icmp_seq=16 ttl=61 time=20.3 ms
64 bytes from 192.168.141.1: icmp_seq=17 ttl=61 time=12.9 ms
64 bytes from 192.168.141.1: icmp_seq=18 ttl=61 time=8.19 ms
64 bytes from 192.168.141.1: icmp_seq=19 ttl=61 time=23.0 ms
64 bytes from 192.168.141.1: icmp_seq=20 ttl=61 time=22.2 ms
64 bytes from 192.168.141.1: icmp_seq=21 ttl=61 time=10.7 ms

  also for my server have done this onmyself maybe it could help:
ese@compaq:~$ ping 192.168.141.2
PING 192.168.141.2 (192.168.141.2) 56(84) bytes of data.
64 bytes from 192.168.141.2: icmp_seq=1 ttl=125 time=90.2 ms
64 bytes from 192.168.141.2: icmp_seq=2 ttl=125 time=144 ms
64 bytes from 192.168.141.2: icmp_seq=3 ttl=125 time=19.6 ms
64 bytes from 192.168.141.2: icmp_seq=4 ttl=125 time=54.3 ms
64 bytes from 192.168.141.2: icmp_seq=5 ttl=125 time=101 ms
64 bytes from 192.168.141.2: icmp_seq=6 ttl=125 time=66.3 ms
64 bytes from 192.168.141.2: icmp_seq=7 ttl=125 time=8.84 ms
64 bytes from 192.168.141.2: icmp_seq=8 ttl=125 time=20.2 ms
64 bytes from 192.168.141.2: icmp_seq=9 ttl=125 time=11.9 ms
64 bytes from 192.168.141.2: icmp_seq=10 ttl=125 time=10.2 ms
64 bytes from 192.168.141.2: icmp_seq=11 ttl=125 time=211 ms
64 bytes from 192.168.141.2: icmp_seq=12 ttl=125 time=21.5 ms
64 bytes from 192.168.141.2: icmp_seq=13 ttl=125 time=50.6 ms
64 bytes from 192.168.141.2: icmp_seq=14 ttl=125 time=26.4 ms
64 bytes from 192.168.141.2: icmp_seq=15 ttl=125 time=26.6 ms
64 bytes from 192.168.141.2: icmp_seq=16 ttl=125 time=16.1 ms
64 bytes from 192.168.141.2: icmp_seq=17 ttl=125 time=13.7 ms
64 bytes from 192.168.141.2: icmp_seq=18 ttl=125 time=8.57 ms
64 bytes from 192.168.141.2: icmp_seq=19 ttl=125 time=15.5 ms
64 bytes from 192.168.141.2: icmp_seq=20 ttl=125 time=252 ms
64 bytes from 192.168.141.2: icmp_seq=21 ttl=125 time=12.6 ms

---

### Post by NetworkGuy on 2006-08-19
Hmmm.

So if I understand this correctly, your PC is setup to  dual boot Windows and Ubuntu.  When you boot into Windows, everything is fine and works as designed.  but when you boot in Ubuntu, not only do you not get the IP address that your NIC is assigned in DHCP, you don't get the proper DNS servers either.

> Now the other thing is that, on Ubuntu i can type an IP address of google on the Firefox address like this [http://72.14.207.99](http://72.14.207.99) and it comes with the hompage but couldn't continue when i click a link form it or when i type [www.google.com](www.google.com) at the address.
I have set IPV6 to true in Firefox.


I don't think this is a FireFox issue since you can't ping anything by name when things break.

I'm wondering, since the guy who owns DHCP, owns the subnet IMO, is it possible that you can hard-code an IP address and the correct DNS servers into your network properties and see what happens?  If this continues to work for a while, we might be able to keep it this way. 

The only way I can think of to try to figure out what is actually going on is to run two network packet captures.  One when you PC boots Windows and tries to obtain an IP address from DHCP and then another packet capture looking for the same thing but in Ubuntu.  Once you have the two packet captures, compare them side by side and try to figure out where the problem lies.   

Granted, nothing created by Micro$oft, is fully compatible with standards, but something as easy as obtaining the correct IP address information should work no matter what OS is running on your PC.

So..  as I stated above, first try hardcoding your IP & DNS address information into your network settings and see what happens.  If everything seems to work fine, you can either let sleeping dogs lie, or move onto step 2 where you try to sniff your network and determine why DHCP doesn't work properly for you.

---

### Post by RSL on 2006-08-28
I don't know if this helps but aren't 192.168.*.* addresses always local? It seems to me like having them as DNS servers might be the problem. [But I'm no expert.] I do know that 4.2.2.1, 4.2.2.2, 4.2.2.3, and 4.2.2.4 work for a lot of people [on various forums].

---

