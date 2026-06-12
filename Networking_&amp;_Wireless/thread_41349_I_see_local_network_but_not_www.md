---
title: "I see local network but not www"
date: 2005-06-13
forum: Networking &amp; Wireless
---

### Post by rutherti on 2005-06-13
I'm connecting via Efficient/Speedstream 6300 (hard-wired in this case) which acts as both router and high-speed modem (to Sympatico). I'm dual-booting WinXP and Ubuntu; WinXP and other Linux distros see the full web without problem. Other machines on the same modem/router have full web access. 

What do I need to do in Ubuntu (5.04) to see the world?

I have previous experience with Mandriva but I'm far from expert.

T'anks
T

---

### Post by KLineD on 2005-06-13
I think you'll have to give some more detail for us to be able to help you.

For instance, does your router automatically assigns the ip (DHCP server) or do you need to specify a static ip? To see this you can boot to winxp and check the network card properties, if it's "Automatically get ip address" or something along those lines then youre on dhcp. If however it's filled with some numbers then you are using static ip.

Then you need to copy the same setup in your ubuntu box. Generally you can make the configuration via the networking app. It's located in the System menu under Administration. Be sure to fill in the DNS server and that you NIC says it's configured.

---

### Post by nocturn on 2005-06-13
Do you need to configure a proxy?

Check the route command, it should list the IP of your router as default gateway.

---

### Post by rutherti on 2005-06-13
WinXP is using DHCP. Network settings "seem" ok, but don't work for me.

Tab: Connections
Ethernet connection eth0 is active (and the default), it is configured for DHCP

Tab: General
Hostname: saturn (the name of local desktop)
Domain name: (empty)
-- I just tried setting hostname to (empty) as well and logon again, no difference

Tab: DNS
DNS Servers 192.168.2.1 (the speedstream)
Search Domains no-domain-set-bellcanada (works like this in WinXP)

Tab: Hosts
127.0.0.1 localhost.localdomain localhost saturn       
-- plus 5 others like:
ff00::0 ip6-mcastprefix
fe00:00 ip6-localnet
ff02:: with (1 ip6-allnodes) (2 ip6-allrouters) and (3 ip6-allhosts)

All of this is "as installed" except the "saturn" entry which I've tried with/without

Thanks for your help thus far, any ideas?

T

---

### Post by rutherti on 2005-06-13
[QUOTE=nocturn]Do you need to configure a proxy?

Check the route command, it should list the IP of your router as default gateway.[/QUOTE]

Route gives:
Kernel IP routing table
Destination  Gateway  Genmask            Flags  Metric  Ref  Use  Iface
192.168.2.0 *          255.255.255.0        U        0         0         0 eth0
default         192.168.2.1  0.0.0.0           UG     0          0         0 eth0


I am configured for DHCP, no proxy

T'anks, any ideas?
T

---

### Post by nocturn on 2005-06-13
[QUOTE=rutherti]Route gives:
Kernel IP routing table
Destination  Gateway  Genmask            Flags  Metric  Ref  Use  Iface
192.168.2.0 *          255.255.255.0        U        0         0         0 eth0
default         192.168.2.1  0.0.0.0           UG     0          0         0 eth0


I am configured for DHCP, no proxy

T'anks, any ideas?
T[/QUOTE]

Hmm, let's see what is happening (if you don't mind)
install traceroute (via synatptic).
run the command 

```
sudo traceroute www.google.com
```

---

### Post by rutherti on 2005-06-13
[QUOTE=nocturn]Hmm, let's see what is happening (if you don't mind)
install traceroute (via synatptic).
run the command 

```
sudo traceroute www.google.com
```[/QUOTE]
 Hmm, synaptic doesn't list traceroute

---

### Post by shakin on 2005-06-13
Can you browse the web if you use IPs instead of domain names? Try [http://64.233.167.104](http://64.233.167.104) for Google.

If that's the case then you need to add your DNS server using the Network config app. This sounds suspiciously like it may be the case.

---

### Post by Cubanismo on 2005-06-13
I have excactly the same problem.

If I put the IP in firefox it works, if I put the URL it doe'snt work.

If you do what alistair says in an other thread :
> If this is because firefox is doing an IPv6 lookup first, you can turn off this behaviour in firefox by doing :

about:config

search for :

network.dns.disableIPv6

and "enable" this (i.e. disable IPv6 lookups). 

It works all the time.

If I put a public DNS address in the Network config it works but after a while the DNS comes back to my router address and firefox works because of the Alistair's tip, but no other net access works (mail, sinaptics, etc...)

Not sure it is Ubuntu or my router config but well it is a DLink router and all works fine with my XP machines.

---

### Post by shakin on 2005-06-13
[QUOTE=Cubanismo]I have excactly the same problem.

If I put the IP in firefox it works, if I put the URL it doe'snt work.

If you do what alistair says in an other thread :
 

It works all the time.

If I put a public DNS address in the Network config it works but after a while the DNS comes back to my router address and firefox works because of the Alistair's tip, but no other net access works (mail, sinaptics, etc...)

Not sure it is Ubuntu or my router config but well it is a DLink router and all works fine with my XP machines.[/QUOTE]

Make /etc/resolv.conf unwritable to prevent your manual setting from being overwritten. Eg. 'chmod 444 /etc/resolv.conf'

---

### Post by Cubanismo on 2005-06-13
[QUOTE=shakin]Make /etc/resolv.conf unwritable to prevent your manual setting from being overwritten. Eg. 'chmod 444 /etc/resolv.conf'[/QUOTE]
 I just tried and it doesn't work. At least when I reboot (it was the shortest way I had to try, instead of waiting I don't know how long to see if it change)

After rebooting the resolv.conf is back with router address

I guess the line 0dns-down (or somthing like that) during loading of Ubuntu is for something in that change.

---

### Post by wylfing on 2005-06-13
> Search Domains no-domain-set-bellcanada (works like this in WinXP)
If the actual text in the Search Domains box is "no-domain-set-bellcanada" then get rid of that. You should be fine with this box empty, and this is definitely not a valid domain to search.

I find it very peculiar that your modem is handing out its own address as a valid DNS. This is possible but seems unlikely to me. Boot into Windows and open a command prompt. Type 'ipconfig /all' and somewhere in that list should be an entry that lists the DNS servers Windows knows about. If there's more than 192.168.2.1 then the Ubuntu dhcp-client isn't (a) asking for or (b) receiving information from the modem correctly. This could be a bug in dhcp-client. (I don't use DHCP so I can't say if it works reliably or not.)

Cubanismo: the DHCP client writes an entirely new resolv.conf at boot time, so trying to disable write access to the file isn't going to help anything.

---

### Post by Cubanismo on 2005-06-13
[QUOTE=wylfing]
Cubanismo: the DHCP client writes an entirely new resolv.conf at boot time, so trying to disable write access to the file isn't going to help anything.[/QUOTE]

Ok then, I can understand that. So where and how can I force it to write a proper resolv.conf?

---

### Post by Cubanismo on 2005-06-13
Ok I left my laptop alone for a while.... And something updated my resolv.conf even write protected, but I guess that write protection can't fight against a system write.

So who is writing whithout in my authorization? ;)

---

### Post by Cubanismo on 2005-06-13
Ok problem solved for me.

The DNS address came from my router. I changed the primary DNS it gives in the DHCP server of the router to a public DNS and all is fine now. Ubuntu get a proper DNS server and all is working.

I just have to understand why it was working under XP, and why the router doesn't find the DNS from my ISP.

But that's another story.........I'll post again if I find something interesting.

Thanks all

---

### Post by rutherti on 2005-06-15
[QUOTE=shakin]Can you browse the web if you use IPs instead of domain names? Try [http://64.233.167.104](http://64.233.167.104) for Google.

If that's the case then you need to add your DNS server using the Network config app. This sounds suspiciously like it may be the case.[/QUOTE]
 This works, - when I enter the IP address bam it connects. So, DHCP seems to be not working. (More replies following to later posts)

---

### Post by rutherti on 2005-06-15
Very confusing at my end - I seem to have it working but not sure exactly why.

The change in about:config to the network.dns.disableIPv6 setting seems to be essential and seems also to be retained between reboots without any special effort on my part. Attaboy Firefox. Now, why is IPv6 on by default if it seems not to work?

I've tried setting DNS servers (4.2.2.1 and 4.2.2.2) on the Network Settings DNS tab but they're not remembered between reboots. That seems not very good.

Search Domain of "no-domain-set.bellcanada" seems to be default in the modem/router (it is custom BellCanada / Sympatico HW/SW). It also seems to have no effect good or bad (looks dumb tho').

I set the Hostname value (Host Settings on the Network Settings - General tab) to "mynetwork" to agree with the value shown in the modem/router. So now it names my router and not my computer. Maybe coincidence, maybe crucial; very cryptic to me.

In short, it appears that the IPv6 setting in Firefox needs to be turned off manually, but it will be remembered after that. As well it seems the Hostname needs to point to the modem/router. It would be much nicer if Hoary worked right out of the box. Now can you tell me how it got network connection to complete the install?

I'm outa here; thanks all for your help. I hope I can return the favour to the community some day (after I learn some more <g>).
T

---

### Post by wylfing on 2005-06-15
1. Firefox tries IPv6. Some people's modems and routers don't like IPv6. It's nothing to do with Hoary.

2. The Hostname value is the name of your computer.

3. If you are using DHCP, manually editing resolv.conf is useless, because dhcp-client writes an entirely new resolv.conf at boot time.

Glad you got things working.

---

