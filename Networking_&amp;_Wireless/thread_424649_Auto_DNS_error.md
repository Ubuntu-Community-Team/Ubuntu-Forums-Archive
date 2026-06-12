---
title: "Auto DNS error"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by laurieaxe on 2007-04-26
My new dapper drake system will not automatically find the correct DNS numbers. I can manually put them in and that works until I restart the machine. This is very annoying when it comes to assertaining DNS from different WIFI servers, when I'm travelling around I've downloade a couple of software packages relating to dhcp identification - but nothing has worked so far.

Yours faithfully 
Laurie

---

### Post by scotthammy on 2007-05-03
Hi there,

Im very new to ubuntu, but Im 99.99% sure i have found the answer to your auto dns..
From a forum message, not my work.

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

