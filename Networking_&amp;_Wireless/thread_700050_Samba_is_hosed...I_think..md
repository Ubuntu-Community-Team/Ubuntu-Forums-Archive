---
title: "Samba is hosed...I think."
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by jumpjet on 2008-02-18
Hello all!

I was trying to set up a mythtv frontend, and somehow in the process hosed my samba, network, etc.

Here is the scoop:

Computer: turbinelinux 192.168.0.107   Running Gutsy
Computer: hal9000 192.168.0.102         Running Gutsy
Computer: Atreyu 192.168.0.100           Windows XP Pro

all run through a di524 router, to the internet.

I can ping all over the network by IP with no problem from any computer.  
turbinelinux has the mythtv backend.  
hall9000 has the mythtv frontend.

Now, the mythtv back and forth works just fine.

On all computers, I can see, and access Atreyu.
On all computer, I can see turbinelinux, but when I try to access it, it errors out.
I cannot see hal9000 on any machine.

I'm not sure where to go about diagnosing the problem.  I think it might be a WINS issue, or DNS, , or Samba, but again, I'm just not sure where to start.

Thanks for everything!

---

### Post by jumpjet on 2008-02-18
Update:

A short while after that post, the windows network went dark.  Nothing in windows network at all.  I wonder if this was because atreyu went to sleep.  Could that mean that the DNS or WINS or something is kept on the Atreyu computer?

---

### Post by njparton on 2008-02-18
If you're connecting via a router you may need to forward samba's ports to each computer you're running samba on.  Google for samba's port numbers I can't remember them off the top of my head.

---

### Post by jumpjet on 2008-02-18
Thanks for your suggestion!

Ok, so I opened those ports, but still no dice.  I tend to lean toward it not being a router issue, since turbinelinux can't even see it's own windows shares.   

Halp?

---

### Post by Iowan on 2008-02-18
Is Samba (smb/nmb) process running? 
(**ps ax** or maybe **sudo ps ax)**

---

### Post by jumpjet on 2008-02-18
Thanks for the help!

I ran ps ax.

This is running.  Is that samba?

 7886 ?        Ss     0:00 /usr/sbin/nmbd -D

---

### Post by Iowan on 2008-02-18
That's at least part of it.  As usual, I wish I could see my server to see what it has running. IIRC, it usually has **smbd** and a couple of instances of **nmbd** running. Might try: ```
sudo /etc/init.d/samba restart 
``` then recheck to see if smbd is running.

---

### Post by jumpjet on 2008-02-18
Ok, after I restarted it, i got an errror


mike@turbinelinux:~$ sudo /etc/init.d/samba restart
[sudo] password for mike:
Stopping Samba daemons...:start-stop-daemon: warning: failed to kill 7890: No such process
.
Starting Samba daemons: nmbd.

Running ps ax again, i find some interesting stuff.

 5452 ?        Ss     0:00 /usr/sbin/winbindd
 5567 ?        S      0:00 /usr/sbin/winbindd
 6577 ?        Ss     0:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0
 7695 ?        S      0:00 /usr/sbin/winbindd
 7696 ?        S      0:00 /usr/sbin/winbindd
26229 ?        Ss     0:00 /usr/sbin/nmbd -D


Isn't winbindd something name server related?  Why is it running 4 times?

---

### Post by jumpjet on 2008-02-18
Update:

I took a look at the log files.  The last time I tried to run SMBD, i got this in the log file

[2008/02/18 15:12:08, 0] smbd/server.c:main(944)
  smbd version 3.0.26a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2007
[2008/02/18 15:12:08, 0] smbd/server.c:main(986)
  standard input is not a socket, assuming -D option
[2008/02/18 15:12:08, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2008/02/18 15:12:08, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
[2008/02/18 15:12:08, 0] passdb/pdb_interface.c:guest_user_info(256)
  guest_user_info: Unable to locate guest account [yes]!
[2008/02/18 15:12:08, 0] smbd/server.c:main(1059)
  ERROR: failed to setup guest info.

---

### Post by jumpjet on 2008-02-18
NMBD log

[2008/02/18 14:00:03, 0] nmbd/nmbd.c:main(697)
  Netbios nameserver version 3.0.26a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2007
[2008/02/18 14:05:46, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396)
  *****
  
  Samba name server TURBINELINUX is now a local master browser for workgroup SPQK on subnet 192.168.0.107
  
  *****
[2008/02/18 14:05:46, 0] nmbd/nmbd_browsesync.c:find_domain_master_name_query_fail(351)
  find_domain_master_name_query_fail:
  Unable to find the Domain Master Browser name SPQK<1b> for the workgroup SPQK.
  Unable to sync browse lists in this workgroup.
[2008/02/18 14:20:51, 0] nmbd/nmbd_browsesync.c:find_domain_master_name_query_fail(351)
  find_domain_master_name_query_fail:
  Unable to find the Domain Master Browser name SPQK<1b> for the workgroup SPQK.
  Unable to sync browse lists in this workgroup.
[2008/02/18 14:27:09, 0] nmbd/nmbd.c:terminate(58)
  Got SIGTERM: going down...
[2008/02/18 14:28:30, 0] nmbd/nmbd.c:main(697)
  Netbios nameserver version 3.0.26a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2007
[2008/02/18 14:29:57, 0] nmbd/nmbd.c:terminate(58)
  Got SIGTERM: going down...
[2008/02/18 14:30:00, 0] nmbd/nmbd.c:main(697)
  Netbios nameserver version 3.0.26a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2007
[2008/02/18 14:35:48, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396)
  *****
  
  Samba name server TURBINELINUX is now a local master browser for workgroup SPQK on subnet 192.168.0.107
  
  *****
[2008/02/18 14:35:48, 0] nmbd/nmbd_browsesync.c:find_domain_master_name_query_fail(351)
  find_domain_master_name_query_fail:
  Unable to find the Domain Master Browser name SPQK<1b> for the workgroup SPQK.
  Unable to sync browse lists in this workgroup.
[2008/02/18 14:50:56, 0] nmbd/nmbd_browsesync.c:find_domain_master_name_query_fail(351)
  find_domain_master_name_query_fail:
  Unable to find the Domain Master Browser name SPQK<1b> for the workgroup SPQK.
  Unable to sync browse lists in this workgroup.
[2008/02/18 15:06:07, 0] nmbd/nmbd_browsesync.c:find_domain_master_name_query_fail(351)
  find_domain_master_name_query_fail:
  Unable to find the Domain Master Browser name SPQK<1b> for the workgroup SPQK.
  Unable to sync browse lists in this workgroup.

---

### Post by jumpjet on 2008-02-18
Interesting...

Check this out:

```
mike@turbinelinux:~$ smbclient -L turbinelinux -R wins
Error connecting to 192.168.0.107 (Connection refused)
Connection to turbinelinux failed (Error NT_STATUS_CONNECTION_REFUSED)mike@turbinelinux:~$ smbclient -L turbinelinux -R wins
Error connecting to 192.168.0.107 (Connection refused)
Connection to turbinelinux failed (Error NT_STATUS_CONNECTION_REFUSED)
```

---

### Post by jumpjet on 2008-02-18
Updates:

Following this guide:

[http://www.faqs.org/docs/samba/ch12.html](http://www.faqs.org/docs/samba/ch12.html)

I ran nslookup and got the following

```
 nslookup turbinelinux
Server:         68.87.72.130
Address:        68.87.72.130#53

** server can't find turbinelinux: NXDOMAIN


```

Then I ran nmblookup and got the following

```
nmblookup -S turbinelinux
querying turbinelinux on 192.168.0.255
192.168.0.107 turbinelinux<00>
Looking up status of 192.168.0.107
        TURBINELINUX    <00> -         H <ACTIVE> 
        TURBINELINUX    <03> -         H <ACTIVE> 
        TURBINELINUX    <20> -         H <ACTIVE> 
        ..__MSBROWSE__. <01> - <GROUP> H <ACTIVE> 
        SPQK            <1d> -         H <ACTIVE> 
        SPQK            <1e> - <GROUP> H <ACTIVE> 
        SPQK            <00> - <GROUP> H <ACTIVE> 

        MAC Address = 00-00-00-00-00-00


```

I have a /etc/resolv.conf, which the faq suggests means that I am running DNS, but it doesn't like the name.  WINS does seem to find it ok.

Here is resolve.conf

```
nameserver 68.87.72.130
nameserver 68.87.77.130
```

---

### Post by jumpjet on 2008-02-18
Update:

I am AGGRAVATED!

But making some progress.

I added the following to the /etc/samba/smb.conf 
```
domain master = yes
        local master = yes
        preferred master = yes
        os level = 64
```

Now I can ping hal9000, and I get a response, HAY!

However, nothing shows up in the windows network at all.

But still, some progress!

---

### Post by jumpjet on 2008-02-18
Updates:

inetd wouldn't start, because it said it had no services.

I checked /etc/inetd.conf and found this
```

<#OFF#>netbios-ssn	stream	tcp	nowait	root	/usr/sbin/tcpd	/usr/sbin/smbd
<#OFF#>netbios-ns      dgram   udp     wait    root /usr/local/samba/bin/nmbd nmbd
<#OFF#>telnet		stream	tcp	nowait	telnetd	/usr/sbin/tcpd	/usr/sbin/in.telnetd

<#OFF#>swat   stream  tcp  nowait  root  /usr/local/samba/bin/swat  swat


```

Off?  Could it be that simple?  I deleted the <#OFF#> for all of them, and then inetd started without a problem.

Now, when I go to windows network, i see the different workgroups, but when I try to go to them, I get an error.

Not quite there, but close!

---

### Post by njparton on 2008-02-19
I've tried going through your posts - is samba actually installed and running?

What do you get if you do:

```
sudo apt-get install samba smbfs
```

---

### Post by Iowan on 2008-02-19
> **jumpjet said:**
> Updates:...
Now, when I go to windows network, i see the different workgroups, but when I try to go to them, I get an error.

Not quite there, but close! What is the error?

---

### Post by jumpjet on 2008-02-19
smbfs was NOT running.  I enabled it last night, on turbinelinux but encountered the same error.

the error when browing SPQK, which all the linux machines should be in:

Sorry, couldn't display all the contents of "Windows Network: spqk".

When another windows machine signs on from a different workgroup, I get this message

"Windows Network: 120appletree" couldn't be found. Perhaps it has recently been deleted.

---

