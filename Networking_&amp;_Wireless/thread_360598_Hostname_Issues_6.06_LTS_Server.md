---
title: "Hostname Issues: 6.06 LTS Server"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by GoJimbo on 2007-02-13
Hello:

I installed Ubuntu 6.06 LTS Server on a new Dell PowerEdge 1950 and configured networking but I cannot seem to get the hostname setup properly and can only ssh via the IP.  I've tried various configs in /etc/hosts but nothing seems to work for me.  

I have an old PowerEdge 2300 in my office running 6.06 Desktop that I configured similarly as a webserver for testing and had no networking or hostname problems.  Planning to use the new machine as a LAMP server to host a website and a few internal staff applications.  Advice and suggestions would be appreciated.  Thanks in advance!

**My /etc/network/interfaces**
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address xxx.xx.xxx.xx
netmask xxx.xxx.xxx.x
broadcast xxx.xx.xxx.xxx
gateway xxx.xx.xxx.x


**My /etc/hostname**
library

**My /etc/hosts **
127.0.0.1 localhost.localdomain   localhost
xxx.xx.xxx.xx  library.csp.edu    library

**My /etc/resolv.conf**
search csp.edu
nameserver xxx.xxx.xx.xx
nameserver xxx.xx.xxx.xx
nameserver xxx.xxx.xx.xx
nameserver xxx.xx.xxx.xx

**uname -n**
library
**hostname -a**
library
**hostname -s**
library
**hostname -d**
cps.edu
**hostname -f**
library.cps.edu
**hostname**
library

**Putty**
Unable to open connection
library.cps.edu
host does not exist

---

### Post by chili555 on 2007-02-13
> Putty
Unable to open connection

If you are using Putty, may I assume you are trying to reach "library" from a Windows machine? There will be no way for your Windows machine to translate library into its IP address, such as 192.whatever.wherever until you amend its hosts file to add:

xxx.xx.xxx.x   library

You may need to be sure to match up the way you Putty into the Ubuntu machine with the Windows hosts file. That is, if you Putty in with "library", thats all you will need in the hosts file of the Windows machine.

Or, have I assumed wrong?

---

### Post by GoJimbo on 2007-02-13
Hi,

You are correct that I putty from a windows machine in my office into the server which is housed elsewhere.  

Before getting the new server I had another machine configured with this hostname and IP but it was here when I took the job and was running Mandrake.  I puttied into the old machine as well and always did it as follows: opening putty and entering myusername @ library.cps.edu and then entering my password when prompted in the terminal.  

I don't recall doing any setup or configuring with Putty in the past, or on my Windows machine.   I just downloaded it and was able to access using the above method.  In fact the test machine I mentioned earlier works the same, I am able to putty into it using myuser @ testbox.cps.edu.

I suppose its not a great problem having to ssh via IP but since I haven't experienced this issue before I feared it might also affect me when I begin configuring apache to serve my pages.

---

