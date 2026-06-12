---
title: "An issue with DHCP"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by ehertlein on 2007-04-26
I am having an issue with DHCP. The DHCP server is a windows machine and it doesn't seem to recognize my machine name. I am able to get an IP address but other machines on the network can't seem to be able to ping based on this machines name. Can someone point me in the right direction to address this problem?

I have already tried editing the dhclient.conf and added the line:

send host-name "BLAH";

where BLAH is my machine name.

---

### Post by dbott67 on 2007-04-26
The problem is "name resolution".  Windows has typically used WINS support to register computer names on the network, which allows you to connect to other devices just based on the Netbios name (such as  "BLAH"):
```
ping blah
``````
\\blah\sharename
```DNS is another way to achieve this.  Basically, every device is registered into the DNS server as blah.yourdomain.com.  A bit of a pain, as you need to run & maintain your own DNS server.

The nice thing about WINS (from a Windows-user standpoint) is that the machines automatically announce themselves and register in the server.

With that said, you do the following:

1. Create static entries in the hosts or lmhosts of each machine (a bit of a pain if you use DHCP)
2. Follow these instructions in post #2:
_[http://ubuntuforums.org/showthread.php?p=2438836#post2438836](http://ubuntuforums.org/showthread.php?p=2438836#post2438836)_

-Dave

---

### Post by ehertlein on 2007-04-26
Unless I missed something, this allows my Ubuntu machine to see the Windows machines. What I am having the issue with is the Windows machines seeing the Ubuntu machine by name.

Did I miss something?

What is odd is this seemed to work just fine in Dapper.

---

### Post by dbott67 on 2007-04-26
And vice-versa.  Once you install & enable **samba** on the Ubuntu machine, the Windows machine will be able to resolve the Ubuntu computer by hostname.  Installing **winbind** on the Ubuntu machine will resolve the Windows machines.

For example, when I remove samba from Ubuntu:
```
dbott@feisty:~/Desktop$ sudo apt-get remove samba
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  samba
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
Need to get 0B of archives.
After unpacking, 8180kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 102987 files and directories currently installed.)
Removing samba ...
 * Stopping Samba daemons...                                                                                                                                                                  [ OK ] 
dbott@feisty:~/Desktop$ 

```

I am unable to ping my Ubuntu computer (aka [COLOR=Blue]feisty[/COLOR]) from an XP computer:
```
C:\Windows>ping feisty
Ping request could not find host feisty.  Please check the name and try again
```

Re-installing samba on Ubuntu:
```
dbott@feisty:~/Desktop$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Recommended packages:
  smbldap-tools
The following NEW packages will be installed:
  samba
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 0B/3338kB of archives.
After unpacking, 8180kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 102945 files and directories currently installed.)
Unpacking samba (from .../samba_3.0.24-2ubuntu1_i386.deb) ...
Setting up samba (3.0.24-2ubuntu1) ...
 * Starting Samba daemons...                                                                                                                                                                  [ OK ] 

dbott@feisty:~/Desktop$ 

```

10 seconds later, I try pinging "feisty" from Windows XP and get:
```
C:\Windows>ping feisty

Pinging feisty [192.168.1.106] with 32 bytes of data:

Reply from 192.168.1.106: bytes=32 time=2ms TTL=64
Reply from 192.168.1.106: bytes=32 time=1ms TTL=64
Reply from 192.168.1.106: bytes=32 time=1ms TTL=64
Reply from 192.168.1.106: bytes=32 time=1ms TTL=64

Ping statistics for 192.168.1.106:
      Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
      Minimum = 1ms, Maximum = 2ms, Average = 1 ms
```

With winbind installed on Ubuntu, I can ping Windows (aka [COLOR=Blue]omega-xp[/COLOR])by hostname as well:
```
dbott@feisty:~/Desktop$ ping omega-xp -c 4
PING omega-xp (192.168.1.105) 56(84) bytes of data.
64 bytes from 192.168.1.105: icmp_seq=1 ttl=128 time=2.47 ms
64 bytes from 192.168.1.105: icmp_seq=2 ttl=128 time=1.87 ms
64 bytes from 192.168.1.105: icmp_seq=3 ttl=128 time=6.76 ms
64 bytes from 192.168.1.105: icmp_seq=4 ttl=128 time=1.83 ms

--- omega-xp ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 15079ms
rtt min/avg/max/mdev = 1.838/3.238/6.761/2.049 ms

```

With winbind removed:
```
dbott@feisty:~/Desktop$ sudo apt-get remove winbind
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  winbind
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
Need to get 0B of archives.
After unpacking, 4801kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 102987 files and directories currently installed.)
Removing winbind ...
 * Stopping the Winbind daemon winbind                                                                                                                                                        [ OK ] 

dbott@feisty:~/Desktop$ ping omega-xp
ping: unknown host omega-xp

```

Hope this clarifies things.

-Dave

---

### Post by ehertlein on 2007-04-26
This does clarify things. Thank you very much. Everything is working just peachy now.

---

### Post by dbott67 on 2007-04-26
Glad to hear it.

If you edit your first post & click "ADVANCED" you can mark this thread as "Resolved".

-Dave

---

