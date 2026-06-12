---
title: "Windows stopped finding Ubuntu shared folders"
date: 2006-11-21
forum: Networking &amp; Wireless
---

### Post by jshamash66 on 2006-11-21
Hi, I'm looking for some help with a network problem I'm having. My Windows computers used to be able to find my Ubuntu computer, but recently they've been giving me errors. I haven't changed my samba configuration file, but nevertheless my shared folders seem to have become inaccessible.
If it helps, my computers have changed internal IP addresses recently (our provider won't allow static IPs). Also, my Ubuntu computer can find my Windows computers by using smb4k, although I must mount the shares manually- scanning the network returns no results. Thanks for the help!

---

### Post by dmizer on 2006-11-22
try configuring your samba server according to the first link in my sig.  your wan ip address should not have any effect on your local network.

have you moved your dns servers to open dns?

---

### Post by jshamash66 on 2006-11-22
> **dmizer said:**
> try configuring your samba server according to the first link in my sig.  your wan ip address should not have any effect on your local network.

have you moved your dns servers to open dns?

Thanks, that's the howto that I followed the first time I set up Samba, and it worked just fine. I checked my config file, and it is exactly the way it should be.

I don't know how to check if I've moved my DNS servers to open DNS. But I don't think it would make a difference, since I definitely didn't change anything about them at the time my problem started. I'm starting to think it might be a Windows problem...

---

### Post by dmizer on 2006-11-23
what happens when you do:
```
smbtree
```
from the ubuntu box?

also, on your ubuntu box, what's the output of:
```
testparm
```

---

### Post by jshamash66 on 2006-11-27
Sorry it took me so long to reply.

The output of "testparm" is:

```
Load smb config files from /etc/samba/smb.conf
Processing section "[print$]"
Processing section "[printers]"
Processing section "[Download]"
Loaded services file OK.
WARNING: passdb expand explicit = yes is deprecated
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = RSWCA
        netbios name = BMENTDL
        server string = 
        null passwords = Yes
        passdb backend = tdbsam
        username map = /etc/samba/smbusers
        syslog only = Yes
        announce version = 5.0
        name resolve order = hosts wins bcast
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
        printcap name = CUPS
        printing = cups
        print command = 
        lpq command = %p
        lprm command = 

[print$]
        path = /var/lib/samba/printers
        write list = root
        create mask = 0664
        directory mask = 0775
        guest ok = Yes

[printers]
        path = /tmp
        guest ok = Yes
        printable = Yes
        browseable = No

[Download]
        path = /home/jake/Download
        force user = jake
        force group = jake
        read only = No
        create mask = 0644
```

When I enter
```
smbtree
```
there is no output. What does it do?

---

### Post by marx2k on 2006-11-28
No output from SMBtree means your samba client may not be running.

SMBTree lists all the samba shares currently on your local network.

---

### Post by featherking on 2006-11-28
try running
```
sudo /etc/init.d/samba restart
```

that will restart the samba daemons, then try to see if smbtree gives any output

---

### Post by marx2k on 2006-11-28
Something interesting I've noticed regarding SAMBA and OpenDNS (Which I think OpenDNS addresses on their site...)

On my system setup, my computers use the router for DHCP and DNS purposes.  The DNS servers on the router are OpenDNS instead of Charter (DIE DIE DIE) DNS.

As a result, on every boot or /etc/init.d/networking restart, the router would throw the two OpenDNS servers into resolv.conf and remove 'nameserver 192.168.11.1' from the list

This would totally screw up smbtree into not seeing many or ANY of the other nodes on the network.

OpenDNS solution:

```

1. Run: sudo gedit /etc/dhcp3/dhclient.conf
2. Change the prepend line to read:

prepend domain-name-servers 208.67.222.222, 208.67.220.220;

This will prepend the OpenDNS addresses to the top of the list. (You can also use "supersede", which will just use them.) You don't have to worry about the DHCP client overwriting settings on each reboot or lease cycle, and your ISP nameservers will still be used as backup.

```

However, this makes my resolv.conf look like 
nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 192.168.11.1

and smbtree still looked awful.  Turns out my router's IP needed to be first in the list. Weird, I know.

So the solution is that instead of adding those IP addresses to the prepend line in dhclient.conf, I added my router's IP and the router does it's job in adding the other two DNS servers.  So now resolv.conf looks like:
nameserver 192.168.11.1
nameserver 208.67.222.222
nameserver 208.67.220.220

...and smbtree looks perfect.

There seem to be a bunch of people who are having trouble with OpenDNS and SAMBA and OpenDNS' solution I think fixes the problem for most, and this solution fixes the problem for me and some other people I hope.

---

### Post by jshamash66 on 2006-11-28
I restarted the Samba daemons, and followed marx2k's instructions (although I'm not sure I did everything properly - I'm pretty new at networking and Internet stuff), yet SMBtree still won't produce any results. If it helps, I have 4 computers on this network- 3 which are running XP, and one running Ubuntu. The Ubuntu box can easily find all three other PCs, with the help of the program smb4k, but none of the WinXP computers can find the Ubuntu box. I even tried pinging Ubuntu from XP, and it didn't work. I'm starting to think that maybe this is a Windows problem...

---

