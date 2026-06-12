---
title: "Mysql Help"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by mkaluza on 2010-04-16
I have installed MySQL server 4.0.
When I type SELECT VERSION(); I get the following answer: 4.0.24_Debian-10sarge2-log

I would like to install the last stable version of MySQL server and client.

I'm logged with su.

[SIZE=3]1. I tried to install it using apt-get.[/SIZE]

Command: apt-get install mysql-server mysql-client
Returns:
Reading Package Lists... Error!
E: Dynamic MMap ran out of room
E: Error occured while processing zabbix-server-mysql (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/http.us.debian.org_debian_dists_stable_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

Also, I tried
Command: apt-get update
Returns: 
Sorry for whole list :)
[SIZE=1]Err [http://non-us.debian.org](http://non-us.debian.org) stable/non-US/main Packages
  Could not resolve 'non-us.debian.org'
Err [http://non-us.debian.org](http://non-us.debian.org) stable/non-US/main Release
  Could not resolve 'non-us.debian.org'
Err [http://non-us.debian.org](http://non-us.debian.org) stable/non-US/contrib Packages
  Could not resolve 'non-us.debian.org'
Err [http://non-us.debian.org](http://non-us.debian.org) stable/non-US/contrib Release
  Could not resolve 'non-us.debian.org'
Err [http://non-us.debian.org](http://non-us.debian.org) stable/non-US/non-free Packages
  Could not resolve 'non-us.debian.org'
Err [http://non-us.debian.org](http://non-us.debian.org) stable/non-US/non-free Release
  Could not resolve 'non-us.debian.org'
Err [http://ftp.carnet.hr](http://ftp.carnet.hr) sarge/main Packages
  404 Not Found
Err [http://security.debian.org](http://security.debian.org) sarge/updates/main Packages
  404 Not Found [IP: 195.20.242.89 80]
Ign [http://security.debian.org](http://security.debian.org) sarge/updates/main Release
Err [http://security.debian.org](http://security.debian.org) sarge/updates/contrib Packages
  404 Not Found [IP: 195.20.242.89 80]
Ign [http://security.debian.org](http://security.debian.org) sarge/updates/contrib Release
Err [http://security.debian.org](http://security.debian.org) sarge/updates/non-free Packages
  404 Not Found [IP: 195.20.242.89 80]
Ign [http://security.debian.org](http://security.debian.org) sarge/updates/non-free Release
Hit [http://security.debian.org](http://security.debian.org) stable/updates/main Packages
Hit [http://security.debian.org](http://security.debian.org) stable/updates/main Release
Hit [http://security.debian.org](http://security.debian.org) stable/updates/contrib Packages
Hit [http://security.debian.org](http://security.debian.org) stable/updates/contrib Release
Hit [http://security.debian.org](http://security.debian.org) stable/updates/non-free Packages
Hit [http://security.debian.org](http://security.debian.org) stable/updates/non-free Release
Ign [http://ftp.carnet.hr](http://ftp.carnet.hr) sarge/main Release
Hit [http://http.us.debian.org](http://http.us.debian.org) stable/main Packages
Hit [http://http.us.debian.org](http://http.us.debian.org) stable/main Release
Hit [http://http.us.debian.org](http://http.us.debian.org) stable/contrib Packages
Hit [http://http.us.debian.org](http://http.us.debian.org) stable/contrib Release
Hit [http://http.us.debian.org](http://http.us.debian.org) stable/non-free Packages
Hit [http://http.us.debian.org](http://http.us.debian.org) stable/non-free Release
Err [http://ftp.carnet.hr](http://ftp.carnet.hr) sarge/contrib Packages
  404 Not Found
Ign [http://ftp.carnet.hr](http://ftp.carnet.hr) sarge/contrib Release
Err [http://ftp.carnet.hr](http://ftp.carnet.hr) sarge/non-free Packages
  404 Not Found
Ign [http://ftp.carnet.hr](http://ftp.carnet.hr) sarge/non-free Release
Hit [http://ftp.carnet.hr](http://ftp.carnet.hr) sarge/main Packages
Hit [http://ftp.carnet.hr](http://ftp.carnet.hr) sarge/main Release
Hit [http://ftp.carnet.hr](http://ftp.carnet.hr) sarge/non-free Packages
Hit [http://ftp.carnet.hr](http://ftp.carnet.hr) sarge/non-free Release
Failed to fetch [http://ftp.carnet.hr/debian/dists/sarge/main/binary-i386/Packages.gz](http://ftp.carnet.hr/debian/dists/sarge/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.carnet.hr/debian/dists/sarge/contrib/binary-i386/Packages.gz](http://ftp.carnet.hr/debian/dists/sarge/contrib/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.carnet.hr/debian/dists/sarge/non-free/binary-i386/Packages.gz](http://ftp.carnet.hr/debian/dists/sarge/non-free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.debian.org/dists/sarge/updates/main/binary-i386/Packages.gz](http://security.debian.org/dists/sarge/updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 195.20.242.89 80]
Failed to fetch [http://security.debian.org/dists/sarge/updates/contrib/binary-i386/Packages.gz](http://security.debian.org/dists/sarge/updates/contrib/binary-i386/Packages.gz)  404 Not Found [IP: 195.20.242.89 80]
Failed to fetch [http://security.debian.org/dists/sarge/updates/non-free/binary-i386/Packages.gz](http://security.debian.org/dists/sarge/updates/non-free/binary-i386/Packages.gz)  404 Not Found [IP: 195.20.242.89 80]
Failed to fetch [http://non-us.debian.org/debian-non-US/dists/stable/non-US/main/binary-i386/Packages.gz](http://non-us.debian.org/debian-non-US/dists/stable/non-US/main/binary-i386/Packages.gz)  Could not resolve 'non-us.debian.org'
Failed to fetch [http://non-us.debian.org/debian-non-US/dists/stable/non-US/main/binary-i386/Release](http://non-us.debian.org/debian-non-US/dists/stable/non-US/main/binary-i386/Release)  Could not resolve 'non-us.debian.org'
Failed to fetch [http://non-us.debian.org/debian-non-US/dists/stable/non-US/contrib/binary-i386/Packages.gz](http://non-us.debian.org/debian-non-US/dists/stable/non-US/contrib/binary-i386/Packages.gz)  Could not resolve 'non-us.debian.org'
Failed to fetch [http://non-us.debian.org/debian-non-US/dists/stable/non-US/contrib/binary-i386/Release](http://non-us.debian.org/debian-non-US/dists/stable/non-US/contrib/binary-i386/Release)  Could not resolve 'non-us.debian.org'
Failed to fetch [http://non-us.debian.org/debian-non-US/dists/stable/non-US/non-free/binary-i386/Packages.gz](http://non-us.debian.org/debian-non-US/dists/stable/non-US/non-free/binary-i386/Packages.gz)  Could not resolve 'non-us.debian.org'
Failed to fetch [http://non-us.debian.org/debian-non-US/dists/stable/non-US/non-free/binary-i386/Release](http://non-us.debian.org/debian-non-US/dists/stable/non-US/non-free/binary-i386/Release)  Could not resolve 'non-us.debian.org'
Reading Package Lists... Error!
E: Dynamic MMap ran out of room
E: Error occured while processing zabbix-server-mysql (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/http.us.debian.org_debian_dists_stable_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.[/SIZE]



[SIZE=3]2. I tried with rpm[/SIZE]
Command: rpm -i MySQL-server-5.1.45-1.glibc23.i386.rpm
Returns:
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - No such file or directory (2)
error: cannot open Packages database in /var/lib/rpm


Could anybody help me.
I don't know anything on Linux.
I'm beginner of all beignners.

Thanks.

---

### Post by new_tolinux on 2010-04-16
Errm.... maybe a dumb question......
Is this about Ubuntu or about Debian, since you're using the Debian repositories.

---

### Post by mkaluza on 2010-04-16
I wrote:
Could anybody help me.
I don't know anything on Linux.
I'm beginner of all beignners.

So, if you would like to help, please help.

Thanks

---

### Post by tica vun on 2010-04-16
Hi, here's the official guide for mySQL on ubuntu server.

[https://help.ubuntu.com/9.10/serverguide/C/mysql.html](https://help.ubuntu.com/9.10/serverguide/C/mysql.html)

---

### Post by Drenriza on 2010-04-16
> **tica vun said:**
> Hi, here's the official guide for mySQL on ubuntu server.

[https://help.ubuntu.com/9.10/serverguide/C/mysql.html](https://help.ubuntu.com/9.10/serverguide/C/mysql.html)

That document says less then less about installing & configuring the mysql-server.
i'll write something down for you twomorrow if i get the chance. On installing and configurating the server.

---

### Post by new_tolinux on 2010-04-16
> **new_tolinux said:**
> Errm.... maybe a dumb question......
Is this about Ubuntu or about Debian, since you're using the Debian  repositories.

If it wasn't clear about this, please let me clear this up.
When I said dumb question, I was referring to myself by asking which distribution you use. I was _absolutely not_ referring to you asking how to setup MySQL.

---

