---
title: "How To Host a Website with 9.10"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by ModderXstatic on 2010-04-20
Hello Everyone! I have recently dumped Windows are picked up Ubuntu 9.10 Server Edition to host my personal business website. Now, I'm not going to beat around the barn, I am a total NOOB with this OS, and I am not used to typing all the commands, I am very well used to being a "click kitty." Can someone please give me some tips on how to host my website with this platform? Any help at all would be great! I need help with everything, as far as Networking, and setting up the website files on the server, along with aiming the registered domain name to those files. Again, any help would be great! Oh, and one more thing, I need to know how to host more than one site on this server, so if someone could also let me know how to set up those files on the server.
:confused::confused::confused::confused::confused::confused::confused:
 
 
Thanks In Advance!
 
Team_ModderXstatic

---

### Post by sandyd on 2010-04-20
> **ModderXstatic said:**
> Hello Everyone! I have recently dumped Windows are picked up Ubuntu 9.10 Server Edition to host my personal business website. Now, I'm not going to beat around the barn, I am a total NOOB with this OS, and I am not used to typing all the commands, I am very well used to being a "click kitty." Can someone please give me some tips on how to host my website with this platform? Any help at all would be great! I need help with everything, as far as Networking, and setting up the website files on the server, along with aiming the registered domain name to those files. Again, any help would be great! Oh, and one more thing, I need to know how to host more than one site on this server, so if someone could also let me know how to set up those files on the server.
:confused::confused::confused::confused::confused::confused::confused:
 
 
Thanks In Advance!
 
Team_ModderXstatic
login and type this in.
```

sudo apt-get update
sudo apt-get install apache2  bind9
wget -c http://downloads.sourceforge.net/project/webadmin/webmin/1.510/webmin_1.510-2_all.deb?use_mirror=hivelocity
sudo dpkg -i webmin_1.510-2_all.deb
sudo apt-get -f install

```you now have the apache webserver and the BIND dns server installed along with Webmin, which is a server GUI.
If you need php and mysql
```

sudo apt-get install php5 php5-curl mysql-server php5-gd php5-imagick php5-imap php5-mcrypt  php5-mcache php5-mysql php5-sqlite php5-suhosin
```go to another computer and browse to
```

https://[server_ip_address_here]:10000

```ignore the certificate warnings
login.
and theres your pretty interface.
and you might want to install a ftp server as well for getting files onto the server.
or samba or ssh.
ssh (use this to remotely log into the computer)
```

sudo apt-get install openssh-server
```samba (sort of like windows workgroups file sharing)
```

sudo apt-get install samba
```ftp (remotely transfer files onto the server)
```

sudo apt-get install pureftpd
```all of these can be managed by webmin.

if you dont know your server ip address, do
```

ifconfig

```under eth0 (unless you have multiple network connections going to that computer), the ip address is listed right after"inet addr"

---

### Post by sandyd on 2010-04-20
oh, and if you want a GUI, just do
```

sudo apt-get install ubuntu-desktop
```
the server and the desktop version of ubuntu can be installed both at once and coexist peacefully.

p.p.p.s. Rembmer to plug in your ethernet cable before starting the instructions in my first post.

---

### Post by Iowan on 2010-04-20
Though not a How-To, the [Server Guide]("https://help.ubuntu.com/9.10/serverguide/C/index.html") has information on many server facets. 
[Here]("https://help.ubuntu.com/community/ServerGUI") is a link with information about a GUI. **webmin** and **ebox** are a couple more options.

---

### Post by 00ber n00b on 2010-04-20
Carlee, I found an error.  ```
sudo dpkg -i webmin_1.5.10-2_all.deb
``` should be ```
sudo dpkg -i webmin_1.510-2_all.deb
```

There's a decimal after 5 and there shouldn't be.

---

### Post by sandyd on 2010-04-20
> **00ber n00b said:**
> Carlee, I found an error.  ```
sudo dpkg -i webmin_1.5.10-2_all.deb
``` should be ```
sudo dpkg -i webmin_1.510-2_all.deb
```There's a decimal after 5 and there shouldn't be.
oh hai thanks!
normal for me to make typos:oops:

---

