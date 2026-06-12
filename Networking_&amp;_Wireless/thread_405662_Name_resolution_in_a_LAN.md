---
title: "Name resolution in a LAN"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by joslinar on 2007-04-10
I recently converted to Ubuntu. I'm getting rid of XP in my PCs ( Yeah, I saw the light!!!) I have a linksys WRT54GL router and I want to network my Ubuntu PCs. I would like to able to conect to an Ubuntu PC without knowing the IP address, I would like to connect just using the host name.
If i try to ping directly the name of a linux (ex. ping guatek) host ubuntu can't find it. But if I try to ping an XP host it will find the ip address.  If I go to the router DHCP tables windows clients have  host name and ip address listed but linux clients only have IP addresses in the table. Why is this and how can I resolve it? I don't want to maintain /etc/host files. How XP does this without a DNS server?

---

### Post by Blyzzard on 2007-04-16
I ahve the same problem i think

i have 3 PCs on my network.

1. Friend next door(XP pro)
2. My Gaming PC (XP pro)
3. TS (and movie) server (Ubuntu 6.06)

The main thing I want to be able to do is us Teamspeak on my PC to talk to my friend next door. now i know that the server address is 192.168.0.9, but I REALLY want to be able to connect to the PC name (avalanche) instead of the IP address.

So i imagine that it's some sort of name resolution that has to occur somewhere.

Additionally, I use VNC to connect to the ubuntu server and I have to use the ip address instead of the PC name. Would be nice to use the name instead.

Ideas anyone?

---

### Post by dbott67 on 2007-04-16
You need to install the following packages from the repos:

```
 sudo apt-get install smbfs smbclient winbind
```[U][B]BACKGROUND

[/B][/U] (This is from another thread that I posted in regarding local name resolution. The full thread is for here: [http://www.ubuntuforums.org/showthread.php?p=1770797#post1770797](http://www.ubuntuforums.org/showthread.php?p=1770797#post1770797))

... some issues arise because of the way SMB shares "announce" themselves to the network. Generally, connecting via IP address works properly, but browsing by 'computer name' can occasionally fail. Windows uses WINS service to allow users to browse by computer name (also known in Windows-speak as Netbios name). WINS binds the computer name to the IP address. For the most part, this has been superceded by DNS, which binds the fully-qualified domain name to the IP address. The problem is that DNS resolution requires that:

a) You're running a DNS server (locally)
b) Each client is registered in the DNS server

The problem here is that most people don't run their own DNS server at home and if you have any Windows computers on the network (or Samba shares), you really should have a WINS server installed.

There is a package in the repositories called 'winbind' that is a service that resolves user and group information on NT-based networks and also allows you to browse by computer name.

This info is provided by 'featherking' from [this thread]("http://www.ubuntuforums.org/showthread.php?t=288022"): 

```
sudo gedit /etc/nsswitch.conf
```find this line (it may not be exactly that)

```
hosts:          files dns mdns
```and add wins, so now it looks like

```
hosts:          files dns mdns wins
```then install winbind
```

sudo apt-get install winbind
```The advantage to using winbind vs. static IPs is that I can add/remove PCs without worrying about editing the hosts file. There are also a few tools that can aid in discovery:
```
dbott@thedrake:~$ sudo smbtree
Password:
WORKGROUP
        \\THEDRAKE                      thedrake server (Samba, Ubuntu) *[COLOR=Blue]<--- My Dapper desktop[/COLOR]*
                \\THEDRAKE\ADMIN$               IPC Service (thedrake server (Samba, Ubuntu))
                \\THEDRAKE\IPC$                 IPC Service (thedrake server (Samba, Ubuntu))
                \\THEDRAKE\dbott
                \\THEDRAKE\print$               Printer Drivers
        \\PIII-600 [COLOR=Blue]*<--- the kids XP PC; no firewall; no shares*[/COLOR]
        \\OMEGA-XP [COLOR=Blue]*<--- My laptop; Running XP firewall*[/COLOR]
Error connecting to 192.168.1.105 (No route to host)
cli_start_connection: failed to connect to OMEGA-XP<20> (192.168.1.105)
        \\NAS-160GB [COLOR=Blue]*<--- My NAS device*[/COLOR]
                \\NAS-160GB\IPC$
                \\NAS-160GB\Videos
                \\NAS-160GB\Music
                \\NAS-160GB\Archive
                \\NAS-160GB\Data
                \\NAS-160GB\PUBLIC
        \\JBOTT-PC [COLOR=Blue]*<--- My wife's laptop; Running Vista firewall; no open shares*[/COLOR]
timeout connecting to 192.168.1.101:445
timeout connecting to 192.168.1.101:139
Error connecting to 192.168.1.101 (Operation already in progress)
cli_start_connection: failed to connect to JBOTT-PC<20> (192.168.1.101)
dbott@thedrake:~$

```All of the discovered data is stored in **var/cache/samba/browse.dat**:
```
dbott@thedrake:~$ cat /var/cache/samba/browse.dat
"WORKGROUP"               c0001000 "THEDRAKE"                    "WORKGROUP"
"THEDRAKE"                40059a03 "thedrake server (Samba, Ubuntu)" "WORKGROUP"
"NAS-160GB"               40412003 ""                            "WORKGROUP"
"OMEGA-XP"                40011203 ""                            "WORKGROUP"
"JBOTT-PC"                40001003 ""                            "WORKGROUP"
"PIII-600"                40011003 ""                            "WORKGROUP"

```After installing samba, winbind & smbfs, you need to configure samba.  Please read this document:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

-Dave

---

