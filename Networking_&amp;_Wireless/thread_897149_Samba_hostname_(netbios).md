---
title: "Samba hostname (netbios)"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by liquidcable on 2008-08-21
I'm trying to configure my server running samba with a hostname / netbios name, but from a windows machine I can only browse share via the IP address.

I'm using the 8.04.1 server install.

/etc/samba/smb.conf
```

[global]
workgroup = lab
netbios name = cerebro2
wins support = yes
server string =
domain master = no
preferred master = yes
max protocol = NT
ldap ssl = No
server signing = Auto

printcap name = cups
printers = cups

security = user
encrypt passwords = yes
smb password file = /etc/samba/smbpasswd
username map = /etc/samba/smbusers
interfaces = lo eth1 eth0
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
hosts deny = 0.0.0.0/0
hosts allow = 127.0.0.1 192.168.0.0/24

create mask = 0770
force create mode = 770
directory mask = 770
force directory mode = 770

force group = holcomb

```

/etc/hostname
```

cerebro2

```

---

### Post by Iowan on 2008-08-21
[Post #12]("http://ubuntuforums.org/showthread.php?t=888290") May not help - try it and let me know.

Be aware:> **dmizer said:**
> Be careful with this.  The order DOES make a difference.  You need to make sure that wins is before dns in this line.  This is a show stopper for some people. Still, I think the Firestarter issue is an entirely different problem.

---

### Post by dmizer on 2008-08-21
For a samba server to allow host name resolution you'll need three things on the server:
1) workgroup option set (you have done this)
2) netbios name option set (you have also done this)
3) name resolve order option set (you have not done this)

Just add this option to your /etc/samba/smb.conf file under the Global options:
```
name resolve order = hosts wins bcast
```

Also, remove the "wins support = yes" option, as this option is only needed if the samba server is also the wins server (any windows machine always acts as its own wins server).

---

### Post by liquidcable on 2008-08-22
It wasn't the name resolve order option.  I also restored the default ubuntu smb.conf file and restarted the samba service, and it still does not show up in browsing (either with Dolphin, Nautilus, or Network Neighborhood).

So from this I'll have to assume it is something other than Samba or the samba configuration file.

---

### Post by liquidcable on 2008-08-22
Ok, I figured it out.  I had to reboot the Ubuntu server.  There must have been a non-samba service running messing something up.  It seems to be working now, and when I make changes now I don't have to reboot I just have to restart the samba service.

[update]
Well that was premature.  I can browse from Windows but not from Ubuntu.

---

### Post by dmizer on 2008-08-22
Browing from ubuntu will require the configuration of /etc/nsswitch.conf, and the installation of winbind.

In /etc/nsswitch.conf, look for the line that says something like:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```
Add "wins" to the line in front of "dns" so it looks something like this:
```
hosts:          files mdns4_minimal [NOTFOUND=return] [COLOR="Red"]wins[/COLOR] dns mdns4
```
The order here is important.

Once thats done, install winbind:
```
sudo aptitude install winbind
```

If you still cannot browse by name, please post the output of:
```
sudo iptables -L
```

---

### Post by liquidcable on 2008-08-22
Using winbind doesn't seam to work (browsing under linux), ie no change.


sudo iptables -L yields the following : 
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

He is my current smb.conf
```

[global]                                                                                                                                                                                             
        netbios name = cerebro2 
        workgroup = lab
        server string =
        security = user
        interfaces = lo, eth0
        map to guest = Bad User
        username map = /etc/samba/smbusers
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
        printcap name = cups

        domain master = Yes
        preferred master = Yes
        local master = Yes
        preferred master = Yes
        wins support = Yes
        os level = 255

        force group = holcomb
        create mask = 0770
        force create mode = 0770
        directory mask = 0770
        force directory mode = 0770

        hosts allow = 127.0.0.1, 192.168.0.0/24
        hosts deny = 0.0.0.0/0

```

---

### Post by dmizer on 2008-08-22
smb.conf does not influence Ubuntu > Windows name resolution.  It ONLY handles Windows > Ubuntu.

However, in this case you're smb.conf does not have any shares listed which may be why Windows cannot browse to it.

---

### Post by liquidcable on 2008-08-22
Windows can browse just fine.  My other two Ubuntu systems can not.  I've tired Gnomes nautilus and KDE's Dolphin.  If I stop the samba service on the server, then the other two Ubuntu systems can "see" each other under smb browsing (Nautilus or Dolphin).

---

### Post by dmizer on 2008-08-23
Is your network static or DHCP?  If it is DHCP and since there is a Windows computer on your network, you should remove this option:
```
wins support = Yes
```

This option may be preventing you from browsing your Windows machines. Here's why from man smb.conf:
>         [noparse]  wins support (G)
             This boolean controls if the nmbd(8) [/noparse]process in Samba will act as
             a  WINS  server. [COLOR="Red"]You should not set this to yes unless you have a
             multi-subnetted network and you wish a particular nmbd to be your
             WINS  server.[/COLOR]  Note that you should NEVER set this to yes on more
             than one machine in your network.

             Default: wins support = no

I have seen at least [one other person](http://ubuntuforums.org/showpost.php?p=5633912&postcount=11) who resolved their network browsing problems by adding this option to smb.conf:
```
name resolve order = hosts wins bcast
```

Edit:
Post 8 and 9 in this thread suggest starting the "server" service in Windows services manager: [http://ubuntuforums.org/showthread.php?t=852029](http://ubuntuforums.org/showthread.php?t=852029)

Edit 2:
Here's another potential solution that was posted today: [http://ubuntuforums.org/showpost.php?p=5647890&postcount=10](http://ubuntuforums.org/showpost.php?p=5647890&postcount=10)
> **simplr said:**
> I found that the Windows shares, except for Windows 3.11, worked correctly in the Places->Network after adding the IP address of one of the Windows computers in System->Administration->Network->DNS->SearchDomains.

This same fix could be accomplished by deleting these options:
```
        domain master = Yes
        preferred master = Yes
        local master = Yes
        preferred master = Yes
        wins support = Yes
        os level = 255
```

and adding this option to your smb.conf file:
```
wins server = ip.of.windows.comp # This may also work if you use your router IP instead.
```

The problem with the way you have things set up now is that your Ubuntu computer thinks it is the domain master, so in order to resolve names correctly with this configuration it needs to have a properly configured winbind server, where /etc/hosts is datafilled with all the names and IP addresses of all the computers on your network.

This will only work if your network is static.

---

### Post by liquidcable on 2008-08-23
Windows browsing works fine.  Linux (Ubuntu) samba browsing does not work.  All system get IP via DHCP router (Linksys).

The suggestions by dmizer have not worked.

FYI.. I just moved my server from Gentoo to Ubuntu, and I didn't have this much trouble getting Samba up and running under Gentoo.  Very weird, because everything else is much easier to setup under Ubuntu.

---

### Post by liquidcable on 2008-08-23
If I turn off the samba service on the server (the problem system), then my other two Ubuntu systems can browse and "see" each other.  It's is something with the Ubuntu sever.

---

### Post by dmizer on 2008-08-23
> **liquidcable said:**
> Windows browsing works fine.  Linux (Ubuntu) samba browsing does not work.  All system get IP via DHCP router (Linksys).

The suggestions by dmizer have not worked.

FYI.. I just moved my server from Gentoo to Ubuntu, and I didn't have this much trouble getting Samba up and running under Gentoo.  Very weird, because everything else is much easier to setup under Ubuntu.

So please post your /etc/samba/smb.conf file as it is currently.

What is the output of:
```
smbtree
```

---

### Post by liquidcable on 2008-08-23
I added entires to /etc/hosts on each machine, I should not have to do this but now I can mount via the netbios/host name now.

I suggest using testparm, as it appears to test your configuration file and omit the useless parameters and can generate the correct output (via stdout). 

My current smb.conf, checked with testparm (I manually added back in the netbios name):
```

[global]
        netbios name = cerebro2
        workgroup = LAB
        server string =
        interfaces = lo, eth0
        map to guest = Bad User
        username map = /etc/samba/smbusers
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
        printcap name = cups
        wins support = Yes
        force group = holcomb
        create mask = 0770
        force create mode = 0770
        directory mask = 0770
        force directory mode = 0770
        hosts allow = 127.0.0.1, 192.168.0.0/24
        hosts deny = 0.0.0.0/0

[heath]
        path = /server/raid/heath
        read only = No
        case sensitive = No

[monica]
        path = /server/raid/monica
        read only = No
        case sensitive = No

[video]
        path = /server/raid/video
        read only = No
        case sensitive = No

[deskjet]
        comment = printers
        path = /var/spool/samba
        guest ok = Yes
        printable = Yes
        printer name = deskjet
        use client driver = Yes

```

---

### Post by liquidcable on 2008-09-01
Warning, just a rant.

OMFG!!  I have never had this much trouble setting us samba on a Linux server before (redhat, suse, gentoo).  I don't know what Ubuntu server has done, but it sucks.  I'm got near the exact setup at work (much larger) with the samba server under Ubuntu Desktop 8.04; while at home Ubuntu Server 8.04 just doesn't work.

---

### Post by gpsmikey on 2008-09-27
for what it's worth, I have seen a number of users posts recently with browsing problems that were solved by removing (or commenting out) the "force group= " line in the config file.  I don't completely understand yet, but there have been quite a few posts where that has allowed it to work.  Give it a shot.

mikey

---

### Post by gregphil on 2008-09-27
You might look into the "host allow" and "hosts deny" as well, the ubuntu folks seem to have decided to use more than 127.0.0.1 as "localhost"  (specificlly 127.0.1.1)

You could try hosts allow = 127.0.0.0/24

---

