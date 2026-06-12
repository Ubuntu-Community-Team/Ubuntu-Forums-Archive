---
title: "No name?"
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by ManyBeers on 2008-09-18
When I enter my routers setup via Firefox and look at the active users
list my computer doesn't show a name. It just says unknown. Im guess I 
didn't name it when I installed Ubuntu 8.04. I don't remember. What if
I wanted it to display a name how would I do that?

ps I connect via ethernet

---

### Post by Iowan on 2008-09-18
If you get your address via DHCP, edit **/etc/dhcp3/dhclient.conf**. Find the line **send host-name "<hostname>";** - change <hostname> to the name of your host.  Save file and restart networking.

But first... you can learn the hostname by typing (in a terminal) **hostname**.

---

### Post by ManyBeers on 2008-09-18
> **Iowan said:**
> If you get your address via DHCP, edit **/etc/dhcp3/dhclient.conf**. Find the line **send host-name "<hostname>";** - change <hostname> to the name of your host.  Save file and restart networking.

But first... you can learn the hostname by typing (in a terminal) **hostname**.
I remember now i left it as Ubuntu. How do I start the edit process. What to I type before /etc... gedit?

---

### Post by Ayuthia on 2008-09-18
> **ManyBeers said:**
> I remember now i left it as Ubuntu. How do I start the edit process. What to I type before /etc... gedit?

You would need to do:
gksu gedit /etc...

Since it is in the /etc directory, it will need admin privileges.

---

### Post by ManyBeers on 2008-09-18
> **Ayuthia said:**
> You would need to do:
gksu gedit /etc...

Since it is in the /etc directory, it will need admin privileges.
Ok I will go take a look and hopefully i won't be afraid to edit it.LOL

---

### Post by ManyBeers on 2008-09-18
> **Ayuthia said:**
> You would need to do:
gksu gedit /etc...

Since it is in the /etc directory, it will need admin privileges.
This doesn't look right does it?[[IMG]http://img295.imageshack.us/img295/5127/screenshot1kl7.th.png[/IMG]]("[URL=http://img295.imageshack.us/my.php?image=screenshot1kl7.png)"][[IMG]http://img295.imageshack.us/img295/5127/screenshot1kl7.th.png[/IMG]](http://img295.imageshack.us/my.php?image=screenshot1kl7.png)[/URL]

---

### Post by ManyBeers on 2008-09-19
> **ManyBeers said:**
> This doesn't look right does it?[[IMG]http://img295.imageshack.us/img295/5127/screenshot1kl7.th.png[/IMG]]("[URL=http://img295.imageshack.us/my.php?image=screenshot1kl7.png)"][[IMG]http://img295.imageshack.us/img295/5127/screenshot1kl7.th.png[/IMG]](http://img295.imageshack.us/my.php?image=screenshot1kl7.png)[/URL]

This doesn't look the right file to edit.

---

### Post by Ayuthia on 2008-09-19
It might be the right file, but it is missing some information.  Here is what mine looks like:
```
# Configuration file for /sbin/dhclient, which is included in Debian's
#   dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#   man page for more information about the syntax of this file
#   and a more comprehensive list of the parameters understood by
#   dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#   not leave anything out (like the domain name, for example), then
#   few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, host-name,
    netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
timeout 30;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

```

---

### Post by ManyBeers on 2008-09-19
> **Ayuthia said:**
> It might be the right file, but it is missing some information.  Here is what mine looks like:
```
# Configuration file for /sbin/dhclient, which is included in Debian's
#   dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#   man page for more information about the syntax of this file
#   and a more comprehensive list of the parameters understood by
#   dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#   not leave anything out (like the domain name, for example), then
#   few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, host-name,
    netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
timeout 30;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

```

What was the exact command you typed in the terminal?

---

### Post by Ayuthia on 2008-09-19
I am one of those geeks that like to use vi/vim in the Terminal so I used:
```
sudo vi /etc/dhcp3/dhclient.conf
```But the following should work for gedit:
```
gksu gedit /etc/dhcp3/dhclient.conf
```

---

### Post by ManyBeers on 2008-09-19
> **Ayuthia said:**
> I am one of those geeks that like to use vi/vim in the Terminal so I used:
```
sudo vi /etc/dhcp3/dhclient.conf
```But the following should work for gedit:
```
gksu gedit /etc/dhcp3/dhclient.conf
```

I tried that second one there. I'll try it again and if I get the same result I will
try that Vi command.

---

### Post by ManyBeers on 2008-09-19
> **ManyBeers said:**
> I tried that second one there. I'll try it again and if I get the same result I will
try that Vi command.
If I use this path dhclient.conf.dpkg-dist  i get that same information as you. Is that  where I 
change the send hostname value. In other words I edit that page. Even though
it says it is a sample page? And if so do I put the name in"<hostname>"or do I remove the quotes and greater than/less than arrows?

---

### Post by ManyBeers on 2008-09-19
It didn't work. Thanks for trying but it seems I just can't get my router to display my computers host-name. It does in WidowsXP though.

---

### Post by Iowan on 2008-09-19
I can never remember the **vi** commands, so I use ```
sudo nano /etc/dhcp3/dhclient.conf
```  Make changes and CTRL-O to save.  As a sample. the line should look like:```
send host-name "myMachine";

```

BTW, the file will need to have this name to be used.

---

### Post by Calabresi on 2008-09-24
Did you remembered to remove the # in line start?

Original:
```
#send host-name "andare.fugue.com";
```

Modified:
```
send host-name "andare.fugue.com";
```

And use:
```
gksu gedit /etc/dhcp3/dhclient.conf
```
to open the file.

Good luck.

---

