---
title: "Bump... network is unreachable"
date: 2006-10-12
forum: Networking &amp; Wireless
---

### Post by uwjames on 2006-10-12
hello, I have gotten little response on my original thread and am sick of scouring the forums and other locations for a fix to my problem.  My network card and my ADSL modem are not talking in Ubuntu (everything is fine in windows).  I have tried dhclient, pppoeconf, etc.. etc.. please check out the original thread (linked below), there is lots posted.

thanks, and sorry about the repost.

[http://ubuntuforums.org/showthread.php?t=275305](http://ubuntuforums.org/showthread.php?t=275305)

---

### Post by kidders on 2006-10-12
Hi there,

Unfortunately, you haven't given us very much to go on :-( You seem (in your other thread) to have tried a weird collection of odd stuff to get things working!

I wonder whether your modem works like mine, (in that it can connect to the internet all by itself). How do you work things in XP?

I suppose the best place to start is to find out whether Ubuntu is detecting your network card, and whether you can manually configure a network connection to *anything* with it. If we know you can do that much, that'll be a big help :-) From there, you'd need to post something about how your connection to your ISP works, and how much of the donkey work your DSL router can do on its own.

---

### Post by uwjames on 2006-10-12
Hi Kidders, thanks for the reply.

I believe the modem does all the "donkey work".  When I boot into XP the internet connection is instantly on. I don't have to log in or run any program for SBCGlobal, all that is taken care of by the modem, as is DHCP serving.  It's a speedstream 4100.  The DNS servers are 
68.94.156.1  dnsr1.sbcglobal.net
68.94.157.1  dnsr2.sbcglobal.net

and the modem IP is 192.168.0.1.

As for the ethernet card, I am not sure if ubuntu is recognizing it properly or not.  I believe I am loading the correct module (8139too) and the ubuntu device manager sees something there.. but how can I know for sure unless it connects to the modem?

in my original post I listed output from ifdown ifup lsmod and ifconfig.  the ifdown and ifup show that whatever device ubuntu thinks eth0 is, it's not receiving DHCP offers from the modem.  I know the modem isn't the problem because XP is getting dynamic ip's just fine.  lsmod has two areas I that seem relevant and probably more:

8139too 26880 0    <------this is the correct module for my 
                   onboard networking card... realtek RTL8139
mii 5888 1 8139too

and also...

pppoe 14400 0
pppox 3720 1 pppoe
ppp_generic 30100 2 pppoe,pppox
slhc 7424 1 ppp_generic

(not sure what this is, but pppoeconf has not worked for me yet, and it says my network cable is either unplugged or another process is interfering)

finally, ifconfig shows that the interface eth0 has no IP and has a hardware address (00:E0:18:21:1C:2D, hopefully the same HWaddress as my onboard ethernet).  I also see eth0 has an inet6 address (not ip though) and I have read in some threads that this can cause troubles.

obviously I have just enough knowledge to be dangerous/sound like an idiot.

-the dangerous idiot

---

### Post by kidders on 2006-10-13
> obviously I have just enough knowledge to be dangerous/sound like an idiot.Lol there's no need to give out about yourself for having gone to the trouble of learning some stuff about networking :-) Hehe.

First thing's first though ... forget about PPPoE, etc. You won't need them. Also, it is starting to sound as if your network card is fine. The next thing I would try is manually assigning myself an IP. Since you don't seem to have anything network aware, other than your modem and your Ubuntu box, we'll just have to make do :-P

So, ignore DHCP and give your Ubuntu box an IP yourself ... say 192.168.0.123. (I'm assuming 255.255.255.0 is an appropriate netmask.) Your default route would be 192.168.0.1. That should give you access to the network. Then, try to ping your router. Off the top of my head, I can't think of anything reasonable that would prevent you from getting this far.

Assuming you can, your problem is very likely something simple, and well-known. It could, for instance, be nothing more than a glitch in the DHCP implementation on your modem or in Ubuntu. If we can get you to a point where you can be reasonably sure something like this is the problem, there are a few things you can play with to sort yourself out.

Hope that helps.

---

### Post by almax00 on 2006-10-13
can you post your: /etc/network/interfaces ? i have had this problem before and somehow an extra line or 2 gets added or deleted from interfaces file and my wifi card can't connect to the network.

---

### Post by Iowan on 2006-10-13
> **almax00 said:**
> can you post your: /etc/network/interfaces ?Unless recently changed, it's in his other thread (current copy might still be nice);) 
Whilst dinking around with my dhclient.conf file, I learned that a misconfigured file results in no IP address - which causes no NIC activation. **kidders** suggestion of a static IP address should help see if the NIC is the problem - or if the DHCP is causing trouble.

---

### Post by almax00 on 2006-10-13
> **Iowan said:**
> Unless recently changed, it's in his other thread (current copy might still be nice);)

johndoe@johndoe-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto dsl-provider     <---------- add this ?
iface dsl-provider inet ppp
provider dsl-provider
johndoe@johndoe-desktop:~$ <----- comment this out ?

check: [http://beranger.org/index.php?article=1153](http://beranger.org/index.php?article=1153). it lists his /etc/network/interfaces near the bottom of the page.

---

### Post by uwjames on 2006-10-14
FIXED!

After reviewing my notes (I can't believe I said that) I realized I had put a redundant 8139too line in /etc/modules . getting rid of it fixed everything. moral of the story, if a module is loading by default, don't add it to the module file.

thanks everyone!

---

