---
title: "i can connect to network, but can't connect to any IP"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by abasoufiane on 2007-05-14
I have a wireless USB Sagem: xg-760N, i used Ubuntu 7.04 CD LIVE to see if evrything works ok, that was the case except for that wifi key.

my card is detected instantly and i can see the network, and even connect to it (at least that's what it says)...  however i can't connect to internet, no website works. i tried to configure thing manualy, adding an ip adress, netmask, default gateway, but no luck may be i did something wrong.

i also tried with hdcp but no luck.


ONe detail that might be very helpful,  i tried the same thing in my firend's house, same cd ubuntu, same wifi card, but his rooter is different than mine and it did work instantly without inputing anything except for his wep key that was requested.

i don't use any wep or wap key , but my friend does. 

may be it has to do with dns servers ?  i don't know mine.

using network tools, and clicking on ping with the adress of my default gateway 10.0.0.2 doesn't do anything, the card is defined as eth1. 

i beg of you gurus out there , help me i'm so stuck and i'm very noob in network.


thank you very much.

---

### Post by abasoufiane on 2007-05-14
come on ! nobody !! hundreds of experts and they just don't have a clue !!  i'm sure it's a minor problem that i can't think of .. come on please some help here :(

---

### Post by bukwirm on 2007-05-14
Please post the output of "cat /etc/resolv.conf".

---

### Post by pmenefee on 2007-05-14
I suspect that there are hundreds of people with the same problem, and not hundreds of experts who know the answer.

I for one, have the same problem and get no answer.  I get connected on XP (dual boot system), but not on Ubuntu 7.04.  I installed WICD to help and that made it worse because now I get nothing, whereas I could connect before but couldn't secure the network.  Now, I see the network and WICD says connected, but I get nothing with Firefox.

---

### Post by abasoufiane on 2007-05-14
Iwconfig:


eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"zd1211"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

cat /etc/resolv.conf didn't work on my ubuntu cd live 

however s on Kubuntu, which is installed on my harddrive 

root@soufiane:/home/soufiane# cat /etc/resolv.conf
nameserver 10.0.0.2
domain 10.0.0.2

i think i added that manualy at a certain time in network setting panel , (10.0.0.2 is my default gateway)


ok i'm trying to connect on ubuntu cd live and not on Kubuntu? 

1) ubuntu can connect to my network , kubuntu only identify yet
2) when i changed some inputs , things that i regularly do in ubuntu, kubuntu just disabled the wireless, even if i try to enable it, it doesn't work, it only sees the wire port.

so let's focus only on ubuntu as the problem in kubuntu sounds more complex

P.S: when i click on connection information  everything is set to 0.0.0.0  from the ip to the dns server to the gateway...
it seems like it ignored all the input ...  
don't forget please that the same card with the same cd worked like a charme for my friend.

thank you for your answers

---

### Post by agurk on 2007-05-14
Can you get to [http://72.14.207.99/](http://72.14.207.99/) (Google)? If you can, it's likely a DNS problem.

---

### Post by abasoufiane on 2007-05-14
no i can't , i can't even connect to my interface rooter 10.0.0.2

---

### Post by scrooge_74 on 2007-05-14
Connect to your router using the ethernet wired card and config your router, if your card is working then probably is more a problem with the config.  Try first using the wifi without any kind of security.  When you have that working then start adding your security.

For DNS you can use the information on [http://www.opendns.com/start/](http://www.opendns.com/start/)

This will eliminate the problem when the router looses its DNS settings from your provider in which case the only way to get them back is to reboot it.  I have instances of friends or family can't use internet and I come along into their house with my PC and I am surfing while they are stuck.

In any case the DNS servers from opendns are: 208.67.222.222, 208.67.220.220

also take out the details you have on resolv.conf

and change the nameserver to the ones from opendns

---

### Post by agurk on 2007-05-14
If no joy, could you post the output of the *route* command, please?

---

### Post by abasoufiane on 2007-05-14
ok i'll try to connect to the rooter tomorrow because it's very inconveniant at the moment.

I should also note that in an interface which i cant remember the name, ONLY ipv6 is displayed to eth1, there is no mention of ipv4...

this is another difference with me and my friend when i compared those interfaces.

can ipv4 be enabled or something ?  

ok please guys do not forget that i'm a total noob in Linux and network, so opendns server say whaaaat??  i know many things in XP though and i just want to try linux for a change... i want also to learn it.  without internet there is no easy reach to documentation and that's very discouraging for me.

---

### Post by scrooge_74 on 2007-05-14
you should be using ipv4, ipv6 is the future, are you sure you have not made any changes to config files trying to make your PC faster?

Check this link it may give you some light [http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)  it maybe that you commented out your ipv4 protocols or something

---

### Post by abasoufiane on 2007-05-15
I have not made any change , that was the default , in the same window my friend had

ipv4  (his adress ip)
ipv6  (5512. 454e . kleh.   anyway something like that)


for me only IPV6 shows:

ipv6 (the adresse)

---

### Post by pmenefee on 2007-05-15
> **scrooge_74 said:**
> Connect to your router using the ethernet wired card and config your router, if your card is working then probably is more a problem with the config.  Try first using the wifi without any kind of security.  When you have that working then start adding your security.

For DNS you can use the information on [http://www.opendns.com/start/](http://www.opendns.com/start/)

This will eliminate the problem when the router looses its DNS settings from your provider in which case the only way to get them back is to reboot it.  I have instances of friends or family can't use internet and I come along into their house with my PC and I am surfing while they are stuck.

In any case the DNS servers from opendns are: 208.67.222.222, 208.67.220.220

also take out the details you have on resolv.conf

and change the nameserver to the ones from opendns

Thanks for the suggestion!  I have 7.04 installed and WICD, but couldn't get the network to connect.  I showed to be connected but Firefox said no server found.
I followed the instructions on opendns for Ubuntu and changed to the DNS servers, and then changed also with WICD.  When the DNS was checked and the numbers pointed  to opendns, it now connects.  I haven't tried to use WEP or other security yet, but at least I have service.  I'll report back on security later.

---

### Post by coolclassic on 2007-05-16
I had the same issues, apparently it's to do with window scaling (what ever that is).

Here was the solution: edit /etc/sysctl.conf
and insert the following line

net.ipv4.tcp_window_scaling=0

to reset

sudo sysctl -p

I also did this with another computer and it also started working.

Here more info if anyones intrested:

[http://ubuntuforums.org/showthread.php?t=394067&highlight=internet+issues](http://ubuntuforums.org/showthread.php?t=394067&highlight=internet+issues)

---

### Post by caspdj on 2007-06-13
edit:removed

---

### Post by Mischa on 2007-10-24
the net.ipv4.tcp_window_scaling=0 fix is a bit to buch :)

to fix it back to original working packed sizes do the following as root: (sudo su -)

vi /etc/sysctl.conf

add the following two lines

net.ipv4.tcp_wmem = 4096 16384 131072
net.ipv4.tcp_rmem = 4096 87380 174760

sysctl -p

see [http://inodes.org/blog/2006/09/06/tcp-window-scaling-and-kernel-2617/](http://inodes.org/blog/2006/09/06/tcp-window-scaling-and-kernel-2617/) for an excellent explanation

---

### Post by alexisbellido on 2007-10-30
Hi, I fixed the problem in Gutsy using the suggested change in sysctl.conf:

net.ipv4.tcp_wmem = 4096 16384 131072
net.ipv4.tcp_rmem = 4096 87380 174760

The sites I couldn't access were [Ohio State University]("http://www.ureg.ohio-state.edu/ourweb/online.html") and [Campaign Monitor]("http://www.campaignmonitor.com/"). After changing sysctl.conf I could access both of them but one subdomain in Campaign Monitor's domain, [app.campaignmonitor.com]("http://app.campaignmonitor.com/"), needed to access members section and API, still didn't work.

I had to install Firestarter to be able to access that subdomain, however I now have a firewall that I didn't wanted in the first place.

Any ideas why this is happening and how to fix it?

I have posted more details about my [problems connecting to websites with Gutsy Gibbon]("http://ventanazul.com/webzine/articles/cannot-access-websites-ubuntu-gutsy-gibbon") at my site.

Cheers.

---

