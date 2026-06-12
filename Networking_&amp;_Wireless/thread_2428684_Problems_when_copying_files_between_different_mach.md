---
title: "Problems when copying files between different machines using scp"
date: 2019-10-07
forum: Networking &amp; Wireless
---

### Post by pneuron on 2019-10-07
I am using Ubuntu 18.04. and am trying to copy a file from a remote machine onto my local machine.

First I tried using this:

scp /path/to/file username@hostname:/path/to/destination
 
and got this error message: 

ssh: Could not resolve hostname <hostname>: Name or service not known
lost connection

I checked that the username and hostname are correct using whoami and hostname.

then I tried to do use my internal IP address instead of the hostname (which I found using hostname -I, but interestingly cannot find it via the command ip add), but this results in the following error message:

ssh: connect to host <IP address> port 22: Connection timed out
lost connection

How can this be resolved? Or is there another easier way to copy files between machines I should try? Thank you in advance.

---

### Post by SeijiSensei on 2019-10-07
Probably the remote machine cannot resolve your local machine's name. 

If you're trying to copy a file from the remote, you should connect from the local machine like this:
```
scp remote:/path/to/file /path/to/local/destination
```

Presumably your machine can resolve the remote's name.

Also if you're behind a firewall router, the remote cannot connect to your local machine (without port forwarding through the router), but your local machine can connect to the remote.

---

### Post by TheFu on 2019-10-07
As SeijiSensei said, sounds like a name resolution issue.  There are different ways to set that up on Unix systems.  Unlike Windows, every other OS needs a phone book to find the *IP <--> computer-name* lookup.

Originally, this was handled using the /etc/hosts file on every machine.  In the early days of the internet, we'd constantly update our local /etc/hosts with the information for all the internet hosts in the world. That doesn't scale too well, but it can work find on a local network.  I still use this on my home network with fewer than 100 devices.

For scalability, DNS was created.  Many people run a DNS server inside their home networks.  Some servers will run both DNS and DHCP with both of those tied together so DHCP clients get added to the DNS automatically.  I've never done that.  However, I do use *DHCP reservations* to force static IPs onto my portable clients, like tablets, phones, and laptops.  Here's how: [https://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](https://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management)

Around 2010-ish or so, attempts began to have Linux work similar to the way Microsoft Netbios works by announcing different services on the subnet for other systems to "find".  Initially, that tool, **avahi**, had lots and lots of issues, but for the last few years, I understand it works pretty well and integrates with the mDNS server on Ubuntu Desktop systems nicely.  Both mDNS and Avahi have been installed on Ubuntu Desktops by default for some time.  There is a trick to use them, however.  They append ".local" to all hostnames.

So, 
```
scp /path/to/file [email]username@**hostname.local[/email]**:/path/to/destination-directory/
```

Obviously, you should put in your real username and the real hostname for this to work.  You can always use the IP address, but if that IP isn't static, it will change from time to time.  I find it is just easier to forced static IPs on the systems here that don't move outside the home network. That would be all Desktops (big cases) and servers.  I use that DHCP reservation technique for portable devices and for a few media players and other small devices like networked TV tuners because it is handy to know that hdhd4 is on 192.168.22.24, always.

If you do have avahi working, you can use a ~/.ssh/config file to setup an xref for hostname ---> hostname.local, so you'd not need to worry about adding that post-fix to every ssh-based command.  For example:
```
host n800
  hostname n800.local

host hdhr4
  hostname   192.168.22.24

host rpi4
  hostname rpi4.local
  user osmc
```
That's just a few examples. 1 or 5,000 stanzas can work.  The hostname entry can be DNS names, IPs, or Avahi names.  I bet IPv6 will work there too.  If you want to use a different userid for the connection, there's an example of that too. If the userid on system A and system B are the same, no need for it.
Sorta handy?

This config file works for all ssh-based tools.  So, ssh, scp, sftp, rsync, rdiff-backup, duplicity, sshfs, and 50 others.  It is very, very handy for connections to AWS or linode or other cloudy VPS provider systems.  You use names that make sense to you, not their funky names that have to be unique in the entire world.

---

