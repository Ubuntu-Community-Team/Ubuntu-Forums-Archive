---
title: "Hostname not populating to Router"
date: 2007-01-23
forum: Networking &amp; Wireless
---

### Post by jimbren on 2007-01-23
I've got an odd problem that I can't seem to get past.  

I've got a network set up with 3 windows computers and 2 Ubuntu computers, connected via wireless to a Netgear router.  

When I look at the connected devices on the Netgear router, the host names for both Ubuntu machines are blank.  

I've uncommented the send host-name line from my /etc/dhcp3/dhclient.conf, so it reads:
```
send host-name "smith"
```
on one machine and 
[CODE send host-name "zion"[/CODE] 
on the other.

I also have winbind installed on both machines, though I haven't attempted to do any configuration of winbind.

The SSID and (and the Windows Workgroup is 'MATRIX'

Should I edit my send host-name lines to read "smith.matrix' and 'zion.matrix'?

Or is there something else I'm missing?


Thanks,


jimbo

---

### Post by billstei on 2007-01-23
I have two Ubuntu computers, and one has the host name registered and the other is blank in my DI-604 router dhcp server.  No idea why.

---

### Post by dannyboy79 on 2007-01-23
within my netgear router both my xubuntu laptop as well as my ubuntu machine both have their hostnames. i am sure it's your /etc/hosts file and the way it has it's hostnames listed in it. here's mine as an example:

127.0.0.1       localhost.localdomain   localhost
192.168.0.3     ubuntu.getmyip.com      ubuntu
192.168.0.5     XUBUNTU
192.168.0.4     WINXP

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

i don't think it has much do with what you have stated due to the fact that I don't use dhcp! both of my mahcines are static ip. basically the 192.168.0.3 entry is my static ip and it's long name is ubuntu.getmyip.com, that's the FQDN but it can also be refered to as just ubuntu which is it's short name. i did this when I setup sendmail I believe. there is a tab between the entries. i can't suggest anything else, sorry. what do you get when you type hostname at the command prompt?

---

### Post by billstei on 2007-01-23
Perhaps there is something that can be done with the hosts file, however both my machines have identical /etc/hosts files (except for the host name specifically), yet one registers and one does not.

---

### Post by dannyboy79 on 2007-01-23
i forgot to mention that I have winbind  3.0.22-1ubuntu3.1 installed on both my machines. as well as samba. don't know if this matters?

---

### Post by billstei on 2007-01-23
Thanks Dannyboy79 for taking the time to consider this.  I did not have winbind on either machine, but installed it on both just to see what would happen and there is no change.  Samba was already running on both machines, and smbclient too.  The /etc/samba/smb.conf files are again identical except for the specific shares listed.

---

### Post by billstei on 2007-01-23
Okay, here is what I came up with...in the file /etc/dhcp3/dhclient.conf on line 14:

Change:
#send host-name "andare.fugue.com";

to:
send host-name "myhostname";

and now the DI-604 shows the name.

---

### Post by dannyboy79 on 2007-01-24
well I am glad it's working for ya now but my machine's hostnames both populate in my router and I don't use dhcp, all my machines are static so obviously there is something else no set up correctly. Well, let me rephrase that, you don't have anything setup INcorrectly, it's just that it's different than mine SOMEHOW which is preventing your machines hostnames to show up in your router without doing what you did in Ubuntu dhcp config. Anyway, glad you got it!

---

