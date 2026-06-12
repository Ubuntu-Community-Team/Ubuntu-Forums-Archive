---
title: "Upgrade to 18.04LTS disables DNS"
date: 2018-11-17
forum: Networking &amp; Wireless
---

### Post by jdowdster on 2018-11-17
I know, this looks like one of many similar threads that have been posted before but the solutions provided have not worked and in fact explain very little.

I had Ubuntu 16.04LTS installed on a PC. That PC is connected via ethernet (not wifi) to my home network. That network has it's own DNS server (Ubuntu server) and it worked just fine for years.

I then performed an update to 18.04LTS on the PC and now I get the following message when I try to ping any hostnames:

ping: google.ca: Temporary failure in name resolution

No hostnames either local (from my own DNS) or global are accessible. However access via IP address works just fine so the PC is on the network.

The error shown above is new to me (I've been a programmer for over 30yrs) but then I am a low level programmer and I just get the servers to work and then get on with the real work! (Ahem..)

I gather there is a new player in town called "netplan"? I did try to configure it with the following file: 01-netcfg.yaml

[COLOR=#008080]network:[/COLOR][INDENT][COLOR=#008080]  version: 2[/COLOR]
[COLOR=#008080]  renderer: networkd[/COLOR]
[COLOR=#008080]  ethernets:[/COLOR]
[/INDENT]
[INDENT=2][COLOR=#008080]    enp0s3:[/COLOR]
[/INDENT]
[INDENT=3][COLOR=#008080]      addresses: [192.168.101.98/24][/COLOR]
[COLOR=#008080]      gateway4: 192.168.101.1[/COLOR]
[COLOR=#008080]      nameservers:[/COLOR]
[/INDENT]
[INDENT=4][COLOR=#008080]        addresses: [8.8.8.8,192.168.101.107,206.248.154.22] 
[/COLOR][/INDENT]
[COLOR=#008080]
[/COLOR]I ran various combinations of netplan commands to no avail.

What is really puzzling is the complete lack of debug/error/information as to what's happening. Nothing in syslog either. I guess what I need is information as to how to track this issue down.

Any help would be appreciated.

Cheers!!

---

### Post by QIII on 2018-11-17
yaml is very sensitive to formatting.

Are those indents literal?  Try to cut and paste the actual text between code tags to preserve formatting.

yaml indentations are two spaces.  I haven't looked more closely than that, but just getting that straightened out may fix the issue.

It should look something like

```
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s3:
      addresses: [192.168.101.98/24]
      gateway4: 192.168.101.1
      nameservers:
        addresses: [8.8.8.8,192.168.101.107,206.248.154.22] 
```

Oh:  Also run

```
sudo netplan apply
```

after you make the changes.

---

### Post by jdowdster on 2018-11-18
Thanks for the reply QIII

In fact it was already 2 spaces for indent. I had to doctor the cut and paste to this forum. So I did as you advised and there is no difference. Here is the output from the netplan command:

```
jdowd@saturn:~$ sudo netplan --debug apply
** (generate:14313): DEBUG: 10:14:20.082: Processing input file //etc/netplan/01-netcfg.yaml..
** (generate:14313): DEBUG: 10:14:20.082: starting new processing pass
** (generate:14313): DEBUG: 10:14:20.082: enp0s3: setting default backend to 1
** (generate:14313): DEBUG: 10:14:20.082: Generating output files..
** (generate:14313): DEBUG: 10:14:20.083: NetworkManager: definition enp0s3 is not for us (backend 1)
DEBUG:netplan generated networkd configuration exists, restarting networkd
DEBUG:no netplan generated NM configuration exists
DEBUG:device lo operstate is unknown, not replugging
DEBUG:netplan triggering .link rules for lo
DEBUG:device wlp2s0 operstate is up, not replugging
DEBUG:netplan triggering .link rules for wlp2s0
DEBUG:device enp0s31f6 operstate is up, not replugging
DEBUG:netplan triggering .link rules for enp0s31f6
```

Cheers!!

---

### Post by chili555 on 2018-11-18
> DEBUG:device [COLOR="#FF0000"]enp0s31f6 [/COLOR]operstate is up, not repluggingI'm confused. Is your interface enp0s3 as declared in the netplan yaml file or is it enp0s31f6? What does this tell us?```
ip addr show
```

---

### Post by jdowdster on 2018-11-18
Sorry, it is in fact enp0s31f6. I'm assuming that the enp0s3 reference will include all of the interfaces starting with that that. I have tried both the full name and this shorter version while testing. It makes no difference.

As per your request:

```
jdowd@saturn:~$ ip addr show[/COLOR]
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default q
len 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host  
       valid_lft forever preferred_lft forever
2: enp0s31f6: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether fc:aa:14:ff:a5:47 brd ff:ff:ff:ff:ff:ff
    inet 192.168.101.98/24 brd 192.168.101.255 scope global enp0s31f6
       valid_lft forever preferred_lft forever
    inet6 fe80::516:b062:5c6d:54ac/64 scope link noprefixroute  
       valid_lft forever preferred_lft forever
4: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 08:d4:0c:a6:c8:4a brd ff:ff:ff:ff:ff:ff
    inet 192.168.101.25/24 brd 192.168.101.255 scope global dynamic noprefixroute w
lp2s0
       valid_lft 73610sec preferred_lft 73610sec
    inet6 fe80::daad:b6a5:4f6d:c049/64 scope link noprefixroute  
       valid_lft forever preferred_lft forever
```

Cheers!!

---

### Post by chili555 on 2018-11-18
> I'm assuming that the enp0s3 reference will include all of the interfaces starting with that that.I don't believe so.

Please change your yaml file and then:```
sudo netplan generate
sudo netplan apply
```Reboot and show us:```
ping -c3 192.168.101.1
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
```

---

### Post by jdowdster on 2018-11-18
So here is the file:

```
# This file describes the network interfaces available on your system# For more information, see netplan(5).
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s31f6:
      dhcp4: no
      addresses: [192.168.101.98/24, ]
      gateway4:  192.168.101.1
      nameservers:
        addresses: [192.168.101.24,206.248.154.22]



```

output from generate/apply
```
jdowd@saturn:~$ sudo netplan --debug generate
DEBUG:command generate: running ['/lib/netplan/generate']
** (generate:17461):DEBUG: 14:40:55.234: Processing input file //etc/netplan/01-netcfg.yaml..
** (generate:17461):DEBUG: 14:40:55.234: starting new processing pass
** (generate:17461):DEBUG: 14:40:55.234: enp0s31f6: setting default backend to 1
** (generate:17461): DEBUG: 14:40:55.234: Generating output files..
** (generate:17461): DEBUG: 14:40:55.235: NetworkManager: definition enp0s31f6 is not for us (backend 1)
```

```
jdowd@saturn:~$ sudo netplan --debug apply
** (generate:17466): DEBUG: 14:41:00.242: Processing input file //etc/netplan/01-netcfg.yaml..
** (generate:17466): DEBUG: 14:41:00.242: starting new processing pass
** (generate:17466): DEBUG: 14:41:00.242: enp0s31f6: setting default backend to 1
** (generate:17466): DEBUG: 14:41:00.242: Generating output files..
** (generate:17466): DEBUG: 14:41:00.243: NetworkManager: definition enp0s31f6 is not for us (backend 1)
DEBUG:netplan generated networkd configuration exists, restarting networkd
DEBUG:no netplan generated NM configuration exists
DEBUG:device lo operstate is unknown, not replugging
DEBUG:netplan triggering .link rules for lo
DEBUG:replug wlp2s0: unbinding 0000:02:00.0 from /sys/bus/pci/drivers/iwlwifi
DEBUG:replug wlp2s0: rebinding 0000:02:00.0 to /sys/bus/pci/drivers/iwlwifi
DEBUG:device enp0s31f6 operstate is up, not replugging
DEBUG:netplan triggering .link rules for enp0s31f6
```

And here is the output from your 3 commands:

```
jdowd@saturn:~$ ping -c3 192.168.101.1           
PING 192.168.101.1 (192.168.101.1) 56(84) bytes of data.
64 bytes from 192.168.101.1: icmp_seq=1 ttl=64 time=0.385 ms
64 bytes from 192.168.101.1: icmp_seq=2 ttl=64 time=0.417 ms
```

```
jdowd@saturn:~$ ping -c3 8.8.8.8                 
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=121 time=15.2 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=121 time=17.6 ms
```

```
jdowd@saturn:~$ ping -c3 [www.ubuntu.com](www.ubuntu.com)
ping: [www.ubuntu.com:](www.ubuntu.com:) Temporary failure in name resolution
```

Cheers!!

---

### Post by jdowdster on 2018-11-18
Very strange as well...

So, I setup wireshark on this PC that I'm working on to trap any traffic from the affected machine (192.168.101.98). I made sure I had no networking issues by just trapping the ping to and from that machine "ping 192.168.101.24" and I can see that wireshark is happily recording the ping traffic.

My next test was to ping using a hostname which would invoke DNS. I did the "ping google.ca". There is no traffic, not even the DNS query going out. So when the error says "DNS Temporary failure in name resolution" this is a failure because the client DNS query is acting as if it's turned off. Does this make sense to anyone?

Cheers!!

---

### Post by jdowdster on 2018-11-18
So I really hope those of you helpful people are still paying attention and that this is helping. If you are...

So more to the story. I had a look at the nsswitch.conf file on the affected machine. I had a look at my wireshark capture as well and in fact I got it wrong. Here's the line of interest in the nsswitch.conf file:

```
hosts:          files mdns4_minimal [NOTFOUND=return] dns
```  

From what I got from my extensive research into nsswith.conf (3 minutes) that means look in the /etc/hosts file first, then check out this mdns4 thingy (Multi-cast DNS). If that returns after not found and it was a local query then stop otherwise move onto dns.

Here is an interesting capture line:
```
1	0.000000000	192.168.101.98	192.168.101.255	NBNS	92	Name query NB WORKGROUP<1d>
```

So, it is actually trying to query but the dns is just plain not being issued.

Cheers!!

---

### Post by chili555 on 2018-11-18
If you can ping by number but not name, it is clearly a DNS issue. Let's also see: ```
cat /etc/resolv.conf
ls -al /etc/resolv.conf
sudo systemd-resolve --status  | grep DNS

```

---

### Post by jdowdster on 2018-11-18
I have solved this issue.

I was experimenting with installing dnsmasq instead of using systemd-resolved and was getting no where. I had to issue the commands:

```
sudo systemctl stop systemd-resolved
sudo systemctl disable systemd-resolved
```

so to undo this I issued:

```
sudo systemctl enable systemd-resolved
sudo systemctl start systemd-resolved
```

I'm not sure if the 2nd line was required but after these 2 commands executed my DNS issue was solved. I did run into a website that mentioned that there was an incompatibility between systemd-resolved and netplan. That fix had me removing systemd-resolved and replacing it with one of a few available DNS query systems out there. Unfortunately I can't put my finger on exactly what went wrong. I didn't do a full install of kubuntu 18.04LTS but rather I went the upgrade path which has always been problematic for me. Once the system stated that it was finished the installation and had been rebooted, that is when the DNS query stopped working. I'm hoping that if at that time I had just typed those 2 lines it would have then started working.

Now how do I tag this thread as solved?

Thanks to chili555 and QIII for your help and patience.

Cheers!!

---

### Post by QIII on 2018-11-20
Please use the default color and font.  To encapsulate code, results and the text of your config files, please use code tags.  This will make your posts much easier to read and code tags will preserve formatting.

To use code tags, either:

1.  Click the # button in the toolbar above the text entry box, place your cursor between the code tags that appear and type or paste your text.  Alternatively, type or paste your text, highlight it and then click the # button.

2.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after your text.  The square brackets are required.

Cheers!

---

