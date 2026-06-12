---
title: "Hamachi Comunication"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by bearglenn on 2007-06-19
I'm running Ubuntu on both my Work PC and my Home PC.

I have Hamachi installed on both machines.  I have them both logged into the same network. 

From my home PC I can see my Work PC's ip address but no star (indicating it's not online)
From my Work PC I can see my Home PC's ip address with the star(indicating it's online)
the two can not communicate at all.

I followed this guide minus part 1a:
[http://ubuntuforums.org/showthread.php?t=135036](http://ubuntuforums.org/showthread.php?t=135036) 


... A little more about my networks:
at home I have a linksys wireless router with DD-WRT for firmware. I'm not forwarding any ports... really no special configurations at all just boosting my wireless signal.

at work I am behind a sonic firewall that I have no control over.

I think it is worth mentioning that my coworker has hamachi working fine between is work pc (ubuntu) and his home pc (windows xp).

thanks for any help you may have.

---

### Post by handband2 on 2007-06-20
I'm not sure if this will help but I like to install hamachi to the specific user.  This is how I always get it working:

```
$ sudo modprobe tun
```
```
$ sudo gedit /etc/modules
```
add[COLOR="Red"]** tun**[/COLOR].
save and close.
```
$ ls /dev/net/tun
```
You should get "/dev/net/tun"
If you don't then do the following:
```
$ sudo mkdir /dev/net
```
```
$ sudo mknod /dev/net/tun c 10 200
```
Download the newest hamachi version from [http://files.hamachi.cc/linux/](http://files.hamachi.cc/linux/) or
```
$ wget wget http://files.hamachi.cc/linux/hamachi-0.9.9.9-20-lnx.tar.gz
```
Extract hamachi
```
$ tar -zxvf hamachi-0.9.9.9-20-lnx.tar.gz
```
Move into hamachi directory
```
$ cd hamachi-0.9.9.9-20-lnx/
```
Install hamachi
```
$ sudo make install
```
Start tuncfg
```
$ sudo tuncfg
```
Create hamachi group
```
$ sudo groupadd hamachi
```
Add myself to the hamachi group
```
$ sudo gpasswd -a handband2 hamachi
```
Add root to the hamachi group
```
$ sudo gpasswd -a root hamachi
```
Change file permissions for tuncfg.sock
```
$ sudo chmod 760 /var/run/tuncfg.sock
```
Change the group for tuncfg.sock
```
$ sudo chgrp hamachi /var/run/tuncfg.sock 
```
Create RSA keypair
```
$ hamachi-init
```
Start hamachi
```
$ sudo hamachi start
```
Create hamachi account name
```
$ sudo hamachi set-nick handband2
```
Login to hamachi network
```
$ sudo hamachi login
```
Join a network
```
$ sudo hamachi join HANDBAND2
```
or Create a network
```
$ sudo hamachi create HANDBAND2
```

Now I add ghamachi:
Download it from here: [http://www.penguinbyte.com/software/ghamachi/](http://www.penguinbyte.com/software/ghamachi/)
or
```
$ wget -L http://purebasic.myftp.org/?filename=files/3/projects/hamachi/v.0.8.1/gHamachi_0.8.1.tar.gz
```
Rename the downloaded file
```
$ mv index.html\?filename\=files%2F3%2Fprojects%2Fhamachi%2Fv.0.8.1%2FgHamachi_0.8.1.tar.gz gHamachi_0.8.1.tar.gz
```
Extract the files
```
$ tar -zxvf gHamachi_0.8.1.tar.gz
```
Move ghamachi to the /usr/bin/
```
$ sudo mv ghamachi /usr/bin/
```
Make ghamachi executable
```
$ sudo chmod +x /usr/bin/ghamachi
```
Download ghamchi icon
```
$ wget http://wonsheimlan.wo.funpic.de/hamachi.png
```
Move icon to /usr/share/pixmaps/ folder
```
$ sudo mv hamachi.png /usr/share/pixmaps/
```
Add hamachi as an application
```
$ sudo gedit /usr/share/applications/hamachi.desktop
```
Add the following
```
[Desktop Entry]
Encoding=UTF-8
Name=Hamachi
Exec=ghamachi %u
Icon=/usr/share/pixmaps/hamachi.png
Type=Application
Categories=Application;Network;
MimeType=text/rss;text/xml;text/php;application/rss+xml
Comment=Instant VPN software
```
[COLOR="Red"]
After this I restart[/COLOR].  Now when you click on hamachi, ghamachi should ask for password (which I like for security).  Don't forget to right click on your network to :go-online"

A great program to use with hamachi:  [http://gnome-rdp.linuxforge.hu/](http://gnome-rdp.linuxforge.hu/)
```
$ sudo apt-get install gnome-rdp
```

I hope this can help.

---

### Post by T0MA on 2007-06-29
cool, it works, thx!

---

