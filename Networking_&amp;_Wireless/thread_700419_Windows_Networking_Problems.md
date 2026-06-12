---
title: "Windows Networking Problems"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by gjrepicky on 2008-02-18
Until a few weeks ago, I had no problems accessing the shared docs folder and printer on our home XP machine from either of my laptops, one with Feisty, the other w/ Gutsy.  I simply used the "Connect to Server" to connect to the XP machine, then installed the printer, and away I went -- only had to do this once w/ each machine, then worked fine anytime I plugged one of the laptops into the network.  (Still using a wired network -- solid, and all I need.)  Now I cannot connect to the XP machine with either laptop.  Nothing I've tried works  (realize that when it comes to networks I take "beginner" to a whole new lever).  I can connect to the internet (through cable modem and wired router).  The network seems to be physically intact -- I can connect to the XP machine from the Windows partitions (W2K and Vista (ugh), respectively) of the laptops.  Help greatly appreciated.

George

---

### Post by Iowan on 2008-02-18
What happens when you try the "Connect to Server" option - network doesn't show?  Can you **ping** the XP box?

---

### Post by gjrepicky on 2008-02-18
"Connect to Server" gives me a network folder on the desktop with the name of the XP machine (jgm).  Clicking on the folder gives (after a many-second pause} a "Folder Contents Could Not Be Displayed" error message.

How to I try to ping?

G.

---

### Post by OffAxis on 2008-02-18
```
ping -c 4 <ip address of the server>
```
**ping **will only test to see that the machine is physically on the LAN and reachable with TCP/IP.

The 'Folder Contents Could Not Be Displayed' message is usually a problem related to permissions. Have you changed user, workgroups, or share permissions lately?

The folder being moved or renamed might do it, too.


**smbclient **is a much better tool for checking your server's availability.
```

smbclient -W <workgroup name> -L <servername>
```

where
<workgroup name> = your windows workgroup name
<server name> = your windows computer's netbios name

It should return all possible shares on your windows pc.

---

### Post by Iowan on 2008-02-18
> **gjrepicky said:**
> "Connect to Server" gives me a network folder on the desktop with the name of the XP machine (jgm).  Clicking on the folder gives (after a many-second pause} a "Folder Contents Could Not Be Displayed" error message.
G. My Samba server did that to me recently - I'm trying to remember what I did to make it start working again.  Curiously, the XP shares were not a problem.

---

### Post by gjrepicky on 2008-02-18
gjrepicky@IBMT21:~$ smbclient -W HOME -L JGM
timeout connecting to 24.28.199.152:445
timeout connecting to 24.28.199.152:139
Error connecting to 24.28.199.152 (Operation already in progress)
Connection to JGM failed (Error NT_STATUS_ACCESS_DENIED)
gjrepicky@IBMT21:~$

---

### Post by OffAxis on 2008-02-18
> timeout connecting to 24.28.199.152:445
That's an awfully strange IP address for a local network...
were you able to ping it?

```
sudo ping -c 4 24.28.199.152
```

you can also run
```
smbtree
```

to get an overview of the available shares for the network.

---

### Post by gjrepicky on 2008-02-18
gjrepicky@IBMT21:~$ sudo ping -c 4 24.28.199.152
[sudo] password for gjrepicky:
PING 24.28.199.152 (24.28.199.152) 56(84) bytes of data.
64 bytes from 24.28.199.152: icmp_seq=1 ttl=243 time=30.0 ms
64 bytes from 24.28.199.152: icmp_seq=2 ttl=243 time=30.1 ms
64 bytes from 24.28.199.152: icmp_seq=3 ttl=243 time=36.8 ms
64 bytes from 24.28.199.152: icmp_seq=4 ttl=243 time=29.1 ms

--- 24.28.199.152 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 29.133/31.548/36.880/3.105 ms
gjrepicky@IBMT21:~$ smbtree
Password: 
HOME
        \\JGM                           Joe's game machine
timeout connecting to 24.28.199.152:445
timeout connecting to 24.28.199.152:139
Error connecting to 24.28.199.152 (Operation already in progress)
cli_start_connection: failed to connect to JGM<20> (24.28.199.152). Error NT_STATUS_ACCESS_DENIED
gjrepicky@IBMT21:~$

---

### Post by Iowan on 2008-02-19
Windows firewall active?

---

### Post by gjrepicky on 2008-02-20
Yes.

Note:  I can get to the XP box w/ Win2K & win Vista running on the same laptops (dual boot) -- no problem.

Note 2:  Is it possible a recent XP update -- I routinely install these as the appear -- changed something?

TIA

G.

---

### Post by maybeway36 on 2008-02-20
Do a [whois]("http://www.whois.net") on that IP address. I use Charter, and when you do a DNS query for something that's not .com or .org or sometihng like that, it redirects to an annoying "search" page with a bunch of sponsered links. This also breaks samba.
Try going into /etc/samba/smb.conf and changing the "resolve order" to put **bcast** first.

---

