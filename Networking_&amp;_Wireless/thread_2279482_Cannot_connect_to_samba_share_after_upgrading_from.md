---
title: "Cannot connect to samba share after upgrading from 14.10 to 15.04"
date: 2015-05-23
forum: Networking &amp; Wireless
---

### Post by janot2012 on 2015-05-23
[COLOR=#111111][FONT=Ubuntu]My Blackberry Playbook mounts samba share when connected via usb cable:
[/FONT][/COLOR]
[ATTACH=CONFIG]262157[/ATTACH]

Now when trying to open share I get following error:

[ATTACH=CONFIG]262158[/ATTACH]

```
~$ smbclient -L 169.254.0.1 -N
    Connection to 169.254.0.1 failed (Error NT_STATUS_IO_TIMEOUT)
```


```
~$ ping -c 1 169.254.0.1
    PING 169.254.0.1 (169.254.0.1) 56(84) bytes of data.
    --- 169.254.0.1 ping statistics ---
    1 packets transmitted, 0 received, 100% packet loss, time 0ms
```

[COLOR=#111111][FONT=Ubuntu]I've tried to reinstall samba completely - no effect[/FONT][/COLOR]

Any ideas? Thanks

---

### Post by bab1 on 2015-05-23
> **janot2012 said:**
> ... when trying to open share I get following error:

[ATTACH=CONFIG]262158[/ATTACH]

```
~$ smbclient -L 169.254.0.1 -N
    Connection to 169.254.0.1 failed (Error NT_STATUS_IO_TIMEOUT)
```


```
~$ ping -c 1 169.254.0.1
    PING 169.254.0.1 (169.254.0.1) 56(84) bytes of data.
    --- 169.254.0.1 ping statistics ---
    1 packets transmitted, 0 received, 100% packet loss, time 0ms
```

[COLOR=#111111][FONT=Ubuntu]I've tried to reinstall samba completely - no effect[/FONT][/COLOR]

Any ideas? Thanks
I don't believe you can use a link local address when using Samba.  The ***smbclient*** and ***ping*** commands clearly shows that you can't connect to the host with the address 169.254.0.1.  What is the ip address of the machine you issued the ping command from?  You can see it with this command```
ifconfig
```...post the output back here.

---

### Post by janot2012 on 2015-05-23
> **bab1 said:**
> I don't believe you can use a link local address when using Samba.  The ***smbclient*** and ***ping*** commands clearly shows that you can't connect to the host with the address 169.254.0.1.  What is the ip address of the machine you issued the ping command from?  You can see it with this command```
ifconfig
```...post the output back here.
169.254.0.2

```
usb0      Link encap:Ethernet  HWaddr 72:d4:f2:02:42:38  
          inet addr:169.254.0.2  Bcast:169.254.0.3  Mask:255.255.255.252
          inet6 addr: fe80::70d4:f2ff:fe02:4238/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2942 (2.9 KB)  TX bytes:15024 (15.0 KB)



```

---

### Post by bab1 on 2015-05-23
> **janot2012 said:**
> 169.254.0.2

```
usb0      Link encap:Ethernet  HWaddr 72:d4:f2:02:42:38  
          inet addr:169.254.0.2  Bcast:169.254.0.3  Mask:255.255.255.252
          inet6 addr: fe80::70d4:f2ff:fe02:4238/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2942 (2.9 KB)  TX bytes:15024 (15.0 KB)



```
Configure both machines to use a network such as 192.168.0.0 (with a subnet mask of 255.255.255.0) so that you can use TCP functionality.  Ping is a TCP/IP tool and you don't have any TCP functions. Samba is the same way.  The Link Local addresses of the 169.254 range will not work.

---

### Post by janot2012 on 2015-05-23
> **bab1 said:**
> Configure both machines to use a network such as 192.168.0.0 (with a subnet mask of 255.255.255.0) so that you can use TCP functionality.  Ping is a TCP/IP tool and you don't have any TCP functions. Samba is the same way.  The Link Local addresses of the 169.254 range will not work.
That's not possible on Blackberry Playbook, even in development mode I can choose only from 169.254.*.*

[ATTACH=CONFIG]262165[/ATTACH]

---

### Post by bab1 on 2015-05-23
> **janot2012 said:**
> That's not possible on Blackberry Playbook, even in development mode I can choose only from 169.254.*.*

[ATTACH=CONFIG]262165[/ATTACH]
[s]Then you will not be able to use Samba.[/s]

[COLOR="#0000FF"]Edit:  Of course as soon as I have said the above I see this Samba reference at Blackberry's web site: [/COLOR] [http://btsc.webapps.blackberry.com/btsc/viewdocument.do;jsessionid=6BA4BA8DDA3D39D029834DD26C98AA95?externalId=KB32702&sliceId=2&cmd=displayKC&docType=kc&noCount=true&ViewedDocsListHelper=com.kanisa.apps.common.BaseViewedDocsListHelperImpl]("http://btsc.webapps.blackberry.com/btsc/viewdocument.do;jsessionid=6BA4BA8DDA3D39D029834DD26C98AA95?externalId=KB32702&sliceId=2&cmd=displayKC&docType=kc&noCount=true&ViewedDocsListHelper=com.kanisa.apps.common.BaseViewedDocsListHelperImpl")

[COLOR="#0000FF"]This might be relevant also:  [/COLOR] [https://supportforums.blackberry.com/t5/BlackBerry-10-Functions-and/How-to-use-blackberry-10-device-from-GNU-Linux-mounting-remote/td-p/2431411]("https://supportforums.blackberry.com/t5/BlackBerry-10-Functions-and/How-to-use-blackberry-10-device-from-GNU-Linux-mounting-remote/td-p/2431411")

[COLOR="#0000FF"]Via Wi-Fi : [/COLOR] [http://www.canbike.org/information-technology/blackberry-playbook-wi-fi-file-share-via-samba.html]("http://www.canbike.org/information-technology/blackberry-playbook-wi-fi-file-share-via-samba.html") [COLOR="#0000FF"]Of course this uses a proper (non-link-local IP address) and Wi-Fi.[/COLOR]

---

### Post by janot2012 on 2015-05-24
> **bab1 said:**
> [s]Then you will not be able to use Samba.[/s]

[COLOR=#0000FF]Edit:  Of course as soon as I have said the above I see this Samba reference at Blackberry's web site: [/COLOR] [http://btsc.webapps.blackberry.com/btsc/viewdocument.do;jsessionid=6BA4BA8DDA3D39D029834DD26C98AA95?externalId=KB32702&sliceId=2&cmd=displayKC&docType=kc&noCount=true&ViewedDocsListHelper=com.kanisa.apps.common.BaseViewedDocsListHelperImpl](http://btsc.webapps.blackberry.com/btsc/viewdocument.do;jsessionid=6BA4BA8DDA3D39D029834DD26C98AA95?externalId=KB32702&sliceId=2&cmd=displayKC&docType=kc&noCount=true&ViewedDocsListHelper=com.kanisa.apps.common.BaseViewedDocsListHelperImpl)

[COLOR=#0000FF]This might be relevant also:  [/COLOR] [https://supportforums.blackberry.com/t5/BlackBerry-10-Functions-and/How-to-use-blackberry-10-device-from-GNU-Linux-mounting-remote/td-p/2431411](https://supportforums.blackberry.com/t5/BlackBerry-10-Functions-and/How-to-use-blackberry-10-device-from-GNU-Linux-mounting-remote/td-p/2431411)

[COLOR=#0000FF]Via Wi-Fi : [/COLOR] [http://www.canbike.org/information-technology/blackberry-playbook-wi-fi-file-share-via-samba.html](http://www.canbike.org/information-technology/blackberry-playbook-wi-fi-file-share-via-samba.html) [COLOR=#0000FF]Of course this uses a proper (non-link-local IP address) and Wi-Fi.[/COLOR]

The thing is that it was "just working" until upgrade to 15.04
When I'm trying to connect using instruction provided at that link to blackberry forums I also get network error:
```
mount error: could not resolve address for PLAYBOOK-41C2: Unknown error
```
Wi-Fi connection is working, but it 's very slow and often interrupts

---

### Post by bab1 on 2015-05-24
> **janot2012 said:**
> The thing is that it was "just working" until upgrade to 15.04
When I'm trying to connect using instruction provided at that link to blackberry forums I also get network error:
```
mount error: could not resolve address for PLAYBOOK-41C2: Unknown error
```
Wi-Fi connection is working, but it 's very slow and often interrupts

It's a little confusing as to what the network setup is.  Are you attempting to use Wi-Fi?  I assume we have an Ubuntu host and the Blackberry host.  Which machine is PLAYBOOK-41C2?  Which machine is the server and which machine is the client?  Are the error messages all from the Ubuntu machine?  What was the command used that generated the error?

What is configured differently between before (14.10) and now (15.04).  The Samba package on Ubuntu has not changed since 14.04.  Is the Blackberry configuration the same as before?

---

### Post by janot2012 on 2015-05-24
> **bab1 said:**
> It's a little confusing as to what the network setup is.  Are you attempting to use Wi-Fi?  I assume we have an Ubuntu host and the Blackberry host.  Which machine is PLAYBOOK-41C2?  Which machine is the server and which machine is the client?  Are the error messages all from the Ubuntu machine?  What was the command used that generated the error?

What is configured differently between before (14.10) and now (15.04).  The Samba package on Ubuntu has not changed since 14.04.  Is the Blackberry configuration the same as before?
I'm not using Wi-Fi here (it works as expected).
PLAYBOOK-41C2 is network name of Blackberry Playbook:

[ATTACH=CONFIG]262185[/ATTACH]

As I understand Blackberry Playbook is server and Ubuntu PC is client here.
All error messages are from Ubuntu PC
Command that generated last error was 
```
sudo mount -t cifs //PLAYBOOK-41C2/media ~/mnt/media -o username=janot%mypassword
```
from post on blackberry forum to which you gave link in your previous post

I haven't changed any network configs since 14.10. At least I don't remember doing that intentionally, maybe just added some network shares. 
Blackberry's configuration is the same (there is practically nothing to change).

---

### Post by bab1 on 2015-05-24
> **janot2012 said:**
> I'm not using Wi-Fi here (it works as expected).
PLAYBOOK-41C2 is network name of Blackberry Playbook:

[ATTACH=CONFIG]262185[/ATTACH]

As I understand Blackberry Playbook is server and Ubuntu PC is client here.
All error messages are from Ubuntu PC
Command that generated last error was 
```
sudo mount -t cifs //PLAYBOOK-41C2/media ~/mnt/media -o username=janot%mypassword
```
from post on blackberry forum to which you gave link in your previous post

I haven't changed any network configs since 14.10. At least I don't remember doing that intentionally, maybe just added some network shares. 
Blackberry's configuration is the same (there is practically nothing to change).

First a comment about your mount command.  You should always use an **absolute path **in your command.  the ~ is not valid here.  First of all the ~ is used to mean the *"user's home directory" *and in this instance the user is root (via sudo), and therefore that would mean */root* (e.g. /root/mnt.media).  The command failed before this became an issue however.  When you use the mount command you should use a directory path that starts with: / (i.e. /mnt.media)

[COLOR="#0000FF"]Edit:  The option **username=janot%mypassword** is not correct either.[/COLOR]

Post the output of this command (always from Ubuntu)```
cat /etc/hosts
```...and this command```
hostname
```...and also this command```
smbtree -d3
```...and lastly this command```
arp -a
```

---

### Post by janot2012 on 2015-05-24
> **bab1 said:**
> First a comment about your mount command.  You should always use an **absolute path **in your command.  the ~ is not valid here.  First of all the ~ is used to mean the *"user's home directory" *and in this instance the user is root (via sudo), and therefore that would mean */root* (e.g. /root/mnt.media).  The command failed before this became an issue however.  When you use the mount command you should use a directory path that starts with: / (i.e. /mnt.media)

[COLOR=#0000FF]Edit:  The option **username=janot%mypassword** is not correct either.[/COLOR]

Post the output of this command (always from Ubuntu)```
cat /etc/hosts
```...and this command```
hostname
```...and also this command```
smbtree -d3
```...and lastly this command```
arp -a
```

Thanks for explanation about mount command

```
$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    ACER


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```
```
$ hostname
ACER

```

```
$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface usb0 ip=169.254.0.2 bcast=169.254.0.3 netmask=255.255.255.252
added interface wlan0 ip=192.168.0.168 bcast=192.168.0.255 netmask=255.255.255.0
added interface virbr0 ip=192.168.122.1 bcast=192.168.122.255 netmask=255.255.255.0
added interface pan1 ip=10.66.145.1 bcast=10.66.145.255 netmask=255.255.255.0
Enter janot's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.168 ( 10.66.145.1 )
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f8c39d58330] mpx_fde[(nil)] fd[14] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f8c39d594c0] mpx_fde[(nil)] fd[12] - disabling
samba_tevent: EPOLL_CTL_MOD EBADF for fde[0x7f8c39d5a650] mpx_fde[(nil)] fd[10] - disabling
Connecting to 10.66.145.1 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 169.254.0.2 ( 10.66.145.1 )
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f8c39d6c080] mpx_fde[(nil)] fd[14] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f8c39d69d70] mpx_fde[(nil)] fd[12] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f8c39d6d210] mpx_fde[(nil)] fd[10] - disabling
Connecting to 10.66.145.1 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
    \\PLAYBOOK-41C2          Samba (localhost)
resolve_lmhosts: Attempting lmhosts lookup for name PLAYBOOK-41C2<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name PLAYBOOK-41C2<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name PLAYBOOK-41C2<0x20>
resolve_hosts: getaddrinfo failed for name PLAYBOOK-41C2 [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name PLAYBOOK-41C2<0x20>
Got a positive name query response from 169.254.0.1 ( 169.254.0.1 )
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f8c39d70320] mpx_fde[(nil)] fd[17] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f8c39d6f1b0] mpx_fde[(nil)] fd[15] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f8c39d6e020] mpx_fde[(nil)] fd[13] - disabling
Connecting to 169.254.0.1 at port 445
Connecting to 169.254.0.1 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f8c39d67c10] mpx_fde[(nil)] fd[12] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f8c39d68b30] mpx_fde[(nil)] fd[13] - disabling
    \\ACER                   ACER server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name ACER<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name ACER<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name ACER<0x20>
Connecting to 127.0.1.1 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\ACER\Samsung-SCX-3400-Series-WiFi    Samsung SCX-3400 Series
        \\ACER\Samsung-SCX-3400-Series-USB    Samsung SCX-3400 Series USB
        \\ACER\print$             Printer Drivers
        \\ACER\IPC$               IPC Service (ACER server (Samba, Ubuntu))

```

```
$ arp -a
? (192.168.0.169) at 70:d4:f2:02:42:33 [ether] on wlan0
? (192.168.0.2) at <incomplete> on wlan0
? (192.168.0.4) at <incomplete> on wlan0
? (192.168.0.100) at c8:dd:c9:d0:0f:4b [ether] on wlan0
? (192.168.0.176) at <incomplete> on wlan0
? (169.254.0.1) at 72:d4:f2:02:42:33 [ether] on usb0
? (192.168.0.1) at c0:4a:00:2d:ea:18 [ether] on wlan0
? (192.168.0.5) at <incomplete> on wlan0
? (169.254.12.73) at <incomplete> on wlan0
? (192.168.0.13) at <incomplete> on wlan0
? (192.168.0.254) at <incomplete> on wlan0

```

---

### Post by bab1 on 2015-05-24
> **janot2012 said:**
> Thanks for explanation about mount command

```
$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    ACER


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```


Add this line to the /etc/hosts file under the localhost and ACER lines```

169.254.0.2 PLAYBOOK-41C2
```...the file should look like this```
127.0.0.1    localhost
127.0.1.1    ACER
169.254.0.2 PLAYBOOK-41C2

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

Then post the output of this again```
cat /etc/hosts
```...and this```
smbtree -d3
```

---

### Post by janot2012 on 2015-05-24
> **bab1 said:**
> 
Then post the output of this again```
cat /etc/hosts
```...and this```
smbtree -d3
```

```
$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    ACER
169.254.0.2 PLAYBOOK-41C2


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

```
$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface usb0 ip=169.254.0.2 bcast=169.254.0.3 netmask=255.255.255.252
added interface wlan0 ip=192.168.0.168 bcast=192.168.0.255 netmask=255.255.255.0
added interface virbr0 ip=192.168.122.1 bcast=192.168.122.255 netmask=255.255.255.0
added interface pan1 ip=10.66.145.1 bcast=10.66.145.255 netmask=255.255.255.0
Enter janot's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.168 ( 10.66.145.1 )
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f8b39ba0650] mpx_fde[(nil)] fd[14] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f8b39b9f400] mpx_fde[(nil)] fd[12] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f8b39b9e270] mpx_fde[(nil)] fd[10] - disabling
Connecting to 10.66.145.1 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.168 ( 10.66.145.1 )
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f8b39bb3230] mpx_fde[(nil)] fd[16] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f8b39bb2090] mpx_fde[(nil)] fd[14] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f8b39bb0f00] mpx_fde[(nil)] fd[12] - disabling
Connecting to 10.66.145.1 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
    \\PLAYBOOK-41C2          Samba (localhost)
resolve_lmhosts: Attempting lmhosts lookup for name PLAYBOOK-41C2<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name PLAYBOOK-41C2<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name PLAYBOOK-41C2<0x20>
Connecting to 169.254.0.2 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\PLAYBOOK-41C2\Samsung-SCX-3400-Series-WiFi    Samsung SCX-3400 Series
        \\PLAYBOOK-41C2\Samsung-SCX-3400-Series-USB    Samsung SCX-3400 Series USB
        \\PLAYBOOK-41C2\print$             Printer Drivers
        \\PLAYBOOK-41C2\IPC$               IPC Service (ACER server (Samba, Ubuntu))
    \\ACER                   ACER server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name ACER<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name ACER<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name ACER<0x20>
Connecting to 127.0.1.1 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\ACER\Samsung-SCX-3400-Series-WiFi    Samsung SCX-3400 Series
        \\ACER\Samsung-SCX-3400-Series-USB    Samsung SCX-3400 Series USB
        \\ACER\print$             Printer Drivers
        \\ACER\IPC$               IPC Service (ACER server (Samba, Ubuntu))

```

---

### Post by bab1 on 2015-05-24
> **janot2012 said:**
> 

[CODE]
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
    \\PLAYBOOK-41C2          Samba (localhost)
resolve_lmhosts: Attempting lmhosts lookup for name PLAYBOOK-41C2<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name PLAYBOOK-41C2<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name PLAYBOOK-41C2<0x20>
Connecting to 169.254.0.2 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\PLAYBOOK-41C2\Samsung-SCX-3400-Series-WiFi    Samsung SCX-3400 Series
        \\PLAYBOOK-41C2\Samsung-SCX-3400-Series-USB    Samsung SCX-3400 Series USB
        \\PLAYBOOK-41C2\print$             Printer Drivers
        \\PLAYBOOK-41C2\IPC$               IPC Service (ACER server (Samba, Ubuntu))
 

Looks like it is working now?  Try and browse to the Playbook shares as you would normally do.  Does it work?  Can you access the shares?

---

### Post by janot2012 on 2015-05-24
> **bab1 said:**
> Looks like it is working now.  Try and browse to the Playbook shares as you would normally do.  Does it work?  Can you access the shares?
Still not working
These lines look strange 
```
[COLOR=#000000]*\\PLAYBOOK-41C2\Samsung-SCX-3400-Series-WiFi Samsung SCX-3400 Series*[/COLOR]
[COLOR=#000000]*\\PLAYBOOK-41C2\Samsung-SCX-3400-Series-USB Samsung SCX-3400 Series USB*[/COLOR]
[COLOR=#000000]*\\PLAYBOOK-41C2\print$ Printer Drivers*[/COLOR]
[COLOR=#000000]*\\PLAYBOOK-41C2\IPC$ IPC Service (ACER server (Samba, Ubuntu))*[/COLOR]
```
Printer is actually connected to Ubuntu PC (ACER)

---

### Post by bab1 on 2015-05-24
> **janot2012 said:**
> Still not working
These lines look strange 
```
[COLOR=#000000]*\\PLAYBOOK-41C2\Samsung-SCX-3400-Series-WiFi Samsung SCX-3400 Series*[/COLOR]
[COLOR=#000000]*\\PLAYBOOK-41C2\Samsung-SCX-3400-Series-USB Samsung SCX-3400 Series USB*[/COLOR]
[COLOR=#000000]*\\PLAYBOOK-41C2\print$ Printer Drivers*[/COLOR]
[COLOR=#000000]*\\PLAYBOOK-41C2\IPC$ IPC Service (ACER server (Samba, Ubuntu))*[/COLOR]
```
Printer is actually connected to Ubuntu PC (ACER)

Those are the shares on PLAYBOOK-41C2.  These are the root of the shared directory and the printer drivers.  

You should see the Windows Sharing folder.  Inside of that should be the WORKGROUP and inside of the WORKGROUP should be all the shares.  What do you see when you browse that way?  Do you have a data share?  Check directly on the Playbook for that.

---

### Post by janot2012 on 2015-05-24
> **bab1 said:**
> Those are the shares on PLAYBOOK-41C2.  These are the root of the shared directory and the printer drivers.  

You should see the Windows Sharing folder.  Inside of that should be the WORKGROUP and inside of the WORKGROUP should be all the shares.  What do you see when you browse that way?  Do you have a data share?  Check directly on the Playbook for that.
But these are not Blackberry Playbook shares, they belong to Ubuntu PC 
Now I can access smb://playbook-41c2 through Nemo and there is print$ directory, but it's just shared printers directory from Ubuntu PC
When I click on "Network" in Nemo, I see "ACER", "PLAYBOOK-41C2" and "Windows Network". But contents of "PLAYBOOK-41C2" are just duplicating contents of "ACER"
The only possible Blackberry Playbook's shared directory can be "/media/", but not "print"

edit: filesharing through USB is turned on on Playbook:
[ATTACH=CONFIG]262188[/ATTACH]

---

### Post by bab1 on 2015-05-24
> **janot2012 said:**
> But these are not Blackberry Playbook shares, they belong to Ubuntu PC 
Now I can access smb://playbook-41c2 through Nemo and there is print$ directory, but it's just shared printers directory from Ubuntu PC
When I click on "Network" in Nemo, I see "ACER", "PLAYBOOK-41C2" and "Windows Network". But contents of "PLAYBOOK-41C2" are just duplicating contents of "ACER"
The only possible Blackberry Playbook's shared directory can be "/media/", but not "print"

edit: filesharing through USB is turned on on Playbook:
[ATTACH=CONFIG]262188[/ATTACH]

Change the IP address in the /etc/hosts file show this (in red)```

$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    ACER
[COLOR="#FF0000"]169.254.**0.1** PLAYBOOK-41C2[/COLOR]


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```...the IP address should end in .0.1 instead of .0.2.

Show me this again```
smbtree -d3
```...try and browse the shares again.  Success?

---

### Post by janot2012 on 2015-05-24
> **bab1 said:**
> Change the IP address in the /etc/hosts file show this (in red)```

$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    ACER
[COLOR=#FF0000]169.254.**0.1** PLAYBOOK-41C2[/COLOR]


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```...the IP address should end in .0.1 instead of .0.2.

Show me this again```
smbtree -d3
```...try and browse the shares again.  Success?

```
$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface usb0 ip=169.254.0.2 bcast=169.254.0.3 netmask=255.255.255.252
added interface wlan0 ip=192.168.0.168 bcast=192.168.0.255 netmask=255.255.255.0
added interface virbr0 ip=192.168.122.1 bcast=192.168.122.255 netmask=255.255.255.0
added interface pan1 ip=10.66.145.1 bcast=10.66.145.255 netmask=255.255.255.0
Enter janot's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.168 ( 10.66.145.1 )
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f34046de650] mpx_fde[(nil)] fd[14] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f34046dd400] mpx_fde[(nil)] fd[12] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f34046dc270] mpx_fde[(nil)] fd[10] - disabling
Connecting to 10.66.145.1 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.122.1 ( 192.168.122.1 )
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f34046eef10] mpx_fde[(nil)] fd[16] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f34046f00a0] mpx_fde[(nil)] fd[14] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f34046f1230] mpx_fde[(nil)] fd[10] - disabling
Connecting to 192.168.122.1 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
    \\ACER                   ACER server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name ACER<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name ACER<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name ACER<0x20>
Connecting to 127.0.1.1 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\ACER\Samsung-SCX-3400-Series-WiFi    Samsung SCX-3400 Series
        \\ACER\Samsung-SCX-3400-Series-USB    Samsung SCX-3400 Series USB
        \\ACER\IPC$               IPC Service (ACER server (Samba, Ubuntu))
        \\ACER\print$             Printer Drivers

```

Still not connecting...

---

### Post by bab1 on 2015-05-24
Disappointing.   :-(

Post the output of this```
ifconfig -a
```

---

### Post by janot2012 on 2015-05-24
> **bab1 said:**
> Disappointing.   :-(

Post the output of this```
ifconfig -a
```

Yup ](*,)
```
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr e8:9a:8f:45:c3:69  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:32665 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32665 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13570536 (13.5 MB)  TX bytes:13570536 (13.5 MB)


pan1      Link encap:Ethernet  HWaddr b2:36:a4:19:96:78  
          inet addr:10.66.145.1  Bcast:10.66.145.255  Mask:255.255.255.0
          inet6 addr: fe80::b036:a4ff:fe19:9678/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14922 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:2581657 (2.5 MB)


usb0      Link encap:Ethernet  HWaddr 72:d4:f2:02:42:38  
          inet addr:169.254.0.2  Bcast:169.254.0.3  Mask:255.255.255.252
          inet6 addr: fe80::70d4:f2ff:fe02:4238/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2586 (2.5 KB)  TX bytes:12480 (12.4 KB)


virbr0    Link encap:Ethernet  HWaddr 52:54:00:32:92:5b  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


virbr0-nic Link encap:Ethernet  HWaddr 52:54:00:32:92:5b  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6560 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6563 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr ec:55:f9:21:6d:8a  
          inet addr:192.168.0.168  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ee55:f9ff:fe21:6d8a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16139215 errors:0 dropped:0 overruns:0 frame:2197045
          TX packets:21871376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3194827596 (3.1 GB)  TX bytes:650428089 (650.4 MB)
          Interrupt:17 

```

---

### Post by bab1 on 2015-05-24
> **janot2012 said:**
> Yup ](*,)
```
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr e8:9a:8f:45:c3:69  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:32665 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32665 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13570536 (13.5 MB)  TX bytes:13570536 (13.5 MB)


pan1      Link encap:Ethernet  HWaddr b2:36:a4:19:96:78  
          inet addr:10.66.145.1  Bcast:10.66.145.255  Mask:255.255.255.0
          inet6 addr: fe80::b036:a4ff:fe19:9678/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14922 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:2581657 (2.5 MB)


usb0      Link encap:Ethernet  HWaddr 72:d4:f2:02:42:38  
          inet addr:169.254.0.2  Bcast:169.254.0.3  Mask:255.255.255.252
          inet6 addr: fe80::70d4:f2ff:fe02:4238/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2586 (2.5 KB)  TX bytes:12480 (12.4 KB)


virbr0    Link encap:Ethernet  HWaddr 52:54:00:32:92:5b  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


virbr0-nic Link encap:Ethernet  HWaddr 52:54:00:32:92:5b  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6560 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6563 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr ec:55:f9:21:6d:8a  
          inet addr:192.168.0.168  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ee55:f9ff:fe21:6d8a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16139215 errors:0 dropped:0 overruns:0 frame:2197045
          TX packets:21871376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3194827596 (3.1 GB)  TX bytes:650428089 (650.4 MB)
          Interrupt:17 

```

All these interfaces need explanation.  Why do you need them?  It appears that the Ubuntu kernel is unable to route the Samba packets to the usb0 interface.

Post the output of this```
route -n
```

---

### Post by janot2012 on 2015-05-24
> **bab1 said:**
> All these interfaces need explanation.  Why do you need them?  It appears that the Ubuntu kernel is unable to route the Samba packets to the usb0 interface.

Post the output of this```
route -n
```

As I understand all these interfaces except eth0, usb0 and wlan0 belong to vmware workstation and virtual box
```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    1024   0        0 wlan0
10.66.145.0     0.0.0.0         255.255.255.0   U     0      0        0 pan1
169.254.0.0     0.0.0.0         255.255.255.252 U     0      0        0 usb0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
169.254.0.1     169.254.0.2     255.255.255.255 UGH   1      0        0 usb0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0

```

---

### Post by bab1 on 2015-05-24
> **janot2012 said:**
> As I understand all these interfaces except eth0, usb0 and wlan0 belong to vmware workstation and virtual box
```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    1024   0        0 wlan0
10.66.145.0     0.0.0.0         255.255.255.0   U     0      0        0 pan1
169.254.0.0     0.0.0.0         255.255.255.252 U     0      0        0 usb0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
169.254.0.1     169.254.0.2     255.255.255.255 UGH   1      0        0 usb0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0

```

The route table looks okay to me.  What do we get with this```
ping -c3 169.254.0.1
```...even if it is an error we need to verify that.

Can you get to the command line of the Playbook?

---

### Post by janot2012 on 2015-05-24
> **bab1 said:**
> The route table looks okay to me.  What do we get with this```
ping -c3 169.254.0.1
```...even if it is an error we need to verify that.

Can you get to the command line of the Playbook?

```
$ ping -c3 169.254.0.1
PING 169.254.0.1 (169.254.0.1) 56(84) bytes of data.
From 192.168.0.168 icmp_seq=1 Destination Host Unreachable
From 192.168.0.168 icmp_seq=2 Destination Host Unreachable
From 192.168.0.168 icmp_seq=3 Destination Host Unreachable


--- 169.254.0.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2001ms
pipe 3

```
There is shell terminal but it's VERY limited

---

### Post by bab1 on 2015-05-24
> **janot2012 said:**
> ```
$ ping -c3 169.254.0.1
PING 169.254.0.1 (169.254.0.1) 56(84) bytes of data.
From[COLOR="#FF0000"] 192.168.0.168[/COLOR] icmp_seq=1 Destination Host Unreachable
From 192.168.0.168 icmp_seq=2 Destination Host Unreachable
From 192.168.0.168 icmp_seq=3 Destination Host Unreachable


--- 169.254.0.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2001ms
pipe 3

```
There is shell terminal but it's VERY limited
Actually this is progress.  The ping packets are actually going out wlan0 instead of usb0.  See the red above.  That address is your wlan0 interface.

I would turn off the wireless and try the ping again.

[COLOR="#0000FF"]Edit: By turn off wireless I mean disable that interface.  Maybe by Network-Manager.[/COLOR]

---

### Post by janot2012 on 2015-05-24
> **bab1 said:**
> Actually this is progress.  The ping packets are actually going out wlan0 instead of usb0.  See the red above.  That address is your wlan0 interface.

I would turn off the wireless and try the ping again.

[COLOR=#0000FF]Edit: By turn off wireless I mean disable that interface.  Maybe by Network-Manager.[/COLOR]

With Wi-Fi turned off
```
$ ping -c3 169.254.0.1
PING 169.254.0.1 (169.254.0.1) 56(84) bytes of data.


--- 169.254.0.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2016ms

```

---

### Post by bab1 on 2015-05-24
> **janot2012 said:**
> With Wi-Fi turned off
```
$ ping -c3 169.254.0.1
PING 169.254.0.1 (169.254.0.1) 56(84) bytes of data.


--- 169.254.0.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2016ms

```
I'm down to thinking this is a cable problem or a Playbook problem.  If you have not changed anything on the Playbook then maybe the cable has a break in it.  Every test we do brings us closer to that answer.

Samba on Ubuntu is working correctly and the hosts file is recognised by Samba.  The routing table is correct, so TCP/IP and Ethernet are correct.  In fact the only lack of connectivity is via usb0 and it's cabling.

I don't know anything about Playbook so I can't help you there.

---

### Post by janot2012 on 2015-05-24
> **bab1 said:**
> I'm down to thinking this is a cable problem or a Playbook problem.  If you have not changed anything on the Playbook then maybe the cable has a break in it.  Every test we do brings us closer to that answer.

Samba on Ubuntu is working correctly and the hosts file is recognised by Samba.  The routing table is correct, so TCP/IP and Ethernet are correct.  In fact the only lack of connectivity is via usb0 and it's cabling.

I don't know anything about Playbook so I can't help you there.
I haven't changed anything on it and tried different cables
I'm beginning to think that's Playbook's software bug. When after couple of months it suddenly stops being recognized through USB until hard reset. Maybe similar thing already happened couple of years ago, not sure.
Thank you for help and sorry for my Playbook :roll:

---

### Post by bab1 on 2015-05-24
I'd check on the Blackberry forums.  Good luck.

---

### Post by mh40 on 2016-01-06
Adding that entry to hosts file resolved my problem, thankyou, but this is ongoing. Why does every samba update bork this??

---

### Post by bab1 on 2016-01-07
> **mh40 said:**
> Adding that entry to hosts file resolved my problem, thank you, but this is ongoing. Why does every samba update bork this??
Samba isn't the problem.  This is basic TCP/IP connectivity stuff. Samba needs proper hosts file entries or local LAN DNS server for name to IP address resolution.

---

