---
title: "[SOLVED] Internal Name Resolution Never has worked"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by Peter09 on 2008-05-22
I have an internal network of three machines plus various laptops running Hardy and previously Gutsy. I also have one or two visiting laptops running windows. 

All are served IP addresses by a NetGear router. The following problem of name resolution occurs on all Ubuntu machines.

Setup

1. Router tables show all connected devices by IP address and Name
2. All machines can resolve external names via the router
3. Browsing the network on all machine shows other machines by Name (Samba Shares)
4. Windows based machines have no problems in name resolution via the router

Problem:
All Ubuntu machines cannot resolve machine names
e.g 
$ping <a local machine name> does not work
$ping <IP address of local machine> works.

I cannot find a simple way of resolving this issue. The router has all the information, windows works, even network browsing works, but Ubuntu does not.

I have seen a lot of people with this issue but not found a satisfactory resolution to what is a basic problem.

Note - using fixed IP addresses and the /etc/hosts file is not a solution. 

This does seem to be a rather basic problem that has followed me around through three versions of Ubuntu without any sign of resolution or any activity by the development community. Whats missing here?

PC

---

### Post by Iowan on 2008-05-22
Let's see if I can remember the right names...
Inside **/etc/dhcp3/dhclient.conf** is a commented line to Send Hostname.  Uncomment that line, substitute the machine hostname, save and restart.

---

### Post by chili555 on 2008-05-22
Or add to /etc/hosts to reference the IP to the name, like this:```
127.0.0.1 localhost
127.0.1.1 LAPTOP60

192.168.1.116 MBR2.linux

192.168.1.101 frankenputer


# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```I can then:```
chili@LAPTOP60:~$ ping -c3 frankenputer
PING frankenputer (192.168.1.101) 56(84) bytes of data.
64 bytes from frankenputer (192.168.1.101): icmp_seq=1 ttl=64 time=93.8 ms
64 bytes from frankenputer (192.168.1.101): icmp_seq=2 ttl=64 time=4.67 ms
64 bytes from frankenputer (192.168.1.101): icmp_seq=3 ttl=64 time=4.34 ms
etc.
```

---

### Post by Peter09 on 2008-05-22
IOWAN,
thanks for the reply,
however it is not the local machine not sending a host name, remember that the router has all the host names, in fact so does Samba/file manager on the client. The problem is that any other application (such as ping, ssh etc) cannot find the target host name, where is the disconnect?

Chili555
Thanks but that is a statically routed schema, sometimes I will not know the IP address of a system without going back to my DHCP router.

PC

---

### Post by Iowan on 2008-05-22
Oops... sorry.  I somehow misread as "this machine is unreachable by hostname".  **/etc/resolv.conf** has router address as nameserver?

---

### Post by terazen on 2008-05-22
How does the router/dns server get the hostnames, manually entered or updated from dhcp?  If the router has the names, can the windows machines ping the ubuntu machines by name?

Apps like ping or firefox get information from what is under the host section of /etc/nsswitch.conf if I remember correctly.  Samba probably uses something else?

---

### Post by Peter09 on 2008-05-22
The router gets the names automatically during the period when it allocates the IP address. So there is some part of this process working without a problem. 

Windows gets host names ok, I have two NAS drives, both can be mounted in windows using their name.

PC

---

### Post by terazen on 2008-05-22
Can you run an nslookup from windows and ubuntu and post what the router replies with?

---

### Post by jetsam on 2008-05-22
> Apps like ping or firefox get information from what is under the host section of /etc/nsswitch.conf if I remember correctly. Samba probably uses something else?

Yes.  To resolve netbios (Samba/Windows networking) names from an Ubuntu system, install winbind:

```
sudo apt-get install winbind
```

and then edit the hosts line of /etc/nsswitch.conf so it reads something like so:

```
hosts:          files **wins** mdns4_minimal [NOTFOUND=return] dns mdns4
```

An important detail is that files and wins should precede other forms of name resolution.  Files should come first so that /etc/hosts gets priority.

**Added**: actually, you might experiment with where the **wins** goes in nsswitch.conf.  This also worked for me, and seems to perform slightly better with normal internet name resolution than the above:

```
hosts:          files mdns4_minimal [NOTFOUND=return] dns **wins** mdns4
```

---

### Post by Peter09 on 2008-05-22
Nslookup from Ubuntu

pc@toshlaptop:~$ nslookup Mesh
Server:		192.168.0.1
Address:	192.168.0.1#53

** server can't find Mesh: NXDOMAIN


PC

---

### Post by jetsam on 2008-05-22
A bit more testing revealed that installing winbind caused some browsing trouble in Nautilus in Hardy.  The following additional change to my /etc/samba/smb.conf seemed to fix that.  It seems to be all working well now, and I can ping from the command line by netbios name as well as browse from Nautilus.

```
name resolve order = lmhosts bcast wins host
```

**Peter**: I'm not quite sure if you've tried the winbind suggestion or not.  There are three ways to approach the problem that I know of; host files like Chili suggested, winbind, and setting up your own DNS server.  Host files is good, but not if you need dynamic ip addresses.  A DNS server is complex, beyond my experience, and raises its own integration issues with Windows.  To the best of my knowledge, that leaves winbind as the most practical solution on a small dynamic network.

---

### Post by Peter09 on 2008-05-23
Thanks Jetsam,
I've not had a chance to try your solution yet but will do. I am just a bit disappointed that Ubuntu does not address these sort of issues out of the box. 

While I guess the average user with a single PC would not really find this a problem, any intermediate user with perhaps a NAS device or running two machines, or perhaps trying a virtualised setup would come across this.

My router is a standard type device that does act as a name server, yet Ubuntu is incapable of using it.

I'll try your solution and report back, thanks for your input.

PC

---

### Post by terazen on 2008-05-23
Did you ever do the nslookup from a windows box?  Ubuntu is definately using your router as a dns forwarder which is why you can surf the internet.

If you can lookup sites like google.com and not mesh, then the issue is that your router doesn't resolve the computer names like you thought it did (netbios is resolving it and you thought the router was which is confusing).  Windows works "out the box" because netbios is on by default and I don't think the Ubuntu folks would do this is a million years. :-)

Anywho Jetsam's suggestion should work.  Let us know!

---

### Post by Peter09 on 2008-06-05
Sorry that I have not progressed this at the moment but I have not been able to due to getting the time available to do it.


One of the things in all of this is that Samba can resolve the machine names (browsing the internal network through nautilus) but that internally the machine cannot, so that ping, ssh etc does not work by machine name, only ip.

PC

---

### Post by wdaniels on 2008-06-06
> **Peter09 said:**
> One of the things in all of this is that Samba can resolve the machine names (browsing the internal network through nautilus) but that internally the machine cannot, so that ping, ssh etc does not work by machine name, only ip.

This has already been explained:

> **terazen said:**
> If you can lookup sites like google.com and not mesh, then the issue is that your router doesn't resolve the computer names like you thought it did (netbios is resolving it and you thought the router was which is confusing).  Windows works "out the box" because netbios is on by default and I don't think the Ubuntu folks would do this is a million years. :-)

You are confusing the fact that the router shows the NetBIOS names in it's DHCP table with it's DNS function - it does not put the NetBIOS names into some local DNS database and resolve them for all the network, that part happens on the client machines. When either Samba or Windows resolves a NetBIOS name for you, it is done via WINS, not via the router's DNS. The configuration given by jetsam just adds WINS as a default name resolution service in Ubuntu, which is essentially the same then as what Windows is doing - the router plays no (direct) part in that in either case.

Since WINS is a Microsoft protocol, there is no reason why Ubuntu would ever use it by default, but I do think there ought to be some easy GUI option to set this up, just like there is with Windows file sharing.

There is no single "default" equivalent to WINS for Linux machines because there are a few common methods used depending on circumstances. But the simplest default equivalent in Ubuntu (since Fiesty I think) is avahi (equivalent to Apple's Zeroconf) which can be used to resolve host names similarly to the way WINS does on a Windows network, only you have to explicitly append the scope e.g.

```
ping mylinuxhost.local
```

---

### Post by Peter09 on 2008-06-12
Just an update here - the changes suggested in the thread, install winbind and edit /etc/nsswitch.conf resolved the problem.

I do think that we should accept that Ubuntu at the moment is liklely to be operating in a windows environment and such details as these should either be default in an install or some optional part of the install procedure. This is not something the 'average' user should be expected to resolve.

Thanks to all who helped.

PC

---

### Post by NomadicExistance on 2011-08-14
Jumping in to the thread three years later, with Natty... Was seeing the same problem. Couldn't ping my NAS device by name.. DHCP table on the router had the name. Was able to modify the nsswitch.conf and get this working without having to install winbind. Am completely new to Ubuntu, so not sure if something's changed in Natty (which is why winbind was not needed)...

---

