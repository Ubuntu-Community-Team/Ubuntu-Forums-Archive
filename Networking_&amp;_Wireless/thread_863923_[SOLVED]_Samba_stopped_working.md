---
title: "[SOLVED] Samba stopped working"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by starfleetcaptainrob on 2008-07-19
So, I turned my server off this evening to kind of clean up some of the cables under my desk.  Then I wired everything back up the same way I had it and suddenly I can't connect to my samba share from my Windows desktop.  I'm not sure what's going on.  All I did was turn off the server, unplug it for about an hour, and turn it back on.  Has this happened to anyone else?

---

### Post by starfleetcaptainrob on 2008-07-19
If it will help, here's my config file.  Although nothing has changed on it from when it was working fine before I shut it down to now...

```

[global]
   bind interfaces only = yes
   deadtime = 15
   default case = lower
   disable netbios = yes
   dns proxy = no
   domain master = yes
   encrypt passwords = true
   guest ok = yes
   guest only = yes
   hosts allow = 192.168.10.0/255.255.255.0 127.0.0.1
   hosts deny = all
   interfaces = em1
   invalid users = nobody root
   load printers = no
   max connections = 10
   netbios name = ironhide
   preferred master = yes
   preserve case = no
   printable = no
   security = share
   server string = Samba Share
   socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536
   strict sync = no
   sync always = no
   syslog = 1
   syslog only = yes
   workgroup = WORKGROUP

[share1]
        create mask = 0400
        directory mask = 0700
        path = /home/fredbear/samba
        writeable = yes



```

---

### Post by superprash2003 on 2008-07-19
is the windows pc able to ping the ubuntu?

---

### Post by starfleetcaptainrob on 2008-07-21
> **superprash2003 said:**
> is the windows pc able to ping the ubuntu?

Yes, I'm also able to SSH into the machine via putty and view webpages from the apache server running on it.

---

### Post by dmizer on 2008-07-22
please post the output of:
```
sudo ifconfig
```

---

### Post by starfleetcaptainrob on 2008-07-22
> **dmizer said:**
> please post the output of:
```
sudo ifconfig
```

Here it is:

```
eth0      Link encap:Ethernet  HWaddr 00:04:23:06:e8:99
          inet addr:192.168.10.10  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::204:23ff:fe06:e899/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:227011 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132033 errors:0 dropped:0 overruns:0 carrier:0
          collisions:265 txqueuelen:1000
          RX bytes:25002560 (23.8 MB)  TX bytes:19500674 (18.5 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4462 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4462 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:392112 (382.9 KB)  TX bytes:392112 (382.9 KB)
```

It's just totally bizarre that it worked until I shut down the machine and nothing (that I'm aware of) changed.  I guess something had to have changed...

---

### Post by gnottage on 2008-07-22
I'm wondering if samba is setup to automatically start. Perhaps trying the following will help:
```
sudo /etc/init.d/samba restart
```

---

### Post by superprash2003 on 2008-07-22
reboot both the ubuntu and the windows machine and then try

---

### Post by starfleetcaptainrob on 2008-07-22
Ok, tried rebooting both the windows and linux servers and gave Samba a restart command.  Neither worked.  I let Vista try to diagnose the problem and it said that "ip address" is not set up to establish a connection on port "File and printer sharing (SMB)" with this computer.  Could it be a closed port?

---

### Post by dmizer on 2008-07-22
okay ... i don't know why it was working before but:

[LIST]
[*]your ifconfig indicates that you're getting internet on eth0 with a local ip of 192.168.10.10.
[*]your smb.conf has these two lines:
[/LIST]
```
bind interfaces only = yes
interfaces = em1
```

what this means is that smb.conf is set to only accept incomming samba connections from the em1 interface.  but you do not have an ethernet connection on em1, your ethernet connection is eth0.

you could do two things to fix this.
1) simply remove those options.
2) change "interfaces = em1" to "interfaces = eth0"

then restart samba:
```
sudo /etc/init.d/samba restart
```

---

### Post by starfleetcaptainrob on 2008-07-22
> **dmizer said:**
> okay ... i don't know why it was working before but:

[LIST]
[*]your ifconfig indicates that you're getting internet on eth0 with a local ip of 192.168.10.10.
[*]your smb.conf has these two lines:
[/LIST]
```
bind interfaces only = yes
interfaces = em1
```

what this means is that smb.conf is set to only accept incomming samba connections from the em1 interface.  but you do not have an ethernet connection on em1, your ethernet connection is eth1.

you could do two things to fix this.
1) simply remove those options.
2) change "interfaces = em1" to "interfaces = eth1"

then restart samba:
```
sudo /etc/init.d/samba restart
```

Bingo!  (Except I had to change it to eth0, no biggie).  That's odd that it worked before too, oh well who cares?  I must have read over that config file a dozen times and I never caught that.  Thanks for the help!

---

### Post by dmizer on 2008-07-22
> **starfleetcaptainrob said:**
> (Except I had to change it to eth0, no biggie).[snip]

oops ... i'll fix that ;)

glad you're working again!

---

### Post by vood002 on 2011-08-03
wow, this worked immediately for me....which begs the question how the hell has it been working for the last 3 months with eth1 set when I had no eth1 connection!

Thanks for the post

---

### Post by virgil_machine on 2011-09-05
I had the similar symptoms--computers on the network, including VMs, could not see each other (ubuntu or windows, although windows 7 computers could see each other only).

I found the following in smb.conf networking section: 
; interfaces=127.0.0.0/8 eth0
; bind interfaces only = yes"

I commented these lines and restarted samba (for me, on lucid, it was "sudo smbd restart") and all was well.

This all happened after a samba update via update manager followed by shutdown/restart of all computers in anticipation of the Hurricane Irene.

Thanks for the help.

---

