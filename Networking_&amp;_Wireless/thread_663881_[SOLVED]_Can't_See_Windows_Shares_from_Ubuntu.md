---
title: "[SOLVED] Can't See Windows Shares from Ubuntu"
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by Derspankster on 2008-01-10
I'm running 7.10 on a desktop with a fixed IP address and cannot see any Windows shares from any of my Windows computers on the same network. All of the Windows computers can see shares from the Ubuntu computer. 

Network File Browsers finds the MSHOME Network but not any of the Windows computers or shares.  I have no problem seeing the Ubuntu shares, reading or writing from those shares from any Windows computer but not the other way around.  

As I said, Ubuntu computer has a fixed IP but the Windows computers are all using DHCP.  I have file file sharing turned on on all the Windows computers and they see all shares on all the Windows computers as well. 

I just cannot see any Windows shares from Ubuntu.

---

### Post by evanchu on 2008-01-10
I have successfully shared files between Ubuntu and Windows Vista (in both directions).  I wrote down some notes at [this page]("http://www.evanchu.com/linux2").  Read the following topics on that page:
* Windows serve files to Linux
* Linux serves files to Windows

---

### Post by Derspankster on 2008-01-10
Thank you for your response, evanchu.  I looked over the two scripts from the 'note' and I have a couple of questions. 1) My Windows computers run XP, not Vista. I am not sure if that makes a difference or not. 2) I'm a little confused as to why a Guest account needs to be turned on on the Windows machines. 3) I already have set up some shared folders on the Windows computers and they have no problem seeing one another and sharing. 4) I have read that Ubuntu (with Samba installed) can access shared Windows folders on the same network. I have never been able to do so on either of my Ubuntu computers. Sorry for being so long winded but I'm finding this very confusing.

EDIT: I can connect to my Windows shares from Ubuntu if I connect to the Windows machines IP.  I can not write to the Windows shares though but I can look at them and I can copy folders/files to my Ubuntu machines. As long as DCHP doesn't assign another IP to that machine, that is.

---

### Post by evanchu on 2008-01-11
1. Windows XP and Vista are very similar in terms of file sharing.  So this factor should not make a difference.

2. I turn on guest account on Windows because I want Windows to allow any guest to access files.  It means any Linux user that does not have a proper username and/or password can automatically access Window files using the guest account.

3. Using my Linux netview script, try netview windowsMachineName.  See if you can contact the Windows machine.

4. All of my machines (Windows and Linux) are on the same IP subnet.  Therefore, they all can see each other.  Are all your machines on the same IP subnet?

---

### Post by Derspankster on 2008-01-11
All machines are on the same router with the same sub net.  I have not been able to contact a Windows machine by machine name, but perhaps I'm using the script incorrectly. As I said before, I can contact the Windows machines by IP but my rights are limited on shared folders.

---

### Post by evanchu on 2008-01-13
From my Ubuntu machine, I run
> netview echome3
where echome3 is my Windows machine name.

I get the following output
> 
Anonymous login successful
Domain=[WORKGROUP] OS=[Windows Vista (TM) Home Premium 6000] Server=[Windows Vista (TM) Home Premium 6.0]

        Sharename       Type      Comment
        ---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
Anonymous login successful
Domain=[WORKGROUP] OS=[Windows Vista (TM) Home Premium 6000] Server=[Windows Vista (TM) Home Premium 6.0]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------


Try it the report back.  Yes, this is confusing.  You have to be patient.  I did and I got it working.

---

### Post by Derspankster on 2008-01-13
Here's my output:

larry47@ubuntu1:~$ netview lairdla
bash: netview: command not found

---

### Post by evanchu on 2008-01-14
Netview is a script that I wrote.  You can [download it]("http://www.evanchu.com/linux2") from my page.  Try it and see what output you get.

---

### Post by horned0wl on 2008-01-14
> **Derspankster said:**
> Thank you for your response, evanchu.  I looked over the two scripts from the 'note' and I have a couple of questions. 1) My Windows computers run XP, not Vista. I am not sure if that makes a difference or not. 2) I'm a little confused as to why a Guest account needs to be turned on on the Windows machines. 3) I already have set up some shared folders on the Windows computers and they have no problem seeing one another and sharing. 4) I have read that Ubuntu (with Samba installed) can access shared Windows folders on the same network. I have never been able to do so on either of my Ubuntu computers. Sorry for being so long winded but I'm finding this very confusing.

EDIT: I can connect to my Windows shares from Ubuntu if I connect to the Windows machines IP.  I can not write to the Windows shares though but I can look at them and I can copy folders/files to my Ubuntu machines. As long as DCHP doesn't assign another IP to that machine, that is.

Hm. How weird.  I have just the opposite problem: Both of my Linux machines can see, share, read, write and execute on my Windows server with no problem at all, but they can't see each other, and my Windows server can't see either of them.  Go figure...  (Once I resolve this issue, I intend to dispense with my Windows server and go fully Linux in my house...

Cheers;
Ed

---

### Post by Derspankster on 2008-01-18
I guess I don't know how to use the script. I can't seem to make it work at all.

---

### Post by evanchu on 2008-01-18
> **Derspankster said:**
> I guess I don't know how to use the script. I can't seem to make it work at all.

I wrote a script, [samba-net-diag1]("http://www.evanchu.com/linux2"), to collect some basic Samba diagnostic information.  Download it from the the "Basic Samba diagnostics" section. Then run
```
bash samba-net-diag1
```
Collect the output and post it here.  I can take a look at the result.

In [another thread]("http://ubuntuforums.org/showthread.php?t=667902"), the Linux firewall was interfering with networking.  If possible, I recommend turning off firewall just for testing.

---

### Post by Derspankster on 2008-01-18
OK, thanks. here's my output:

larry47@ubuntu1:~$ bash samba-net-diag1
enter other computer's IP address and press enter: 192.168.1.11
enter other computer's name and press enter: lairdla
##########
try pinging lairdla
PING lairdla.MSHOME (208.67.217.130) 56(84) bytes of data.

--- lairdla.MSHOME ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2008ms

press enter to continue
##########
try pinging 192.168.1.11
PING 192.168.1.11 (192.168.1.11) 56(84) bytes of data.
64 bytes from 192.168.1.11: icmp_seq=1 ttl=128 time=4.58 ms
64 bytes from 192.168.1.11: icmp_seq=2 ttl=128 time=0.149 ms
64 bytes from 192.168.1.11: icmp_seq=3 ttl=128 time=0.149 ms

--- 192.168.1.11 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 0.149/1.628/4.587/2.092 ms
press enter to continue
##########
is 192.168.1.11 on local subnet?
PING 192.168.1.11 (192.168.1.11) 56(84) bytes of data.
64 bytes from 192.168.1.11: icmp_seq=1 ttl=128 time=0.155 ms
64 bytes from 192.168.1.11: icmp_seq=2 ttl=128 time=0.149 ms
64 bytes from 192.168.1.11: icmp_seq=3 ttl=128 time=0.149 ms

--- 192.168.1.11 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.149/0.151/0.155/0.003 ms
press enter to continue
##########
try Samba node status query lairdla
added interface ip=192.168.1.230 bcast=192.168.1.255 nmask=255.255.255.0
querying lairdla on 192.168.1.255
Got a positive name query response from 192.168.1.11 ( 192.168.1.11 )
192.168.1.11 lairdla<00>
Looking up status of 192.168.1.11
        LAIRDLA         <00> -         M <ACTIVE> 
        MSHOME          <00> - <GROUP> M <ACTIVE> 
        LAIRDLA         <20> -         M <ACTIVE> 
        MSHOME          <1e> - <GROUP> M <ACTIVE> 

        MAC Address = 04-4B-80-80-80-03

press enter to continue
##########
try Samba node status query 192.168.1.11
added interface ip=192.168.1.230 bcast=192.168.1.255 nmask=255.255.255.0
Looking up status of 192.168.1.11
        LAIRDLA         <00> -         M <ACTIVE> 
        MSHOME          <00> - <GROUP> M <ACTIVE> 
        LAIRDLA         <20> -         M <ACTIVE> 
        MSHOME          <1e> - <GROUP> M <ACTIVE> 

        MAC Address = 04-4B-80-80-80-03

press enter to continue
##########
try Samba node status query on local subnet
added interface ip=192.168.1.230 bcast=192.168.1.255 nmask=255.255.255.0
querying * on 192.168.1.255
Got a positive name query response from 192.168.1.230 ( 192.168.1.230 )
192.168.1.230 *<00>
press enter to continue
##########
try Samba list services on lairdla
added interface ip=192.168.1.230 bcast=192.168.1.255 nmask=255.255.255.0
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
timeout connecting to 208.67.217.130:445
timeout connecting to 208.67.217.130:139
Error connecting to 208.67.217.130 (Operation already in progress)
Connection to lairdla failed (Error NT_STATUS_ACCESS_DENIED)
press enter to continue
larry47@ubuntu1:~$

---

### Post by evanchu on 2008-01-19
> **Derspankster said:**
> 
enter other computer's IP address and press enter: 192.168.1.11
enter other computer's name and press enter: lairdla
##########
try pinging lairdla
PING lairdla.MSHOME (208.67.217.130) 56(84) bytes of data.

##########
try Samba list services on lairdla
added interface ip=192.168.1.230 bcast=192.168.1.255 nmask=255.255.255.0
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
timeout connecting to 208.67.217.130:445
timeout connecting to 208.67.217.130:139
larry47@ubuntu1:~$


I assume the Windows computer is named lairdla and it has 192.168.1.11.  I also assume it is on your home network with your Linux machine.

1. In the section "try pinging lairdla," the Linux machine thinks lairdla is lairdla.MSHOME with 208.67.217.130.  This is very strange.  Did you configure something like this?

2. In the section "list services on lairdla," the Linux machine, again, tries to query 208.67.217.130, which fails.

---

### Post by kbracer on 2008-01-19
I had been experiencing the same symptoms describe in a number of threads about issues accessing Windows shares. I solved of my problems accessing Windows shares by...

[LIST]
[*]Go to System>Administration>Network
[*]Select the General Tab of the Network Settings window.
[*]Set Domain Name to be the same as your home network workgroup name.
[/LIST]

I can now browse all of my machines and their shared folders through Places>Network

---

### Post by Derspankster on 2008-01-19
> **evanchu said:**
> I assume the Windows computer is named lairdla and it has 192.168.1.11.  I also assume it is on your home network with your Linux machine.

1. In the section "try pinging lairdla," the Linux machine thinks lairdla is lairdla.MSHOME with 208.67.217.130.  This is very strange.  Did you configure something like this?

2. In the section "list services on lairdla," the Linux machine, again, tries to query 208.67.217.130, which fails.

I did not configure anything like that. The network address of the Linux machine if fixed at 192.168.1.230. And yes, your assumption is correct, the Linux machine is on the same network as the Windows machine. Actually, there are 2 Windows machines, another Linux (laptop) and a Macbook Pro all on the same network. 

In response to the other gentleman, the general tab of my network settings is set to the network name. 

I can connect to the Windows machine by connecting directly to the IP 192.168.1.11 but not by querying the network or by machine name lairdla.

---

### Post by evanchu on 2008-01-20
> **Derspankster said:**
> I can connect to the Windows machine by connecting directly to the IP 192.168.1.11 but not by querying the network or by machine name lairdla.

Let us try to figure out why lairdla resolves to lairdla.MSHOME with 208.67.217.130.  Can you post the content of /etc/hosts, /etc/resolv.conf, /etc/samba/lmhosts?  You may not have lmhosts file.  Also post the output of ifconfig.

---

### Post by Derspankster on 2008-01-20
> **evanchu said:**
> Let us try to figure out why lairdla resolves to lairdla.MSHOME with 208.67.217.130.  Can you post the content of /etc/hosts, /etc/resolv.conf, /etc/samba/lmhosts?  You may not have lmhosts file.  Also post the output of ifconfig.

**OK, here's the various files and outputs**

**First - /etc/hosts**

127.0.0.1 localhost
127.0.1.1 ubuntu1.MSHOME

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

**/etc/resolv.conf**

nameserver 208.67.222.222
nameserver 208.67.220.220
domain MSHOME

[B]NOTE: These are OpenDNS nameservers

I have no lmhosts file

Finally, the output of ifconfig[/B]

eth0      Link encap:Ethernet  HWaddr 00:11:09:E9:7E:C0  
          inet addr:192.168.1.230  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:9ff:fee9:7ec0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37337 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44947 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16169728 (15.4 MB)  TX bytes:26478402 (25.2 MB)
          Interrupt:18 Base address:0xb800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:275 errors:0 dropped:0 overruns:0 frame:0
          TX packets:275 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25975 (25.3 KB)  TX bytes:25975 (25.3 KB)

Again, thank you for your patience.

---

### Post by Derspankster on 2008-01-20
I have successfully solved my problem. It had to do with the fact that I was using OpenDNS namerservers. I had to add my network name as an exception. on the OpenDNS dashboard.  I noticed that the address  being pinged was 208.67.217.130 and that it was close to the actual OpenDNS nameservers;

nameserver 208.67.222.222
nameserver 208.67.220.220

So I went to the OpenDNS site and poked around until I found the dashboard exceptions page, added my network name and now I can browse my network and all shared folders from any of my computers to any other computer.

It certainly was a strange problem that only affected my Linux computers on my network. I sincerely appreciate the help I received.

---

