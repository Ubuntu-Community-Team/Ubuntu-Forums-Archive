---
title: "Problem Browsing Network Servers"
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by dschaller on 2007-04-11
I'm currently running Edgy and I've had this problem for a long time. Often when I go to Places -> Network Servers, nothing shows up in Nautilus. No names for anything on the network. Not even the name of the local computer will show up. However, when I browse using the IP of the computer (for example, smb://192.168.1.101) then I can access shared folders, etc. When I browse using the name of the machine (for example, smb://molly) then no go.

Oddly, sometimes after a reboot, it works correctly and will show the names of the computers on the network. Sometimes it doesn't. I cannot figure why. Is it looking for specific IP addresses to match with specific host names and sometimes when I boot the IP handed out by my router is what it's looking for and sometimes it isn't? I have no idea. I know very little about networking.

I've looked at a lot of threads here and haven't been able to find a solution. Something is going on with resolving the names of the computers on the network.

Does anyone know how I can fix this?

---

### Post by dbott67 on 2007-04-11
You need to install the following packages from the repos:

```
 sudo apt-get install samba smbfs smbclient winbind
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

### Post by dschaller on 2007-04-11
I am still having the same problem. I think I have everything installed and configured according to these directions.

---

### Post by dschaller on 2007-04-11
When I do a "sudo smbtree" this is what I get:

WORKGROUP
	\\MOLLY          		Samba 3.0.22
Error connecting to 192.168.1.100 (No route to host)
cli_start_connection: failed to connect to MOLLY<20> (192.168.1.100)

It is like the name is resolving to the wrong address. MOLLY is at 192.168.1.101

When I do "sudo findsmb" everything is shown correctly.

---

### Post by dschaller on 2007-04-12
I just did a clean install of Edgy on another computer. Exactly the same problem. Nautilus won't show any machines on the network.

---

### Post by MikeEvans on 2007-04-23
I had this same problem.  In fact I was just looking for more information on it when I found this thread.  I ran smbtree to see what type of info it could provide and I saw my smb network without any errors.  Then I tried browsing the network and it worked!  I did not perform any of the steps listed in this thread.  Yesterday I followed this guide:

[HOWTO: Setup Samba peer-to-peer with Windows]("http://ubuntuforums.org/showthread.php?t=202605")

When I finished I ran some tests and it seemed that network browsing by name still wasn't working.  Since then all my machines have rebooted at least once and it seems that the configuration eventually started working.  Here are some more observations about my issue.

[LIST]
[*]I got into Ubuntu for the first time about a month ago with a clean Edgy install.
[*]For the first week I could browse my SMB network.  This worked out-of-the-box.  No configuration.  I'm not sure if the WINS server is activated by default or not.
[*]Suddenly, during the second week, I could no longer browse the network or resolve network names.  The only change to the system that might of affected the network was some routine updates provided by the built-in notifier.
[*]I could still access SMB shares through the IP address.
[*]Upgraded to Feisty and still had the same issue.
[*]Been trying to fix it ever since and now, suddenly, it seems to be working  :)
[*]My best guess is that the guide I linked to above fixed it.
[/LIST]

---

### Post by Strannik on 2007-05-11
I want to also say that i have this problem. and it looks like i started to have it after i installed samba. i tried to deinstall it but it didn't help. i put the security level to share and still it asks for the password. Can anybody help me with this annoying problem? i just can't see the whole list of servers in the workgroup.. if i put their name in or ip, it works ok... please help =)

---

### Post by servant74 on 2007-07-31
I am having the same issue with 6.06LTS.

        \\TESLA                         Tesla server (Samba, Ubuntu)
                \\TESLA\dfx             Epson DFX-8000 Dot-Matrix
                \\TESLA\Epson           Stylus-Color-740
 <snip>
                \\TESLA\outgoing        Files you may want
                \\TESLA\incoming        Put incoming files here
                \\TESLA\IPC$            IPC Service (Tesla server (Samba, Ubuntu))
                \\TESLA\ADMIN$          IPC Service (Tesla server (Samba, Ubuntu))
        \\JACK                          Dining room
cli_start_connection: failed to connect to JACK<20> (0.0.0.0)
        \\EDISON                        edison server (Samba, Ubuntu)
                \\EDISON\print$                 Printer Drivers
                \\EDISON\cdrom                  Samba server's CD-ROM
                \\EDISON\outgoing               Files you might want
                \\EDISON\NC                     Incoming NC Programs
                \\EDISON\IPC$                   IPC Service (edison server (Samba, Ubuntu))
                \\EDISON\ADMIN$                 IPC Service (edison server (Samba, Ubuntu))
        \\CAROL                         Carol under the stairs
                \\CAROL\Incomming
                \\CAROL\C$              Default share
                \\CAROL\ADMIN$          Remote Admin
                \\CAROL\My Pictures
                \\CAROL\AdobePDF        Adobe PDF
<snip>

JACK is XPPro, ans so is CAROL, all machines are in the same workgroup.

Any suggestions?

---

