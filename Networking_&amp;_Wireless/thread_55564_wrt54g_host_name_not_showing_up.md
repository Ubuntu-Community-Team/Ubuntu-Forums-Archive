---
title: "wrt54g host name not showing up"
date: 2005-08-09
forum: Networking &amp; Wireless
---

### Post by makhand on 2005-08-09
I use a linksys wrt54g wireless router and usually have between 2-3 ubuntu machines on my network. However, the host names never show up in the DHCP Clients table. Using the webadmin interface of the router, i get to the table where all the host are listed by going to:
Status>Local Network>DHCP Clients Table

I usually get something like what you see below. 

**Client Host Name --- IP Address --- MAC Address --- Expires**
compaq	  ---         192.168.1.100  --   00:0C:FF:FF:FF:FF	--     1 days, 10:45:40	
jessica	       -----       192.168.1.102 --	00:0F:FF:FF:FF:FF --	1 days, 10:45:40	
**<blank>** -	   192.168.1.104 --     00:90:FF:FF:FF:FF	--    15:56:22
**<blank> **	-   192.168.1.105  --   00:0C:FF:FF:FF:FF	--    13:13:42


This is a problem because if I want to forward certain ports, its always a pain to try to figure out which machine is which. The windows machines are on top, they identify themselves just fine. Has anyone found a way to get around this?

Also, another (probably well-documented) issue is how to deal with wanting to forward ssh (port 22?) to two different computers behind the same router? Useful links or quick explanations are welcome. 

thanks...

---

### Post by eJamesPC on 2005-12-05
Yup, I have the same problem with my LinkSys as well...  
Unfortunatly, I live in a city and don't want to allow unidentified traffic, there for can't get past the router.  I still can't get my wireless to work either.  For a configurable OS this is amazingly unconfigurable.
:( 
Sorry to start flaming, I know that I am not a linux guru, but believe I know what I am doing.  First linux unleashed book was for RH6.  I guess with ubuntu it is a bad idea to rename your PC in your hosts file?  looks like I can't log in as root anymore.  Never did understand why setup only asks for one name, and then sets the sudo password to the user accounts password.  There is a reason that Linux uses 2 passwords...

---

### Post by Joeak on 2005-12-05
Try editing your /etc/dhcp3/dhclient.conf file and unremming/editing the line:

send host-name "yourhostnamehere";

Then do:

sudo /etc/init.d/networking restart
sudo ifup eth0

---

### Post by brallan on 2006-08-01
that woorked great, I've been having network failures very often when booting up dapper boxes, I have had to continuously reset the router, and with the solution above, everything seems to work great. thanks sooooo much.

Is there any reason Dapper can't come with this one line uncommented and correct by default?

---

