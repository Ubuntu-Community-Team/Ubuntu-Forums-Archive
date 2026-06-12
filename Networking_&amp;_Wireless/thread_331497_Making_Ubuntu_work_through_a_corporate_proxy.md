---
title: "Making Ubuntu work through a corporate proxy"
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by penguin007 on 2007-01-04
1. The program "apt" is used to update and manage packages on Ubuntu. In
order to get it to talk through a proxy, do the following:

1.1 Edit the apt configuration file: sudo gedit /etc/apt/apt.conf

1.2 and add the following lines to that (might be empty) file:
	
	ACQUIRE {
	http::proxy "http://userid:password@172.16.1.71:8080/"
	}

where 	userid = your user id on the proxy; 
		password = your user password on the proxy; 
		172.16.1.71 = the IP address of the proxy on the LAN; 
		and 8080 = the port that the proxy uses. 
Please note that these would be different for each LAN; get the correct
values from your network administrator.

Save the file and exit.


2. That takes care of the apt program. However, Ubuntu uses the "wget"
program quite often, (e.g. in Automatix), so that also has to be set up.

2.1 Edit the wget config file: sudo gedit /etc/wgetrc
2.2 Find the following section:

	# You can set the default proxies for wget to use for http and
ftp.
	# They will override the value in the environment.
	#http_proxy = http://proxy.yoyodyne.com:18023
	#ftp_proxy = http://proxy.yoyodyne.com:18023
	# If you do not want to use proxy at all, set this to off.
	#use_proxy = on
	
and change to:

	# You can set the default proxies for wget to use for http and
ftp.
	# They will override the value in the environment.
	http_proxy = http://userid:password@172.16.1.71:8080
	ftp_proxy = http://userid:password@172.16.1.71:8080
	# If you do not want to use proxy at all, set this to off.
	use_proxy = on
	
The same rules regarding userid etc. applies as above.

Save the file and exit.


NOTE: if your password changes on the proxy you (obviously) will have to
change the password in these two files. On a Windows LAN, Windows AD
quite often is set up to force the users to change their passwords every
3 months or so; change these files at the same time. Or get your IT people to set up a single proxy userid / password.

---

