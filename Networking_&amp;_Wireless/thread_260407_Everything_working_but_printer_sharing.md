---
title: "Everything working but printer sharing"
date: 2006-09-18
forum: Networking &amp; Wireless
---

### Post by lakelovers on 2006-09-18
Hopefully, somebody can tell me why I can't get my Ubuntu box printer shared by a WinXP laptop.My printer is a Canon i560 running through TurboPrint. No Windows driver. The printer setup in Windows can't find the printer saying that I'm using the wrong printer name. I'm not sure what my printer's ip address is. I've used 127.0.0.1, and I've used 192.168.0.100. I've set the cups.conf to allow 192.0.0.1, and I've set the port to 631. On Cups, the printer name is tpO. I've tried that on the WinXP add printer setup but it doesn't work. I suspect that I don't have the correct IP address or the wrong printer name, or perhaps Windows can't work with TurboPrint. Your help will lower my blood pressure, for sure.

---

### Post by tbonius on 2006-09-18
First off.. I assume you "sharing" it via CUPS?  Well you dont want to "connect" to 127.0.0.1.. thats a localhost loopback address.  

Secondly.. make sure that are allowing hosts on your network to "see" the printer.  192.0.0.0 wont do it if you dont use the right CIDR block.  I assume its a NAT'ed class C so try something like:

Allow From 192.168.0.0/24

Third of all.. if you want to use SMB printing.. you need to setup Samba to use cups.  Share the printer in the smb.conf file and point it to use the cups printing system.

Finally.. if you do not want to use SMB.. you can use IP direct printing and add the printer as something like : 

[http://192.168.0.1:631/printers/PRINTERNAME](http://192.168.0.1:631/printers/PRINTERNAME)

Subustitute the IP for the actual IP address of your Ubuntu server.. and PRINTERNAME for the name of the printer you are "sharing".. assuming you used the CUPS admin to set it up (or some other GNOME-like frontend).

Also.. you have to manually install the correct printer driver in Windows when using a remote printer.  The spooler service is retarded and if the remote print queue isnt Windows (in which the driver is either pushed out.. or the spooler just hands it off to the print server) then the spooler doesnt know what to do with it.

T

---

### Post by lakelovers on 2006-09-18
T. . .
Thanks for the reply. I'm using CUPS, but I can only get the "local printer" to work.  I've tried setting up a network printer (CUPS IPP) without success.

> if you dont use the right CIDR block. I assume its a NAT'ed class C so try something like:

Allow From 192.168.0.0/24

I don't know what CIDR or NAT'ed class C means but I did edit cups.conf to  Allow From 192.168.0.0/24

> you can use IP direct printing and add the printer as something like :

[http://192.168.0.1:631/printers/PRINTERNAME](http://192.168.0.1:631/printers/PRINTERNAME)

I tried this also but used the actual IP address "67.128.176.208" as well as "http://192.168.0.1:631"

I've tried installing the Canon-i560 driver in Windows but have been unsuccessful. I don't have the CD, but I've selected a driver from the Windows list, and it doesn't seem to install.

Bottom line: still can't get printer sharing to work. I'll try, again, to install a Window driver for the printer. I still wonder if TurboPrint is a problem. What do you think?

---

### Post by lakelovers on 2006-09-19
I've made some progress. On the WindowXP laptop, I got to a screen asking for the printer's user name and password. I put in my user name and password for the Ubuntu box. No soap. So I put in the user name and password for the WinXP. Still not accepted. Actually, the WinXP labtop does not have a password. Which box password is being requested? I am certain of the Ubuntu box password/user name because I use it everyday. The laptop is my wife's which I set up and did not enter a password (the wife hates passwords). I also tried a proxy. That didn't work. More high blood pressure. :confused:

---

### Post by tbonius on 2006-09-19
If you dont know what a NAT or a CIDR block is then we are in trouble here.

NAT is Network Adress Translation.  I assume you have an internal LAN that connects through some sort of router to your internet provider.  The internal IP address range is non routable to the extrnal internet.  You mus use a device to route packets out of your network.  This is where the router/firewall comes in.  It also performs a function such as NAT that allows all internal addresses to request services out on the external network.. which in this case is the internet.  When setting up services for use on your internal network.. you need to configure such services to use the internal IP address range (192.168.x.x or 10.0.x.x)

CIDR (cider) blocks are classless internet domain routing decimal blocks that allow you to substitute subnetwork mask ranges with binary digits in order to limit traffic to a scope.  In this case maybe your subnet mask is something like 255.255.255.0, which consists of 4 sets of octets represented by decimal values of each octet.  The binary equivalent of 255 is 11111111.  The Binary equivalent of 0 is 00000000.  The network mask of 255.255.255.0 is shown as 11111111.11111111.11111111.00000000 in binary.  When added together.. they make 24.  The CIDR block for a default class C network mask is /24.. so if you say 192.168.0.0/24.. that means all hosts on a default class C subnet in the network address range of 192.168.0 will be allowed access to a service.

Unless you plan on allowing public access to your print server.. do not specify the 67.128.176.x IP address.. for this is most likely your public IP address assigned by your ISP.  Instead use your private LAN IP address for CUPS.

Once CUPS is listening and allowing connections on the correct IP address.. you should be able to browse to the INTERNAL IP of the CUPS server on port 631 and see the CUPS admin.. assuming that you allowed connections in your cupsd.conf.  Try starting with something simple like:

```
DefaultCharset notused
LogLevel info
Printcap /var/run/cups/printcap
User cupsys
Group lpadmin
RunAsUser Yes
Port 631
Include cupsd-browsing.conf
BrowseAddress @LOCAL
SystemGroup lpadmin

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.0.0/24
</Location>

<Location /jobs>
AuthType Basic
AuthClass User
</Location>

<Location /admin>
AuthType Basic
AuthClass System
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.0.0/24
</Location>
```


This allows printer connection and administration from the address range of 192.168.0.x.  Of course you would substitute the IP address range and CIDR block with whatever your private IP address range is.

T

---

### Post by lakelovers on 2006-09-19
Hi T. . .

You're way over my head, but I got the printer shared with our WinXP. I used this url: http:/192.168.2.102:631/printer/tp0. Then I edited "cups.conf" the same and also "Allow From All," which is probably not advisable but works. Only my wife and I use the computers. I tried with "Deny From All." but that required a user name and password, which I couldn't get working even though I used both our user names and passwords for computer access. The printer must have different user names and passwords assigned but I don't know how to access that or change it. I may have set one months ago when I was trying SAMBA to configure our file and printer sharing. Right now, I'm afraid of changing anything. I forgot to tell you that I'm using a wireless network with a Linksys router and a DSL internet connection.
Jerry

---

### Post by lakelovers on 2006-09-20
> **tbonius said:**
>  substitute the IP address range and CIDR block with whatever your private IP address range is.
T

T, I've re-read your post and I think I have a general grasp of what you say, One thing I don't know is how do I determine/find what my private IP address range is? The question reflects my computerees ignorance.
Jerry

---

### Post by meech on 2006-09-20
At this point, it might be helpful to Google some of your questions.

Meech

---

