---
title: "Need advice for script : detecting connection"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by Cathou on 2007-02-07
Hi,

in a package of mine I provide a script which is supposed to be executed via sudo. A part of its purpose is to check that the machine is connected to internet.

As of now, this is implemented as a double ping command:
```

ping <dotted inet address>
ping <named inet address>

```
Of course I check ret values for these commands, and this is sufficient in most cases. 
However, a user pointed out that his firewall (iptables rules) makes this fail. It could even be worse: some ISPs may implement ICMP filtering themselves..

So on second thought, my double ping trick is quite naive :(

Instead, I presume that I could silently invoke netstat and interpret its output as smartly as I can, but I don't have enough networking knowledge so that the connected/disconnected diagnosis be reliable.

Can anyone suggest the correct way to do this, or any other smart method? TIA

---

### Post by lloyd_b on 2007-02-07
First off, there is NO way to guarantee that a machine is connected to the internet by just looking at netstat results.  Those will only tell you about *active* connections, but not whether or not the machine can *potentially* reach the internet.

 Looking at routing table will tell you if there's a default route that could potentially be used for internet connections, but it cannot detect if there's actually a path to the internet available.

Your double ping solution isn't entirely worthless, except when somebody is filtering ICMP (which isn't all that unusual, unfortunately).

The only way to guarantee that internet access is available is to actually open up a connection and fetch something.  For example, ```
wget  www.google.com/robots.txt
``` will attempt to lookup "www.google.com", and open up a connection to that site and fetch the "robots.txt" file.  Run this command, and after it completes check if there is a "robots.txt" file in the current directory.  If so, then you have internet access.  Since this uses HTTP, it's VERY unlikely to be firewalled.

The only problem with this is that there's no guarantee that "wget" is installed on the machine in question.  You could make "wget" a dependency of your package, but it seems like a waste to require it just for a simple test like this (though it is a very useful utility).

Lloyd B.

---

### Post by koenn on 2007-02-07
you could use hping, which allows use of utp and tcp i.s.o. icmp. You'd have to have it installed, so your package will need to depend on it. 

alternative, using your netstat suggestion:

you can filter a connection to a given IP address out of netstat output with something like
netstat -n |grep 64.233.183.147. |grep ESTABLISHED
return is captured in $?
0 = 2nd grep successful, so there is a line in netstat output that has 64.233.183.147 an ESTABLISHED
1= grep failed, so ip address and "ESTALISHED" are not found in same line of output.

netstat -n : numeric, ip addresses. names work to (without -n, name resolution by default)

> /dev/null will make it silent (redirect output to 'nowhere')

For this to work, you need to establish a connection first - presumably on tcp port 80 of a given (arbitrary ? ) ip address. You could use telnet (with & to put it in background)

so you could take this for a start:
```
#connection attempt to google.be at port 80
telnet 64.233.183.147 80 & 

# connection established ?
netstat -n |grep 64.233.183.147 |grep ESTABLISHED 

# test grep return value to produce feedback
[ $? = "0" ] && echo "connection: success" || echo "connection failed" ;
```

---

