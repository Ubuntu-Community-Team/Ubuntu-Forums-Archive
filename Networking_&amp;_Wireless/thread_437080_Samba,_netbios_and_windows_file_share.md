---
title: "Samba, netbios and windows file share"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by bagguley on 2007-05-08
Hey

Ive had a p2p file sharing network going for about a year between windows machines. In order to see each other i had to install NETBIOS onto the wired network connection. Simple and it worked. However I now use and love Ubuntu.

Now the networks still fine but I cant see anyone and no-one can see me.

What Ive done so far.

1.  Installed Samba smbfs smbclient and winbind
2.  Changed the workgroup name in etc/samba/smb.conf
3.  Shared files by right click, share, share through windows network (SMB) etc..

Any ideas?

---

### Post by spd106 on 2007-05-10
Have you added the line

netbios name = <hostname>

to your smb.conf?

---

### Post by dbott67 on 2007-05-10
Here's my little HOWTO:

Install the following packages from the repos:

```
 sudo apt-get install samba smbfs smbclient winbind
```[U][B]

BACKGROUND

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

```After installing samba, winbind & smbfs, you need to configure samba and add your Windows XP accounts to samba, where *[COLOR=Blue]username[/COLOR]* is the login name of your Windows XP computer (use the same password for both accounts)
```
sudo  smbpasswd -a [COLOR=Blue]*username*[/COLOR]

New SMB password:
Retype new SMB password:
Added user username.
```For more information, please read this document:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

-Dave

---

### Post by bagguley on 2007-05-12
Yup did that.

I can now see the network but cant access it. I havn`t put any password in as the windows shares are completely password free.

---

### Post by Flocculus on 2007-06-20
dbott67, I am an ubuntu and Unix newbie and was having one heckuva time figuring out why I could see my Vista share but not access files in it. Your HowTo solved my problem. Thank you very much.

---

