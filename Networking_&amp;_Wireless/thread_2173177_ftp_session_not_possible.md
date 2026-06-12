---
title: "ftp session not possible"
date: 2013-09-08
forum: Networking &amp; Wireless
---

### Post by felix4 on 2013-09-08
Hi,

I cannot open any ftp connection and don't know why. I see two possible causes (cable modem or pc), but do not know how to check where the problem is. Please help.

Situation: When I got the new cable modem, I installed a ubuntu 12.04 on my pc and since then I cannot start a ftp connection. Whenever I try to start typ "ftp metalab.unc.edu" in the shell, I run into a timeout and do not even get a login request. same happens for any other ftp server and even the modems IP address. Same happens if I ping an outside server.

The new cable modem TC7200 is by Technicolor.
- The modem provides DHCP service
- Connection by http or ubunutu software center works fine
- I have admin access to the modem
- No forwarding, filter or trigger settings are done.  But as I am not trying to run a server but to open a client connection,  I would be surprised if this is neccessary. 

The PC is a Scaleo Siemens PC, connecting to the cable modem by wireless.

Option A) Problem is with the cable modem. Seems unlikely, as http and software center works. But seems likely as ftp and ping does not work. I could not find any reference to ftp setup issues, except when running a ftp server behind the modem, which is not what I am trying to do.

Option B) Problem is with the ubuntu pc. This would imply a special setup (user?, ports?) would be required to allow this. Which sounds very odd to me.

How to check for these two options?
And yes, I am ambarrased to ask this question.

Ciao, Felix

---

### Post by steeldriver on 2013-09-08
Hello and welcome to the forums

Can you be as specific as possible - for example "ping does not work" ... does that mean pinging metalab.unc.edu by name? if so does it fail to resolve the name to an IP address? or resolve OK but is unable to find a route to the host? A cut-and-paste of the exact terminal commands you typed and the output messages would help a lot - preferably between [CODE] ... [&#8725;CODE] tags

---

### Post by felix4 on 2013-09-08
Hi

>Can you be as specific as possible
I will try

Regarding ftp
Orginally I experienced the problem using gftp with the setup from pre-12.04 installation, but could not get a session established. Only after that I tried at the shell level.
As the test runs for ftp were done as root, the user setup issue seems not likely.
When I ftp the PC itself, I get a connection refused, as no ftp server is run on this PC. Would that be sufficient reason, to argue the problem is with the modem, not the PC?
```

root@felix-desktop:~# ftp felix-desktop
ftp: connect: Connection refused
ftp> bye
root@felix-desktop:~# ping felix-desktop
PING felix-desktop (127.0.1.1) 56(84) bytes of data.
64 bytes from felix-desktop (127.0.1.1): icmp_req=1 ttl=64 time=0.061 ms
64 bytes from felix-desktop (127.0.1.1): icmp_req=2 ttl=64 time=0.044 ms

```

Regarding ping:
Address resolving seems to work fine: metalab.unc.edu is resolved to 152.19.134.40, but ping does not get one package back.
```

root@felix-desktop:~# ping  metalab.unc.edu
PING metalab.unc.edu (152.19.134.40) 56(84) bytes of data.
^C
--- metalab.unc.edu ping statistics ---
142 packets transmitted, 0 received, 100% packet loss, time 142126ms

```
The admin logon to the cable modem is available at [http://192.168.0.1/](http://192.168.0.1/) . If I ping this address, I do get a normal reply with 2-3 ms turnaround time. Ftp to the modems address does not lead to a login prompt, but I assume the modem is not setup as a ftp server, so that would not be telling us anything anyway.
```

root@felix-desktop:~# ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_req=1 ttl=64 time=2.34 ms
64 bytes from 192.168.0.1: icmp_req=2 ttl=64 time=2.90 ms
root@felix-desktop:~# ftp 192.168.0.1
ftp: connect: Connection timed out
ftp> bye
root@felix-desktop:~# 

```

Regarding PC:root@felix-desktop:~# uname -a
Linux felix-desktop 3.5.0-39-generic #60~precise1-Ubuntu SMP Wed Aug 14 15:28:09 UTC 2013 i686 athlon i386 GNU/Linux



Thanks,
Ciao, Felix

---

### Post by carlwsnyder on 2013-09-08
I suspect that your 'modem' is actually a 'modem/router' since it supplies DHCP, and you will have to access the router as an administrator/root to allow passing Port 21 through the NAT firewall on the router to enable FTP.

---

