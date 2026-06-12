---
title: "Internet Connection Sharing - frustrations"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by dave-ubu on 2007-06-13
Hi, 

I finally took the plunge and installed Feisty as a dual boot on my main machine. I'd set up Internet connection sharing on an XP through to an ubuntu box and all was fine. 

However, setting up on Ubuntu doesn't seem as straight forward. 

I've googled and followed several guides now in setting up connection sharing, but as yet - nothing seems to work permantly (the closest i've got is following this :- [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370) and then using Firestarter (following the wizard to set up connection sharing)

My set up is as follows

Main PC - eth1: is internet via wireless - an Access point plugged direct into the cable modem
                 eth0: is networked to another dedicated ubuntu box with ip address of 192.168.0.1

2nd PC   - eth0: is static at 192.168.0.100
                  eth1: is wireless card - currently set to roaming mode - no connection (access point for Main PC is "hidden" so it doesnt accidentally connect to this pc)

with firestarter working - the 2nd PC can access the net ok - i had to add a rule for 192.168.0.100 to "allow connections from host" within the policy tab


I have LAMP installed on the 2nd PC and would like to have access to this externally through connection sharing - though setting "forward service" in firestarter for port 80 and 443 doesn't work ? am i missing something?


i have webmin installed on both pc's for configuration - this uses port 10000 but again i can access the main pc externally, but when seeting up a rule to forward port 10000 to 192.168.0.100 i still access the main pc 

any help, guidance etc is welcome as i'm now running out of ideas / options - i'm pretty sure its something very basic I'm missing, but i cant for the life of me suss what it is!

Regards and Thanks in advance. 

Dave

---

### Post by dave-ubu on 2007-06-13
I really could do with some help here.... please.

---

### Post by eks on 2007-06-13
Me too.... :(

I have a similar setup, PC with eth0 on adsl and eth1 connected to a windows laptop. I've been trying to make everything work and trying to understand how to work with iptables and ifconfig (I want to learn how they work, not just solve my problem). Weird is that with FIrestarter, if I try to turn it on with eth1 for internet connection sharing, it says "The device eth1 is not ready".

Some links I've found on the subject:

[https://help.ubuntu.com/community/InternetConnectionSharing?highlight=%28connection%29%7C%28sharing%29%7C%28internet%29](https://help.ubuntu.com/community/InternetConnectionSharing?highlight=%28connection%29%7C%28sharing%29%7C%28internet%29)
[http://en.wikipedia.org/wiki/Iptables](http://en.wikipedia.org/wiki/Iptables)
[http://www.linuxguruz.com/iptables/howto/maniptables.html](http://www.linuxguruz.com/iptables/howto/maniptables.html)
[http://www.openbsd.org/cgi-bin/man.cgi?query=ifconfig](http://www.openbsd.org/cgi-bin/man.cgi?query=ifconfig)
[http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php) (firestarter help on internet connection sharing)

I'm reading all this literature now, might post again later.


eks

---

### Post by eks on 2007-06-13
This is my progress.....

[http://ubuntuforums.org/showthread.php?t=473032](http://ubuntuforums.org/showthread.php?t=473032)


eks

---

### Post by dave-ubu on 2007-06-14
well.. my progress... if in doubt - re-install!

MAIN pc in now a fresh install with firestarter installed - without messing with iptables i've managed to get internet connection sharing set up by :-

setting the IP on the 2nd pc with 192.168.0.100 - 255.255.255.0 and gateway to 192.168.0.1 and editing the resolv.conf with a single entry of an IP of the namessever that was on MAIN pc resolv.conf

on the MAIN pc eth1: is wireless with DHCP - eth0: is set at 192.168.0.1 - 255.255.255.0 with no gateway set

after setting this up - a reboot was needed - then running through the firestarter wizard and then another reboot of both systems.

HOWEVER, port forwarding is still not working - i set a policy up in firestarter to direct port 80 to 192.168.0.100 port 80 - but still no redirect to the webserver on the 2nd pc

---

### Post by dave-ubu on 2007-06-15
I've come to a stop with port forwarding :( 

Just bumping this up to see if anyone could offer any other advice

Regards

Dave

---

### Post by dave-ubu on 2007-06-15
it cant be that hard surely - and if it was easy - i'd had done it!

---

### Post by deanlinkous on 2007-06-15
apt-get install ipmasq

---

### Post by dave-ubu on 2007-06-15
do i install this on one or both ubuntu installs?

---

### Post by deanlinkous on 2007-06-15
ipmasq should be installed on the *gateway* but not sure how it will do with all the stuff you have already done...

---

### Post by eks on 2007-06-16
Sorry I didn't post my progress earlier, I wanted to make sure it was working. And it is!

I ended giving up starting the DHCP server and just running Firestarter and configuring the other machine IP manually. Problem was that Avahi somehow was locking eth1 somehow, and Firestarter could not enable it. So I had to do "ifconfig eth1 192.168.0.1", which would then assign the ip to eth1 and Firestarter could start. On the other (WinXP) machine I configured IP 192.168.0.10, subnet mask 255.255.255.0, and default gateway the IP of the Ubuntu machine 192.168.0.1

But Firestarter seems to consume lots of resources, I might try that with iptables...

Problem is I can't create a complete step-by-step because I don't know if ipmasg and dnsmasq are required to this, since I installed them [trying this procedure]("https://help.ubuntu.com/community/InternetConnectionSharing"). dnsmasq is currently running, but not ipmasq. I might try to uninstall it later to see if it still works.

As for the port fowarding, I dunno exactly what it is because my father is just using web and MSN. I would supose that it is working because MSN is a different port than the usual 80 for web?

Now I just need to find out how to start everything on boot...


eks

---

### Post by dave-ubu on 2007-06-17
success!

heres what I did - installed Webmin on the main PC 
installed firestarter and set up the rules needed - even though it doesnt seem to work! 
logged into webmin - into networking and then linux firewall - its shows as a text file (you'll see if you follow the above) and at the bottom asks if you want to parse it into webmin format. converted and a neat list of rules appears - these now efectively make firestarter redundant - so uninstalled - checked the rules were ok in webmin - and click apply - Voila! all woking

I appreciate the rules could be made up manually - but doing it the above way populates a standard ruleset that you can then tinker with in a nice GUI via web

HTH!

Regards

Dave

---

### Post by jrev on 2007-06-19
I have 3 PC's in a nfs network and the ICS PC is connected to the net through an external modem 56k
the network is operating Ok 

ipmasq and firestarter are not implemented on any machine...

---

