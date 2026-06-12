---
title: "DNS changing on every reconnect"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by php_penguin on 2007-05-03
I am using a HP nx6110 (not that this makes any diff surely) and i am connecting to the internet with a wired connection.

To make the internet work i have to change the DNS adress from 10.0.0.38 to 192.168.0.254 every time i connect the cable, and the computer is a laptop so i cant just leave it in.

Is there any way to stop the network manager from resetting the DNS to 10.0.0.38 each time? Has anyone else had this problem?

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
Not to undermine scotthammy's advice (because it is a valid fix), but sometimes it's caused by more than 1 active interface.  Here's a link to the [OpenDNS hack]("http://ubuntuforums.org/showthread.php?p=2416223&highlight=208.67.222.222#post2416223") that scotthammy describes.

Is this a laptop or does the computer have multiple NICs?  If so, try disabling one of the interfaces (if you post the output of **ifconfig -a** we'll be able to confirm).

You'll need to determine which interface is the 'wired' one that you're using to connect to the internet (ie. 192.168.0.xxx).   Let's suppose the wired interface is **eth0** and the other one is **eth1**.  To disable eth1 you would type:
```
sudo ifdown eth1
```Then type:
```
sudo dhclient eth0
``` to renew your IP (and other network settings, such as your DNS server).

-Dave

---

