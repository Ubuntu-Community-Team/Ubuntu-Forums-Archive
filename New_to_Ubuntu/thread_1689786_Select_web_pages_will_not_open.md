---
title: "Select web pages will not open"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by Pharnavaziani on 2011-02-17
Hey,

I recently started dual-booting Lucid Lynx on my laptop with Windows 7 and use Lynx as my primary and default OS.  I noticed recently that I could not open some web pages (for an example, the comic [SMBC]("http://www.smbc-comics.com/") does not open) and reported that they timed out.  Using other computers, I've verified that the problem is not with the sites but with my computer, and Windows 7 had no problem with these sites.  I use both Google Chrome and Firefox and neither is capable of opening the sites, which is a problem because some of the sites are academic and therefore important.  I looked up this problem but couldn't seem to find anything....anyone know what's going on?

My computer has 2 GB of RAM and a Core 2 Duo processor.

---

### Post by Frogs Hair on 2011-02-17
I am able to connect and play video on the link with Firefox and Opera using 10.10. The only things that come to mind are missing plug -ins (flash) , add-ons problems caused No Script or Adblock type extensions .

---

### Post by Pharnavaziani on 2011-02-17
Could it be a problem with 10.04, then?

The link does not work on my computer and has consistently failed to work.  Any suggestions on why?

---

### Post by Frogs Hair on 2011-02-17
In Firefox you could look at Tools > Error Console and see if there are related errors . That may give you a starting point.

---

### Post by Pharnavaziani on 2011-02-17
The error console tells me nothing is wrong with the example page.

---

### Post by Frogs Hair on 2011-02-17
When connecting to the site with  Windows are you using are you using Firefox and Chrome also ? 
 
I came across a post that indicated it could be ISP related and if you using FF or Chrome on Windows this would be ruled out.
 
The other suggestions included checking router . firewall , network , and Ipv settings.

---

### Post by Pharnavaziani on 2011-02-17
Yes, I use FF and Chrome for Windows as well - mainly FF.  Thanks for the help :)

Is there a simple way to check the .firewall and other settings?

---

### Post by Frogs Hair on 2011-02-17
For the firewall gui I use gfw in the software center , it has simple settings , enable , allow outgoing and deny incoming. It will appear on the administration menu when installed.
 
Network info can be located on system menu and if using a router you will have to find that on your own . I am on a network , but the router settings are contolled by another user and  settings vary depending on brand.  
 
Another thread suggested cleaning the cache in both browsers may help. Welcome to forums BTW.

---

### Post by pqwoerituytrueiwoq on 2011-02-17
Site works fine for me 
Mozilla/5.0 (X11; Linux x86_64; rv:2.0b12pre) Gecko/20110217 Firefox/4.0b12pre ID:20110217030357
Ubuntu 10.04.2 LTS
see if you can ping the site

---

### Post by Pharnavaziani on 2011-02-28
I don't know how to see if I'm pinging the sites.  
Ubuntu 10.04 on an HP G71-340US Notebook.  The pages do not open regardless of my connection or speed; and they do not open on either Firefox or Chrome.
I'm concerned - while this is only a webcomic, I've also been unable to access academic pages that are important - and would like to know if there are any explanations that come to mind.

---

### Post by TechWiz2100 on 2011-02-28
There was a post that was put up here a while ago and the issue turned out to be many many dropped packets due to a faulty driver.

Please run the following commands in terminal and post results.
```
ping -c 10 google.com
ping -c 10 <website that has problems>
lspci
cat /etc/network/interfaces
ifconfig

```

---

### Post by Pharnavaziani on 2011-02-28
> **TechWiz2100 said:**
> There was a post that was put up here a while ago and the issue turned out to be many many dropped packets due to a faulty driver.

Please run the following commands in terminal and post results.
```
ping -c 10 google.com
ping -c 10 <website that has problems>
lspci
cat /etc/network/interfaces
ifconfig

```

Ok.  I ran the code and got the following results:

>                       p { margin-bottom: 0.08in; }  :~$ ping -c 10 google.com 
 PING google.com (74.125.226.114) 56(84) bytes of data. 
 64 bytes from 74.125.226.114: icmp_seq=1 ttl=49 time=11.4 ms 
 64 bytes from 74.125.226.114: icmp_seq=2 ttl=49 time=10.6 ms 
 64 bytes from 74.125.226.114: icmp_seq=3 ttl=49 time=19.0 ms 
 64 bytes from 74.125.226.114: icmp_seq=4 ttl=49 time=10.4 ms 
 64 bytes from 74.125.226.114: icmp_seq=5 ttl=49 time=10.7 ms 
 64 bytes from 74.125.226.114: icmp_seq=6 ttl=49 time=10.3 ms 
 64 bytes from 74.125.226.114: icmp_seq=7 ttl=49 time=10.6 ms 
 64 bytes from 74.125.226.114: icmp_seq=8 ttl=49 time=10.4 ms 
 64 bytes from 74.125.226.114: icmp_seq=9 ttl=49 time=10.3 ms 
 64 bytes from 74.125.226.114: icmp_seq=10 ttl=49 time=10.3 ms 
  
 --- google.com ping statistics --- 
 10 packets transmitted, 10 received, 0% packet loss, time 45181ms 
 rtt min/avg/max/mdev = 10.303/11.452/19.076/2.563 ms 
 matteo@matteo-laptop:~$ ping -c 10 smbc.com 
 PING smbc.com (209.61.212.130) 56(84) bytes of data. 
  
 --- smbc.com ping statistics --- 
 10 packets transmitted, 0 received, 100% packet loss, time 9070ms 
  
 lspci 
 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07) 
 00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) 
 00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) 
 00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) 
 00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) 
 00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) 
 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03) 
 00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) 
 00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03) 
 00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) 
 00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) 
 00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) 
 00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) 
 00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) 
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) 
 00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03) 
 00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) 
 00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03) 
 00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03) 
 02:00.0 Network controller: Intel Corporation WiFi Link 1000 Series 
 03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02) 
 matteo@matteo-laptop:~$ cat /etc/network/interfaces 
 auto lo 
 iface lo inet loopback 
  
 ifconfig 
 eth0      Link encap:Ethernet  HWaddr c8:0a:a9:2a:4d:78   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
           Interrupt:26  
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:17620 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:17620 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:3152317 (3.1 MB)  TX bytes:3152317 (3.1 MB) 
  
 wlan0     Link encap:Ethernet  HWaddr 00:26:c7:0f:0a:b2   
           inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0 
           inet6 addr: fe80::226:c7ff:fe0f:ab2/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:82922 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:54393 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:113667224 (113.6 MB)  TX bytes:5996471 (5.9 MB) 
  
 

---

### Post by TechWiz2100 on 2011-02-28
smbc.com does not respond to ping and redirect to some bodybuilding site in web browser on my end however since google.com is responding well with no loss I think you may possibly have the wrong URL and that your network is functioning properly. Try another URL with ping -c 10

---

### Post by vivek.pandey on 2011-02-28
well smbc.com is not a wrong url it pings when i try here

---

### Post by TechWiz2100 on 2011-02-28
> **neo_aryan said:**
> well smbc.com is not a wrong url it pings when i try here

The OP said something about some comics being at smbc.com but that isn't the case, at least not from my perspective. Also network-tools.com is failing to tracert and ping the site as well. Maybe they are dropping ping packets from certain IP ranges?

---

### Post by Pharnavaziani on 2011-02-28
You're right, it's my bad.  It should be smbc-comics.com, which still does not load.

---

### Post by Pharnavaziani on 2011-02-28
The response for smbc-comics.com ping -c is "bad number of packets to transmit".

---

### Post by TechWiz2100 on 2011-02-28
```
ping -c 10 smbc-comics.com
```
Try again ^^

---

### Post by Pharnavaziani on 2011-02-28
I get
> --- smbc-comics.com ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 45255ms
rtt min/avg/max/mdev = 18.182/20.499/31.584/3.774 ms
~$ 


---

### Post by TechWiz2100 on 2011-02-28
I think you are having a DNS problem because your wireless adapter seems to be well supported by Ubuntu and the rest of the stuff seems to check out.

Try editing your /etc/resolv.conf to have nameserver set to 4.2.2.5 and 4.2.2.6

FYI You can put nameserver down multiple times

---

### Post by jeannot_unbu on 2011-02-28
Sorry to barge in like this, but I am having the same problem (with different websites - see my last post). I will be following this one too to see if a solution appears. BTW I use Firefox, Google Chromium and another web browser (can't remember the name now), and they all have the same problem, though with different sites.
JC

---

### Post by TechWiz2100 on 2011-02-28
> **jeannot_unbu said:**
> Sorry to barge in like this, but I am having the same problem (with different websites - see my last post). I will be following this one too to see if a solution appears. BTW I use Firefox, Google Chromium and another web browser (can't remember the name now), and they all have the same problem, though with different sites.
JC

Please elaborate: By different sites do you mean other than smbc-comic.com or different sites for each browser?
Post the results of the commands I listed off for the OP as well and we can help you too.

Thanks

---

### Post by jeannot_unbu on 2011-02-28
> **TechWiz2100 said:**
> Please elaborate: By different sites do you mean other than smbc-comic.com or different sites for each browser?
Post the results of the commands I listed off for the OP as well and we can help you too.
 
Thanks
Thanks TechWiz, I will. I am waiting to receive an ethernet cable to go wired first and see what happens. From what I have read so far, and replies I have received from this forum it may be a problem with my wireless card. But don't worry I will get back to you with whatever the outcome. Thanks for the offer :biggrin:
 
JC

---

### Post by Pharnavaziani on 2011-02-28
I'm not the owner of resolv.conf...how do I change permissions/overwrite?

---

### Post by TechWiz2100 on 2011-02-28
> **Pharnavaziani said:**
> I'm not the owner of resolv.conf...how do I change permissions/overwrite?


```
gksudo gedit /etc/resolv.conf
```

---

### Post by Pharnavaziani on 2011-02-28
I've replaced the resolv.conf and the fix does not work.  The ping still reads the same message and the site does not load.

---

### Post by Pharnavaziani on 2011-03-01
Any ideas on reasons why certain pages would have this problem?  I have similar issues on a seemingly random distribution of pages, from academic GIS pages to some news stories.

---

### Post by TechWiz2100 on 2011-03-01
Inability to get certain pages is usually a combination of lag and DNS lookup issues. *Usually* its solved via restarting router/modem, computer or simply the connection at times.

I made the assumption you tried all of the above already but if you haven't please do. I know there is a way to get a record of DNS lookups and their respective errors in linux but I forget the log name and command (daemon.log?)

Maybe someone with a little more unix networking experience can help.

---

### Post by Pharnavaziani on 2011-03-01
Yes, I did.  It still says "bad number of packets" and won't load.

I can't see how it's the router, as everything was fine before I made the transition to linux.

---

### Post by Pharnavaziani on 2011-03-01
Changing networks and even changing the input (wireless to wired) was unsuccessful.  I doubt it's a lag issue with the wired connection, as the wired internet where I am is extremely fast.  Changing browsers was not useful and ping -c with different networks and with wired only did not change the result of "bad number of packets to transmit".  Googling this problem hasn't helped much, either.

Additionally, the number of websites that will not load is increasing, this time to my primary academic page.  I'm now getting really concerned as this problem has gone from a nuisance to a threat to my ability to use Ubuntu.

---

### Post by Pharnavaziani on 2011-03-01
I repeated the experiment I was advised to do earlier, this time with a more important site.

> 
~$ ping -c 10 google.com
PING google.com (74.125.226.114) 56(84) bytes of data.
64 bytes from 74.125.226.114: icmp_seq=2 ttl=50 time=9.55 ms
64 bytes from 74.125.226.114: icmp_seq=3 ttl=50 time=9.24 ms
64 bytes from 74.125.226.114: icmp_seq=4 ttl=50 time=9.36 ms
64 bytes from 74.125.226.114: icmp_seq=5 ttl=50 time=9.91 ms
64 bytes from 74.125.226.114: icmp_seq=6 ttl=50 time=9.50 ms
64 bytes from 74.125.226.114: icmp_seq=7 ttl=50 time=9.51 ms
64 bytes from 74.125.226.114: icmp_seq=8 ttl=50 time=12.0 ms
64 bytes from 74.125.226.114: icmp_seq=9 ttl=50 time=9.24 ms
64 bytes from 74.125.226.114: icmp_seq=10 ttl=50 time=9.17 ms

--- google.com ping statistics ---
10 packets transmitted, 9 received, 10% packet loss, time 41286ms
rtt min/avg/max/mdev = 9.178/9.732/12.071/0.859 ms

~$ ping -c 10 thehub.hampshire.edu
PING erebus.hampshire.edu (192.33.12.112) 56(84) bytes of data.

--- erebus.hampshire.edu ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 9071ms

~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Intel Corporation WiFi Link 1000 Series
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

~$ ifconfig
eth0      Link encap:Ethernet  HWaddr c8:0a:a9:2a:4d:78  
          inet addr:172.30.149.162  Bcast:172.30.151.255  Mask:255.255.248.0
          inet6 addr: fe80::ca0a:a9ff:fe2a:4d78/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6391 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1094 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1296022 (1.2 MB)  TX bytes:202018 (202.0 KB)
          Interrupt:26 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:103365 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103365 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8833866 (8.8 MB)  TX bytes:8833866 (8.8 MB)

wlan0     Link encap:Ethernet  HWaddr 00:26:c7:0f:0a:b2  
          inet6 addr: fe80::226:c7ff:fe0f:ab2/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1030181 errors:0 dropped:0 overruns:0 frame:0
          TX packets:550045 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1171947643 (1.1 GB)  TX bytes:59400013 (59.4 MB)
~$ 


---

### Post by TechWiz2100 on 2011-03-01
You are getting a bad packet number error because syntax for ping -c is 
```

ping -c <number of packets> <target>
e.g
ping -c 10 google.com

```

And restarting the router clears the router's DNS cache because a query to cache is faster than an actual DNS query so many routers/modems and sometimes even OS's cache DNS requests to save time. The problem is that sometimes the results are too old and are not refreshed right away so you get timeouts and 404's where you should not. Ubuntu however does not cache by default so flush-cache does not exist for Ubuntu unless its been set to cache DNS.

---

### Post by TechWiz2100 on 2011-03-01
Is fresh install or LiveCD out of the question? I'm thinking you have a bad install at this point because none of the common network troubleshooting methods are working. If LiveCD gets flawless internet access then you need to do something about your install. Also I've read somewhere (I don't remember what the issue was) that disabling IPv6 on your network connections solved someone's networking issue; try that.

---

### Post by pauleralivre on 2011-06-23
Hi, I also have problem accesing some websites using firefox or chrome under ubuntu 11. This doesn't happen in the same machine and same connection when I run Windows Vista.
Some web sites, like the newspaper El Pais (elpais.com), open occasionally. Others, like Hotmail, never open!
I've checked the IPv6 and it was already set up as "ignore".

Would really appreciate some help!

paulinho@Toshiba:~$ ping -c 10 google.com
PING google.com (209.85.148.104) 56(84) bytes of data.
64 bytes from google.com (209.85.148.104): icmp_req=1 ttl=54 time=76.6 ms
64 bytes from google.com (209.85.148.104): icmp_req=2 ttl=53 time=80.7 ms
64 bytes from google.com (209.85.148.104): icmp_req=3 ttl=54 time=77.8 ms
64 bytes from google.com (209.85.148.104): icmp_req=4 ttl=53 time=74.2 ms
64 bytes from google.com (209.85.148.104): icmp_req=5 ttl=53 time=74.7 ms
64 bytes from google.com (209.85.148.104): icmp_req=6 ttl=54 time=74.8 ms
64 bytes from google.com (209.85.148.104): icmp_req=7 ttl=54 time=75.1 ms
64 bytes from google.com (209.85.148.104): icmp_req=8 ttl=53 time=75.6 ms
64 bytes from google.com (209.85.148.104): icmp_req=9 ttl=54 time=76.6 ms
64 bytes from google.com (209.85.148.104): icmp_req=10 ttl=54 time=75.7 ms

--- google.com ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9012ms
rtt min/avg/max/mdev = 74.269/76.228/80.725/1.822 ms
paulinho@Toshiba:~$ ping -c 10 hotmail.com
PING hotmail.com (65.55.72.135) 56(84) bytes of data.
64 bytes from hotmail.com (65.55.72.135): icmp_req=1 ttl=240 time=183 ms
64 bytes from hotmail.com (65.55.72.135): icmp_req=2 ttl=240 time=182 ms
64 bytes from hotmail.com (65.55.72.135): icmp_req=3 ttl=240 time=182 ms
64 bytes from hotmail.com (65.55.72.135): icmp_req=4 ttl=240 time=181 ms
64 bytes from hotmail.com (65.55.72.135): icmp_req=5 ttl=240 time=182 ms
64 bytes from hotmail.com (65.55.72.135): icmp_req=6 ttl=240 time=183 ms
64 bytes from hotmail.com (65.55.72.135): icmp_req=7 ttl=240 time=182 ms
64 bytes from hotmail.com (65.55.72.135): icmp_req=8 ttl=240 time=183 ms
64 bytes from hotmail.com (65.55.72.135): icmp_req=9 ttl=240 time=182 ms
64 bytes from hotmail.com (65.55.72.135): icmp_req=10 ttl=240 time=181 ms

--- hotmail.com ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9011ms
rtt min/avg/max/mdev = 181.462/182.547/183.539/0.714 ms
paulinho@Toshiba:~$ ping -c 10 elpais.com
PING elpais.com (194.169.201.203) 56(84) bytes of data.

--- elpais.com ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 8999ms

paulinho@Toshiba:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
05:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
0c:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0c:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0c:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0c:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
paulinho@Toshiba:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

paulinho@Toshiba:~$ ifconfig
eth0      Link encap:Ethernet  Endereço de HW 00:1b:38:b3:7b:c2  
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
          IRQ:45 Endereço de E/S:0x4000 

lo        Link encap:Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:952 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:952 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:38580 (38.5 KB) TX bytes:38580 (38.5 KB)

wlan0     Link encap:Ethernet  Endereço de HW 00:1b:9e:8e:c4:97  
          inet end.: 192.168.2.100  Bcast:192.168.2.255  Masc:255.255.255.0
          endereço inet6: fe80::21b:9eff:fe8e:c497/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:82261 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:68207 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:77381176 (77.3 MB) TX bytes:12958202 (12.9 MB)

---

### Post by prat22 on 2011-08-25
Now, I am having the same problem. Sites like ubuntuforums, piratebay, yahoo doesnt load with either Firefox 6 or Chrome (On 10.10).

Someone told me to change the MTU from automatic to some random value. Didnt help!

Now, I am using a proxy site in firefox, and ubuntuforums are loaded! So, proxy is the key, I guess.

But my question is, How do I set proxy server in firefox to automatically use those settings? A real example would be of greater help.

By the way, Plz rule out any addons (proxyfoxy, etc) since addons.mozilla doesnt load either!gl

---

### Post by prat22 on 2011-08-29
Got it working! Thanks to [mail.prabal]("http://ubuntuforums.org/member.php?u=874812")!Go to terminal, and
> sudo -i
#ifconfig eth0 mtu 1400
#ifconfig ppp0 mtu 1400
#gedit /etc/network/if-up.d/mtu


Add the following lines:

#! /bin/sh
ifconfig ppp0 mtu 1412

Save and exit.

Make it executable by

> 
sudo chmod 755 /etc/network/if-up.d/mtu


Exit, and restart!

---

