---
title: "Trouble with DNS and file sharing"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by gantww on 2007-05-29
Hello all,
I'm trying to get my small network operational. I can now see my server (192.168.3.1, aka. Sauron). Both my desktop and laptop can see it. All three are running Ubuntu and are on the same subnet using DHCP. Anyway, there are two things I can't seem to do, which may or may not be related.

1) I can't resolve the name Sauron on my network. All I can do is hit it by IP address. As recommended, I installed Bind on the server (Sauron, in this case). However, I'm not sure what to do to get the other machines to recognize that the server is a DNS server.
2) I also can't seem to share files from the server to either of the clients, using either NFS or Samba. I dimly remember a professor in my networking class talking about a similar issue with Samba failing when DNS didn't work, but I wasn't paying close enough attention. I'm not even really sure how to connect to an NFS share, as all I've ever used in the past were samba shares.

Any ideas?

---

### Post by gantww on 2007-05-29
A little more information, I'm not seeing Bind listed under services, even though it is installed. I haven't done any configuration on it. Could it be turned off by default? I also did a portscan on the machine, and it doesn't appear to be listening for DNS requests.

Thoughts?

---

### Post by dbott67 on 2007-05-29
Setting up a DNS server can be overly complex (and perhaps overkill) for what you're trying to achieve.

**Dynamic name resolution** can be achieved through **DNS** or through **WINS** (which is the old Microsoft way of doing things).  In Linux, the 'winbind' package takes care of this.

**Static name resolution** can be achieve by placing the ip address & hostname of each computer in the **/etc/hosts** file.  Of course, this method relies on static IP addresses, or else you may have name resolution issues if the DHCP server assigns a different IP address to a client.

So, if you want a fast & easy way to have dynamic name resolution, there are 2 essential ingredients to make this work: [B]samba & winbind

[/B]*[COLOR=Purple]Note: this part was originally written for name resolution issues between Linux & Windows, but it works just as well between Linux machines.[/COLOR]*

1. Install **samba, smbclient, smbfs** and **winbind** [COLOR=Blue]*(I also install smbclient & smbfs so that I can mount smb shares)*[/COLOR]
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

### Post by bennyj on 2007-05-30
Very nice explanation!

---

