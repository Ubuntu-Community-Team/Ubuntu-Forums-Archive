---
title: "Edgy: /etc/resolv.conf gets overwritten, need to add DNS after each boot"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by halfvolle melk on 2006-11-24
Hi,
I use a static IP, or at least, that's how I configured /etc/network/interfaces. The file /etc/resolv.conf says not to edit it manually because it will be overwritten and indeed that's what happens. Some mucking about in /etc/dhcp3/dhclient.conf hasn't helped either so far. GUI didn't work either.
Might DHCP be running anyway and if so how do I shut it off? Or else how to prevent resolv.conf from being overwritten or otherwise keep my DNS settings? I don't want a DHCP solution, I want a static IP.
Thanks in advance,
HM

---

### Post by trubblemaker on 2006-11-24
static ip's are setup up via /etc/network/interfaces if you man 'interfaces' you will see how it's supposed to be setup.

here's an example:

```
auto eth0
iface eth0 inet static
    address 192.168.1.1
    netmask 255.255.255.0
```

---

### Post by trubblemaker on 2006-11-24
if you use the network gui to do anything it has a bad habit of overwriting your /etc/network/interfaces file.  If you don't have your interface after booting it means that something in the interfaces file failed.

---

### Post by halfvolle melk on 2006-11-25
Edit: Fixed. fdoving @ #kubuntu suggested to add the nameserver to /etc/resolvconf/resolv.conf.d/head. This requires the resolvconf package.

Thanks for your reply but the interfaces file is just fine.
After a reboot I can ping stuff just fine. But the DNS is wiped from the resolv.conf file just like it says in the file itself. So where can I manually enter the DNS and make it stick?

---

### Post by trubblemaker on 2006-11-25
k you want a static ip or you want to set your dns servers, the two aren't the same which do you want?

---

### Post by halfvolle melk on 2006-11-25
> **trubblemaker said:**
> k you want a static ip or you want to set your dns servers, the two aren't the same which do you want?
trubblemaker, thanks for your input.
I'v got this set-up:

Kubuntu 6:10 desktop, static IP.
|
Debian server, no dhcp sever
|
internet

In Dapper one could just add the DNS to /etc/resolv.conf without it being overwritten and put the static adress in /etc/network/interfaces and that was it.
After a default install of Edgy there is apparently a script in place for dynamic resolving. The options suggested [here](http://ubuntuforums.org/showthread.php?t=305275) did not work for me. However, as posted above you can get around this by adding your DNS to /etc/resolvconf/resolv.conf.d/head. It will generate a resolv.conf with your DNS in it.

---

### Post by Linuturk on 2007-01-29
I spent a few minutes working on this, and I thought I'd explain it a bit more for the confused.

First, make sure you have internet access, and make sure resolvconf is installed on your system.

"sudo aptitude install resolvconf"

Next, let me explain the elements of resolvconf.

/etc/resolvconf/resolv.conf.d/head is the header file for the dynamic generation. Leave this alone.

/etc/resolvconf/resolv.conf.d/base is the "meat" of the file, or the middle. Define your nameservers here using this syntax: "nameserver xxx.xxx.xxx.xxx" where xxx.xxx.xxx.xxx is the ip of your nameserver.

/etc/resolvconf/resolv.conf.d/tail is the ending of this file. Leave this one alone too.

/etc/resolvconf/resolv.conf.d/original is the original configuration of the file. These isn't anything you have to do for this file.

After you have applied your changes, but **before** you restart your network service, run this command:

"sudo resolvconf -u"

This will run the script and update your /etc/resolv.conf file. This apparently should happen every time the machine boots.

After that, restart your networking service with this command:

"sudo /etc/init.d/networking restart"

Voila!

---

### Post by dbott67 on 2007-01-29
> **halfvolle melk said:**
> Hi,
I use a static IP, or at least, that's how I configured /etc/network/interfaces. The file /etc/resolv.conf says not to edit it manually because it will be overwritten and indeed that's what happens. Some mucking about in /etc/dhcp3/dhclient.conf hasn't helped either so far. GUI didn't work either.
Might DHCP be running anyway and if so how do I shut it off? Or else how to prevent resolv.conf from being overwritten or otherwise keep my DNS settings? I don't want a DHCP solution, I want a static IP.
Thanks in advance,
HM

By default, the dhclient.conf file will overwrite the resolv.conf file each reboot, so you need to edit the dhclient.conf file:

1. Backup the file first:
```
sudo cp /etc/dhcp3/dhclient.conf /etc/dhcp3/dhclient.conf.bak
```

2. Edit the dhclient.conf file:
```
sudo gedit /etc/dhcp3/dhclient.conf
```

3. Look for the following line:
```
#prepend domain-name-servers 127.0.0.1;
```
Remove the comment (#) and change it to:
```
prepend domain-name-servers **[COLOR="Red"]your.preferred.dns.server[/COLOR]**;
```

4. Next, look for the **[COLOR="Red"]domain-name-servers,[/COLOR]** and ***remove*** it:

```
**[COLOR="Blue"]prepend domain-name-servers your.preferred.dns.server;[/COLOR]**
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, **[COLOR="Red"]domain-name-servers,[/COLOR]** host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
```

5. Restart your network
```
dbott@edgy:~$ sudo/etc/init.d/networking restart
```

-Dave

---

### Post by johnaaronrose on 2007-04-25
Using Feisty (last week's release) on a Dell Inspiron laptop, I previously altered the prepend statement (on the /etc/dhcp3/dhclient.conf file) for the wired ethernet (eth0) connection to show the open OpenDNS IPs (i.e. 208.67.222 & 208.67.220.220) by handy in November 2005 and that worked fine using Swiftfox (I'd previously used the same technique successfully on an older Acer laptop using Edgy with Firefox).

However, as soon as I'd got the wireless connection working, I disabled the wireless connection (using System/Administration/Network and the Connections tab) and I tried to run Swiftfox. I couldn't browse to any web site and so I checked the DNS tab on System/Administration/Network. And there were no entries other than 0.0.0.0. By the way, the router I'm using doesn't have the DNS IPs storable in it. When I put the appropriate entries in and saved, web sites could be browsed. So Feisty appears to clear DNS IPs when there is a wireless connection. Any work around to save me reloading these IPs at every logon?

---

