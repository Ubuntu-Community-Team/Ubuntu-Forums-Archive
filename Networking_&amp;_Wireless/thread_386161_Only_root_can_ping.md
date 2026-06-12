---
title: "Only root can ping"
date: 2007-03-16
forum: Networking &amp; Wireless
---

### Post by mjfleck2000 on 2007-03-16
This one has me baffled!  I have been working on it for several days!

Running Kubuntu edgy.  If I sudo su to root,and as *root  *I can ping local machines (as defined in /etc/hosts) and Internet sites (google.com, yahoo.com,etc).

If I am a *user*, I can not ping local machines but I can ping the Internet.



**root can ping**
[www.google.com](www.google.com)
localhost
localhost.localdomain
happy.myhome.net
happy

**user can ping**
 [www.google.com](www.google.com)


but the error message "Unknown host" is returned for:
localhost
localhost.localdomain
happy.myhome.net
happy

DNS is hosted by our ISP, there is not a local DNS running.

My files setup:

/etc/hosts
127.0.0.1  localhost.localdomain localhost
192.168.1.1 happy.myhome.net happy
192.168.1.2 grumpy.myhome.net grumpy
192.168.1.3 sleeply.myhome.net sleepy

/etc/resolv.conf
search myhome.net
nameserver 216.255.223.194
nameserver 216.255.223.195

/etc/host.conf
order hosts,bind
multi on

/etc/nsswitch.conf

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns mdns
networks:       files

protocols:      files
services:       files
ethers:         files
rpc:            files

netgroup:       nis


Now... If  I remove all nameservers from  (or just delete ) the resolv.conf file, users CAN ping localhost,happy,grumpy BUT can not ping [www.google.com](www.google.com)

It seems as if, for a user, that the host.conf file is being ignored.

The permissions on /etc/hosts is:
-rw-r--r-- 1 root root 3809 2007-03-16 13:00 /etc/hosts


and for /etc/resolv.conf is:
-rw-r--r-- 1 root root 78 2007-03-16 13:35 /etc/resolv.conf


I tried creating a new user and testing... same problem.  So, at the moment, a user can either resolve local machines or DNS machines.

Can someone suggest what I am overlooking?

Mike

---

### Post by chili555 on 2007-03-16
Gosh, your /etc/hosts looks a bit complex. If it is for reasons I don't understand, feel free to ignore my reply as daft. Here is my /etc/hosts, in part: ```
$cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       LAPTOP

192.168.1.116   MBR2.linux
192.168.1.118   GBR1

```
I wonder if, after backing up your current /etc/hosts, you amended yours to look like: ```
192.168.1.1 happy
192.168.1.2 grumpy
192.168.1.3 sleepy
``` it might work?

---

### Post by dbott67 on 2007-03-17
Pinging by hostname alone (i.e. happy), as opposed to the fully-qualified domain name (i.e. happy.myhome.net) requires the **/etc/lmhosts** file:

1. Create the lmhosts file:
```
sudo touch /etc/lmhosts
```2. Add your client hosts:

        ```
# Sample Samba lmhosts file.
#
127.0.0.1    localhost        
192.168.1.1 happy
192.168.1.2 grumpy
192.168.1.3 sleepy
```You seem to be knowledgable about networking, but I'll try to be very explicit for anyone else that may come across this thread in the future.  *I've also posted the output & permissions of my network settings at the bottom of the post for comparison.*

The real issue here is the difference between DNS and SMB/WINS and how they perform name resolution.  DNS requires a DNS server (or a manually maintained **/etc/hosts** file), while SMB requires a WINS server (winbind in linux) or a manually maintained **/etc/lmhosts** file.

Using your method of populating the hosts file *should* work when using the FQDN, but you would need to create an lmhosts file for simple host resolution.  For this type of setup I've been using winbind.  

You need to install the following packages from the repos:

```
 sudo apt-get install smbfs smbclient winbind
```[U][B]BACKGROUND

[/B][/U] (This is from another thread that I posted in regarding local name resolution. The full thread is for here: [http://www.ubuntuforums.org/showthread.php?p=1770797#post1770797](http://www.ubuntuforums.org/showthread.php?p=1770797#post1770797))

... some issues arise because of the way SMB shares "announce" themselves to the network. Generally, connecting via IP address works properly, but browsing by 'computer name' can occasionally fail. Windows uses WINS service to allow users to browse by computer name (also known in Windows-speak as Netbios name). WINS binds the computer name to the IP address. For the most part, this has been superceded by DNS, which binds the fully-qualified domain name to the IP address. The problem is that DNS resolution requires that:

a) You're running a DNS server (locally)
b) Each client is registered in the DNS server

The problem here is that most people don't run their own DNS server at home and if you have any Windows computers on the network (or Samba shares), you really should have a WINS server or 'winbind' installed.

There is a package in the repositories called 'winbind' that will allow you to browse by computer name.

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
```The advantage to using winbind vs. static IPs is that I can add/remove PCs without worrying about editing the hosts file.  There are also a few tools that can aid in discovery:
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

```###############################################

For reference, here are the same commands on my machine. 

Contents of my /etc/resolv.conf file. I've got a D-Link DI-614+ router that uses DNS forwarding to obtain DNS resolution (so my machines just ask the router & it forwards to request to my ISPs DNS server):

```
 dbott@thedrake:~$ cat /etc/resolv.conf
nameserver 192.168.1.1
```Permissions of my /etc/resolv.conf file (same as yours):

```
 dbott@thedrake:~$ ls -all /etc/resolv.conf
-rw-r--r-- 1 root root 23 2007-03-16 17:22 /etc/resolv.conf
```Contents of my hosts file:

```
 dbott@thedrake:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       thedrake

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```Permissions of my /etc/hosts file (same as yours):
```
 dbott@thedrake:~$ ls -all /etc/hosts
 -rw-r--r-- 1 root root 244 2006-12-10 17:53 /etc/hosts
```Pinging external sites:
```
dbott@thedrake:~$ ping [www.google.com]("http://www.google.com/")
PING [www.l.google.com]("http://www.l.google.com/") (64.233.161.104) 56(84) bytes of data.
64 bytes from od-in-f104.google.com (64.233.161.104): icmp_seq=1 ttl=234 time=47                      .2 ms
64 bytes from od-in-f104.google.com (64.233.161.104): icmp_seq=2 ttl=234 time=50                      .5 ms
64 bytes from od-in-f104.google.com (64.233.161.104): icmp_seq=3 ttl=234 time=44                      .0 ms
64 bytes from od-in-f104.google.com (64.233.161.104): icmp_seq=4 ttl=234 time=47                      .7 ms

--- [www.l.google.com]("http://www.l.google.com/") ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3011ms
rtt min/avg/max/mdev = 44.064/47.398/50.522/2.291 ms
```Pinging a internal/local Win XP computer (firewall disabled):

```
 dbott@thedrake:~$ ping piii-600
PING piii-600 (192.168.1.102) 56(84) bytes of data.
64 bytes from 192.168.1.102: icmp_seq=1 ttl=128 time=0.217 ms
64 bytes from 192.168.1.102: icmp_seq=2 ttl=128 time=0.219 ms
64 bytes from 192.168.1.102: icmp_seq=3 ttl=128 time=0.241 ms

--- piii-600 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2007ms
rtt min/avg/max/mdev = 0.217/0.225/0.241/0.020 ms
```And pinging my NAS storage device:
```
dbott@thedrake:~$ ping NAS-160
PING NAS-160 (192.168.1.2) 56(84) bytes of data.
64 bytes from 192.168.1.2: icmp_seq=1 ttl=32 time=0.230 ms
64 bytes from 192.168.1.2: icmp_seq=2 ttl=32 time=0.227 ms
64 bytes from 192.168.1.2: icmp_seq=3 ttl=32 time=0.230 ms

--- NAS-160 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2007ms
rtt min/avg/max/mdev = 0.227/0.229/0.230/0.001 ms
```I hope this was useful and helps explain the difference between the various ways of setting up your network. You can use whatever method works, but I find the winbind package the easiest once it's setup.

-Dave

---

### Post by chili555 on 2007-03-17
> Pinging by hostname alone (i.e. happy), as opposed to the fully-qualified domain name (i.e. happy.myhome.net) requires the /etc/lmhosts file:Not on my system: ```
$ cat /etc/lmhosts
cat: /etc/lmhosts: No such file or directory
```

I guess it's a Samba thing. We no speaka da windows here.

---

### Post by dbott67 on 2007-03-17
> **chili555 said:**
> Not on my system: ```
$ cat /etc/lmhosts
cat: /etc/lmhosts: No such file or directory
```I guess it's a Samba thing. We no speaka da windows here.

Well... not to belabour the issue too much here, but to clarify:

Samba is a reverse-engineered version of SMB (which is a basic networking component of Windows) that allows Unix-like machines to communicate (and behave like) Windows servers.  You don't need any Windows machines on the network to use Samba, however, if you'd like the machines to 'behave' like a Windows machine for file-sharing, printer sharing, name resolution and what-not, then Samba is your answer.

So, it's not really a Samba thing --- it's just a name resolution thing.  If you want to do it the 'Windows' way then you need Samba and winbind (or configure your /etc/lmhosts file); if you want to do it the 'other' way, then you need a DNS server (bind - [http://www.bind9.net/](http://www.bind9.net/)) or configure your /etc/hosts file.

For all the Samba info you could ever care to know, check out this link:
[http://us4.samba.org/samba/docs/SambaIntro.html](http://us4.samba.org/samba/docs/SambaIntro.html)

Unix has other ways of doing things: NFS (Network File System)
More details here: [http://en.wikipedia.org/wiki/Network_File_System_(Sun](http://en.wikipedia.org/wiki/Network_File_System_(Sun))

-Dave

---

### Post by dbott67 on 2007-03-17
More thinking out loud here...

For some strange reason, when I originally read this post I was assuming the other machines were Windows computers.  My first post (#3) is still valid provided that you're running smbfs and smbclient on the other workstations (if they're linux) or if they're running Windows and you want to share file/resources "the windows way".

Anyhow, after some further research about the /etc/hosts file, it appears as though the format listed below **should work** for just the hostname (as you have it set up presently):
```
127.0.0.1  localhost.localdomain localhost
192.168.1.1 happy.myhome.net happy
192.168.1.2 grumpy.myhome.net grumpy
192.168.1.3 sleeply.myhome.net sleepy
```The link below has a slightly modified version where the hostname is listed first, followed by the FQDN, so you may want to try changing it to this:

```
127.0.0.1  localhost.localdomain localhost
192.168.1.1 [COLOR=Red]happy [/COLOR]happy.myhome.net
192.168.1.2 [COLOR=Red]grumpy[/COLOR] grumpy.myhome.net
192.168.1.3 [COLOR=Red]sleepy[/COLOR] sleeply.myhome.net
```
I have found an article [here]("http://www.samspublishing.com/articles/article.asp?p=25845&seqNum=3&rl=1") that elaborates on some of the usage of the files in question.  It does have one recommendation that you might try and that is to change the line:
```
127.0.0.1  [COLOR=Red]localhost.localdomain[/COLOR] localhost
```to just
```
127.0.0.1  localhost
```Another suggestion may be to remark out the** search myhome.net** in the resolv.conf file (as it's a real domain name and may be causing some confusion for the computer) or changing the TLD to localdomain (ie. happy.myhome.localdomain).

Sorry to ramble on... just trying to help find an answer.

-Dave

---

### Post by Mr. C. on 2007-03-17
mjfleck2000

I believe this is a simple problem.

You have inadvertently changed permissions on /etc/hosts to root read-only.  Change permission on /etc/hosts to 644 and all should be fine again.

His host file itself is fine.  lmhosts is not necessary, and is used by Windows.

btw "sudo su" is not necessary.  Just use "sudo -s" to create a root shell.

MrC

---

### Post by dbott67 on 2007-03-17
> **Mr. C. said:**
> You have inadvertently changed permissions on /etc/hosts to root read-only.  Change permission on /etc/hosts to 644 and all should be fine again.


The default permissions on the file are correct (they are the same on my computer), so I don't think he changed it.  It *should* be world-readable.  If you can type 'cat /etc/hosts' and see the output, the permissions are okay.

> **Mr. C. said:**
> 
His host file itself is fine.  

It does appear to be okay, but the link that I referenced had a couple of recommendations to try.  I've seen the odd issue with files that have been edited being read properly (the get some sort of corruption).

He could also try deleting the file and then re-creating it from scratch.

> **Mr. C. said:**
> lmhosts is not necessary, and is used by Windows.

Just to clarify, the lmhosts would be required on a Samba network that was not running a WINS/winbind server for name resolution (i.e. for using UNC names such as  **\\computername\sharename** and other 'Network Neighborhood' like browsing).  It is primarily (but not exclusively) found on Windows computers and networks that contain a both Windows and Linux.

In Mike's case, it may not be an issue, but I just want to be clear for those that reference this thread in the future.

-Dave

---

### Post by Mr. C. on 2007-03-17
I had not noticed the OP's hosts file permissions.  Apologies for missing that.

Nonetheless, I believe this is still a simple problem.  The key is that root *can* successfully resolve all the names in /etc/hosts, but a non-root user cannot.  This is a permissions problem.

What are the permissions of /etc/nsswitch.conf ?

If either /etc/hosts or /etc/nsswitch.conf are not world-readable, this will result:

$ ping: unknown host localhost

dbott67, you're a sharp guy; but let's not confuse this simple matter with Samba and Windows, and other irrelevant matters.  You're not sure what the cause is, so please don't confuse other users with irrelevant networking protocols.  And there is no "sort of corruption" in /etc/hosts that root can magically un-corrupt,, but non-privileged users cannot.  Let's try to focus on the "science" in computer science, not voodoo.

What we don't see is the OP's *exact* error message - we see only an interpretation.  This makes diagnosis more difficult.  Actual error messages are important.

The users /etc/hosts file is just fine the way it is (was).  For any entry, all names after the first are aliases, and are perfectly acceptable and interchangable in use.  FQDN are also fine in /etc/hosts.  All lookups from /etc/hosts are simple sting comparison operations.

DNS does not play any part in this problem.  That google can be name translated by all users indicates DNS resolution is working.  The *only* failure point here is the inability for a local user to read or access /etc/hosts or /etc/nsswitch.conf.

MrC

---

### Post by mjfleck2000 on 2007-03-18
Thank you everyone for your suggestions.  I have not (yet!) resolved this problem.  

An important point to note is that , AS ROOT, everything works as expected.  This means that name resolution does function.  It is only AS A USER, that name resolution does not work as expected.

This leads me to think that there are three likely explanations.
1) A path problem
2) file permission problem
3) unidentified corrupted file somewhere (I'm guessing here :)   )

Just to check, I gave a user the same path as root.... no go.
I changed the permissions on /etc/hosts /etc/host.conf and /etc/resolv.conf to 777.... not go. ( I , of course, changed the permission back to the original 644)

Odd... very odd.

---

### Post by mjfleck2000 on 2007-03-18
>The *only* failure point here is the inability for a local user to read or access >/etc/hosts or /etc/nsswitch.conf.

BINGO!!!

The one file that, as a test, I did NOT change the permissions on was /etc/nsswitch.conf.  ls -l showed 600!  I changed it to 644 and users can ping  /etc/hosts machines.

Thank you all for helping.

Mike

---

### Post by Mr. C. on 2007-03-18
Science works.

Set your permission back to 640 for /etc/hosts.conf, /etc/resolv.conf, and /etc/nsswitch.conf.  You certainly don't want those group/world writable.

Cheers,
MrC

---

### Post by dbott67 on 2007-03-18
Glad you got it working.  Good call, Mr. C.

I'm sorry if I sent you down the wrong path at the start, Mike. Mr. C.'s methodology is right --- look for the simple and obvious first, as it's probably the cause.

-Dave

---

### Post by TheTank on 2008-02-06
Sorry for dragging this one out from the ground but I would like to thank the posters for helping me with an issue I had, being that I was not able to resolve the hostname.

It was the nsswitch.conf permissions! argh!

Dunno what broke it but it works again. Thanks!

---

