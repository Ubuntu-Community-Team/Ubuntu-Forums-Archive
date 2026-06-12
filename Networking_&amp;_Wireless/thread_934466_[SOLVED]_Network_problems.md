---
title: "[SOLVED] Network problems"
date: 2008-09-30
forum: Networking &amp; Wireless
---

### Post by tontikki on 2008-09-30
Or so i think! My wireless connection seems to be working perfectly both home and at work, connects automatically and everything is fine as long as I'm using browser. 

But the rest of the laptop for some reason do not have access to the internet! Update manager, add/remove programs, package manager - neither can access internet:(( 

Also what i noticed is that when I go System/Network Settings, the 'Unlock' button is greyed out so i can't change there anything! I made sure I login as Administrator but to no avail:((

I'm using Xubuntu Hardy.

Please help!:cry::cry:

---

### Post by tontikki on 2008-09-30
Ok one problem is solved - apparently the greyed out 'Unlock' button is a BUG (many people have this problem), the way around is to open the Network settings dialoge not through the menu, but by clicking on the Network-manager icon in the taskbar and selecting Manual configuration. Then the button Unlock works.


But my other problem still there - what do i need to change in settings to make sure the updater, the package manager etc could access internet???

Thanks so much!!

---

### Post by Sealbhach on 2008-09-30
Sounds weird. See if you can ping the BBC from your terminal:
```

 ping www.bbc.co.uk -c 5
```

The other thing to check is your System/Administration/Software Sources.

.

---

### Post by Crafty Kisses on 2008-09-30
What are the results of this command?
```
lshw -C network
```

---

### Post by tontikki on 2008-09-30
Thanks Sealbhach, does it look ok?
```
PING www.bbc.net.uk (212.58.251.195) 56(84) bytes of data.
64 bytes from www-vip.telhc.bbc.co.uk (212.58.251.195): icmp_seq=1 ttl=116 time=15.9 ms
64 bytes from www-vip.telhc.bbc.co.uk (212.58.251.195): icmp_seq=2 ttl=116 time=15.2 ms
64 bytes from www-vip.telhc.bbc.co.uk (212.58.251.195): icmp_seq=3 ttl=116 time=11.5 ms
64 bytes from www-vip.telhc.bbc.co.uk (212.58.251.195): icmp_seq=4 ttl=116 time=19.3 ms
64 bytes from www-vip.telhc.bbc.co.uk (212.58.251.195): icmp_seq=5 ttl=116 time=11.7 ms

--- www.bbc.net.uk ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4001ms
rtt min/avg/max/mdev = 11.501/14.746/19.342/2.918 ms
```

In software sources everything seems to be ok, almost everything is checked...

The thing is when i first fresh-installed Hardy everything was working OK and I was able to update and to install/uninstall programs via Add/Remove and Package manager. But then all of a sudden these tools stopped accessing the internet, I thought I messed up with something, so tonight i reinstalled Xubuntu (just the /root as /home is on separate logical partition with all my documents and settings) but it didn't help! Still can perfectly access internet via browser but not via other programs.

:confused:

---

### Post by Crafty Kisses on 2008-09-30
I also forgot can you connect through IRC or elinks?

---

### Post by tontikki on 2008-09-30
Codename:
```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:17:42:63:1c:62
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:1b:9e:2a:3e:46
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.100 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

```

Thanks!!

---

### Post by tontikki on 2008-09-30
> **Codename said:**
> I also forgot can you connect through IRC or elinks?

i'm not sure i don't have IRC (and don't know what elinks are:redface:)

---

### Post by tontikki on 2008-09-30
Oh I almost forgot - I also use Thunderbird mail, which connects to internet and is working fine.

---

### Post by Sealbhach on 2008-09-30
> **tontikki said:**
> Thanks Sealbhach, does it look ok?
```
PING www.bbc.net.uk (212.58.251.195) 56(84) bytes of data.
64 bytes from www-vip.telhc.bbc.co.uk (212.58.251.195): icmp_seq=1 ttl=116 time=15.9 ms
64 bytes from www-vip.telhc.bbc.co.uk (212.58.251.195): icmp_seq=2 ttl=116 time=15.2 ms
64 bytes from www-vip.telhc.bbc.co.uk (212.58.251.195): icmp_seq=3 ttl=116 time=11.5 ms
64 bytes from www-vip.telhc.bbc.co.uk (212.58.251.195): icmp_seq=4 ttl=116 time=19.3 ms
64 bytes from www-vip.telhc.bbc.co.uk (212.58.251.195): icmp_seq=5 ttl=116 time=11.7 ms

--- www.bbc.net.uk ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4001ms
rtt min/avg/max/mdev = 11.501/14.746/19.342/2.918 ms
```

In software sources everything seems to be ok, almost everything is checked...

The thing is when i first fresh-installed Hardy everything was working OK and I was able to update and to install/uninstall programs via Add/Remove and Package manager. But then all of a sudden these tools stopped accessing the internet, I thought I messed up with something, so tonight i reinstalled Xubuntu (just the /root as /home is on separate logical partition with all my documents and settings) but it didn't help! Still can perfectly access internet via browser but not via other programs.

:confused:

Yeah, it looks fine. There's some problem with the package manager. Do you get any messages when you sudo apt-get from the terminal?

What happens if you do 

```
sudo apt-get update
```

??


.

---

### Post by tontikki on 2008-10-02
> **Sealbhach said:**
> Yeah, it looks fine. There's some problem with the package manager. Do you get any messages when you sudo apt-get from the terminal?

What happens if you do 

```
sudo apt-get update
```

??


.


unfortunately nothing happens:(

```
sudo apt-get update
[sudo] password for oli: 
Err http://archive.canonical.com hardy Release.gpg                                                                                                           
  Could not connect to archive.canonical.com:80 (91.189.90.142), connection timed out
Err http://archive.canonical.com hardy/partner Translation-en_GB                                                                                             
  Unable to connect to archive.canonical.com http:
Err http://security.ubuntu.com hardy-security Release.gpg                                                                                                    
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err http://security.ubuntu.com hardy-security/restricted Translation-en_GB                             
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com hardy-security/main Translation-en_GB                                   
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com hardy-security/multiverse Translation-en_GB                             
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com hardy-security/universe Translation-en_GB                               
  Unable to connect to security.ubuntu.com http:
Err http://archive.ubuntu.com hardy Release.gpg                                        
  Could not connect to archive.ubuntu.com:80 (91.189.88.45), connection timed out [IP: 91.189.88.45 80]
Err http://archive.ubuntu.com hardy/main Translation-en_GB
  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://archive.ubuntu.com hardy/restricted Translation-en_GB
  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://archive.ubuntu.com hardy/universe Translation-en_GB
  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://archive.ubuntu.com hardy/multiverse Translation-en_GB
  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://archive.ubuntu.com hardy-security Release.gpg
  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.45 80]
Reading package lists... Done                       
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Could not connect to archive.ubuntu.com:80 (91.189.88.45), connection timed out [IP: 91.189.88.45 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_GB.bz2  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.45 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_GB.bz2  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.45 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_GB.bz2  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.45 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_GB.bz2  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.45 80]

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg  Could not connect to archive.canonical.com:80 (91.189.90.142), connection timed out

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_GB.bz2  Unable to connect to archive.canonical.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_GB.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_GB.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_GB.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_GB.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.45 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```

what do i do?](*,) :confused::confused::confused:

---

### Post by Sealbhach on 2008-10-02
OK, perhaps you're using a proxy server? If so, see the instructions here:

[http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html](http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html)


Or you could try some other mirrors?

Have a look on the Google Search results page where people have reported the same problem...
[URL="http://www.google.co.uk/search?hl=en&safe=off&q=ubuntu+%22Failed+to+fetch+http%3A%2F%2Farchive.ubuntu.com%22&btnG=Search&meta="]
Google Search results[/URL]


Good luck.


.

---

### Post by taladan on 2008-10-02
is it possible that you've munged up your sources.list file?

post the output of the following up if you could:

```
cat /etc/apt/sources.list
```

it's odd that everything would work except package management etc.

Tal

---

### Post by tontikki on 2008-10-05
ok these two days i've been searching google for possible solutions and no luck. finally i gave up and reinstalled again - this time formatting /home as well to make sure none of the settings that might had been messed up are saved.

so clean system, connect to wireless fine, browser, pidgin, thunderbird working fine, 

updates and package manager DO NOT:( still get the message 'Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10), connection timed out'

funny enough, i tried to ping the above either way and it goes through fine:

```
oli@cactus:~$ ping -c3 194.169.254.10
PING 194.169.254.10 (194.169.254.10) 56(84) bytes of data.
64 bytes from 194.169.254.10: icmp_seq=2 ttl=52 time=36.7 ms
64 bytes from 194.169.254.10: icmp_seq=3 ttl=52 time=15.7 ms

--- 194.169.254.10 ping statistics ---
3 packets transmitted, 2 received, 33% packet loss, time 1999ms
rtt min/avg/max/mdev = 15.762/26.250/36.739/10.489 ms


oli@cactus:~$ ping -c3 gb.archive.ubuntu.com
PING gb.archive.ubuntu.com (194.169.254.10) 56(84) bytes of data.
64 bytes from ubuntu.datahop.net (194.169.254.10): icmp_seq=1 ttl=52 time=17.0 ms
64 bytes from ubuntu.datahop.net (194.169.254.10): icmp_seq=2 ttl=52 time=34.3 ms
64 bytes from ubuntu.datahop.net (194.169.254.10): icmp_seq=3 ttl=52 time=53.7 ms

--- gb.archive.ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 17.042/35.073/53.793/15.011 ms

```

but i can't update or use package manager.


> **Sealbhach said:**
> OK, perhaps you're using a proxy server? If so, see the instructions here:

[http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html](http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html)

Now i actually do think the problem is the proxy, but i have no clue what that proxy is!!](*,)

In firefox, pidgin etc in network settings if i tick 'no proxy' or 'direct connection to the internet' they stop connecting. So i use 'auto-detect proxy settings' option instead and then it works.

But in Synaptic package manager network settings i don't have this option, only either 'direct connection' or 'manual proxy configuration', and not knowing proxy of corse i can't configure manually.

Strangely enough is that i never needed that setting, everything was working fine untill one day it stopped connecting for no reason:( Tomorrow i'm going to call our IT support but unfortunately they are not very linux friendly,,,

---

### Post by tontikki on 2008-10-05
So I was thinking is there any way to findout myself which proxy my network is using??

here's the contents of my /etc/resolv.conf which looks fine:

```
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4882
#
### END INFO

search sns.nottingham.ac.uk


nameserver 128.243.40.193
nameserver 128.243.40.192


```

and /etc/nsswitch.conf:

```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

and /etc/sysctl.conf

```
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# the following stops low-level messages on console
kernel.printk = 4 4 1 7

# enable /proc/$pid/maps privacy so that memory relocations are not
# visible to other users.  (Added in kernel 2.6.22.)
kernel.maps_protect = 1

# Increase inotify availability
fs.inotify.max_user_watches = 524288

# protect bottom 64k of memory from mmap to prevent NULL-dereference
# attacks against potential future kernel security vulnerabilities.
# (Added in kernel 2.6.23.)
vm.mmap_min_addr = 65536

##############################################################3
# Functions previously found in netbase
#

# Comment the next two lines to disable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
net.ipv4.conf.default.rp_filter=1
net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# This disables TCP Window Scaling (http://lkml.org/lkml/2008/2/5/167)
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.ip_forward=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Ignore ICMP broadcasts
#net/ipv4/icmp_echo_ignore_broadcasts = 1
#
# Ignore bogus ICMP errors
#net/ipv4/icmp_ignore_bogus_error_responses = 1
# 
# Do not accept ICMP redirects (prevent MITM attacks)
#net/ipv4/conf/all/accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net/ipv4/conf/all/secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net/ipv4/conf/all/send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net/ipv4/conf/all/accept_source_route = 0
#
# Log Martian Packets
#net/ipv4/conf/all/log_martians = 1
#
# Always defragment packets
#net/ipv4/ip_always_defrag = 1

```

and finally /etc/network/interfaces:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

```


if they could be of any help??

Thanks.....

---

### Post by tontikki on 2008-10-05
Oh i almost forgot, i'm using a router, too - if it could be a part of the problem?...

---

### Post by tontikki on 2008-10-06
:bump:

Just off the phone to our IT support who were very supportive indeed but of litle help.. They don't deal with linux, they suggested the proxy address and promised to pass the issue to someone else but I don't have much hopes:(

In synaptic package manager in settings/preferences/network there are two options to choose from, direct connection to the internet and manual proxy configuration. When direct connection is choosen the package manager times out on attempt to connect to internet.

```
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10), connection timed out

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_GB.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_GB.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_GB.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_GB.bz2  Unable to connect to security.ubuntu.com http:

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

The proxy our uni is using is wwwcache.nottingham.ac.uk and port 3128 (128.243.220.20:3128). When tick manual proxy configuration and fill that in,it seems to quickly go to 25 out 36 repositories, but then stops and displays the error:

```
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz  403 Forbidden
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.gz  403 Forbidden
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.gz  403 Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz  403 Forbidden
Some index files failed to download, they have been ignored, or old ones used instead.
```

We have even tried putting the automatic proxy configuration script in the http proxy field (wwwcache.nottingham.ac.uk/proxy.pac) which doesn't really belong there but just in case, the package manager similarly quickly goes to 25 out 36 repositories and stops, but the error is now 404:

```
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.gz  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```

please help :shock:

---

### Post by tontikki on 2008-10-06
This is the etc/apt/sources.list...

```
oli@cactus:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Xubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main multiverse restricted universe

# deb cdrom:[Xubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main multiverse restricted universe
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu hardy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe
# deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

,,,

---

### Post by LiquidFX on 2008-11-03
im having the same problem

---

### Post by tontikki on 2008-11-20
solved - the problem was to enter the correct proxy in Preferences>Network

---

### Post by k-bot on 2009-05-04
> **tontikki said:**
> solved - the problem was to enter the correct proxy in Preferences>Network

I had the same problem. This didn't work for me. I went to Synaptic Package Manager > Settings > Preferences > Network and altered the proxy setting there. Now its working fine.

---

