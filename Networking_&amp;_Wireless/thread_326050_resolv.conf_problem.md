---
title: "resolv.conf problem"
date: 2006-12-26
forum: Networking &amp; Wireless
---

### Post by Mateo on 2006-12-26
lately when i boot the internet **extremely** (i stress this) slow.  I can fix it by opening up /etc/resolv.conf and commenting out an irrelevant nameserver. But it reappears when I reboot.  Why is this happening and how do I fix it?

---

### Post by dbott67 on 2006-12-26
By default, the dhclient.conf file will overwrite the resolv.conf file each reboot, so you need to edit the dhclient.conf file to include the one you want, and exclude the one you don't:

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
The line above will force the listed name server to be included in the resolv.conf file first.

4. Next, look for the **[COLOR="Red"]domain-name-servers,[/COLOR]** and ***remove*** it (this part is what's causing the irrelevant nameserver from re-appearing each time):

```
**[COLOR="Blue"]prepend domain-name-servers your.preferred.dns.server;[/COLOR]**
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, **[COLOR="Red"]domain-name-servers,[/COLOR]** host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
```

5. Restart your network
```
dbott@edgy:~$ sudo /etc/init.d/networking restart
```

-Dave

---

### Post by 454redhawk on 2006-12-27
> **Mateo said:**
> lately when i boot the internet **extremely** (i stress this) slow.  I can fix it by opening up /etc/resolv.conf and commenting out an irrelevant nameserver. But it reappears when I reboot.  Why is this happening and how do I fix it?


Edit the file and add your DNS values.

Then apply this
```
sudo chattr +i /etc/resolv.conf
```

That will lock down that file and prevent overwriting.

To unlock it, 

```
sudo chattr -i /etc/resolv.conf
```

This has created much disscussion and would appear to be a bug. It seems alot of people are having a similar problem (myself included). The above is a fix that has worked for me and others.
[http://www.ubuntuforums.org/search.php?query=sudo+chattr+%2Bi+%2Fetc%2Fresolv.conf&searchuser=&exactname=1&starteronly=0&forumchoice[]=0&childforums=1&titleonly=0&showposts=0&searchdate=0&beforeafter=after&sortby=lastpost&sortorder=descending&replyless=0&replylimit=0&searchthreadid=0&saveprefs=1&quicksearch=0&searchtype=0&exclude=&nocache=0&ajax=0&imagehash=&imagestamp=&](http://www.ubuntuforums.org/search.php?query=sudo+chattr+%2Bi+%2Fetc%2Fresolv.conf&searchuser=&exactname=1&starteronly=0&forumchoice[]=0&childforums=1&titleonly=0&showposts=0&searchdate=0&beforeafter=after&sortby=lastpost&sortorder=descending&replyless=0&replylimit=0&searchthreadid=0&saveprefs=1&quicksearch=0&searchtype=0&exclude=&nocache=0&ajax=0&imagehash=&imagestamp=&)

---

