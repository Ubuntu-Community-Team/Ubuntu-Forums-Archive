---
title: "How to connect using this PPoe Dsl program"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by stvdel on 2008-04-25
Hello, my ISP uses a special program that you have to set up
and then once installed it will let you set up your username
and password and connect. I am using Ubuntu 8.04 and I 
downloaded their tar.gz program and unpacked it. This is the
readme.txt that came with it but I am not sure how to follow
this since I can't connect to the internet.

Here is the read me:

1. It is necessary to have root privileges in order to use this client to access the network.Before getting start, confirm the dhcp client module(dhcpcd) have been installed on your Linux OS and the network interface have been set up to "Use dynamic Ip configuration ". The version of c share lib in system is more than 2.3.



2. Install: Extract the installing file to the path(denoted by $dest_path. $dest_path should be used below, and should be changed to actual value when you use it), and then it is ok.



3. Environment setting: environment variable RACERC=$dest_path should be added to root user, and $dest_path should be added to PATH environment variable of root user.



4. Configuration: Edit the file racer.ini to modify the value of Server1 and Server2. Server1 and Server2 mean the ip address of server. Server1 and Server2 should be set to one server ip if there is only one server ip address.



5. User's guide: 
	

Logon: 		$dest_path/racer/ecou.sh start
	
Check status: 	$dest_path/racer/ecou.sh status
	
logoff: 	$dest_path/racer/ecou.sh stop

---

### Post by stvdel on 2008-04-26
bump

---

