---
title: "[SOLVED] /etc/network/interfaces ignored on boot?!"
date: 2006-07-26
forum: Networking &amp; Wireless
---

### Post by SPW06 on 2006-07-26
Hi,

Im running kubntu 6.06 trying to set up a static ip address for port forwarding with on my router, a linksys WRT54GS witth up to date firrmware.

My problem is this:

I edited /etc/network/interfaces with


  GNU nano 1.3.10         File: /etc/network/interfaces

# /etc/network/interfaces -- configuration file for ifup(8), ifdown(8)

# The loopback interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static

address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1


But after boot ifconfig eth0 shows

eth0      Link encap:Ethernet  HWaddr 00:0D:87:AA:53:51
          inet addr:169.254.207.173  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::20d:87ff:feaa:5351/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2918 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2446 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2277570 (2.1 MiB)  TX bytes:348581 (340.4 KiB)
          Interrupt:11 Base address:0xdc00

and thats not even close to what my IP sshould be. DCHP is turned off on my router; and I still get internet (no idea how)!

I can run ifdown eth0 and then ifup eth0

and get after each command

postconf: fatal: open /etc/postfix/main.cf: No such file or directory

Maybe thats causing my problem?
but ifconfig eth0 shows it works

eth0      Link encap:Ethernet  HWaddr 00:0D:87:AA:53:51
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:87ff:feaa:5351/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3000 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2493 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2283737 (2.1 MiB)  TX bytes:353965 (345.6 KiB)
          Interrupt:11 Base address:0xdc00

After that a neeed to re-type tthe workgroup in Samba.

**UPDATE:  none of the above steps any more ](*,)**
ot.

Any ideas on a fix for this? I'm not the only one wwho uses this computer, and I need samba working!

---

### Post by vorplex on 2006-07-31
I'm having the same exact problem as you. I changed eth0 to a static IP but upon reboot I have to run [COLOR="seagreen"]**ifup eth0**[/COLOR] to get it to work.

/etc/network/interfaces
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
iface eth0 inet static
         address 172.16.0.1
         netmask 255.255.255.0
         gateway 172.16.0.254

```

So how do I get eth0 to start automatically on boot like it did when it was DHCP?

---

### Post by mips on 2006-07-31
It's not a fix but you can do that in a init script when ubunutu boots up. Bring the interface down then up again.

---

### Post by bensexson on 2006-07-31
Do you have the file etc/postfix/main.cf?

This is mine:
# See /usr/share/postfix/main.cf.dist for a commented, more complete version

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

myhostname = localhost.localdomain
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = <my hostname>, localhost.localdomain, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only

---

### Post by vorplex on 2006-07-31
DOH! I had taken out [COLOR="Green"]**auto eth0**[/COLOR], after putting in back in my eth0 works fine on bootup.
/etc/network/interfaces
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 172.16.0.1
netmask 255.255.255.0
gateway 172.16.0.254
```

---

