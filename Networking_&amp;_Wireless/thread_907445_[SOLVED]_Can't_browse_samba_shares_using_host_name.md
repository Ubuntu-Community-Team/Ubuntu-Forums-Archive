---
title: "[SOLVED] Can't browse samba shares using host names."
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by nikkko on 2008-09-01
Hi all.

I'm trying to browse shared folders using host names without success. 

I browse Workgroups and computers names but nothing happen when i open a folder.

If i type the IP address instead the host works.

I'm using the default smb.conf file, i just change the WORKGROUP var.

Any idea? There is a lot of computers at work, and is really heavy to deal with IPs all the time.

Thanks, and excuse my basic english.

**Edit:** I also changed the 'security' to 'security = share' so i can use usershares. And that is another thing, Windows users can browse my shared folders using the hostname or IP.

--
Nico

---

### Post by bab1 on 2008-09-01
This sounds like a name resolution problem (DNS).  I don't believe this is a samba problem.  Can you ping by name other **local** hosts from the command line?

---

### Post by nikkko on 2008-09-02
No, i can't ping hostnames. It tries to resolve it like a web domain.

Yes, it seems to be a network setting (that i'm missing)


**My network setup from Network Manager:**

**- Connection:** Roaming mode enabled.

**- General:**
* Hostname: maya
* Domaing name: (empty)

**- DNS:**
* Dns server: 192.168.1.1
* Search domains: (none)

Any idea?

*Thanks*

---

### Post by dracvs on 2008-09-02
> **nikkko said:**
> No, i can't ping hostnames. It tries to resolve it like a web domain.

Yes, it seems to be a network setting (that i'm missing)


**My network setup from Network Manager:**

**- Connection:** Roaming mode enabled.

**- General:**
* Hostname: maya
* Domaing name: (empty)

**- DNS:**
* Dns server: 192.168.1.1
* Search domains: (none)

Any idea?

*Thanks*

if you are inside a network (or else you would'nt be using samba) try: 

```
smb://hostname/nameofthefolder
```

I have found something like this when trying to connect from Ubuntu 8.04 to any flavor of windows.

Could you specify what version of Ubuntu are you using?

8.04 has a problem with GVFS (they changed the file system from VFS) meanwhile 8.4.1 ...solved it partially. And if the folder is not shared properly on the host server Our Dear ubuntu is deaf and blind.

---

### Post by nikkko on 2008-09-02
smb://hostname/nameofthefolder <-- Yes, that is exactly the problem

hehe, yes.. the folders are ok, everybody else can browse them.. except by me :(

I'm using 7.10, and i think it uses VFS.

Thanks,

--
Nico

---

### Post by nikkko on 2008-09-02
Maybe this can help: 

```
daniel@maya:~$ nbtscan 192.168.1.100-110
Doing NBT name scan for addresses from 192.168.1.100-110

IP address       NetBIOS Name     Server    User             MAC address      
------------------------------------------------------------------------------
192.168.1.104    MAYA             <server>  MAYA             00:00:00:00:00:00
192.168.1.100    TRABAJO          <server>  TRABAJO          00:13:8f:aa:e6:24
192.168.1.105    MARDAK           <server>  MARDAK           00:1e:4c:23:58:00
192.168.1.101    ANDREA           <server>  <unknown>        00:02:55:2a:0f:02
daniel@maya:~$
```


00:00:00:00:00:00 about my pc???? :confused:

---

### Post by bab1 on 2008-09-02
Windows stopped using NETBIOS with W2k. You do not need to use NETBIOS to resolve hostnames when using Samba.  

You do need to **configure DNS** for your hosts.  DNS is an important part of your network configuration.

I see that you have designated 192.168.1.1 as your DNS server.  I'm guessing this is your router.  I use my router the same way.  I use static addresses in my network so I just map the name to the IP address.  If you use DHCP for IP addressing you will need to research how to configure your DHCP client on each host to use the what you want as a hostname for that machine.

---

### Post by nikkko on 2008-09-02
Thanks for your answer.

yes, we use DHCP.. i found that adding:

```
send host-name "maya";
```

to **/etc/dhcp3/dhclient.conf** sets the hostname correctly.

I spoke with the admin(not very linux-friendly guy :() (there is normally ~25 computers on network) and he told me that yes, the host is "maya", not empty anymore.

But that doesn't help a lot, i still can't resolve the hostnames :(

As i said, 'my' host isn't the problem: 'They' can browse my computer, but i can't do the same with the rest of the network.

---

### Post by bab1 on 2008-09-02
Can you ping your own host (maya) by name?  If I understand correctly, you have set the hostname and are using DHCP.  Have you setup DNS?  Is your DNS server 192.168.1.1?  Do you manage it?  what does this mean:> ...and he told me that yes, the host is "maya", not empty anymore

---

### Post by nikkko on 2008-09-02
```
daniel@maya:~$ ping maya -c 1
PING maya (127.0.1.1) 56(84) bytes of data.
64 bytes from maya (127.0.1.1): icmp_seq=1 ttl=64 time=0.042 ms

--- maya ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.042/0.042/0.042/0.000 ms
daniel@maya:~$
```

Yes i can.

Yes, the nameserver is 192.168.1.1. And i don't manage it at all.

> **bab1 said:**
>  what does this mean:
That's mean: on the name server/router/dhcp server, or whatever it calls it shows that my hostname is 'maya' (correctly).

---

### Post by bab1 on 2008-09-02
Have the other hosts been added to DNS?  Can you ping them?

---

### Post by gregphil on 2008-09-02
I believe this is because Ubuntu and kubuntu have basic peer-to-peer file sharing broken. (it use to work in earlier disto's) 

With Samba setup correctly, make sure your /etc/hosts has lines like (note the WORKGROUP on end of the 127.0.1.1 line):

127.0.0.1 localhost
127.0.1.1 LIVING-ROOM.MYGROUP
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
etc

AND (very important) set the network "domain" to the WORKGROUP you are trying to browse (in my case MYGROUP) then after about 10 minutes (the browse master updates slowly) I will be able to do the command line

smbtree

and "see" all the sahres on my network, both windows boxes and Linux boxes

I can querry each one with (for example)

smbclient -L LIVING-ROOM

However there are two problems here.  In both ubuntu and kubuntu the "domain" does not persist across reboots and must be reset each time.  Further with the Kubuntu GUI I can browse the shares while under ubuntu (gnome) the network browser fails as you report above, it shows the computers with shares but will not let you expand the shares. (as root or otherwise)

Does ANYONE have a solution for this?  I just want basic peer-to-peer (no server, no specific machine must be running) sharing to work.  I can make it work on CentOS 5.2 using KDE....

---

### Post by nikkko on 2008-09-03
> **bab1 said:**
> Have the other hosts been added to DNS?  Can you ping them?

No, i can't. Add where? The problem here isn't other hosts, they can browse and ping all the hosts on the network.

**Other hosts can also ping and browse my shared folders**

Yes gregphil, that is exactly my problem: **local network hosts doesn't resolve for Samba**

---

### Post by bab1 on 2008-09-03
I believe that you need to configure your networking settings to include your local DNS server.  See your sys admin for advice.

---

### Post by nikkko on 2008-09-03
> **bab1 said:**
> I believe that you need to configure your networking settings to include your local DNS server.  See your sys admin for advice.
Then i don't understand how the others computers resolve all hosts fine.. but i can't

---

### Post by Kelen.Chang on 2008-09-03
hey, guy, your problem seem like this, going to try this way.
[http://ubuntuforums.org/showthread.php?t=909020](http://ubuntuforums.org/showthread.php?t=909020)

---

### Post by nikkko on 2008-09-03
> **Kelen.Chang said:**
> hey, guy, your problem seem like this, going to try this way.
[http://ubuntuforums.org/showthread.php?t=909020](http://ubuntuforums.org/showthread.php?t=909020)

**Thanks! Thanks! Thanks!** You are my new Ubuntu-God!

It Works!!!

The only difference was to change the order of hosts in */etc/nsswitch.conf* (wins first):

```
hosts: files mdns4_minimal [NOTFOUND=return] wins dns mdns4 
```

And thanks all for the replies and suggestions.

SOLVED! :):):):)

---

