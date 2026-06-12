---
title: "How do I find network shares via the CLI"
date: 2013-12-13
forum: Networking &amp; Wireless
---

### Post by Herbon on 2013-12-13
I recently upgraded to 13.10, and found that completely lost access to shares via the CLI, but not the GUI.

The main reasons I used the CLI is,  I wanted to set up Rsync, automation, and manually moving certain files.

I tried the following commands but never found the path to my shares.

Yet the GUI shows the shares and files


> smbclient -L

:(
> Enter Newbie's password: 
session setup failed: NT_STATUS_LOGON_FAILURE


:(
> find . -wholename "smb://10.10.2.4./"



---

### Post by steeldriver on 2013-12-13
try ```
smbtree
```

---

### Post by Herbon on 2013-12-15
> **steeldriver said:**
> try ```
smbtree
```

So I tried this, but it don't show the path to drive. :(





 [http://www.samba.org/samba/docs/man/manpages/smbtree.1.html](http://www.samba.org/samba/docs/man/manpages/smbtree.1.html)

---

### Post by bab1 on 2013-12-15
> **Mr_Imhotep said:**
> So I tried this, but it don't show the path to drive. :(

 [http://www.samba.org/samba/docs/man/manpages/smbtree.1.html](http://www.samba.org/samba/docs/man/manpages/smbtree.1.html)

What does smbtree show?  Post the output of ```
smbtree
```

Samba hides the real path to the directory.  The display is /SERVER_NAME/share_name.  The path is defined in th the smb.conf file.  For example I have a share at */srv/data* but the share **name ** is _public_.  This share is shown as //SERVER_NAME/public.  No pathnames are displayed.

Post the output of ```
testparm -s 
```

---

### Post by Herbon on 2013-12-16
:confused:

> Terbon@11:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
Terbon@11:~$ 



---

### Post by bab1 on 2013-12-16
> **Mr_Imhotep said:**
> :confused:

Does this mean there is NO output from the command *smbtree*?  If so then post the output of ```
smbtree -d3
```...this raises the debug level.

I don't see any shares created by editing the smb.conf file.  What is the output of this command```
net usershare list --long
```...this lists any usershares you created using the GUI.

---

### Post by Herbon on 2013-12-17
[QUOTE=bab1;12875392]Does this mean there is NO output from the command *smbtree*?  If so then post the output of ```
smbtree -d3
```...this raises the debug level.

Terbon@11:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::216:36ff:fec6:ae0b%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=10.10.2.211 bcast=10.10.2.255 netmask=255.255.255.0
Enter Terbon's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_wins: Attempting wins lookup for name WORKGROUP<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 10.10.2.4 ( 10.10.2.4 )
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name NUBIA.COM<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name NUBIA.COM<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name NUBIA.COM<0x1d>
Got a positive name query response from 10.10.2.4 ( 10.10.2.4 )
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
Connecting to host=10.10.2.4
Connecting to 10.10.2.4 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
NUBIA.COM
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name NUBIA.COM<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name NUBIA.COM<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name NUBIA.COM<0x1d>
Got a positive name query response from 10.10.2.4 ( 10.10.2.4 )
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
Connecting to host=10.10.2.4
Connecting to 10.10.2.4 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
    \\STORA                  Stora
Connecting to host=STORA
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name STORA<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name STORA<0x20>
resolve_wins: Attempting wins lookup for name STORA<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name STORA<0x20>
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
Connecting to 98.124.195.10 at port 445
Connecting to 98.124.195.10 at port 139
Error connecting to 98.124.195.10 (Success)
cli_start_connection: failed to connect to STORA<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
    \\SOL_SYSTEM             
Connecting to host=SOL_SYSTEM
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name SOL_SYSTEM<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name SOL_SYSTEM<0x20>
resolve_wins: Attempting wins lookup for name SOL_SYSTEM<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name SOL_SYSTEM<0x20>
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
Connecting to 98.124.195.10 at port 445
Connecting to 98.124.195.10 at port 139
Error connecting to 98.124.195.10 (Success)
cli_start_connection: failed to connect to SOL_SYSTEM<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL


```
net usershare list --long
```
terbon@11:~$ net usershare list --long
net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

### Post by bab1 on 2013-12-17
> **Mr_Imhotep said:**
> 
```
Terbon@11:~$ smbtree -d3
added interface eth0 ip=10.10.2.211 bcast=10.10.2.255 netmask=255.255.255.0 [COLOR="#0000FF"]**<-- Using 10.0.0.0/24 network**[/COLOR]
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 10.10.2.4 ( 10.10.2.4 ) [COLOR="#0000FF"]**<-Master Browse List found**[/COLOR]

name_resolve_bcast: Attempting broadcast lookup for name NUBIA.COM<0x1d>[COLOR="#FF0000"]<- This is wrong.  You should not use 
a tld like .com domain with a private IP address[/COLOR]
Got a positive name query response from 10.10.2.4 ( 10.10.2.4 )[COLOR="#0000FF"]**Samba did connect in this instance**[/COLOR]
Connecting to host=10.10.2.4
Connecting to 10.10.2.4 at port 445
Doing spnego session setup (blob length=58)
SPNEGO login failed: Logon failure NUBIA.COM [COLOR="#FF0000"]But failed the login.[/COLOR]
```

Samba knows the host is available but can't log in
> 
```

SPNEGO login failed: Logon failure[COLOR="#FF0000"]Samba tries multiple times to log in but fails again[/COLOR]
    \\STORA                  Stora
Connecting to host=STORA

resolve_hosts: Attempting host lookup for name STORA<0x20> [COLOR="#FF0000"]Again it tries using hostname[/COLOR]

Connecting to 98.124.195.10 at port 445[COLOR="#800080"][B]Because you have used a public DNS tld (.com) the DNS routines 
are looking to the Internet for resolution -- This needs to be fixed by your reconfiguring the hostname and sufix[/B][/COLOR]
Connecting to 98.124.195.10 at port 139
Error connecting to 98.124.195.10 (Success)
cli_start_connection: failed to connect to STORA<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
    \\SOL_SYSTEM             
Connecting to host=SOL_SYSTEM

Connecting to 98.124.195.10 at port 445
Connecting to 98.124.195.10 at port 139
Error connecting to 98.124.195.10 (Success)
cli_start_connection: failed to connect to SOL_SYSTEM<20> (0.0.0.0). [COLOR="#800080"]Error NT_STATUS_UNSUCCESSFUL -- Most
likely due to lack of name resolution.[/COLOR]

```
The above appears to be 2 problems -- can't log in and can't resolve the hostname to NETBIOS name.
```
net usershare list --long
```
terbon@11:~$ net usershare list --long
net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
Do you really have any shares at all?  The above says no.  So how are you seeing these shares via the GUI?  Explain the steps or provide a screen shot showing the shares.

I think the entire thing should be redone.  By that I mean you should move the /etc/samba/smb.conf file to /etc/samba/smb.conf .old  Then copy a known good copy of this file.  I will attach one for you to use.

Then you need to edit the /etc/hosts file for the host SOL and the host NUBIA.COM.  How many hosts (computers) are there in this network?

Post the output of these 2 commands from both machines```
hostname

cat /etc/hosts
```

---

### Post by Herbon on 2013-12-18
I'm able to do a drag and down via the GUI, and I even saved the link in my bookmarks.

I'll check my set up later tonight

---

### Post by bab1 on 2013-12-18
> **Mr_Imhotep said:**
> I'm able to do a drag and down via the GUI, and I even saved the link in my bookmarks.

I'll check my set up later tonight
What does that really mean?  The prior output says there are no shares created? Explain with a little more detail.  I can't really visualize what out mean by the above.  The GUI interface is really Gnome Nautilus that can browse the local machine as well as mounting remote file systems to the local host.  You should be more specific in what you are describing.

---

### Post by Herbon on 2013-12-20
> **bab1 said:**
> What does that really mean?  The prior output says there are no shares created? Explain with a little more detail.  I can't really visualize what out mean by the above.  The GUI interface is really Gnome Nautilus that can browse the local machine as well as mounting remote file systems to the local host.  You should be more specific in what you are describing.


If your familiar with 13.10, under "File" folder, there and option to "Connect to server"
I entered my NAS address (10.10.2.4) in the listed box, which then displays the following "smb://10.10.2.4./music/" in the GUI aka Graphic User Interface

Yet when I type in "*smb://10.10.2.4./music/*" in the CLI, I get "-bash: smb://10.10.2.4./music/: No such file or directory". :(

I ran "*find /. -iname "*.mp3*"

Which showed me the following path "/run/user/1000/gvfs/smb-share:server=10.10.2.4.,share=mylibrary/Network_Media_Audio/" 

I shortened it to "/run/user/1000/gvfs/" and ran "*LS*" to show all of my share. :)

Has anyone seen this before??

---

### Post by bab1 on 2013-12-21
> **Mr_Imhotep said:**
> If your familiar with 13.10, under "File" folder, there and option to "Connect to server"
I entered my NAS address (10.10.2.4) in the listed box, which then displays the following "smb://10.10.2.4./music/" in the GUI aka Graphic User Interface

Yet when I type in "*smb://10.10.2.4./music/*" in the CLI, I get "-bash: smb://10.10.2.4./music/: No such file or directory". :(

I ran "*find /. -iname "*.mp3*"

Which showed me the following path "/run/user/1000/gvfs/smb-share:server=10.10.2.4.,share=mylibrary/Network_Media_Audio/" 

I shortened it to "/run/user/1000/gvfs/" and ran "*LS*" to show all of my share. :)

Has anyone seen this before??
That is the normal LOCAL *mount point *for a Samba share.  It is not the path to the share in the server side sense.  You should not need to do anything extra from the client side afer you mount the share via the gui (e.g. smb://server_IP/SHARE_NAME. or clicking on the icon that appears, showing the share as mounted on the client side machine).  

If you can mount the share and it doesn't appear on the left of the file manager then we need to dig deeper on the server side.  I was under the impression we already were doing that.  :-(

From the server CLI -- post the output of this ```
testparm -s
```

For the time being we are only testing the server. Later we will test on the client.

---

### Post by Morbius1 on 2013-12-21
>  Yet when I type in "*smb://10.10.2.4./music/*" **[COLOR=#0000cd]in the CLI[/COLOR]**, I get "-bash: smb://10.10.2.4./music/: No such file or directory". :sad:
Because bash has no idea what "smb://10.10.2.4./music/" means - there is no command there.

If you want the equivalent of how "connect to server" does it the command in the terminal is this:
```
gvfs-mount smb://10.10.2.4./music
```
And the share will be mounted in the same place "Connect to Server" would have mounted it: /run/user/1000/gvfs/

---

### Post by bab1 on 2013-12-21
> **Morbius1 said:**
> Because bash has no idea what "smb://10.10.2.4./music/" means - there is no command there.

If you want the equivalent of how "connect to server" does it the command in the terminal is this:
```
gvfs-mount smb://10.10.2.4./music
```
And the share will be mounted in the same place "Connect to Server" would have mounted it: /run/user/1000/gvfs/
Nice catch there.  I guess this distracted me> I ran "find /. -iname "*.mp3".  Which [COLOR="#0000FF"]showed me the following path "/run/user/1000/gvfs[/COLOR]/smb-share:server=10.10.2.4.,share=mylibrary/Network_Media_Audio/".  I shortened it to "/run/user/1000/gvfs/" and[COLOR="#0000FF"] ran "LS" to show all of my share[/COLOR]

How can the share data be available at the mount point if the obviously incorrect command has been issued?  Your considerate comments are always welcome.  Everyone has there own method of diagnosis.  I tend to start with the server.  It appears that the OP and I where not on the same page.

---

### Post by Morbius1 on 2013-12-21
There's actually many things about the data presented I don't understand:

*** He's entering the ip address with a trailing dot which I didn't even know you can do until I tried it myself.

*** He specifies the ip address and the music share in "connect to server" and ends up with a mount point at .... "share=mylibrary/Network_Media_Audio/" instead of ... well ... music.

*** Any why is it "/run/user/1000/gvfs/..." and not "/run/user/mr_imhotep/gvfs/..."

But he's been pretty persistent over the last several days in his insistence on entering "smb://10.10.2.4./music" in the terminal and expecting a different result so ...

[COLOR=#0000cd]**EDIT**: Well I figured out "/run/user/1000/gvfs" - it seems 13.10 does that now. Seems like a bad idea to me but who am I.[/COLOR]

---

### Post by bab1 on 2013-12-21
> **Morbius1 said:**
> There's actually many things about the data presented I don't understand:

*** He's entering the ip address with a trailing dot which I didn't even know you can do until I tried it myself.

*** He specifies the ip address and the music share in "connect to server" and ends up with a mount point at .... "share=mylibrary/Network_Media_Audio/" instead of ... well ... music.

*** Any why is it "/run/user/1000/gvfs/..." and not "/run/user/mr_imhotep/gvfs/..."

But he's been pretty persistent over the last several days in his insistence on entering "smb://10.10.2.4./music" in the terminal and expecting a different result so ...
In a way, that's why I just want the OP to just give me the info I want (what my eyes expect to see).  But when he is using the CLI on the client and I want server info...well...we get confusion on both sides. ;-)

> [COLOR="#0000FF"]EDIT: Well I figured out "/run/user/1000/gvfs" - it seems 13.10 does that now. Seems like a bad idea to me but who am I.[/COLOR]I hate it when the do that.  As to the second question, we are just the end user.  Not very important.  I only read the change logs when I update.  I'm on 12.04

---

