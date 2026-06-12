---
title: "WEBMIN on Ubuntu 10.04"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by Wood Worker on 2010-08-26
All, I wrote a few people and they suggested I write my issue and post a screen shot of my terminal.

Trying to set up a LAMP to run in my office as a test machine (for now). Started with 6.06 to 8.04 to 10.04. Alll seemed to go well.  found Webmin and tried to install.  Failed each time.  I have installed and removed about 8 times.  Here is what I received.  Based on an article on i seen on unixmen, during the install I should have had a larger database file.  50500 if I remember correctly. I have highlighted in green and made the number larger toward the bottom.

Thank you so much for those who can assist.  

michael@ubuntu:~$ wget [http://ftp.debian.org/pool/main/libm/libmd5-perl/libmd5-perl_2.03-1_all.deb](http://ftp.debian.org/pool/main/libm/libmd5-perl/libmd5-perl_2.03-1_all.deb) 
--2010-08-26 07:54:39--  [http://ftp.debian.org/pool/main/libm/libmd5-perl/libmd5-perl_2.03-1_all.deb](http://ftp.debian.org/pool/main/libm/libmd5-perl/libmd5-perl_2.03-1_all.deb)
Resolving ftp.debian.org... 130.89.149.226, 2001:610:1908:a000::149:226
Connecting to ftp.debian.org|130.89.149.226|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5700 (5.6K) [application/x-debian-package]
Saving to: `libmd5-perl_2.03-1_all.deb.2'

100%[======================================>] 5,700       36.7K/s   in 0.2s    

2010-08-26 07:54:40 (36.7 KB/s) - `libmd5-perl_2.03-1_all.deb.2' saved [5700/5700]

michael@ubuntu:~$ sudo dpkg -i libmd5-perl_2.03-1_all.deb
(Reading database ... 137032 files and directories currently installed.)
Preparing to replace libmd5-perl 2.03-1 (using libmd5-perl_2.03-1_all.deb) ...
Unpacking replacement libmd5-perl ...
Setting up libmd5-perl (2.03-1) ...
Processing triggers for man-db ...
michael@ubuntu:~$ wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.510-2_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.510-2_all.deb)
--2010-08-26 07:55:14--  [http://prdownloads.sourceforge.net/webadmin/webmin_1.510-2_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.510-2_all.deb)
Resolving prdownloads.sourceforge.net... 216.34.181.59
Connecting to prdownloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/webadmin/webmin/1.510/webmin_1.510-2_all.deb](http://downloads.sourceforge.net/project/webadmin/webmin/1.510/webmin_1.510-2_all.deb) [following]
--2010-08-26 07:55:14--  [http://downloads.sourceforge.net/project/webadmin/webmin/1.510/webmin_1.510-2_all.deb](http://downloads.sourceforge.net/project/webadmin/webmin/1.510/webmin_1.510-2_all.deb)
Resolving downloads.sourceforge.net... 216.34.181.59
Reusing existing connection to prdownloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://softlayer.dl.sourceforge.net/project/webadmin/webmin/1.510/webmin_1.510-2_all.deb](http://softlayer.dl.sourceforge.net/project/webadmin/webmin/1.510/webmin_1.510-2_all.deb) [following]
--2010-08-26 07:55:14--  [http://softlayer.dl.sourceforge.net/project/webadmin/webmin/1.510/webmin_1.510-2_all.deb](http://softlayer.dl.sourceforge.net/project/webadmin/webmin/1.510/webmin_1.510-2_all.deb)
Resolving softlayer.dl.sourceforge.net... 74.86.229.28
Connecting to softlayer.dl.sourceforge.net|74.86.229.28|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 14504260 (14M) [application/octet-stream]
Saving to: `webmin_1.510-2_all.deb'

100%[======================================>] 14,504,260   636K/s   in 24s     

2010-08-26 07:55:39 (602 KB/s) - `webmin_1.510-2_all.deb.3' saved [14504260/14504260]

michael@ubuntu:~$ sudo dpkg -i webmin_1.510-2_all.deb
Selecting previously deselected package webmin.
(Reading database ... [SIZE=4][COLOR=Lime]137032[/COLOR][/SIZE] files and directories currently installed.)
Unpacking webmin (from webmin_1.510-2_all.deb.3) ...
dpkg: dependency problems prevent configuration of webmin:
 webmin depends on libnet-ssleay-perl; however:
  Package libnet-ssleay-perl is not installed.
 webmin depends on libauthen-pam-perl; however:
  Package libauthen-pam-perl is not installed.
 webmin depends on apt-show-versions; however:
  Package apt-show-versions is not installed.
dpkg: error processing webmin (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead ...
Errors were encountered while processing:
 webmin
michael@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  webmin
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 90.2MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 153129 files and directories currently installed.)
Removing webmin ...
Processing triggers for ureadahead ...

---

### Post by jtarin on 2010-08-26
Well the first thing you will have to do is take care of the dependency problems.....[Try this succesful guide]("http://www.kelvinwong.ca/2010/05/22/installing-webmin-on-ubuntu-server-10-04-lts-lucid/")...it will provide some insight into why you are having difficulties.

---

### Post by Randy Wells on 2010-09-27
I have a Webmin problem so I looked at the guide, which was well presented and understandable.  My problem is that I seem to have Webmin installed properly, but.. I can't get to it with any of my window machines.  The server seems not to allow connection.  I've tried both Firefox and IE.  No luck.

I get:
> This web server is running in SSL mode. Try the URL [https://fileserver.local:10000/](https://fileserver.local:10000/) instead.

That doesn't work either.

Does anyone have any thoughts.  Is it a firewall problem?  How do I tell?

Thanks
Randy

---

### Post by dragos_iliescu_2005 on 2010-09-30
1. Check the firewall settings if port 10000 is open
2. Check if webmin is running

---

### Post by Randy Wells on 2010-10-06
Since I'm a very rusty UNIX guy, how do I check to see if port 10000 is open on the Ubuntu fileserver?  

Thanks
Randy

---

### Post by CharlesA on 2010-10-06
Run this from the server:

```
netstat -ln | grep 10000
```

You will probably have to modify yer firewall as well.

Else you can run nmap against the machine and it'll list open ports.

---

### Post by alexblodøks on 2010-10-22
Hello!
I am all new to linux and have just started up a server, now trying to install webmin i run in to some errors. I checked out jtarin's link, and it solved most except installing the webmin. When i run the [COLOR=green]**sudo dpkg -i webmin_1.510-2_all.deb**[/COLOR] command, i get 
pr@server3212:~$ sudo dpkg -i webmin_1.510-2_all.deb
dpkg: error processing webmin_1.510-2_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 webmin_1.510-2_all.deb

i dont know what i have done wrong, i followed the link exactly as stated. all help appreciated.
Please tell me what information you need.

edit: ive figured out the problem now. Instead of sudo dpkg -i webmin_1.510-2_all.deb
the file was saved as something else, so i wrote sudo dpkg -i webmin_1.510-2_all.deb?use_mirror=cdnetworks-us-1 and it worked fine

---

### Post by lunat1k on 2010-10-27
> **alexblodøks said:**
> Hello!
I am all new to linux and have just started up a server, now trying to install webmin i run in to some errors. I checked out jtarin's link, and it solved most except installing the webmin. When i run the [COLOR=green]**sudo dpkg -i webmin_1.510-2_all.deb**[/COLOR] command, i get 
pr@server3212:~$ sudo dpkg -i webmin_1.510-2_all.deb
dpkg: error processing webmin_1.510-2_all.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
webmin_1.510-2_all.deb
 
i dont know what i have done wrong, i followed the link exactly as stated. all help appreciated.
Please tell me what information you need.
 
edit: ive figured out the problem now. Instead of sudo dpkg -i webmin_1.510-2_all.deb
the file was saved as something else, so i wrote sudo dpkg -i webmin_1.510-2_all.deb?use_mirror=cdnetworks-us-1 and it worked fine
 
Thank this worked perfectly

---

