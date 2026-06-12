---
title: "Hostnames on LAN"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by KAding on 2007-05-15
Hello everyone,

This post is not about hostname resolve problems between windows and linux boxes. Even if I only run ubuntu boxes on my LAN they are unable to ping eachother by using the hostname. Windows boxes can ping both linux and windows boxes. I assume this is because it is using Netbios and I'm running samba on the linux boxes.

But anyway, I have a US Robotics 8054 wireless router. It is running as a DHCP server as well. The DHCP table lists the hostnames correctly. The DNS on my ubuntu boxes is also automatically set to the router IP 192.168.0.10.

Yet, for some reason the linux computers can't resolve eachothers hostnames.  So whats going on? Is the router DNS faulty or something?

This shouldn't be a /etc/nsswitch.conf problem, right? Since the router should handle the resolving using DNS? No winbind crap necessary? The nsswitch.conf file shows the following btw:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```

So in short:
1. Router acts as DHCP server and handles DNS
2. Ubuntu boxes receive IP through DHCP and have the router IP as DNS 
3. Router lists the hostnames and IPs in the DHCP table
4. Yet, ubuntu boxes won't resolve any host names on the LAN (internet works fine)
5. Windows boxes resolve all hostnames just fine (because they don't use dns to resolve the hostnames)

Any ideas?

Btw, this is on feisty.

---

### Post by gfowler on 2007-05-15
> **KAding said:**
> Hello everyone,

This post is not about hostname resolve problems between windows and linux boxes. Even if I only run ubuntu boxes on my LAN they are unable to ping eachother by using the hostname. Windows boxes can ping both linux and windows boxes. I assume this is because it is using Netbios and I'm running samba on the linux boxes.

But anyway, I have a US Robotics 8054 wireless router. It is running as a DHCP server as well. The DHCP table lists the hostnames correctly. The DNS on my ubuntu boxes is also automatically set to the router IP 192.168.0.10.

Yet, for some reason the linux computers can't resolve eachothers hostnames.  So whats going on? Is the router DNS faulty or something?

This shouldn't be a /etc/nsswitch.conf problem, right? Since the router should handle the resolving using DNS? No winbind crap necessary? The nsswitch.conf file shows the following btw:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```

So in short:
1. Router acts as DHCP server and handles DNS
2. Ubuntu boxes receive IP through DHCP and have the router IP as DNS 
3. Router lists the hostnames and IPs in the DHCP table
4. Yet, ubuntu boxes won't resolve any host names on the LAN (internet works fine)
5. Windows boxes resolve all hostnames just fine (because they don't use dns to resolve the hostnames)

Any ideas?

Btw, this is on feisty.

If the router by default setsthe domain to .local there may be the rub.  Fiesty and avahi do not like to work well in .local domains   Change or comment out the host line in your nsswitch in one of your ubuntu machines to 'hosts   files dins mdns4' (sans the quotes). and see if you can ping by host names.

If not, it is a blown fuse or something else, my bet on the latter!:) 
Jerry

---

### Post by merlinus on 2007-05-15
Don't know if this will work for you, but I resolved this problem by assigning static IP addresses to the computers on my LAN.

Everything works perfectly, and no problems with Internet access.

I am using ssh-server.

-merlin

---

### Post by dannyboy79 on 2007-05-15
i am gonna bet that your router is not a true dns server. most home routers are only dns forwarders so this is always a problem for internal name resolution. the reason that windows machines work is because you're right, they are broadcasting their names to each other and to the linux boxes, so you eirther need to install a full dns server or use the hosts file to associate your hosts to an ip address. I have written up a very good explaination of resolving hostnames in linux versus windows. check it out:

[http://ubuntuforums.org/showthread.php?t=391601&highlight=resolution](http://ubuntuforums.org/showthread.php?t=391601&highlight=resolution)

---

### Post by KAding on 2007-05-16
Thanks for all the replies. I think dannyboy79 is right, the router is not really a DNS server, it merely forwards to the ISP DNS server.

The solution of installing a DNS server is basically out of the question, since that would mean I would have to have one of my computers running permanently as DNS server.

The other solution of using static IPs gives two problems though. Firstly, three of the computers on the network are laptops. These are laptops that also frequently connect to other LANs (university and parents house for example). Setting a static IP is just too cumbersome then? Another problem is that if I set the hosts for one network in the /etc/hosts file it might cause problems when I connect to another network. Two of the networks I connect to use the same IP range, which means that hostnames in the /etc/hosts file might make sense on one network but not the other. I suppose I should use different IP ranges to solve that problem.

A shame that there isn't a more elegant solution that doesn't rely on somekind of permanent DNS server or rather rigid static IPs. I hate to say this, but the windows approach certainly does seem more flexible :p. I guess I'll just have to deal with it.

Btw, I assume there are routers that do act as true DNS servers and also resolve hostnames on the LAN? Any brands in particular that support this?

Thanks for the help anyhow. Much appreciated.

---

### Post by dannyboy79 on 2007-05-16
well according to here: [http://www.geocities.com/rlcomp_1999/hostname.html](http://www.geocities.com/rlcomp_1999/hostname.html)
you can still use dhcp and have your hostnames be able to be resolved. you would just add a hostname line in your interfaces file. OR you could always make your ubuntu box the dhcp server instead of your router. that way your ubuntu box will always hand out the same ip to the same MAC address each time and this way you could add each of the machine's and their respective ip's to each of the hosts files on all the computers. OR, what if you just use a WINS server?

I know my netgear router has an option to always hand out the same ip address based on the MAC address so this way, you know for sure that your laptops will always receive the same ip from your router at home at least. I know this would be a half assed aproach but you could add the static dhcp ip in your hosts file within ubuntu but then also have another hosts file that you can use when you take your laptop elsewhere, just name them

hosts-home
hosts-away

and then just use 

sudo cp /etc/hosts-home /etc/hosts
sudo /etc/init.d/networking restart
when you leave get home and then
sudo cp /etc/hosts-away /etc/hosts
sudo /etc/init.d/networking restart

othewise I am not sure how else to help you.I think that adding the hostname thing to the interfaces thing is the best bet because then when you're out and about and your computer requests an ip frmo the dhcp server it'll also register that hostname with it. (wouldn't it?) I mean, come on, think about it, you can't be the first person that wants to use DHCP and be able to resolve hostnames in Linux on a laptop. also, you could check out dhclient.conf to see what is all be requested from the dhcp server. good luck

---

### Post by KAding on 2007-05-16
Thanks for the help. It certainly much clearer for me now.

I'll figure something out based on your suggestions.

---

### Post by dannyboy79 on 2007-05-16
please post back so that others can get help with linux hostname resolution and dhcp. I might actually just create a new thread using that as the title. or you could once you figure it out.

---

### Post by swoskow on 2007-05-18
> **dannyboy79 said:**
> please post back so that others can get help with linux hostname resolution and dhcp. I might actually just create a new thread using that as the title. or you could once you figure it out.

I am having the same probems - so yes please post back how you worked this out.  It would be very helpful.

Thank you

---

### Post by dannyboy79 on 2007-05-18
well I provided him with plenty of solutions, have you tried any of them? are you using static ip's or dhcp?

---

### Post by swoskow on 2007-05-18
I am in the process of working through it now.  I am resetting all my computers (names, static IP etc) now following your guide.  Thanks so much for jumping in to help.  

Just for background:
  I have 5 computers I want to network (this is a home network). At this time I have 2 desktops (one running Ubuntu, one on Windows XP but soon to be dual boot with Ubuntu).  Both have static IP.
  2 laptops - 1 windows (and it will stay windows - this is for work so it does not really need to be on the network) and 1 older laptop with Ubuntu.
  and finally - 1 Mac

I can get all the windows computers to remote connect and I can get the ubuntu desktop to remote connect to the windows computers but not visa versa.

I may try just getting 2 comuters hooked up first then tackle all the others- I would start with the desktops since I already have static ip's set up.

I will check back with questions I will certainly have.  I will read through the guide an use it - it looks straightforward.

---

### Post by dbott67 on 2007-05-18
There are 2 essential ingredients to make this work (from Windows to Linux & vice-versa): [B]samba & winbind

[/B]1. Install **samba, smbclient, smbfs** and **winbind** [COLOR=Blue]*(I also install smbclient & smbfs so that I can mount smb shares)*[/COLOR]
```
sudo apt-get install samba smbfs smbclient winbind
```2. Edit the **/etc/nsswitch.conf** file
```
sudo gedit /etc/nsswitch.conf
```3. Look for the following line (or similar):
```
hosts:          files dns mdns
```4. Add the word [COLOR=Red]wins[/COLOR]:
```
hosts:          files dns mdns [COLOR=Red]wins[/COLOR]
```5. Restart computer

Once you install & enable **samba** on the Ubuntu machine, the Windows machine will be able to resolve the Ubuntu computer by hostname.  Installing **winbind** on the Ubuntu machine will resolve the Windows machines.

For example, when I remove samba from Ubuntu:
```
dbott@feisty:~/Desktop$ **[COLOR=Red]sudo apt-get remove samba[/COLOR]**
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

```I am unable to ping my Ubuntu computer (aka [COLOR=Blue]feisty[/COLOR]) from an XP computer:
```
C:\Windows>**[COLOR=Red]ping feisty[/COLOR]**
Ping request could not find host feisty.  Please check the name and try again
```Re-installing samba on Ubuntu:
```
dbott@feisty:~/Desktop$ [COLOR=Red]**sudo apt-get install samba**[/COLOR]
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

```10 seconds later, I try pinging "feisty" from Windows XP and get:
```
C:\Windows>[COLOR=Red]**ping feisty**[/COLOR]

Pinging feisty [192.168.1.106] with 32 bytes of data:

Reply from 192.168.1.106: bytes=32 time=2ms TTL=64
Reply from 192.168.1.106: bytes=32 time=1ms TTL=64
Reply from 192.168.1.106: bytes=32 time=1ms TTL=64
Reply from 192.168.1.106: bytes=32 time=1ms TTL=64

Ping statistics for 192.168.1.106:
      Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
      Minimum = 1ms, Maximum = 2ms, Average = 1 ms
```With winbind installed on Ubuntu, I can ping Windows (aka [COLOR=Blue]omega-xp[/COLOR])by hostname as well:
```
dbott@feisty:~/Desktop$ [COLOR=Red]**ping omega-xp -c 4**[/COLOR]
PING omega-xp (192.168.1.105) 56(84) bytes of data.
64 bytes from 192.168.1.105: icmp_seq=1 ttl=128 time=2.47 ms
64 bytes from 192.168.1.105: icmp_seq=2 ttl=128 time=1.87 ms
64 bytes from 192.168.1.105: icmp_seq=3 ttl=128 time=6.76 ms
64 bytes from 192.168.1.105: icmp_seq=4 ttl=128 time=1.83 ms

--- omega-xp ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 15079ms
rtt min/avg/max/mdev = 1.838/3.238/6.761/2.049 ms

```With winbind removed:
```
dbott@feisty:~/Desktop$[COLOR=Red]** sudo apt-get remove winbind**[/COLOR]
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

dbott@feisty:~/Desktop$ [COLOR=Red]**ping omega-xp**[/COLOR]
[COLOR=Red] ping: unknown host omega-xp[/COLOR]

```If you want to be able to connect to shared folders, you need to configure samba and add your Windows XP accounts to samba, where *[COLOR=Blue]username[/COLOR]* is the login name of your Windows XP computer (use the same password for both accounts)
 ```
sudo  smbpasswd -a [COLOR=Blue]*username*[/COLOR]
 
 New SMB password:
 Retype new SMB password:
 Added user username.
```For more information, please read this document:
 
 [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

The advantage to using winbind vs. static IPs is that I can add/remove PCs without worrying about editing the hosts file. There are also a few tools that can aid in discovery:
```
dbott@thedrake:~$ **sudo smbtree**
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

```Hope this helps clarify things.

-Dave

---

### Post by gantengx on 2007-06-07
I tried what dannyboy79 said, but the windows machine cannot get my hostname, it can connect to my local ip address though. 

I can ping the windows machine hostname. 

What did i do wrong?

Here's my smb.conf
```

[global]
workgroup = WORKGROUP
netbios name = GANTENGX
server string = Ganteng 4 Life
wins support = no
dns proxy = no
name resolve order = lmhosts host wins bcast
interfaces = lo eth0
bind interfaces only = true

log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d

security = share
encrypt passwords = true
passdb backend = tdbsam
obey pam restrictions = yes

guest account = nobody
invalid users = root

passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
socket options = TCP_NODELAY

hosts allow = 127.0.0.1 192.168.1.100/24


#======================= Share Definitions =======================

[Multimedia]
        comment = Multimedia
        path = /media/multimedia
        read only = yes
        guest ok = yes
	guest only = yes

```


and my nsswitch.conf file
```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files wins mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

i use static ip and  installed winbind....

---

### Post by dannyboy79 on 2007-06-07
> **gantengx said:**
> I tried what dannyboy79 said, but the windows machine cannot get my hostname, it can connect to my local ip address though. 

installing winbind IF you have a static IP is definitely NOT what I suggested so I don't why you thought that's what I wrote but I didn't.

Oddly enough, now that I upgraded to Feisty I am having an issue with smbtree command. Maybe some1 can help me for once. This is what it returns:

LINUX
        \\UBUNTU                        Dans Linux Desktop
timeout connecting to xxxxxxxxxxx:445
timeout connecting to xxxxxxxxxxxx:339
Error connecting to xxxxxxxxxxxx (Operation already in progress)
cli_start_connection: failed to connect to UBUNTU<20> (xxxxxxxxxxx)

What's very weird is that I don't understand why it's using the external IP, (i put x's instead of the IP for obvious reasons) does this have something to do with my hosts file maybe? I do have a FQDN (Fully Qualified Domain Name) registered with dyndns. I used the same exact smb.conf as when I had everything working great in Dapper. The hosts file is a little different based on an article I read. 
**UPDATE**: the above error only happens when I run smbtree from the Ubuntu machine itself (this is what I want to be the Local Master Browser), the error didn't happen when I ran the smbtree command from my Gutsy Xubuntu Dell machine, so maybe that's normal?

This is what my hosts file looks like:
127.0.0.1 localhost localhost.localdomain UBUNTU.getmyip.com
127.0.1.1 UBUNTU.getmyip.com

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.0.4 WINXP
192.168.0.5 XUBUNTU-FIESTY
192.168.0.3 UBUNTU.getmyip.com

and my smb.conf file
    netbios name = UBUNTU
    server string = Dans Linux Desktop
    workgroup = LINUX
    encrypt passwords = true
#    guest ok = yes
    smb passwd file = /etc/samba/smbpasswd
    domain master = yes
    local master = yes
    preferred master = yes
    os level = 99
    idmap uid = 10000-20000
    idmap gid = 10000-20000
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
#   passdb backend = tdbsam
    null passwords = true
    username map = /etc/samba/username.map
#   name resolve order = wins lmhosts host bcast
    hosts allow = 127.0.0.1 127.0.1.1 192.168. EXCEPT 192.168.0.20
    hosts deny = 0.0.0.0/0
#   hostname lookups = yes
#   hosts equiv = /etc/samba/lmhosts
#   map to guest = Bad User
#   guest account = nobody
#   wins support = yes
#   smb ports = 139
    browse list = yes
    mangled names = yes
    default case = lower
    case sensitive = no
    preserve case = yes
    short preserve case = yes

#global logging
    syslog = 1
    syslog only = yes

#global printing settings
    printing = CUPS
    printcap name = CUPS

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
wins support = no

[homes]
    valid users = daniel root
    create mode = 0600
    directory mode = 0755
    browseable = no
    read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.

[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = yes

; Uncomment if you need to share your CD-/DVD-ROM Drive                                                              [ ok ]
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

;These are private shares that only
[UBUNTUFILES]
    path = /home/daniel

    read only = no
    guest ok = no
    valid users = %U root
    create mask = 0644
    directory mask = 0755
    force user = daniel
    force group = daniel
    available = yes
    public = no
    writable = yes

browsable = no
;These are shares that everyone can access, even guests

[500gb]
path = /media/500gb
comment = 500gb on Ubuntu
available = yes
browsable = yes
public = yes
writable = yes
guest ok = yes
force user = daniel
force group = daniel

[MYTHTV Recordings]
path = /media/400gb/mythtv
comment = MythTV Recordings
available = yes
browsable = yes
public = yes
writable = yes
guest ok = yes
force user = daniel
force group = daniel

[fat32]
path = /media/fat32
comment = Fat32 on Ubuntu
available = yes
browsable = yes
public = yes
writable = yes
guest ok = yes
force user = daniel
force group = daniel


hostname command returns:
UBUNTU
and dnsdomainname -v returns:
dnsdomainname -v
getmyip.com
and then of course the command, hostname --fqdn returns:
UBUNTU.getmyip.com
My nsswitch.conf file is stock, meaning it still looks like this:
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

Because I don't want to use wins. It doesn't have any rules for iptables -L

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

So I am at a lose? Also, another weird occurance is that I can't ssh into my Xubuntu Laptop anymore, I get a, no route to host error? I made sure there are no firewall rules on that box either, any suggestions? I will say this, everything works however, when all my machines are on, my xbox's, my Xubuntu Laptop, my newly acquired Dell Dimension 8200 with Xubuntu Gutsy, my WinXP Pro, and my Ubuntu Feisty Server/Desktop, I can connect to each of the machines, I can stream using XBMC from any machine that is sharing folders etc etc, it's just this weird smbtree error. 

OH YEAH, I also see this in the logs constantly: 
Jun  6 20:52:53 UBUNTU smbd[1781]: [2007/06/06 20:52:53, 0] lib/util_sock.c:get_peer_addr(1229)
Jun  6 20:52:53 UBUNTU smbd[1781]:   getpeername failed. Error was Transport endpoint is not connected
Jun  6 20:52:53 UBUNTU smbd[1781]: [2007/06/06 20:52:53, 0] lib/util_sock.c:get_peer_addr(1229)
Jun  6 20:52:53 UBUNTU smbd[1781]:   getpeername failed. Error was Transport endpoint is not connected
Jun  6 20:52:53 UBUNTU smbd[1781]: [2007/06/06 20:52:53, 0] lib/access.c:check_access(327)
Jun  6 20:52:53 UBUNTU smbd[1781]: [2007/06/06 20:52:53, 0] lib/util_sock.c:get_peer_addr(1229)
Jun  6 20:52:53 UBUNTU smbd[1781]:   getpeername failed. Error was Transport endpoint is not connected
Jun  6 20:52:53 UBUNTU smbd[1781]:   Denied connection from  (0.0.0.0)
Jun  6 20:52:53 UBUNTU smbd[1781]: [2007/06/06 20:52:53, 0] lib/util_sock.c:write_data(562)
Jun  6 20:52:53 UBUNTU smbd[1781]:   write_data: write failure in writing to client 192.168.0.4. Error Connection reset by peer
Jun  6 20:52:53 UBUNTU smbd[1781]: [2007/06/06 20:52:53, 0] lib/util_sock.c:send_smb(769)
Jun  6 20:52:53 UBUNTU smbd[1781]:   Error writing 5 bytes to client. -1. (Connection reset by peer)


Does anyone know what it means??????? I have googled it with not much success as to how to make it go away.

---

### Post by kevdog on 2007-06-07
Thanks for the winbind tip.  I regularly read the forums and this is the first time Ive seen this particular package mentioned.  Worked like a charm!

---

### Post by gantengx on 2007-06-09
I tried to use dhcp with winbind now but when i tried to ping to the windows machine, i get the public ip instead of the local ip. if i use static ip+winbind i get the local ip but the windows machine just can't get my hostname..

And now i'm using dhcp, looks like winbind doesn't work properly

on nsswitch.conf i tried to use

```

hosts:          files wins

```

to check whether winbind works but i still can't get the local ip address for the windows machine. I restarted samba,winbind,networking service but still no luck. Is there a way to fix it? I don't mind use static ip on my computer, but the other computers aren't mine.

---

### Post by gantengx on 2007-06-10
oops, my bad, winbind is working, i just have to restart my computer, now i can ping to the windows machine, but still have the same problem, windows machine can't resolve my hostname...

i already put
```

workgroup=WORKGROUP
netbios name=gantengx
wins support=no

```

in my smb.conf.

Anyone know how to solve this?

Thanks

---

### Post by dbott67 on 2007-06-10
> **gantengx said:**
> oops, my bad, winbind is working, i just have to restart my computer, now i can ping to the windows machine, but still have the same problem, windows machine can't resolve my hostname...

i already put
```

workgroup=WORKGROUP
netbios name=gantengx
wins support=no

```in my smb.conf.

Anyone know how to solve this?

Thanks

I believe you need to put the semi-colon (**[COLOR=Red];[/COLOR]**) back in front of the [COLOR=Blue]wins support[/COLOR] line.  In my smb.conf file, it's still commented out and everything works fine on my computer:
```

workgroup=WORKGROUP
netbios name=gantengx
[COLOR=Red]**; **[/COLOR]wins support=no  [COLOR=Purple]*<-- add a semi-colon to the beginning of this line*[/COLOR]

```

-Dave

---

### Post by dannyboy79 on 2007-06-11
that wouldn't be the solution because if you do "man smb.conf" you would see that the default settings for wins support is no, which is the same as having it UN-commented and putting "no". So unless there's some weird phenomonon going on, that will not the be the problem and or commenting it back it will not be the solution.

---

### Post by dbott67 on 2007-06-11
> **dannyboy79 said:**
> that wouldn't be the solution because if you do "man smb.conf" you would see that the default settings for wins support is no, which is the same as having it UN-commented and putting "no". So unless there's some weird phenomonon going on, that will not the be the problem and or commenting it back it will not be the solution.

I just checked this & dannyboy79 is right --- adding the [COLOR=Blue]**;**[/COLOR] back has no effect.  I removed the semi-colon from my smb.conf file, restarted samba and my Windows machine can still resolve the Ubuntu hostname (even after flushing the DNS in Windows).  

Not that I didn't believe danny or the man pages --- it just seems weird to comment out a setting that says "**wins support = no**" (you'd think they'd set it to "**wins support = yes**" if the default is already 'no'.  Anyhow, better to confirm and know for sure.

Are you running any sort of firewall on either computer?  If so, try disabling any & all firewalls and try again.

-Dave

---

### Post by gantengx on 2007-06-13
I'm not sure if its the firewall problem, I'm using firestarter and I enabled ping into my machine.

I tried to ping my ip from windows machine and it worked fine, but i just can't ping my hostname.

This problem is driving me crazy :(

---

### Post by dannyboy79 on 2007-06-13
if you have static ip's and a small network, than you don't neccessarily need winbind. check this thread out and see if that helps. [http://ubuntuforums.org/showthread.php?t=391601](http://ubuntuforums.org/showthread.php?t=391601)
also, have you enabled ntebios over tcp/ip within windows? also, do you have the nmbd daemon running? it's broadcasts the hostname of your ubuntu machine. what do these commands show?

smbtree

findsmb

---

### Post by dbott67 on 2007-06-13
> **gantengx said:**
> I'm not sure if its the firewall problem, I'm using firestarter and I enabled ping into my machine.

I tried to ping my ip from windows machine and it worked fine, but i just can't ping my hostname.

This problem is driving me crazy :(

Try disabling the firewall.  Under normal circumstances, you would need to have ports 137, 138, 139 and 445 open for NetBIOS & SMB.  We need to eliminate the firewall as the potential source of the problem.  

Try following procedure to disable your firewall:

1. Save firewall rules
```
sudo iptables-save > /root/firewall.rules
```

2. Type the following commands:
```
sudo iptables -X
sudo iptables -t nat -F
sudo iptables -t nat -X
sudo iptables -t mangle -F
sudo iptables -t mangle -X
sudo iptables -P INPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT
```-Dave

---

### Post by gantengx on 2007-06-13
> **dbott67 said:**
> Try disabling the firewall.  Under normal circumstances, you would need to have ports 137, 138, 139 and 445 open for NetBIOS & SMB.  We need to eliminate the firewall as the potential source of the problem.  

Try following procedure to disable your firewall:

1. Save firewall rules
```
sudo iptables-save > /root/firewall.rules
```

2. Type the following commands:
```
sudo iptables -X
sudo iptables -t nat -F
sudo iptables -t nat -X
sudo iptables -t mangle -F
sudo iptables -t mangle -X
sudo iptables -P INPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT
```-Dave

aargh... its the firewall problem. Finally found the solution. I have to turn off "Block broadcasts from external network" in the Preferences->Advanced.

I found out how to fix the firestarter from [http://ubuntuforums.org/showthread.php?t=190542](http://ubuntuforums.org/showthread.php?t=190542)

But i just got one question about the firestarter. Why do i have to turn off the "Block broadcast from external network" option? Isn't the netbios broadcast is from the internal network?

Thanks dbott67 and dannyboy79 :D

---

### Post by dannyboy79 on 2007-06-13
yeah, that doesn't sound good to be honest!! I don't use firestarter, I just use iptables. there are scripts everywhere that all you have to do is run it, and it'll ask you simpl questions about which ports/services to open which to me is just as easy as using a gui. did you read further and see his post number 4, maybe you can uncheck that accept broadcasts from external network if you add what he did to the /etc/firestarter/inbound/setup file? don't know as I said though as I don;'t use firestarter.

---

