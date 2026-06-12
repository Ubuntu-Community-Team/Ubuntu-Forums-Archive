---
title: "DNS Problems"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by tjb_15 on 2007-03-02
I have two computers on my network a Windows XP and one with Windows 2000 and Ubuntu. When I try to access files of the XP I have to take the DNS off ubuntu but It won't go on the internet with out it. I have the DNS servers typed in to my router. Is there a way that I can access the internet and my other Computer at the same time?

---

### Post by rjfioravanti on 2007-03-02
what kind of internet connection do you get from your ISP. Typically I thought DNS was always provided by ISP, and the router knows where those, so why do you have to put them in Ubuntu

How does your ubuntu connect to your router

---

### Post by tjb_15 on 2007-03-02
> **rjfioravanti said:**
> what kind of internet connection do you get from your ISP. Typically I thought DNS was always provided by ISP, and the router knows where those, so why do you have to put them in Ubuntu

How does your ubuntu connect to your router

I Have A wireless connection. The reason I have a dns is I'm using opendns. The computer is connected to the router via Lan cable. Ubuntu put them in there when I installed it. If I take them out I can't get on the internet. If I leave them in I can't see the files on my other computer.

---

### Post by rjfioravanti on 2007-03-02
I just looked opendns up, sounds pretty cool, but I haven't heard of it until now. Is it possible to type the address of opendns directly into your router?

---

### Post by tjb_15 on 2007-03-02
> **rjfioravanti said:**
> I just looked opendns up, sounds pretty cool, but I haven't heard of it until now. Is it possible to type the address of opendns directly into your router?

I do have it in my router

---

### Post by dannyboy79 on 2007-03-02
dns servers would not prevent samba to work. it must just be a coincidence. are you trying to get to your network computers by computer name or ip address? all open dns is according to its' website it: OpenDNS uses its distributed network of DNS servers to speed up your Internet experience, increase reliability, improve security and make DNS smarter for users all over the world. So instead of you using your isp's dns servers, you're using open dns's servers. and yes, without dns server's defined, you won't be able to resolve internet website, you'd be able to surf to them if you knew their ip address. can you ping your windows box when the open dns settings are in tact? if so, than the open dns settings aren't causing your network issues. it's something else. make sure your open dns settings are set and then show me the output from these commands:

ps aux | grep mbd

smbtree

findsmb

---

### Post by tjb_15 on 2007-03-02
> **dannyboy79 said:**
> dns servers would not prevent samba to work. it must just be a coincidence. are you trying to get to your network computers by computer name or ip address? all open dns is according to its' website it: OpenDNS uses its distributed network of DNS servers to speed up your Internet experience, increase reliability, improve security and make DNS smarter for users all over the world. So instead of you using your isp's dns servers, you're using open dns's servers. and yes, without dns server's defined, you won't be able to resolve internet website, you'd be able to surf to them if you knew their ip address. can you ping your windows box when the open dns settings are in tact? if so, than the open dns settings aren't causing your network issues. it's something else. make sure your open dns settings are set and then show me the output from these commands:

ps aux | grep mbd

smbtree

findsmb

Yes I can ping the windows computer with the dns intact. Why would they need to be in both the router and the settings? I don't have them set on the windows computer

---

### Post by dannyboy79 on 2007-03-02
> **tjb_15 said:**
> Yes I can ping the windows computer with the dns intact. Why would they need to be in both the router and the settings? I don't have them set on the windows computer

you have obviously misunderstood me. You have informed us that if you "remove" the opendns settings from ubuntu, than you can't get online but you can view your samba connections correct? But if you put the dns settings back in ubuntu, that you can get online but can't see winxp. Well, I am saying, make it so that your ubuntu can get on the internet (ie: put the dns settings on) and then tel me what the output is from the commands I have suggested. otherwise I can't provide any suggestions otr help. Also, let me see the output from the these command as well as you doing what I already asked for

cat /etc/network/interfaces

cat /etc/resolv.conf

---

### Post by tjb_15 on 2007-03-02
> **dannyboy79 said:**
> you have obviously misunderstood me. You have informed us that if you "remove" the opendns settings from ubuntu, than you can't get online but you can view your samba connections correct? But if you put the dns settings back in ubuntu, that you can get online but can't see winxp. Well, I am saying, make it so that your ubuntu can get on the internet (ie: put the dns settings on) and then tel me what the output is from the commands I have suggested. otherwise I can't provide any suggestions otr help. Also, let me see the output from the these command as well as you doing what I already asked for

cat /etc/network/interfaces

cat /etc/resolv.conf
Sorry. I think I got what you wanted now...
------------------------------------------------------------------------
onthehill14@onthehill-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
address 192.168.1.9
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
----------------------------------------------------------
onthehill14@onthehill-desktop:~$ cat /etc/resolv.conf
nameserver 208.67.222.222
nameserver 208.67.220.220

---

### Post by dannyboy79 on 2007-03-02
are those 2 numbers within resolv.conf your open dns servers you were told to use? are those the same numbers within your router? 

i am guessing that since you are using dhcp, that your dns settings aren't being saved or they are but they're wrong try this. Edit your /etc/dhcp3/dhclient.conf file and uncomment this line:
#prepend domain-name-servers 127.0.0.1;

and change the number to match your open dns server numbers.  put 1 space in between your 2 dns server numbers. it should look like this if the numbers within the resolv.conf file are correct:

prepend domain-name-servers 208.67.222.222 208.67.220.220;

also, comment out all those interfaces, if you don't have the interfaces than you don't need them. only leave these 2 sections:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
address 192.168.1.9
netmask 255.255.255.0
gateway 192.168.1.1

and comment out all the rest like this:

#auto eth1
#iface eth1 inet dhcp

Plus you never gave me what I asked for first. If you want my help, than help me help you otherwise I give up.

ps aux | grep mbd

smbtree

findsmb

---

### Post by tjb_15 on 2007-03-02
> than you can't get online but you can view your samba connections correct?
I was going places/network places and finding my other computer
> **dannyboy79 said:**
> are those 2 numbers within resolv.conf your open dns servers you were told to use?  Yes

> are those the same numbers within your router? 
Yes
> 
i am guessing that since you are using dhcp, that your dns settings aren't being saved or they are but they're wrong try this. Edit your /etc/dhcp3/dhclient.conf file and uncomment this line:
#prepend domain-name-servers 127.0.0.1;

and change the number to match your open dns server numbers.  put 1 space in between your 2 dns server numbers. it should look like this if the numbers within the resolv.conf file are correct:

prepend domain-name-servers 208.67.222.222 208.67.220.220;

also, comment out all those interfaces, if you don't have the interfaces than you don't need them. only leave these 2 sections:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
address 192.168.1.9
netmask 255.255.255.0
gateway 192.168.1.1

and comment out all the rest like this:

#auto eth1
#iface eth1 inet dhcp

Plus you never gave me what I asked for first. If you want my help, than help me help you otherwise I give up.

ps aux | grep mbd

smbtree

findsmb

It won't let me save these. Is there a special way that I'm suppose to change them? I'm Kind of a noob.

---

### Post by dannyboy79 on 2007-03-02
you need to be specific and yet you still haven't given me the info I needed.

---

### Post by tjb_15 on 2007-03-02
> **dannyboy79 said:**
> you need to be specific and yet you still haven't given me the info I needed. And what would that be?

---

### Post by dannyboy79 on 2007-03-02
im sorry but if you aren't going to READ my responses and provide the information that I ask so that I can help YOU out, than I will continue on my quest to help others. i have been very patient and have asked you  for specific info in order to troubleshoot this and you haven't provided it on 2 seperate occassions and you have to ask what it is I want to see in order to troubleshoot? Ha. i do however wish you luck I just don't have to patience to help you anymore.

---

### Post by tjb_15 on 2007-03-02
> **dannyboy79 said:**
> im sorry but if you aren't going to READ my responses and provide the information that I ask so that I can help YOU out, than I will continue on my quest to help others. i have been very patient and have asked you  for specific info in order to troubleshoot this and you haven't provided it on 2 seperate occassions and you have to ask what it is I want to see in order to troubleshoot? Ha. i do however wish you luck I just don't have to patience to help you anymore.
This must be what you want. Sorry I didn't see.
---------------------------------------------------------------------------------------------------
onthehill14@onthehill-desktop:~$ ps aux | grep mbd
root      4401  0.0  0.3   5888  1368 ?        Ss   11:34   0:00 /usr/sbin/nmbd -D
root      4403  0.0  0.5   8760  2164 ?        Ss   11:34   0:00 /usr/sbin/smbd -D
root      4420  0.0  0.2   8760   944 ?        S    11:34   0:00 /usr/sbin/smbd -D
1000      5918  0.0  0.1   2796   752 pts/0    R+   12:16   0:00 grep mbd
---------------------------------------------------------------------------------------------------

---

### Post by dannyboy79 on 2007-03-02
now, on 3 different occassions I have asked for this info:


ps aux | grep mbd

smbtree

findsmb 

you have provided me with the ps aux and that was it. I also asked you to be more specific about WHAT you can't save. I have no idea what you are asking me. How do you expect people to help you when you aren't being specific and you aren't providing the info we need to help you? You need to read thru my posts and provide answers or don't bother asking for help.

---

### Post by tjb_15 on 2007-03-02
(---------------------------------------------------------------------------------------------------------------------------------)
onthehill14@onthehill-desktop:~$ smbtree
Password: 
LAN
        \\DELL1          
timeout connecting to 208.69.32.130:445
timeout connecting to 208.69.32.130:139
Error connecting to 208.69.32.130 (Operation already in progress)
cli_start_connection: failed to connect to DELL1<20> (208.69.32.130)
(---------------------------------------------------------------------------------------------------------------------------------)
onthehill14@onthehill-desktop:~$ findsmb 

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.3     unknown nis name [      LAN           ]

(---------------------------------------------------------------------------------------------------------------------------------)
> i am guessing that since you are using dhcp, that your dns settings aren't being saved or they are but they're wrong try this. Edit your /etc/dhcp3/dhclient.conf file and uncomment this line:
#prepend domain-name-servers 127.0.0.1;

and change the number to match your open dns server numbers. put 1 space in between your 2 dns server numbers. it should look like this if the numbers within the resolv.conf file are correct:

prepend domain-name-servers 208.67.222.222 208.67.220.220;

also, comment out all those interfaces, if you don't have the interfaces than you don't need them. only leave these 2 sections:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
address 192.168.1.9
netmask 255.255.255.0
gateway 192.168.1.1

and comment out all the rest like this:

#auto eth1
#iface eth1 inet dhcp
I can't Make these changes. It says there read only

---

### Post by dannyboy79 on 2007-03-02
> **tjb_15 said:**
> (---------------------------------------------------------------------------------------------------------------------------------)
onthehill14@onthehill-desktop:~$ smbtree
Password: 
LAN
        \\DELL1          
timeout connecting to 208.69.32.130:445
timeout connecting to 208.69.32.130:139
Error connecting to 208.69.32.130 (Operation already in progress)
cli_start_connection: failed to connect to DELL1<20> (208.69.32.130)
(---------------------------------------------------------------------------------------------------------------------------------)
onthehill14@onthehill-desktop:~$ findsmb 

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.3     unknown nis name [      LAN           ]

(---------------------------------------------------------------------------------------------------------------------------------)

I can't Make these changes. It says there read only

well in order for you to do any administrative work or change a file that is not owned by you, you would need to use sudo or gksudo (gksudo is used for root access using gui type programs), which gives you root privalages temporarily for a set amount of time. so the command would be, 
gksudo gedit /etc/network/interfaces
and 
gksudo gedit /etc/dhcp3/dhclient.conf

HANG ON THOUGH. I would like you to "un-set" your dns settings again (whatever you were doing before to get rid of dns on ubuntu) so that you can view your other windows computer thru network and then I want you to again, do those commands:

smbtree

findsmb


Also, please tell me what all your ip addresses are everything, even your router's external ip not only the internal ip. (you can find that out by going to [http://whatismyipaddress.com/](http://whatismyipaddress.com/)) the above info you posted after smbtree is VERY weird and something is really wrong!!!

---

### Post by tjb_15 on 2007-03-02
> **dannyboy79 said:**
> well in order for you to do any administrative work or change a file that is not owned by you, you would need to use sudo or gksudo (gksudo is used for root access using gui type programs), which gives you root privalages temporarily for a set amount of time. so the command would be, 
gksudo gedit /etc/network/interfaces
and 
gksudo gedit /etc/dhcp3/dhclient.conf
 Okay this is done
> 
HANG ON THOUGH. I would like you to "un-set" your dns settings again (whatever you were doing before to get rid of dns on ubuntu) so that you can view your other windows computer thru network and then I want you to again, do those commands:

smbtree

findsmb
I was going "system/administration/networking" But I Changed something and now Bug Buddy opens and asks me to send an error 

> 
Also, please tell me what all your ip addresses are everything, even your router's external ip not only the internal ip. (you can find that out by going to [http://whatismyipaddress.com/](http://whatismyipaddress.com/)) the above info you posted after smbtree is VERY weird and something is really wrong!!!
Routers: 192.168.1.1
My IP Address (from Link above): 216.228.196.154 
Windows XP: 192.168.1.2
Ubuntu: 192.168.1.3

---

### Post by dannyboy79 on 2007-03-02
you're NOT reading again!!!! im done helping you. sorry I couldn't be patient enough to help you. good luck

---

### Post by tjb_15 on 2007-03-02
> **dannyboy79 said:**
> you're NOT reading again!!!! im done helping you. sorry I couldn't be patient enough to help you. good luck
I just reread every thing and don't see anything I missed.

---

### Post by symbo978 on 2007-03-03
I am also having DNS address issues which may be related or may be a bug. I enter my ISP DNS server addresses in the network setup dialogue. Internet access via my wired router is fine. Some time later however, Ubuntu deletes these addesses and inserts my router address instead and Internet access is lost. Network access to other, Windows, PCs on the network is fine in either condition. Is there any way to prevent Ubuntu from changing the DNS addesses?

---

### Post by dannyboy79 on 2007-03-03
> **symbo978 said:**
> I am also having DNS address issues which may be related or may be a bug. I enter my ISP DNS server addresses in the network setup dialogue. Internet access via my wired router is fine. Some time later however, Ubuntu deletes these addesses and inserts my router address instead and Internet access is lost. Network access to other, Windows, PCs on the network is fine in either condition. Is there any way to prevent Ubuntu from changing the DNS addesses?

yes, since you are using dhcp, you need to prepend your dns servers in the /etc/dhcp3/dhclient.conf file just like I told the other guy. good luck. also, this has been explained already in several threads, use a forum search if my suggestion about the prepend line a few posts back doesn't work but i am pretty sure it will work as that's what the suggestions have been in other threads..

---

### Post by dannyboy79 on 2007-03-03
> **tjb_15 said:**
> I just reread every thing and don't see anything I missed.


well you're obviously not reading good enough then, post #18 CLEARLY stated:

HANG ON THOUGH. I would like you to "un-set" your dns settings again (whatever you were doing before to get rid of dns on ubuntu) so that you can view your other windows computer thru network and then I want you to again, do those commands:

smbtree

findsmb

BUT you didn't provide it and after having to ask and re-ask over and over for info, I am done trying to help you.

---

