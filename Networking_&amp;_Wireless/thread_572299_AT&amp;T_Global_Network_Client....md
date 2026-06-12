---
title: "AT&amp;T Global Network Client..."
date: 2007-10-10
forum: Networking &amp; Wireless
---

### Post by sn4265 on 2007-10-10
Hey all...  I am attempting to replace my work Windows laptop with Linux.  Ubuntu installed fine, but I ran into a couple of issues.  Some of these I can deal with and try to figure out later, but a couple are absolute show stoppers.  The first of these is getting VPN connectivity working under Linux.  We use AT&T's VPN network, so none of the usual Linux VPN clients work with this to my knowledge.  As such I am attempting to install a 5 year old Linux client from AT&T.  Unfortunately, but not surprisingly, I am running into problem and so I turn to you for help.

The laptop is a Dell Latitude 505 running Ubuntu 7.0.4.  I am attempting to install the AT&T Global Network Client for Linux and I'm running into dependency issues.  Here are the dependency requirements listed in the documentation:

  LibXext.so.6
• LibX11so.6
• Libstdc++-libc6.1-1.so.2
• Libm.so.6
• Libc.so.6
• /lib/ld-linux.so.2

Here is what happens when I attempt to execute the setup program for the software:
root@scott:/home/scott/Desktop# ./setup
./setup: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory

I attempted creating a the following link and trying this again, and here is the results of this:
root@scott:/usr/lib# ln -s libstdc++.so.6.0.8 /usr/lib/libstdc++-libc6.1-1.so.2
root@scott:/home/scott/Desktop# ./setup
./setup: symbol lookup error: ./setup: undefined symbol: __builtin_new

Any help would be greatly appreciated.  I would really love to get off of Windows completely.  I'm a Unix admin here at work, so I really have no need or love for Windows.

Scott

---

### Post by Jussi Kukkonen on 2007-10-10
Package libstdc++2.10-glibc2.2 contains libstdc++-libc6.2-2.so.3

Try making a link to that...

---

### Post by sn4265 on 2007-10-10
Thanks loads for the hint.  This got the installation working and everything looked good until the realization hit that this is purely a PPP dialer connection.  I'm really needing something similar to the Windows client that allows you to connect via an existing Ethernet/Broadband connection.  Unfortunately, I think I'm pretty much sunk.

My one hope is that someone knows of a way to connect to the AT&T VPN network using another tool.  If so, I would really love to know how to do this.  Otherwise, thanks again for the help.

Scott:(

---

### Post by mips on 2007-10-10
Will the OpenVPN or CiscoVPN client not do the job ?

---

### Post by Lambert on 2007-10-10
> **mips said:**
> Will the OpenVPN or CiscoVPN client not do the job ?

Hey there mips, long time.

tried to send you a PM said your box was full.

Hope things are well with you.

sorry for the hijack.

---

### Post by mips on 2007-10-10
> **Lambert said:**
> Hey there mips, long time.

tried to send you a PM said your box was full.

Hope things are well with you.

sorry for the hijack.

Hi Lambert,

Yeah, long time no see, all is well.

Try the PM again as I did a cleanup ;)

---

### Post by barbolani on 2008-01-22
Hey guys, can you share your wisdom on the setup of the ATT VPN over an existing Internet connection? I dream of accessing the company network from home using Linux and not having to carry home my crippled Windows Laptop.

---

### Post by barbolani on 2008-01-23
Finally I found this on Google:

[http://gallery.kosternet.dk/archives/2008/01/15/installing_at&t_global_network_client_on_ubuntu/index.html](http://gallery.kosternet.dk/archives/2008/01/15/installing_at&t_global_network_client_on_ubuntu/index.html)

It does not work on my machine because my connection is not via SSL and the network client only supports SSL. But everything else was fine. Now at least those with connections via SSL can use it.

---

### Post by ajoergensen on 2008-01-23
Actually the right URL is [http://www.nowhere.dk/archives/2008/01/15/installing_at&t_global_network_client_on_ubuntu/index.html](http://www.nowhere.dk/archives/2008/01/15/installing_at&t_global_network_client_on_ubuntu/index.html)

---

### Post by titaniumlou on 2008-03-21
> **barbolani said:**
> Finally I found this on Google:

[http://gallery.kosternet.dk/archives/2008/01/15/installing_at&t_global_network_client_on_ubuntu/index.html](http://gallery.kosternet.dk/archives/2008/01/15/installing_at&t_global_network_client_on_ubuntu/index.html)

It does not work on my machine because my connection is not via SSL and the network client only supports SSL. But everything else was fine. Now at least those with connections via SSL can use it.

Can you elaborate on this a little?

I have mine installed now and it says the connection is established, but I cannot resolve any IP addresses that are inside the VPN, I can only get DNS responses from Internet DNS servers...

Thanks in advance

---

### Post by mips on 2008-03-22
Stupid question but have you specified the VPN DNS ip addresses?

---

### Post by aftertaf on 2008-03-22
same here... 
my account visibly isn't authorized to access VPN servers via SSL protocol...

so, is there a plan to allow non SSL access in the ATT linux client?
or, is there a workaround of any kind... i.e. an encapsulation method to convert SSL to normal between the client and the VPN servers?

Otherwise, good work ATT guys, this is most definitely a step forward
:guitar:

---

### Post by titaniumlou on 2008-03-22
> **mips said:**
> Stupid question but have you specified the VPN DNS ip addresses?

I haven't manually added those to my network configuration, but when I type "route" in a terminal window I do see that there are routes defined for the VPN addresses.

One weird thing though is that "ifconfig" doesn't show any packets as going through the tunnel adapter, it still all goes through my wireless card, but maybe that's the way it's supposed to work.

I'm still interested in the SSL piece of this, as I would think that the VPN would be using SSL to encrypt all of its traffic (as opposed to TLS for example) but do you guys think that all of your connections have to be made via SSL in order for any of the VPN traffic to work??

EDIT:
Ok, so I found some more details that I think let me know why the problem is occurring, I'm just not sure how to go about fixing it.

At the end of dmesg I see the following:
```

[ 2750.856000] tun0: Disabled Privacy Extensions
[ 2790.288000] Unknown OutputIN= OUT=tun0 SRC=9.48.60.203 DST=9.0.9.1 LEN=56 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=32787 DPT=53 LEN=36 
[ 2791.288000] Unknown OutputIN= OUT=tun0 SRC=9.48.60.203 DST=9.0.8.1 LEN=56 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=32788 DPT=53 LEN=36 

```

I've posted this info in the AT&T Linux client support forums so we'll see where this goes...

---

### Post by titaniumlou on 2008-03-26
bump?

---

### Post by aftertaf on 2008-04-03
rebump...:popcorn:
i also asked on the forum on ATT
[http://attnetclient.com/forum/viewtopic.php?t=721](http://attnetclient.com/forum/viewtopic.php?t=721)

---

