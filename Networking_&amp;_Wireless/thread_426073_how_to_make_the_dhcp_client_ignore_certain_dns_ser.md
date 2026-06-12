---
title: "how to make the dhcp client ignore certain dns servers?"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by whatever on 2007-04-28
when i use dhcp in my local network, my router's dhcp server submits 3 dns server ips to the client. one of these is the router's own ip (192.168.1.1), the other two are external servers. 
i'd like to force ubuntu (feisty) to ignore the local ip and use the external dns servers instead.
is there a simple and clean way to achieve this? like some config file where i can tell the dhcp client to skip the local ip when writing /etc/resolv.conf?

---

### Post by scotthammy on 2007-05-03
The Case of the Disappearing DNS's
This is the way to prepend the resolv.conf file with your known good ISP's Domain Name Servers (DNS)

Editing the /etc/dhcp3/dhclient.conf

(If you are unfamiliar with using the Terminal have a look down this page for the Text & the Terminal section.)
Enter the following line in the Terminal: 
sudo gedit /etc/dhcp3/dhclient.conf
and just before the request line in your dhclient.conf file that you are looking at in gedit, add the following line, or remove the comment # from the start of the line if it is allready exists):
prepend domain-name-servers 208.67.222.222, 208.67.220.220;

You will probably want to swap your ISP's DNS addresses for the ones in the above example. 

( You may also choose to leave them, as they are the legitimate OpenDNS IP's, & will work IF you edit your router's firmware via your browser & replace your ISP's DNS addresses with the OpenDNS ones. There are very simple & straight forward instructions for this on the OpenDNS website. If you don't know your ISP's DNS addresses, the OpenDNS how-to will show you how to get it from 95% of routers. If you still can't access your router you will have to google for the information.

You can also allways check your ISP's web site or phone them if you don't have access to the addresses in documentation that your ISP supplied. 
I have been using OpenDNS for some time & am very pleased with the faster browsing speed, highly recommended. )
For multiple addresses, separate with a comma and don't forget the semicolon at the end.
This will have the effect of prepending your ISP's nameservers and of having your routers DNS address automaticaly come up at the bottom of the list in resolv.conf. 
Reboot or just bring your interface down and up again by entering the following in the Terminal:
sudo /etc/init.d/networking restart

---

### Post by dbott67 on 2007-05-03
One other thing that you'll need to do is remove the local DNS server (outlined in step #4).  Everything else is just as scotthammy noted, but I'll post the step-by-step instructions for clarity:

1. Backup the file first:
```
sudo cp /etc/dhcp3/dhclient.conf /etc/dhcp3/dhclient.conf.bak
```2. Edit the dhclient.conf file:
```
sudo gedit /etc/dhcp3/dhclient.conf
```3. Look for the following line:
```
#prepend domain-name-servers 127.0.0.1;
```Remove the comment (#) and change it to:
```
prepend domain-name-servers **[COLOR=Red]208.67.222.222, 208.67.220.220[/COLOR]**;
```4. Next, look for the **[COLOR=Red]domain-name-servers,[/COLOR]** and ***remove*** it:

```
**[COLOR=Blue]prepend domain-name-servers 208.67.222.222, 208.67.220.220;[/COLOR]**
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, **[COLOR=Red]domain-name-servers,[/COLOR]** host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
```5. Restart your network
```
dbott@edgy:~$ sudo/etc/init.d/networking restart
```-Dave

---

