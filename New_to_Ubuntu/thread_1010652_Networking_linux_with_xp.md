---
title: "Networking linux with xp"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by wstay on 2008-12-14
I am having problem with networking.
The problem is after connecting both my ubuntu8.04 and my wins xp computers, I can see ubuntu shared files from wins xp
but I cannot see wins xp shared files from ubuntu even with firewall turn to off in wins xp 
(though I can see the wins xp network computer from ubuntu).
What should I put under [global] in the smb.conf file to solve this problem?

---

### Post by tuskenraider on 2008-12-14
> **wstay said:**
> I am having problem with networking.
The problem is after connecting both my ubuntu8.04 and my wins xp computers, I can see ubuntu shared files from wins xp
but I cannot see wins xp shared files from ubuntu even with firewall turn to off in wins xp 
(though I can see the wins xp network computer from ubuntu).
What should I put under [global] in the smb.conf file to solve this problem?


have you tried to type in the ip addy of the winxp machine  192.168.XXX.XXX?  try that..  and if it works book mark it.  ive had to do that...  hope that helps.

tusken

---

### Post by superprash2003 on 2008-12-14
this should help [http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html](http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by Kellemora on 2008-12-14
Hi Wstay

Before all the guru's give you a million and one things to try that probably won't work, hear me out.

I'm running 8 computers here in my office, two of them are XP machines, all the rest Hardy.

I've had 3 months of nightmares with networking, that finally appears to finally be resolved (you didn't hear me say that out loud!)......

I made changes to the smb.conf file until I was blue in the face and nothing worked.  Why, simple, there's a BUG in Ubuntu that has been unresolved now for over 2 years.  But the ONLY problem it causes is that sometimes your shares do not appear under Places/Network.  You can still get to them via IP in Go/Location.

That being said, let's move on.

Besides Samba, which is obviously installed and working since your Doze machines can see your Ubuntu shares.  You should install smbclient.
```
sudo apt-get install smbclient
```
or do it from Synaptic Package Manager.
Also install smbtree while you are there, and IF you see smbfs is checked, uncheck it, it causes problems also.

Now onto your smb.conf file
The ONLY change you probably need to make is to place your WORKGROUP NAME behind the global entry WORKGROUP.
It currently reads WORKGROUP = WORKGROUP
Windows is usually named MSHOME if you didn't change it to another workgroup name, which is a good idea to do!

I've learned the hard way that when you boot up your computer it DOES NOT normally read the smb.conf file!
So changes you make their will not be readily apparent.

The file your computer reads for Samba is located at /var/lib/samba, this is a binary file, uneditable by us humanoids.

The way to get a changed smb.conf file to STORE itself in /var/lib/samba is to reboot your computer three times in quick succession.  (Guru's may not agree with me on this either, but it works!)

BUT, don't expect that to mean the BUG in Places/Network is resolved!
If you go to Terminal and type smbtree, all of your shares should be shown, including the computers that are on-line and every folder that is shared.

Now, if you have smbfs installed, you will find some of the folders missing, sometimes whole computers missing from smbtree, that's why I said uninstall it if it's installed.

If your shares do not show up under Places/Network, while there go up to Go/Location and type the IP address of the machine.  They should show up now for you.  

You can continue to keep rebooting your Ubuntu machine until it finally shows the shares under Places/Network, but Ubuntu has some bad days where 50 boots won't do it, and the next day they will show up with ease and keep working until you get another upgrade, then they will disappear again.

I really shouldn't continue to say that, because since the upgrade before last, our shares on all 8 machines have been showing up just fine, despite power outages and fried power supplies going berserk.  So maybe they finally fixed it?

Also, don't forget about your /etc/hosts file!
Check it to make sure it's OK too.

Good Luck

TTUL
Gary

---

### Post by wstay on 2008-12-15
I type smbtree onto the terminal and I got the following message:

wstay@MSHOME:~$ smbtree\
> 
Password: 
MSHOME
	\\UBUNTU         		Ubuntu Server
timeout connecting to 203.106.203.238:445
timeout connecting to 203.106.203.238:139
Error connecting to 203.106.203.238 (Operation already in progress)
cli_start_connection: failed to connect to UBUNTU<20> (203.106.203.238). Error NT_STATUS_ACCESS_DENIED
	\\3AF8D6D8756845F		Partition1
timeout connecting to 203.106.203.238:139
Error connecting to 203.106.203.238 (Operation already in progress)
cli_start_connection: failed to connect to 3AF8D6D8756845F<20> (203.106.203.238). Error NT_STATUS_ACCESS_DENIED
wstay@MSHOME:~$

How can I correct the error ´NT_STATUS_ACCESS_DENIED´?

---

### Post by Kellemora on 2008-12-16
Hi Wstay

Did YOU type that backslash behind smbtree??????

If so, it don't belong there!  
Just type smbtree

That being said, I tried it on my own computer and it didn't do anything.

I'm a noob too, so whatever else is causing the output you got is probably way over my head.

TTUL
Gary

---

### Post by deputy on 2008-12-16
Have you setup the samba user with the smbpasswd command? 

Also if you make changes to your smb.conf file you can restart samba with:
/etc/init.d/samba restart . This way samba uses the new configurations.

---

### Post by deputy on 2008-12-16
I forgot to mention to run smbpasswd with root privileges:

```
sudo smbpasswd
```

Same when restarting samba:

```
sudo /etc/init.d/samba restart
```

---

### Post by wstay on 2008-12-16
> **deputy said:**
> Have you setup the samba user with the smbpasswd command? 

Also if you make changes to your smb.conf file you can restart samba with:
/etc/init.d/samba restart . This way samba uses the new configurations.


I tried with sudo smbpasswd and and restarted wuth sudo /etc/init.d/samba restart and I still cannot get connected with smbtree:

wstay@MSHOME:~$ sudo smbpasswd
New SMB password:
Retype new SMB password:
wstay@MSHOME:~$ sudo /etc/init.d/samba restart
 * Stopping Samba daemons                                                [ OK ] 
 * Starting Samba daemons                                                [ OK ] 
wstay@MSHOME:~$ smbtree
Password: 
MSHOME
	\\WSTAY-PC       		
timeout connecting to 203.106.203.238:445
timeout connecting to 203.106.203.238:139
Error connecting to 203.106.203.238 (Operation already in progress)
cli_start_connection: failed to connect to WSTAY-PC<20> (203.106.203.238). Error NT_STATUS_ACCESS_DENIED
	\\UBUNTU         		
timeout connecting to 203.106.203.238:445
timeout connecting to 203.106.203.238:139
Error connecting to 203.106.203.238 (Operation already in progress)
cli_start_connection: failed to connect to UBUNTU<20> (203.106.203.238). Error NT_STATUS_ACCESS_DENIED
wstay@MSHOME:~$

By the way could you please tell me what is:
timeout connecting to 203.106.203.238:445
timeout connecting to 203.106.203.238:139

Why is it connecting to 203.106.203.238:445 and  203.106.203.238:139?
What ip addresses and/or ports are these?

My linux computer is using static ip 192.168.1.34 with subnet 255.255.255.0
and gateway 192.168.1.1

I tried to ping my network computer ip 192.168.1.33 and this is what I get:
wstay@MSHOME:~$ ping 192.168.1.33
PING 192.168.1.33 (192.168.1.33) 56(84) bytes of data.
64 bytes from 192.168.1.33: icmp_seq=1 ttl=128 time=0.362 ms
64 bytes from 192.168.1.33: icmp_seq=2 ttl=128 time=0.215 ms
64 bytes from 192.168.1.33: icmp_seq=3 ttl=128 time=0.235 ms
64 bytes from 192.168.1.33: icmp_seq=4 ttl=128 time=0.215 ms
64 bytes from 192.168.1.33: icmp_seq=5 ttl=128 time=0.224 ms
64 bytes from 192.168.1.33: icmp_seq=6 ttl=128 time=0.224 ms
64 bytes from 192.168.1.33: icmp_seq=7 ttl=128 time=0.227 ms
64 bytes from 192.168.1.33: icmp_seq=8 ttl=128 time=0.228 ms
64 bytes from 192.168.1.33: icmp_seq=9 ttl=128 time=0.217 ms
64 bytes from 192.168.1.33: icmp_seq=10 ttl=128 time=0.230 ms
64 bytes from 192.168.1.33: icmp_seq=11 ttl=128 time=0.237 ms
64 bytes from 192.168.1.33: icmp_seq=12 ttl=128 time=0.217 ms
64 bytes from 192.168.1.33: icmp_seq=13 ttl=128 time=0.230 ms
64 bytes from 192.168.1.33: icmp_seq=14 ttl=128 time=0.231 ms
64 bytes from 192.168.1.33: icmp_seq=15 ttl=128 time=0.208 ms
64 bytes from 192.168.1.33: icmp_seq=16 ttl=128 time=0.225 ms
64 bytes from 192.168.1.33: icmp_seq=17 ttl=128 time=0.229 ms
64 bytes from 192.168.1.33: icmp_seq=18 ttl=128 time=0.217 ms
64 bytes from 192.168.1.33: icmp_seq=19 ttl=128 time=0.245 ms
64 bytes from 192.168.1.33: icmp_seq=20 ttl=128 time=0.241 ms
64 bytes from 192.168.1.33: icmp_seq=21 ttl=128 time=0.227 ms
....................................................................................
.....................................................................................
and it goes on and on like an infinite loop.

So is it possible to figure out what and where my problem is?

---

### Post by handydan918 on 2008-12-16
Do you deal with an isp in kuala lumpur?
Output of whois....
```
[whois.apnic.net node-2]
% Whois data copyright terms    http://www.apnic.net/db/dbcopyright.html

inetnum:      203.106.203.160 - 203.106.203.255
netname:      INFRA-TMNET
descr:        TMNET
country:      MY
admin-c:      TA35-AP
tech-c:       TA35-AP
mnt-by:       TM-NET-AP
changed:      fuwaizah@tm.net.my 20040410
status:       ASSIGNED NON-PORTABLE
changed:      hm-changed@apnic.net 20070209
source:       APNIC

route:        203.106.0.0/16
descr:        TMnet route object
origin:       AS4788
mnt-by:       TM-NET-AP
changed:      hm-changed@apnic.net 20080328
source:       APNIC

role:         TMNET IP Administrators
address:      Level 17, TM Annexe,
address:      Jalan Pantai Baru,
address:      50672 Kuala Lumpur.
country:      MY
phone:        +603-22406120
phone:        +603-22402118
fax-no:       +603-22402126
e-mail:       ainols@tm.com.my
trouble:      abuse@tm.net.my
admin-c:      AS115-AP
admin-c:      SM135-AP
tech-c:       AS115-AP
tech-c:       SM135-AP
nic-hdl:      TA35-AP
mnt-by:       TM-NET-AP
changed:      hm-changed@apnic.net 20070209
source:       APNIC


```

---

### Post by deputy on 2008-12-16
Oops I forgot to mention that when using the smbpasswd command you should specify the user that you want to setup:

```
sudo smbpasswd username
```

Otherwise you setup the password for root. If you setup for example yourself then after you would use smbtree like this:

```
smbtree -U username
```

Then you use the password that you setup using smbpasswd. I'm not sure why those IP's are showing up. You might try following this How-to that helped me out. I believe the trick is in configuring the smb.conf file correctly:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Let me know how it goes.

---

### Post by wstay on 2008-12-17
> **deputy said:**
> Oops I forgot to mention that when using the smbpasswd command you should specify the user that you want to setup:

```
sudo smbpasswd username
```

Otherwise you setup the password for root. If you setup for example yourself then after you would use smbtree like this:

```
smbtree -U username
```

Then you use the password that you setup using smbpasswd. I'm not sure why those IP's are showing up. You might try following this How-to that helped me out. I believe the trick is in configuring the smb.conf file correctly:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Let me know how it goes.

Still the same problem:

wstay@MSHOME:~$ smbtree -U wstay
Password: 
MSHOME
	\\WSTAY-PC       		
timeout connecting to 203.106.203.238:445
timeout connecting to 203.106.203.238:139
Error connecting to 203.106.203.238 (Operation already in progress)
cli_start_connection: failed to connect to WSTAY-PC<20> (203.106.203.238). Error NT_STATUS_ACCESS_DENIED
	\\UBUNTU         		
timeout connecting to 203.106.203.238:445
timeout connecting to 203.106.203.238:139
Error connecting to 203.106.203.238 (Operation already in progress)
cli_start_connection: failed to connect to UBUNTU<20> (203.106.203.238). Error NT_STATUS_ACCESS_DENIED
wstay@MSHOME:~$

If only we can figure out why my computer is connecting to   203.106.203.238:445 and  203.106.203.238:139 and what are these ip addresses/ports?

---

### Post by Kellemora on 2008-12-17
Hi Wstay

WHERE did you get those IP numbers from?????

I'm no expert, but they seem out of range for a Local Area Network....

They may be Ok, but I'm used to seeing numbers like 192.168.1.101 and up.
And your loopback 127.0.0.1, etc.

Those look possibly like ISP connection IP numbers????

Nevermind, I just didn't read far enough down your list before I started responding.

Since PING works, then smbtree should work.
This if the first time I've ever seen one work and not the other!

So, I'll leave it up to the guru's!

TTUL
Gary

---

### Post by wstay on 2008-12-17
> **Kellemora said:**
> Hi Wstay

WHERE did you get those IP numbers from?????

I'm no expert, but they seem out of range for a Local Area Network....

They may be Ok, but I'm used to seeing numbers like 192.168.1.101 and up.
And your loopback 127.0.0.1, etc.

Those look possibly like ISP connection IP numbers????

Nevermind, I just didn't read far enough down your list before I started responding.

Since PING works, then smbtree should work.
This if the first time I've ever seen one work and not the other!

So, I'll leave it up to the guru's!

TTUL
Gary

Those IP numbers???? were from when I typed smbtree in the terminal and pressed enter. May be those numbers were from the ISP connection because I connected to the internet when I typed smbtree. You could be right.

My PING did not work. When I PING my network computer, it gave me a never ending list as follow:

wstay@MSHOME:~$ ping 192.168.1.33
PING 192.168.1.33 (192.168.1.33) 56(84) bytes of data.
64 bytes from 192.168.1.33: icmp_seq=1 ttl=128 time=0.192 ms
64 bytes from 192.168.1.33: icmp_seq=2 ttl=128 time=0.193 ms
64 bytes from 192.168.1.33: icmp_seq=3 ttl=128 time=0.183 ms
64 bytes from 192.168.1.33: icmp_seq=4 ttl=128 time=0.195 ms
64 bytes from 192.168.1.33: icmp_seq=5 ttl=128 time=0.191 ms
64 bytes from 192.168.1.33: icmp_seq=6 ttl=128 time=0.196 ms
64 bytes from 192.168.1.33: icmp_seq=7 ttl=128 time=0.193 ms
64 bytes from 192.168.1.33: icmp_seq=8 ttl=128 time=0.187 ms
64 bytes from 192.168.1.33: icmp_seq=9 ttl=128 time=0.198 ms
64 bytes from 192.168.1.33: icmp_seq=10 ttl=128 time=0.196 ms
64 bytes from 192.168.1.33: icmp_seq=11 ttl=128 time=0.193 ms
64 bytes from 192.168.1.33: icmp_seq=12 ttl=128 time=0.202 ms
64 bytes from 192.168.1.33: icmp_seq=13 ttl=128 time=0.193 ms
64 bytes from 192.168.1.33: icmp_seq=14 ttl=128 time=0.193 ms
64 bytes from 192.168.1.33: icmp_seq=15 ttl=128 time=0.195 ms
64 bytes from 192.168.1.33: icmp_seq=16 ttl=128 time=0.193 ms
64 bytes from 192.168.1.33: icmp_seq=17 ttl=128 time=0.193 ms
64 bytes from 192.168.1.33: icmp_seq=18 ttl=128 time=0.190 ms
64 bytes from 192.168.1.33: icmp_seq=19 ttl=128 time=0.200 ms
 
May be you can guess what is my probllem from this?

---

### Post by Kellemora on 2008-12-18
Hi Wstay

Your PING to machine 192.168.1.33 IS working just fine!
No problem there!

Now go to Places/Network and on the top bar select Go/Location
and in the bar type ```
SMB://192.168.1.33
```
and see if your shares show up then.

If so, then do the same thing only using your WorkGROUP name instead.  I think in your case it will be
```
smb://MSHOME
``` and see if that works also.

If so, then you are configured correctly and the problem of shares not showing up automatically in Places/Network is a known bug that has not been resolved for like 2 years now.

TTUL
Gary

---

### Post by Kellemora on 2008-12-18
Hi Wstay

One other thing!

In your smb.conf file, near the top under Global where it originally said WORKGROUP = WORKGROUP have you changed that to read WORKGROUP = MSHOME (if you are using MSHOME as your Group Name, which I think you are).

But before you do that, it's wise to change your Workgroup Name to something a little bit more Unique.  You should do this in Windows, in Ubuntu and in your smb.conf file so all your machines are on the same workgroup.

TTUL
Gary

---

### Post by hotstovejer on 2008-12-18
Wstay,

Could you please post your smb.conf for us to look at? It is located in /etc/samba

That would really help to look at it.

Thanks!

Jeremy

---

### Post by wstay on 2008-12-20
> **hotstovejer said:**
> Wstay,

Could you please post your smb.conf for us to look at? It is located in /etc/samba

That would really help to look at it.

Thanks!

Jeremy

Hi Jeremy,
Please see attachment.

---

### Post by wstay on 2008-12-20
> **Kellemora said:**
> Hi Wstay

One other thing!

In your smb.conf file, near the top under Global where it originally said WORKGROUP = WORKGROUP have you changed that to read WORKGROUP = MSHOME (if you are using MSHOME as your Group Name, which I think you are).

But before you do that, it's wise to change your Workgroup Name to something a little bit more Unique.  You should do this in Windows, in Ubuntu and in your smb.conf file so all your machines are on the same workgroup.

TTUL
Gary

> **Kellemora said:**
> Hi Wstay

Your PING to machine 192.168.1.33 IS working just fine!
No problem there!

Now go to Places/Network and on the top bar select Go/Location
and in the bar type ```
SMB://192.168.1.33
```
and see if your shares show up then.

If so, then do the same thing only using your WorkGROUP name instead.  I think in your case it will be
```
smb://MSHOME
``` and see if that works also.

If so, then you are configured correctly and the problem of shares not showing up automatically in Places/Network is a known bug that has not been resolved for like 2 years now.

TTUL
Gary

I tried the methods you mentioned. It did not work.
I am using ubuntu 8.04.
May be I should install ubuntu 8.10.

---

### Post by wstay on 2008-12-21
> **Kellemora said:**
> Hi Wstay

Before all the guru's give you a million and one things to try that probably won't work, hear me out.

I'm running 8 computers here in my office, two of them are XP machines, all the rest Hardy.

I've had 3 months of nightmares with networking, that finally appears to finally be resolved (you didn't hear me say that out loud!)......

I made changes to the smb.conf file until I was blue in the face and nothing worked.  Why, simple, there's a BUG in Ubuntu that has been unresolved now for over 2 years.  But the ONLY problem it causes is that sometimes your shares do not appear under Places/Network.  You can still get to them via IP in Go/Location.

That being said, let's move on.

Besides Samba, which is obviously installed and working since your Doze machines can see your Ubuntu shares.  You should install smbclient.
```
sudo apt-get install smbclient
```
or do it from Synaptic Package Manager.
Also install smbtree while you are there, and IF you see smbfs is checked, uncheck it, it causes problems also.

Now onto your smb.conf file
The ONLY change you probably need to make is to place your WORKGROUP NAME behind the global entry WORKGROUP.
It currently reads WORKGROUP = WORKGROUP
Windows is usually named MSHOME if you didn't change it to another workgroup name, which is a good idea to do!

I've learned the hard way that when you boot up your computer it DOES NOT normally read the smb.conf file!
So changes you make their will not be readily apparent.

The file your computer reads for Samba is located at /var/lib/samba, this is a binary file, uneditable by us humanoids.

The way to get a changed smb.conf file to STORE itself in /var/lib/samba is to > reboot your computer three times in quick succession.  (Guru's may not agree with me on this either, but it works!)

BUT, don't expect that to mean the BUG in Places/Network is resolved!
If you go to Terminal and type smbtree, all of your shares should be shown, including the computers that are on-line and every folder that is shared.

Now, [QUOTE]if you have smbfs installed, you will find some of the folders missing, sometimes whole computers missing from smbtree, that's why I said uninstall it if it's installed.

> If your shares do not show up under Places/Network, while there go up to Go/Location and type the IP address of the machine.  They should show up now for you.  

You can continue to keep rebooting your Ubuntu machine until it finally shows the shares under Places/Network, but Ubuntu has some bad days where 50 boots won't do it, and the next day they will show up with ease and keep working until you get another upgrade, then they will disappear again.

I really shouldn't continue to say that, because since the upgrade before last, our shares on all 8 machines have been showing up just fine, despite power outages and fried power supplies going berserk.  So maybe they finally fixed it?

> Also, don't forget about your /etc/hosts file!
Check it to make sure it's OK too.

Good Luck

TTUL
Gary[/QUOTE]


Hi Gary,
I uninstalled  smbfs.
I also go up to Go/Location and type the ip address of the machine.
I checked my /etc/hosts file and it showed 127.0.1.1 as mshome (that is suppose to be my workgroup computer - am I correct?). I had already changed my workgroup from mshome to taycomputer in the smb.conf file. So I changed the entry for 127.0.1.1 from mshome to taycomputer in the hosts file. 
After I had done all these and did 3 successive reboots  (by restarting  before I had logged in as a user) , I am still having problem viewing my shared files on the windows os from my linux os.

---

### Post by wstay on 2008-12-21
I found out now that when I type smbtree on the terminal:

wstay@ubuntu:~$ smbtree
INFO: Current debug levels:
  all: True/25
  tdb: False/0
  printdrivers: False/0
  lanman: False/0
  smb: False/0
  rpc_parse: False/0
  rpc_srv: False/0
  rpc_cli: False/0
  passdb: False/0
  sam: False/0
  auth: False/0
  winbind: False/0
  vfs: False/0
  idmap: False/0
  quota: False/0
  acls: False/0
  locking: False/0
  msdfs: False/0
  dmapi: False/0
doing parameter max log size = 1000
doing parameter read only = no
doing parameter interfaces = eth* 192.168.1.1/255.255.255.0
doing parameter hosts allow = 192.168.1. 127.
doing parameter guest account = nobody
doing parameter security = user
pm_process() returned Yes
lp_servicenumber: couldn't find homes
set_server_role: role = ROLE_STANDALONE
Attempting to register new charset UCS-2LE
Registered charset UCS-2LE
Attempting to register new charset UTF-16LE
Registered charset UTF-16LE
Attempting to register new charset UCS-2BE
Registered charset UCS-2BE
Attempting to register new charset UTF-16BE
Registered charset UTF-16BE
Attempting to register new charset UTF8
Registered charset UTF8
Attempting to register new charset UTF-8
Registered charset UTF-8
Attempting to register new charset ASCII
Registered charset ASCII
Attempting to register new charset 646
Registered charset 646
Attempting to register new charset ISO-8859-1
Registered charset ISO-8859-1
Attempting to register new charset UCS2-HEX
Registered charset UCS2-HEX
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
added interface ip=192.168.1.34 bcast=192.168.1.255 nmask=255.255.255.0
added interface ip=192.168.1.35 bcast=192.168.1.255 nmask=255.255.255.0
added interface ip=192.168.1.1 bcast=192.168.1.255 nmask=255.255.255.0
Password: 

the IP address 192.168.1.35 on the second last line is not my network computer IP address. It should be 192.168.1.33 which is my vista os network IP address.
My linux os  IP address is 192.168.1.34 .There is no other network computer on my network  with IP 192.168.1.35. So why is there is IP 192.168.1.35 annd how do I correct this?

---

### Post by hotstovejer on 2008-12-22
Do you have more than one network interface on the Ubuntu box that is active? Is the IP of your router 192.168.1.1, or .35? 

Also, your home directories are not set to be browsable. In your smb.conf, please change > [homes] 
    browsable = no
    map archive = yes


to 

> [homes] 
    browsable = yes
    map archive = yes


Let us know if you still need help!

Thanks

Jeremy

---

### Post by Kellemora on 2008-12-22
Glad you caught that Jeremy!

Don't know how I missed seeing it either, but it's been a long day here!  Ole Murphy is at it again, hi hi.........

TTUL
Gary

---

### Post by wstay on 2008-12-23
> **hotstovejer said:**
> Do you have more than one network interface on the Ubuntu box that is active? Is the IP of your router 192.168.1.1, or .35? 

Also, your home directories are not set to be browsable. In your smb.conf, please change 

to 



Let us know if you still need help!

Thanks

Jeremy
Still the same problem.
I have two network interface and only one is active  at a time.
The IP for the router (gateway) is 192.168.1.1 not .35
I changed my vista network computer to IP 192.168.1.35 with subnet mask 255.255.255.0 and I checked the status in the network connection, it gave me another set of IP: 169.254.135.106 with subnet mask 255.255.0.0 
Why is it giving me this set of IP??

---

### Post by wstay on 2008-12-23
> **wstay said:**
> Still the same problem.
I have two network interface and only one is active  at a time.
The IP for the router (gateway) is 192.168.1.1 not .35
I changed my vista network computer to IP 192.168.1.35 with subnet mask 255.255.255.0 and I checked the status in the network connection, it gave me another set of IP: 169.254.135.106 with subnet mask 255.255.0.0 
Why is it giving me this set of IP??

I found out that the IP 192.168.1.35 belongs to my other network interface card
installed on my linux computer. That means  that it is showing this interface card IP though it is not active (not switch on) but it does not means that it is connecting to it when I type smbtree om the terminal.

---

### Post by eder.apt-get on 2008-12-23
So would post the output of ```
ifconfig
```?

---

### Post by Brynster on 2008-12-23
personally i would simply edit my hosts file in windows machine.

Its not an Ubuntu problem if it can see and read/write to your windows shared drive.

What usually happens is a network resolving problem caused windows can see the machine but cannot retrieve the host details from it.
So if you tell Windows what it is called by adding the ip address and computer name to the host file then it will resolve the network correctly and be able to see the Ubuntu box correctly.

---

### Post by wstay on 2008-12-28
I did a new installation of ubuntu8.10 and now I find that I cannot edit the manual configuration for my network adaptor to have static address for my network.
Is there a way to go about it?

---

