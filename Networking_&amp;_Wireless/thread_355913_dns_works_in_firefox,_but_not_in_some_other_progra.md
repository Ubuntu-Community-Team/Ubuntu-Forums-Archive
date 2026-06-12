---
title: "dns works in firefox, but not in some other programs"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by abuntoyoutoo on 2007-02-07
I'm having a dns problem where firefox is working perfectly, but others like gaim, apt-get, add/remove programs and evolutions are not working.

The main problem is with installing applications. For example, in attempting to install Kolf, i typed this into the terminal
```

sudo apt-get install kolf

```
This resulted in the following output
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libktnef1 libkcal2b libjack0.100.0-0 libqt4-qt3support libapr0 libqt4-core
  libsqlite0 mysql-common libmysqlclient15off libsvn0 kdesvn-kio-plugins
  libqt4-gui libkdepim1a libntfs8 libqt4-sql ntfsprogs libsdl-mixer1.2
  libsvnqt2 libsmpeg0
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  kolf
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 946kB of archives.
After unpacking 2200kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  kolf
Install these packages without verification [y/N]?

```
When I typed 'y', the result was
```

Err http://au.archive.ubuntu.com edgy/main kolf 4:3.5.5-0ubuntu1
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/kolf_3.5.5-0ubuntu1_i386.deb  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```
Note how it thinks the IP address is (1.0.0.0)
However ping instantly gave the correct IP address (211.29.132.173) and successfully sends pings to it. Also, I can open and save the file [http://au.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/kolf_3.5.5-0ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/kolf_3.5.5-0ubuntu1_i386.deb) by going through firefox. The weird thing is, after opening it in firefox, apt-get install works!

I've disabling IPv6 to get firefox to work. However apt-get didn't work while IPv6 was enabled.

Other problems I have had is GAIM doesn't open any of my accounts, and evolution can't open my gmail account.

Can anyone help me with this problem?

---

### Post by mkoyle on 2007-02-07
I'm still looking for an explanation somewhere.  You can at least get apt-get to work by changing to the IP instead of the dns address:

[http://forums.debian.net/viewtopic.php?t=5665&view=previous&sid=7facf7d49eff150f01bf05ff9e9cee80](http://forums.debian.net/viewtopic.php?t=5665&view=previous&sid=7facf7d49eff150f01bf05ff9e9cee80)

If I find an explanation or think a bug should be filed, I'll post back.

--Matthew

---

### Post by mkoyle on 2007-02-07
Looks like if you do choose to do that, they have changed IPs

211.29.132.173

---

### Post by mkoyle on 2007-02-07
I see at least three different possibilities.  One is something in the /etc/apt.conf file.  The next is a proxy problem.  The other might be a problem with your router's DNS forwarding (this is unlikely, but possible).

This hard to resolve issue has been a seemingly endless problem for many users (because it is hard to know which of the fixes will correct it).  These posts might have the fix for you:

[http://www.ubuntuforums.org/showthread.php?t=193178&page=5](http://www.ubuntuforums.org/showthread.php?t=193178&page=5)
[http://www.ubuntuforums.org/showthread.php?t=190679](http://www.ubuntuforums.org/showthread.php?t=190679)
[http://ubuntuforums.org/showthread.php?p=2092697](http://ubuntuforums.org/showthread.php?p=2092697)

If you can't find the solution there and want more help, you could post the content of:

gedit /etc/resolv.conf

the output of the route command

route

and make sure we can't blame IPv6 (from [http://www.ubuntuforums.org/archive/index.php/t-6841.html](http://www.ubuntuforums.org/archive/index.php/t-6841.html) ).

1. sudo gedit /etc/modprobe.d/aliases (or your preferred text editor)
2. Find the line: alias net-pf-10 ipv6
3. Edit this to: alias net-pf-10 off
4. Save the file and reboot

---

### Post by abuntoyoutoo on 2007-02-07
> This hard to resolve issue has been a seemingly endless problem for many users (because it is hard to know which of the fixes will correct it). These posts might have the fix for you:
Thanks for the links. However none of them helped unfortunately...

Output of gedit /etc/resolv.conf
```

nameserver 192.168.1.1

```

Output of route:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         mygateway1.ar7  0.0.0.0         UG    0      0        0 eth0

```
That output looks interesting, as the default value is 0.0.0.0 (which can't be right)

---

### Post by mkoyle on 2007-02-08
Actually, your route table looks fine; here's mine:

```

Kernel IP routing table
Destination    Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0        0        0   eth0
link-local          *               255.255.0.0      U     1000   0        0   eth0
default         192.168.1.1     0.0.0.0           UG    0        0        0   eth0
```

I am just wondering if your router is causing the problem.  I had a DSL modem that didn't quite follow standard specifications for DNS and it caused me similar problems.

Did you try editing your resolv.conf file like one of those posts mentioned?

sudo gedit /etc/resolv.conf 

And change 192.168.1.1 to one of the following (whichever is closer):
    * ns1.de.opennic.glue (Cologne, DE) - 217.115.138.24
    * ns1.jp.opennic.glue (Tokyo, JP) - 219.127.89.34
    * ns2.jp.opennic.glue (Tokyo, JP) - 219.127.89.37
    * ns1.nz.opennic.glue (Auckland, NZ) - 202.89.131.4
    * ns1.uk.opennic.glue (London, UK) - 194.164.6.112
    * ns1.phx.us.opennic.glue (Phoenix, AZ, US) - 63.226.12.96
    * ns1.sfo.us.opennic.glue (San Francisco, CA, US) - 64.151.103.120
    * ns1.co.us.opennic.glue (Longmont, CO, US) - 216.87.84.209
    * ns1.ca.us.opennic.glue (Los Angeles, CA, US) - 67.102.133.222
    * ns1.be.opennic.glue (Luik, Belgium) - 83.217.93.246 

If that makes it work better, we need to figure out how to make your router not mirror DNS and just provide your ISP's DNS server address in stead.  If that doesn't fix it, I am left wondering what else it could be.  

If that did not fix it temporarily, just a couple more questions to eliminate possible problems one a time:
Did you turn IPv6 off globally (with those instructions above) and check for system-wide proxy settings?

Does firefox have a proxy set while nothing else does?  

Try clearing your global proxy setting:

export http_proxy=

If you are required to use a proxy, you could add your proxy's IP and port to /etc/apt/apt.conf
```

ACQUIRE {
http::proxy "http://172.16.1.71:8080/"
}

```

--Matthew

---

### Post by mips on 2007-02-08
disable ipv6 and also drop the au. from your sources.list.

---

### Post by abuntoyoutoo on 2007-02-08
Thanks for the responses!
Unfortunately, nothing suggested fixed the problem. I definitely have ipv6 disabled, and I'm not using a proxy. I think it is basically a hardware problem with my cheapo router not playing nice with ubuntu.

Luckily however I found a workaround which got everything I needed working. What I did was found the IP addresses that weren't working using ping, then added them to my /etc/hosts list. My hosts list is now:
```

127.0.0.1 localhost
127.0.1.1 DAVIDS-COMPUTER

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
211.29.132.173 au.archive.ubuntu.com
140.211.166.4 chat.freenode.net
64.233.163.111 pop.gmail.com
207.46.96.153 messenger.hotmail.com
82.211.81.166 ubuntu.com

```

With those added, the only thing that isn't working is software verification, and MSN in GAIM (but it works in aMSN so it isn't a problem).

---

### Post by mips on 2007-02-09
A better option would be to specify your ISPs DNS servers in the resolv.conf file else you are going to constantly have to add more hosts to that file.

---

### Post by abuntoyoutoo on 2007-02-09
> **mips said:**
> A better option would be to specify your ISPs DNS servers in the resolv.conf file else you are going to constantly have to add more hosts to that file.
Unfortunately, that didn't work for me. The whole problem never made sense to me, as ubuntu could easily access the dns server to gain IP addresses (otherwise how did ping and Firefox work?). Also note that firefox could get onto any site (such as ftp, http, https) I tried and chatzilla could log on to irc. aMSN can get onto MSN, but GAIM cannot log on to anything.

From my understanding, if ping could get an address resolved and retrieve its ip address and successfully send pings to the target, then the internet is correctly configured. A simple software hack such as 
```

if retrievedIpAddress == "0.0.0.1" then
    dig address // the address being looked up
    if dig was successful
        set retrievedIPAddress to ip address found by dig
    end if
end if

```
would solve many problems.

The only possible cause that might be it is that although I disabled IPv6, and the lack of output from
```

ip a | grep inet6

```
supports that idea, maybe some internal parts of ubuntu ignore those settings, and continue to use IPv6. 
The operation of wget (downloads files from the internet from the terminal) supports this idea, as with wget , a command like
```

wget www.google.com

```
will fail, while using
```

wget www.google.com --inet4-only

```
will successfully download the page. So I assume any program that uses wget would suffer the same problem.

But on the other hand, the documentation of wget clearly states that if an ipv6 lookup fails, it will then look it up using ipv4.
> 
`-4'
`--inet4-only'
`-6'
`--inet6-only'
     Force connecting to IPv4 or IPv6 addresses.  With `--inet4-only'
     or `-4', Wget will only connect to IPv4 hosts, ignoring AAAA
     records in DNS, and refusing to connect to IPv6 addresses
     specified in URLs.  Conversely, with `--inet6-only' or `-6', Wget
     will only connect to IPv6 hosts and ignore A records and IPv4
     addresses.

     Neither options should be needed normally.  By default, an
     IPv6-aware Wget will use the address family specified by the
     host's DNS record.  If the DNS responds with both IPv4 and IPv6
     addresses, Wget will try them in sequence until it finds one it
     can connect to.  (Also see `--prefer-family' option described
     below.)

     These options can be used to deliberately force the use of IPv4 or
     IPv6 address families on dual family systems, usually to aid
     debugging or to deal with broken network configuration.  Only one
     of `--inet6-only' and `--inet4-only' may be specified at the same
     time.  Neither option is available in Wget compiled without IPv6
     support.

So it should work regardless of the --inet4-only setting.

---

### Post by Dumdideldum on 2007-02-21
I face exactly the same problem with same behavior of Ubuntu.

---

### Post by Dumdideldum on 2007-02-21
Don´t ask me why or the reason why these entries are in this file, but my problem is fixed by editing the /etc/nsswitch.conf from:

```

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

```

into:

```

hosts: files dns

```

maybe someone can explain why

---

### Post by mips on 2007-02-21
Nice find.

nsswitch.conf specifies which name service to use for a particular machine: NIS, NIS+, DNS, or local files etc

The list you see specifies in which order it should use the various resources.

```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```

files:
Network Database     Local Files
hosts                        /etc/inet/hosts
netmasks                  /etc/inet/netmasks
ethers                      /etc/ethers 
bootparams              /etc/bootparams
protocols                  /etc/inet/protocols
services                   /etc/inet/services
networks                  /etc/inet/networks

mdns4:
multicast DNS service discovery. It allows programs to publish and discover services and hosts running on a local network with no specific configuration. For example you can plug into a network and instantly find printers to print to, files to look at and people to talk to. mdns4_minimal is obviously a minimal subset of mdns4

dns:
your normal DNS service

[NOTFOUND=return]:
means that the search for an entry should stop if the search in the previous entry turned up nothing. Note that if the search failed due to some other reason (like no NIS server responding) then the search continues with the next entry.

From the bit of reading I've done it is suggested that mdns only be called after dns if dns fails. I dont see how mdns is going to benefit you if you only have one pc on the LAN. Then again i'm not clued up on mdns at all so i might be sprouting nonsense.

Ive changed mine to reflect as:
hosts:          files dns mdns4_minimal [NOTFOUND=return] mdns4

I'll see if this improves anything.

---

### Post by abuntoyoutoo on 2007-02-22
Thanks for the replies. I found another way to fix it on my computer anyway. I changed by etc/resolv.conf file to
```

nameserver 204.117.214.10
nameserver 217.32.105.91
nameserver 198.32.64.12

```
Clearly my original DNS server didn't work with ipv6. Strangely, I tried that fix previously but it didn't work. But after getting a lot of help from irc, and changing a lot of things, I did it again and it worked! So its worth a shot anyway, even if you have already tried changing your nameservers.

---

