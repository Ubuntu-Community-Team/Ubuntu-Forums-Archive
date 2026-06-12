---
title: "My resolv.conf wont update"
date: 2007-04-09
forum: Networking &amp; Wireless
---

### Post by moore757 on 2007-04-09
Hey there folks,

I'm experiencing an incredibly weird problem and i'm hoping somebody out there might have seen this before and have a solution.  I've been using Ubuntu 6.10 for quite awhile and have had no problems with my networking whatsoever.  I use DHCP at work to acquire my IP address and have been doing so for awhile.  

The other day I discovered I was not able to resolve any webpages.  nslookup would continually fail.  Strangely though I was successfully being provided with all necessary information via DHCP.  My IP address and gateway were still being set correctly.  

However, when I did a cat on my /etc/resolv.conf I saw that the value had mysteriously been set to 192.168.1.1

I manually edited the file and entered in the appropriate DNS entry and everything started working nicely again.  The problem is now that whenever my DHCP lease renews the resolv.conf is set back to 192.168.1.1....

anybody have any ideas why this is happening? or how i can make my resolv.conf more permanent and not subject to the changes when my lease is renewed?  

thanks

---

### Post by dbott67 on 2007-04-09
'nameserver 192.168.1.1' is typically the IP address of your router. Most routers have built-in DNS relay services that forward all internal requests to your ISP's DNS server, so this is normal. Some users experience name resolution problems with the configuration above and have added the OpenDNS servers to the resolv.conf file.

Personally, I have a D-Link DI-614+ and have the same configuration as you do right now and have never had any problems (with either ipv6 or name resolution). **What make & model router do you have?**

You can try manually adding the OpenDNS servers (or whatever your preferred DNS server is, such as your ISP's) to your /etc/resolv.conf file and comment out your current one:
```
sudo gedit /etc/resolv.conf
``````
[B][COLOR=Red]nameserver 208.67.222.222
nameserver 208.67.220.220[/COLOR][/B]
**[COLOR=Red]#[/COLOR]** nameserver 192.168.1.1
```If you notice an improvement (or it cures the problem) then you can make it permanent. After a few minutes, you'll notice that the file get overwritten.

By default, the dhclient.conf file will overwrite the resolv.conf file each reboot, so you need to edit the dhclient file:

1. Backup the file first:
```
sudo cp /etc/dhcp3/dhclient.conf /etc/dhcp3/dhclient.conf.bak
```2. Edit the dhclient.conf file:
```
sudo gedit /etc/dhcp3/dhclient.conf
```3. Look for the following line:
```
#prepend domain-name-servers 127.0.0.1;
```Remove the comment (#) and change it to:
```
prepend domain-name-servers **[COLOR=Red]208.67.222.222, 208.67.220.220[/COLOR]**;
```4. Next, look for the **[COLOR=Red]domain-name-servers,[/COLOR]** and ***remove*** it:

```
**[COLOR=Blue]prepend domain-name-servers 208.67.222.222, 208.67.220.220;[/COLOR]**
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, **[COLOR=Red]domain-name-servers,[/COLOR]** host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
```5. Restart your network
```
dbott@edgy:~$ sudo/etc/init.d/networking restart
```Like I said, I've never had to resort to this, however, there are a number of people in this forum that this technique has helped them.

-Dave

---

### Post by moore757 on 2007-04-09
First of all, thank you very very much for your prompt and detailed answer.  I had an idea that there was something such as the dhclient.conf which would allow me to define what networking information I wanted to do manually and automatically, problem was I just had no idea where it was :roll: 

In regards to the actual router i'm using, that answer is a little bit stickier.  The problem I am currently experiencing is happening here at my place of employment.  We use two DNS servers here.  192.168.5.5 and 192.168.64.5.  Whenever I put these values in manually I am able to get web pages no problem.  However, I am very confused as to why my resolve.conf would be populated with 192.168.1.1 whenever my dhcp lease renews.  I have asked my coworkers and none of them have reported any problems.  So I dont believe there is a problem with the DNS server itself.  

I talked to our network manager and he is able to verifying that my machine is correctly being provided dhcp information and is infact requesting dns.  To further complicate the matter, I am running a vmware machine (windows) which has its own static IP address and that is working fine.  So i know there is no problem with the actual connection coming into my office.  

Either way the changes you suggested to my dhclient.conf worked wonderfully and i'm very happy to have learned something new.  Thanks again.

---

### Post by dbott67 on 2007-04-09
What is the IP address of your machine?  Is it on the 192.168.1.xxx subnet?  Could you please post the output of the following commands:
```
dbott@feisty:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:50:BA:C0:A7:55  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7965 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6034 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6843762 (6.5 MiB)  TX bytes:811527 (792.5 KiB)
          Interrupt:16 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:984 errors:0 dropped:0 overruns:0 frame:0
          TX packets:984 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:49660 (48.4 KiB)  TX bytes:49660 (48.4 KiB)

```and your routing table:
```
dbott@feisty:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```What are the static numbers you used in VMware (for comparison)?
Are you connected to any sort of Linksys/D-Link/Netgear router?
What is the IP address of your DHCP server?


There is a package in the repos that can let you know if a DHCP server is running on a particular IP address:
```
sudo apt-get install dhcping
```Then run the program against the known IP address.  I'm running a D-Link DI-614+ Router at home with DHCP and these are my results:
```
dbott@feisty:~$ sudo dhcping -s 192.168.1.1
Got answer from: 192.168.1.1

```

If your DHCP is running on 192.168.1.1 and uses DNS forwarding to forward requests to the DNS servers (192.168.5.5 & 192.168.64.5), it would be the reason that 'nameserver 192.168.1.1' is showing up in your resolv.conf file.  I have never had an issue with this type of setup myself, but there are many users in this forum that report problems with DNS forwarding and have to resort to the hack noted above.
-Dave

---

