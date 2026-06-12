---
title: "No internet connection in Ubuntu 7.10"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by eXeCuTeR+ on 2007-10-20
I installed UBUNTU yesterday, and now it doesn't let me get into the internet.
My question is:
W-H-Y-?!

On windows my network works great!

I tried to reset my router and it didn't work.
ifconfig & lspic both work fine.
lspic contains the Ethernet Connection (it goes like: Bridge: NVIDIA ....... Ethernet Connection) and ifconfig contains eth0 and lo.
This makes the situation really weird.
Please help me, I'm exhausted.

Edit:
```
eth0
link encap: Ethernet HW addr 00:04:61:90:38:57
inet addr: 10.0.0.1 Bcast: 10.255.255.255 Mask: 255.0.0.0
inet6 addr: fe80::204:61ff:fe9d:3857/64 scope: Link
UP BROADCAST RUNNING MULTICAST MTU: 1500 METRIC: 1
RX packets: 7 errors: 0 dropped: 0 overruns: 0 frame: 0
TX packets: 39 errors: 0 dropped: 0 overruns: 0 carrier: 0
RX bytes: 1598 (1.5 KB) TX bytes: 5947 (5.8 KB)
interrupt: 16

lo
Link encap: Local Loopback
inet addr: 127.0.0.1 Mask: 255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU: 16436 Metric: 1
RX packets: 0 errors: 0 dropped: 0 overruns: 0 frame: 0
TX packets: 0 errors: 0 dropped: 0 overruns: 0 carrier: 0
callisions: 0 txqueeulen: 0
RX bytes: 0 (0.0 b) TX bytes: 0 (0.0 b)
```
Piece of the data is probably wrong because I typed the info by hand (with a pencil :O).
You'll understand.

BTW,
I got NVIDIA nForce Networking Controller.

H-E-L-P-!

---

### Post by mpierce on 2007-10-20
You haven't posted enough info for anyone to help you. 

You need to start with the output of ifconfig and the output from /etc/network/interfaces. 

I don't know it you are using Ubuntu or Kubuntu which I use. Both have a network configuration tool that should work by writing it's output back to /etc/network/interfaces.

---

### Post by eXeCuTeR+ on 2007-10-20
```
eth0
link encap: Ethernet HW addr 00:04:61:90:38:57
inet addr: 10.0.0.1 Bcast: 10.255.255.255 Mask: 255.0.0.0
inet6 addr: fe80::204:61ff:fe9d:3857/64 scope: Link
UP BROADCAST RUNNING MULTICAST MTU: 1500 METRIC: 1
RX packets: 7 errors: 0 dropped: 0 overruns: 0 frame: 0
TX packets: 39 errors: 0 dropped: 0 overruns: 0 carrier: 0
RX bytes: 1598 (1.5 KB) TX bytes: 5947 (5.8 KB)
interrupt: 16

lo
Link encap: Local Loopback
inet addr: 127.0.0.1 Mask: 255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU: 16436 Metric: 1
RX packets: 0 errors: 0 dropped: 0 overruns: 0 frame: 0
TX packets: 0 errors: 0 dropped: 0 overruns: 0 carrier: 0
callisions: 0 txqueeulen: 0
RX bytes: 0 (0.0 b) TX bytes: 0 (0.0 b)
```
Piece of the data is probably wrong because I typed the info by hand (with a pencil :O).
You'll understand.


How do I check the output of /etc/network/interfaces?

---

### Post by eXeCuTeR+ on 2007-10-20
Help please, come on, I'm sure you know how to handle this.

---

### Post by JackCrowley on 2007-10-20
Seems to be happening to a lot of us. I'm not sure whether you are wired or wireless, so I'm assuming the latter. A lot of the wireless drivers are proprietary (restricted), and don't come with the basic distribution, apparently due to licensing issues.

After Googling around with phrases like "Intel 3945 Gutsy Upgrade" , I got a solution from another post [http://ubuntuforums.org/showthread.php?p=3553103]("http://ubuntuforums.org/showthread.php?p=3553103")

The solution for me was to reload the restricted drivers via the command
[B][FONT="Courier New"]sudo apt-get install linux-restricted-modules
[/FONT][/B]
To get this command to work, you will need a live internet connection ... not necessarily a catch 22 situation, but sort of.

I rebooted my machine, selected the previous Linux kernel (2.6.20.16), and found that my network connection was OK. Then I did the command noted above. 

I could have also used a hardwired Internet connection. Or downloaded them from another working computer, burned them to CD-ROM, then add the CD-ROM to my repository list in Update Manager.

---

### Post by eXeCuTeR+ on 2007-10-20
I have Wired Connection, forgot to mention.

Hmm,
Does what you wrote affect only on Wireless Connections or Wired Connections also?
BTW,
previous Linux kernel? what do you mean? I don't have a previous version, I'm new to Linux, this is the first time I've ever downloaded Ubuntu or any other Linux OS.
And how could I possibly get a live internet connection except of my Window's internet connection?
OR! there are 3 options while opening the computer - I always take the first one or the 4th (Windows) one.
What are the other 2 - the 2nd and 3rd option? Does it have a live internet connection?

Sorry for my English, I'm tired (5:03 am here - I wanna solve this problem before I go to sleep)

Help me please :'(

---

### Post by kabuche on 2007-10-20
I have the same problem, i upgraded from 7.09 to 7.10, now at startup the network icon appears as disconnected. My onboard NIC has the link light on. If i disconnect and then connect the cable, network manager detects everything and i´m working again. It´s a very strange and uncomfortable bug  .

---

### Post by eXeCuTeR+ on 2007-10-20
Kabuche, I'm gonna try your solution.
I tried to reset and it didn't work, I'm wondering if disconnecting the cable works, but it sounds like a good idea.

So Jack, what am I supposed to do?
Type this command on the Terminal and restart my computer?

---

### Post by JackCrowley on 2007-10-20
Mine was a wireless problem, yours is wired. So the solution that I found does not seem appropriate.:(

And your situation is an initial install, mine was an upgrade. So, let's see what can be done.


In general, I've had my best success by simple Google searches, specific to the problem. In my case I searched for the keywords "Gutsy" "upgrade" "failed" "wireless" "Intel" "3945" and "Toshiba". I found hits on six or seven sites, tried three or four things, and finally succeeded.

If you know the specific hardware data , maybe from an lshw or lspci command, you probably will find someone with the same problem, hopefully solved.  These commands are run in the Terminal ... you probably already know that, but just in case you don't, the Terminal is started with alt-F2 or by the Menu Applications ... Accessories .. Terminal

For any command like lshw you can get an extended help screen by typing the word "man" before the command such as     man lshw.   To get out of the help screen you type Ctrl-Z

So search by specific Hardware Names and Model Numbers, specific problems, specific keywords such as Ubuntu, Gutsy, etc.  

I have never been the first guy with any specific problem with any hardware or software. There always has been someone who found the bug first.  Usually they have the solution, too. 

I assume from reading your original post that you have already found the Ubuntu troubleshooting page [http://ubuntuforums.org/showthread.php?t=25557]("http://ubuntuforums.org/showthread.php?t=25557")

Good luck ... get some sleep ... that helps too.:)

---

### Post by eXeCuTeR+ on 2007-10-20
Thanks mate :)
I've been trying to search tutorials/articles/and some other stuff in google and many more webs for a long time tho.

BTW!
I don't have school tomorrow, so I stayed awake with my friends (I mean, we are using ventrilo so we talk and do cool stuff all night lolz :D)

---

### Post by nanbudh on 2007-10-21
I am having same problem too. Just installed Gutsy and the internet is not working. I have an "always on connection" and on windows it works fine. previously i had 6.06 and all i had to do was configure ethernet's static ip address and it worked fine. Now in 7.10 there is this 'wired connection' option and i did configure its staic ip address but nothing happens and firefox des not connect. I do not know anything about networking tools but i have a feeling that using networking tool( located in admin) i can easily find out where the problem is.BTW i have an adsl modem and all the 4 lights are blinking bright(if nothing else :-))

---

### Post by eXeCuTeR+ on 2007-10-21
Hmm,
I will try to call my internet provider.
Meh :/

---

### Post by eXeCuTeR+ on 2007-10-21
Please help me! I'm so exhausted and tired of this :'(

---

### Post by nanbudh on 2007-10-22
i got my net working! it was simple, i had not filled in the DNS address of my wired connection. i did that and the browser came alive.

---

### Post by frodon on 2007-10-22
eXeCuTeR+, you should read this :
[http://ubuntuforums.org/showthread.php?t=582790](http://ubuntuforums.org/showthread.php?t=582790)

---

### Post by eXeCuTeR+ on 2007-10-22
> **nanbudh said:**
> i got my net working! it was simple, i had not filled in the DNS address of my wired connection. i did that and the browser came alive.

What? What do you mean? My gateway's address is there, is there supposed to be another address except from the gateway?
Please answer quickly, thanks :)

frodon, I'll read and edit my post, thanks :D

---

### Post by rbo83 on 2007-10-22
I had the very same problem upon initial 7.10 installation for a wired connection, where the IP address is pre-selected (no DHCP from a router or internet provider). The 3 things to get it to work :

1-) Click on the 'Wired COnnection' and go to 'Properties'. Fill the 3 boxes. Click on 'OK'
2-) Click on the 'DNS' tab. Enter the desired DNS address in the box AND HIT THE ENTER KEY. DO NOT CLICK ON THE ADD BUTTON. The ADD button is only for the subsequent DNSs if applicable. That behavior should be fixed. It obviously did not go through quality assurance by Canonical. 
3-) Go back to the Properties and set the Checkbox on the 'Wired Connection'. In my case I had to un-check it first, then re-check it. Click the 'OK' Button

I fail to understand why this display is not brought up automatically upon Installation, as obviously the installer knows that no connection is active after trying DHCP, while it actually found a wired connection. I suspect it is the same problem with NON-DHCP wireless connection. Quality, Quality, Quality...

---

### Post by eXeCuTeR+ on 2007-10-22
Wait,
I have to change it to Static IP Address instead of DHCP?
and BTW,
I don't know other DNS addresses except from my gateway's address. Where can I check for more?

Please help. thanks.

---

### Post by eXeCuTeR+ on 2007-10-22
Whoops!
rbo83, your solution didn't work.
How can I add a DNS address without pressing Add?

---

### Post by eXeCuTeR+ on 2007-10-22
Sorry, but please help me :'( please :'(

---

### Post by eXeCuTeR+ on 2007-10-22
Got it fixed :D
Edited 2 files in the etc directory. :)
Meh I'm good lol

---

### Post by ndaru on 2007-11-07
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/81057](https://bugs.launchpad.net/ubuntu/+bug/81057) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This one is related to bug #81057

[https://bugs.launchpad.net/ubuntu/+bug/81057](https://bugs.launchpad.net/ubuntu/+bug/81057)

Simply open **/etc/modprobe.d/aliases**. Look for **alias net-pf-10 ipv6**. Change it to **alias net-pf-10 off**. Restart Ubuntu. That's all.

---

### Post by kotak07 on 2007-11-07
i tried the ipv6  bug..but no chance for me..i was hoping it would work. nothing thats related to internet works on my laptop right now..i have wireless btw..i need to get it fixed since i am a student.

---

