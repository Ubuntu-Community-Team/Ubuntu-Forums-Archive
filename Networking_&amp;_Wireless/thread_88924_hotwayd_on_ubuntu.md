---
title: "hotwayd on ubuntu"
date: 2005-11-11
forum: Networking &amp; Wireless
---

### Post by Adamal on 2005-11-11
Does anyone have any instructions on how to install hotwayd on ubuntu.  I've gone to hotwayd.sourceforge.net but the site has been down for over a week.

---

### Post by Adamal on 2005-11-11
Well I thought I'd try to install hotwayd without any instructions and it worked.  I thought I'd post those instructions here:

Install nessessary packages (you may need more but these where the ones I needed on a server install):
> sudo apt-get install xinetd
sudo apt-get install libxml2


Get the files and create/install the deb package
> wget [http://easynews.dl.sourceforge.net/sourceforge/hotwayd/hotwayd-0.8.4-1.i386-fc2.rpm](http://easynews.dl.sourceforge.net/sourceforge/hotwayd/hotwayd-0.8.4-1.i386-fc2.rpm)
sudo alien -d hotwayd-0.8.4-1.i386-fc2.rpm
sudo dpkg -i hotwayd_0.8.4-2_i386.deb

I had to modify the port from 110 to 555 because 110 was already in use

/etc/xinetd.d/hotwayd
> 
service hotwayd
{
#only_from = 192.168.0.0/24
disable = no
type = unlisted
socket_type = stream
protocol = tcp
wait = no
user = nobody
groups = yes
server = /usr/sbin/hotwayd
#server_args = -p [http://proxy:8080](http://proxy:8080)
port = 555
}

Restart xinetd to update the settings
> sudo /etc/init.d/xinetd restart

Test the configuration
> telnet 127.0.0.1 555
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
+OK POP3 hotwayd v0.8.4 -> The POP3-HTTPMail Gateway. Server on server.fqdn.com active.
quit


---

