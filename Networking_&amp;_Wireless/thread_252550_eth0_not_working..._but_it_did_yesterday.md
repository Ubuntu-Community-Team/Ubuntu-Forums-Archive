---
title: "eth0 not working... but it did yesterday"
date: 2006-09-07
forum: Networking &amp; Wireless
---

### Post by Bubs on 2006-09-07
ok this boggles my mind... ha

my Ethernet isn't working I have it plugged in and it says that the eth0 is active but no I can't go to any webpages.  

the wierd thing is that it worked yesterday and for a long time before that. 

the only thing I did was unplug the laptop and let the battery run down till the lappy shut off.

start it up today and tried to get on synaptic and it said it couldn't connect, so I tried firefox and got and nothing there either.  


W  T  F  !!!!  !!!!  ](*,)

---

### Post by electricshoes on 2006-09-07
If you type ifconfig does eth0 have an ip address?

If you have an IP but are unable to browse it could be a DNS problem. See if you can ping an IP - Try google.

```
 ping 64.233.167.99
``` 
Do you get replies? if so then set your DNS.

System>Administration>Networking>DNS tab.

Put your DNS servers in here if they are not already.

---

### Post by Bubs on 2006-09-07
this is the result of the if config...


```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:11:36:0E
          inet6 addr: fe80::2c0:9fff:fe11:360e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46343 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2870278 (2.7 MiB)  TX bytes:18252 (17.8 KiB)
          Interrupt:11 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)
```

doesn't look like I have an IP in eth0

um... where can I find my DNS server info?  > System>Administration>Networking>DNS tab.

Put your DNS servers in here if they are not already.

all I have in there now is one IP address

---

### Post by wieman01 on 2006-09-07
It's probably your DNS settings. Could you open "/etc/resolv.conf" and delete the entry? Make a safety copy of it before you do so and restart the computer. 

This should solve your problem. Had the same issue before.

---

### Post by wieman01 on 2006-09-07
What's the output if you run "iwconfig"?

---

### Post by Bubs on 2006-09-07
hold on I just restarted.

wouldn't iwconfig be for wireless?

I removed the wireless card becasue I didn't have a wireless network anymore.  (pcmcia)

---

### Post by wieman01 on 2006-09-07
Sorry... yes, it's for wireless. Please ignore the last comment. Nonsense of course. 

What's the result now?

---

### Post by Bubs on 2006-09-07
ok I deleted the nameserver and ip that were in resolv.conf (it was the only entry) did you want me to delete the entire file or whats in it?  cause I restarted and there is nothing in it but I still can't get online

---

### Post by wieman01 on 2006-09-07
Ok, the file's not updated properly. Now add a single line...
> nameserver xxx.xxx.xxx.xxx
"xxx.xxx.xxx.xxx" being the dotted decimal address of your router or any other DNS server.

Then restart again.

---

### Post by wieman01 on 2006-09-07
Also can you ping your router? Do you get a response?

---

### Post by Bubs on 2006-09-07
I ping my router and I do get a response...

and nameserver is in the file still not working.

I put in the DNS address from my primary windows comp.  under network settings -> status it gave me a DNS Server address

I'm not sure how to find that info in linux.

but I'll have to read further updates tomarrow... it's 2am and i'm getting tired

---

### Post by wieman01 on 2006-09-07
Ok, but try to put in your router's IP address. Normally that should do as your router acts as a DNS server.

---

### Post by wieman01 on 2006-09-07
Last question: Are you using DHCP? 

It could also help if you posted this file: /etc/network/interfaces

---

### Post by Bubs on 2006-09-07
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by Bubs on 2006-09-07
yes using dhcp

---

### Post by wieman01 on 2006-09-07
Could you try and remove these lines?
> address 127.0.0.1
netmask 255.0.0.0

Not sure what's wrong to be honest. Everything looks fine (except the mentioned).

---

### Post by BLTicklemonster on 2006-09-07
Go and look at it again, and where it says it's active, disable it. Then enable it again. (im on a windows machine, or I'd post exactly where to go to do that in case someone else comes along some day looking for answers and finds this thread... sorry)

I had this problem once before and that took care of it.

---

### Post by Bubs on 2006-09-07
yea I tried that one already, cause I also had a similar problem and that fixed it...  I've tried live cd's to see if there was something wrong with the distro but no everything I try I can't get on the internet.

---

### Post by tbonius on 2006-09-07
Where are you getting an IP from?  What DHCP server?  Is this some sort of consumer firewall/router (Like a Linksys) or is the computer connected directly to your DSL/cable modem?

You dont need to remove the 127.0.0.1 entries from your interfaces file.. that is for local host loopback interface only.. it should be fine.  

It sounds like the issue is specifically your DNS entries.  If you have an IP address.. and you can ping your default gateway.. then the only issue after that should be your assigned DNS server entries.

check netstat -rn

what is your default gateway listed as?

Can you ping that?

Can you ping an external internet address such as yahoo.com (except we will use the IP address instead of the name)

ping 209.131.36.158

Do you get a reply?  If you do then your connectivity is fine.. you just need good DNS servers to use.. and if you are dynamically assigned an address (DHCP) then this is the responsibility of your DHCP server.  Make sure you are getting valid DNS entries in your /etc/resolv.conf.  Try pinging the IP address of the DNS servers in /etc/resolv.conf.  Try an nslookup on a domain:

nslookup [www.yahoo.com](www.yahoo.com)

what do you get back?

T

---

### Post by name_user on 2006-09-07
I have the same problem. Ping the IP address above returned "Network is unreacheable"

---

### Post by tbonius on 2006-09-07
Again.. who runs your DHCP server?  What IP address are you getting assigned?  What are your DNS server settings? Can you ping your DHCP server by IP address.  If it is a NAT.. can you ping the external IP address of the gateway (the public IP address assigned by an internet provider)?

T

---

### Post by Bubs on 2006-09-07
where can I find all that information?

I have no clue

---

### Post by pyros on 2006-09-07
ok, what are you connecting to? the internet? a local network? 
If you are connecting to the internet, are you using dialup? are you using wireless? are you connected using a cable modem or DSL?

---

### Post by Bubs on 2006-09-07
the internet, cable modem, using DHCP

---

### Post by pyros on 2006-09-08
are you connecting directly to the cable modem, or are you goiong through a router? If it's directly to the modem, try reseting the cable modem. usually you just unplug it. if that doesn't work, you can get your ip address from the cable company.

---

### Post by wieman01 on 2006-09-08
I am sorry, I am at my wit's end. This is the last thing I can come up with (assuming that your router/DSL modem has assigned an IP to your computer - as your have highlighted)... Please update **/etc/resolv.conf** once again using my own (current) 
> search domain
nameserver 202.96.209.134
nameserver 202.96.209.6

Restart the computer & see if it works.

---

### Post by tbonius on 2006-09-08
There should be no need to restart the computer.. as the DNS settings will be overwritten upon reboot.. unless corrected with dhclient-enter-hooks.  You should be able to put in a domain name and known good DNS server into /etc/resolv.conf and simply go from there.

T

---

### Post by wieman01 on 2006-09-08
> **tbonius said:**
> There should be no need to restart the computer.. as the DNS settings will be overwritten upon reboot.. unless corrected with dhclient-enter-hooks.  You should be able to put in a domain name and known good DNS server into /etc/resolv.conf and simply go from there.

Generally you're right. But having played around with wireless for a while I can tell that this does not hold true in all cases. Sounds odd but for some reason unknown to me there is a need to restart the computer from time to time. So if you want to play safe, you need to restart.

But you are right... This command should do the trick (in MOST of the cases):
> sudo /etc/init.d/networking restart
The DNS settings are a problem... I've had similar problems.

---

### Post by tbonius on 2006-09-08
Well wireless is a different story, but in most assumptions.. DNS settings should be handed out dynamically from a DHCP server.. especially over a wireless network where most clients are very specifically dynamic.

If the interfaces are set for DHCP, and you edit the /etc/resolv.conf.. and then reboot.. your settings in /etc/resolv.conf will be overwritten unless you set the file immutable or you use a dhclient-enter-hooks script to replace settings in the resolv.conf during bootup (check /etc/dhcp3/dhclient-enter-hooks.d).

```

#!/bin/bash
for server in "list of DNS server IPs, seperated with spaces" ; do
    if ! grep $server /etc/resolv.conf ; then
        echo "nameserver "${server} >> /etc/resolv.conf
    fi
done
```

This is how I save myself alot of pain with using an internal DNS server.. and rejecting the one that my ISP assigns to me.

T

---

### Post by wieman01 on 2006-09-08
Ok. Back to the original question... I really think this has nothing to do with Ubuntu but rather with the service provider or DSL modem. As far as I can tell from what I see here there seems to be an issue with the modem. What do you think?

---

### Post by tbonius on 2006-09-08
I guess I am lost.  What issue with the modem?  Do you not get an IP from your provider at all?  If you do not then try rebooting your cable/dsl modem and then reboot your Ubuntu computer.  If it is directly connected to the modem then it should get an IP from your provider (unless they lock down access to a specific MAC address).  Afterwards you can check your resolv.conf for DNS entries... whatever entries you receive should be valid DNS servers on their network.  Try and ping the IPs of the DNS servers.. and then try nslookup of some random external domain:

nslookup [www.yahoo.com](www.yahoo.com)

Whatever IP it returns you should be able to ping:

ping 209.131.36.158

You should get replies.  Let me know if I missed your original question.. as I read through to the originator of this post.

T

---

### Post by S.O.P on 2006-09-08
I'm having the exact same problem which manifested itself today.  The internet connection is fine, as I can still use Windows.

As I'm at work, my troubleshooting options are limited so I decided to have a browse of the forums to narrow it down.

The only things I changed the night before was GrubEd and I loaded Kubuntu for a look-see.  Started up this morning and connectivity is gone, even though everything appears to be normal and setup correctly.

I'll watch this thread with some interest, if the OP sorts out the problem, let us know...

---

### Post by linuxusr50 on 2006-09-08
Try the following and then show us ifconfig again.  Also send the contents of /etc/network/interfaces

```
sudo ifup --all
```
```
sudo dhclient
```

---

### Post by mbaker514 on 2006-09-09
Hi
 You may want to check out this post.

[http://www.ubuntuforums.org/showthread.php?t=193850](http://www.ubuntuforums.org/showthread.php?t=193850)

There's some fixes in there that work for some people. If I remember correctly, I think there was a ifupdown upgrade released a couple of days ago   and that could be the source of the problem.  I'm not incredibly knowledgable about networking but maybe this will get someone pointed in the right direction.

Good luck

---

### Post by S.O.P on 2006-09-09
Alright, I've just got home and after reading a few threads, and even the one above before it was posted, I've fixed the problem by adding
```
dns-nameservers 192.168.1.1
```
to my interfaces file.


```
gksu gedit /etc/network/interfaces
```

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.50
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 192.168.1.1


auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

---

### Post by wieman01 on 2006-09-09
> **S.O.P said:**
> Alright, I've just got home and after reading a few threads, and even the one above before it was posted, I've fixed the problem by adding
```
dns-nameservers 192.168.1.1
```
to my interfaces file.

Mmm... This is no surprise, buddy. You're using Static IPs rather than DHCP. Guess your problem has nothing to do with the original thread. Nonetheless glad you have solved it.

---

### Post by linuxusr50 on 2006-09-09
Just a note:

Looks like you may be running a linksys router by the IP you posted.  If this happens to be a WRT54G v5 or v6 you may want to add your external DNS to your /etc/resolv.conf file.  I work for an ISP and we have observed pleanty of problems with the way these versions are handling DHCP and DNS requests.

It seams that Linksys decided to stop running a linux firmware after version 4. Version 4 routers and below do not seem to exibit these problems.

To update your resolv.conf file do the following:

```
sudo gedit /etc/resolv.conf
```

Add the following lines:

```
nameserver     x.x.x.x
nameserver     x.x.x.x
```

and save the changes.

x.x.x.x  are the nameservers of your ISP.  If you are not sure what they are you can go to [http://www.dnsstuff.com](http://www.dnsstuff.com)
and find them.

If the router is not handling dns request properly this should bandaid the problem. Linksys needs to fix the issue in the firmware for a permenant fix.

---

### Post by S.O.P on 2006-09-09
> **wieman01 said:**
> Mmm... This is no surprise, buddy. You're using Static IPs rather than DHCP. Guess your problem has nothing to do with the original thread. Nonetheless glad you have solved it.
Its still relevant as it *was* working fine for a couple of weeks and then, all of a sudden, it wasn't.  The topic title defined exactly what the problem was.  Even though I don't need a static for Linux as I do all my torrenting in Windows, I thought I'd set it up the same anyway.  Still learning I suppose...

**linuxusr50**:  I'm running a WRT54GL, which is a linux based firmware, with a 3rd party offering, Thibor.  Would you suggest I still follow your instructions?

---

### Post by Heliopolis on 2006-09-09
> **S.O.P said:**
> Alright, I've just got home and after reading a few threads, and even the one above before it was posted, I've fixed the problem by adding
```
dns-nameservers 192.168.1.1
```
to my interfaces file.


Thanks very much for this info.

I too found I was unable to access eth0 after it was working for almost 2 months since install. I was able to rememdy by accessing 'Networking' from 'System->Administration' and simply setting the location and exiting. This seemed to kick eth0 in the butt. However, it was a pain and other users of the system were inconvenienced.

This simple addition to the interfaces file has saved me from what I thought would be a re-install. I still have a long way to go with Linux and am so grateful I was able to fix this problem with your assistance.

Regards,

Heliopolis.

---

### Post by 0be1 on 2006-09-10
FYI;

I just did another post, and here is what I did to fix my problem. Working great and have not dropped yet.

[http://www.ubuntuforums.org/showthread.php?t=254625](http://www.ubuntuforums.org/showthread.php?t=254625)

regards...

0be1

---

### Post by linuxusr50 on 2006-09-10
> 
**linuxusr50**:  I'm running a WRT54GL, which is a linux based firmware, with a 3rd party offering, Thibor.  Would you suggest I still follow your instructions?

**S.O.P**:

The WRT54GL should be ok, however I would consider running one of the other open source firmwares like openwrt for example as it increases your options and seems to cause less problems than linksys versions. Just my 2 cents!

---

### Post by S.O.P on 2006-09-10
> **linuxusr50 said:**
> **S.O.P**:

The WRT54GL should be ok, however I would consider running one of the other open source firmwares like openwrt for example as it increases your options and seems to cause less problems than linksys versions. Just my 2 cents!

Yep, Thibor is HyperWRT, seems to run reasonably flawless except for some IRC dropouts when I'm torrenting but thats probably another issue.

[http://www.thibor.co.uk/](http://www.thibor.co.uk/) if you want to check it out.

---

