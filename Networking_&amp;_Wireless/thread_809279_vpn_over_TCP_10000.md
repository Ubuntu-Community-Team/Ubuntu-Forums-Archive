---
title: "vpn over TCP 10000"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by tamoneya on 2008-05-27
My company network uses TCP 10000 for its vpn network.  I have used vpnc before and understand how to make the conf files with encrypted passwords and such but I cant figure out how to get it to work over TCP 10000.  I have experimented around in my xp dual boot and I found that it is necessary to use the TCP 10000 instead of th jsut the default because initally I forgot to set it to TCP 10000 and it did not work even though I had all the correct passwords. 
The vpn uses group authentication so so far I have the three following lines in my default.conf:
```
IPSec gateway _my_IP_
IPSec ID _network_name_
IPSec secret _im_not_telling_
```
Currently when I try to connect with vpnc through command line I get this:```
tamoneya@tamoneyat61:~$ sudo vpnc default
Enter username for _my_IP_: 
Enter password for @_my_IP_: 
vpnc: no response from target

```

---

### Post by jcostom on 2008-05-27
> **tamoneya said:**
> My company network uses TCP 10000 for its vpn network.

Then, unfortunately, you're sunk.  According to the VPNC home page, they don't support tunneling over tcp.  If you can get them to allow you to do standard udp encapsulation (i.e. nat-t, which Cisco does support) in addition to the tcp/10000 tunnels, you'd be home free.

---

### Post by tamoneya on 2008-05-27
are there any other programs that out there that will support the tcp 10000 tunneling.

---

### Post by Rob_H on 2008-09-11
> **tamoneya said:**
> are there any other programs that out there that will support the tcp 10000 tunneling.

Yes! The closed-source Cisco VPN Client handles IPsec over TCP. I am using it now in openSUSE, but it should work just as well with Ubuntu. It can be tricky to get it from their web site, though, unless you (or your IT department) has a support agreement with them. If you google around, you can find older versions of the client on some web sites, but I discovered that only the latest version works with the openSUSE 11.0 kernel. Good luck!

---

### Post by ar_hnazari on 2010-11-03
Hi everyone

Just got it done like peace of cake

The problem is not VPNC

it's all about network-manager-vpnc

So we'll forget it and use vpnc itself

> $ sudo apt-get install vpnc

Then after installation:

> $ nano /etc/vpnc/PROFILE-NAME.conf

Put below inside the file, save, quit:

> IPSec gateway <gateway-ip-address>
IPSec id <group-name>
IPSec secret <group-key-or-pass>
Xauth username <your-user-name>
Xauth password <your-password>
Enable Single DES

So everything is ready ha?

> $ sudo vpnc PROFILE-NAME

It says:
> VPNC started in background (pid: PID-NO)...

And you are connected ...

Sure for disconnecting you have to kill vpnc:

> $ sudo kill PID-NO

And don't ask, of course I connected through IPSec over TCP :)
 
Have fun friends

---

### Post by noravanq on 2011-06-30
I just wanted to confirm that the solution suggested by ar_hnazari works. Thanks a lot! 

After countless hours spent trying all sorts of things without any success, such a simple solution.

I had a .pcf file so used the perl script [http://svn.unix-ag.uni-kl.de/vpnc/trunk/pcf2vpnc](http://svn.unix-ag.uni-kl.de/vpnc/trunk/pcf2vpnc) to convert it to .conf

To run the script, simply do

```
perl pcf2vpnc.pl <name.pcf> <name.conf>
```

---

