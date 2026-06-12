---
title: "How to View The Services Running?"
date: 2011-08-20
forum: New to Ubuntu
---

### Post by NCMS on 2011-08-20
I am running  Ubuntu 10.04.3 LTS,  and I am wondering how can I view/list the services and enable them, for example how to enable the FTP service and how to configure the users list that are allowed and disallowed, etc.

IN RedHat we use  **CHKCONFIG**  

Thanks...

---

### Post by blade4 on 2011-08-20
Hi , I'm assuming you want something similar to services.msc in windows .   You can see the running services/processes list by entering "top" (minus the quotes ) in terminal . To actually enable or disable them , I find it easier to use boot up manager    

sudo apt-get install bum   


It will allow you to see all common services and start/stop them .I don't know if this will list the ftp services as I don't use them, but its the closest thing to services.msc that I know of .

---

### Post by spiky001 on 2011-08-20
How about applications/system/system monitor will this help

Sorry misread your post

---

### Post by spiky001 on 2011-08-20
I found this any good [http://linuxhostingsupport.net/blog/what-is-equivalentalternative-of-chkconfig-in-ubuntu-or-debian](http://linuxhostingsupport.net/blog/what-is-equivalentalternative-of-chkconfig-in-ubuntu-or-debian)

Another might be more what you want [http://slashzeroconf.wordpress.com/2008/02/16/chkconfig-for-ubuntu-sysv-rc-conf/](http://slashzeroconf.wordpress.com/2008/02/16/chkconfig-for-ubuntu-sysv-rc-conf/)

---

### Post by NCMS on 2011-08-20
[SIZE=3][B][SIZE=4]blade4[/SIZE]
[/B] Thanks for the  **boot up manager**  but this does not list all the services, for example I don't see the FTPD or FTP service listed whether it is OFFF or ON ..  
or 
do I have to install it first to see it on the list?  i.e., is the  bootup manager   shows all the installed services?!


-----
**Spiky001**
    Thanks but I am not looking for this


**THANKS,...**
[/SIZE]

---

### Post by spiky001 on 2011-08-20
Did you see this part?

"
If you actually want the chkconfig command in ubuntu, do the following:
$ apt-get install libnewt0.51
$ ln -s /usr/lib/libnewt.so.0.51 /usr/lib/libnewt.so.0.50
$ wget [http://www.tuxx-home.at/projects/chkconfig-for-debian/chkconfig_1.2.24d-1_i386.deb](http://www.tuxx-home.at/projects/chkconfig-for-debian/chkconfig_1.2.24d-1_i386.deb)
$ dpkg –force-all -i chkconfig_1.2.24d-1_i386.deb 
OR, 
1. Download chkconfig-1.2.24h-7.i386.rpm from  [http://rpmfind.net//linux/RPM/PLD/dists/ac/ready/i](http://rpmfind.net//linux/RPM/PLD/dists/ac/ready/i)  386/chkconfig-1.2.24h-7.i386.html
2. Convert rpm to deb with: sudo alien chkconfig-1.2.24h-7.i386.rpm
3. Double-click on the deb file. This will invoke the package installer. 





[http://ubuntu2.cica.es/ubuntu/ubuntu/pool/universe/c/chkconfig/](http://ubuntu2.cica.es/ubuntu/ubuntu/pool/universe/c/chkconfig/)
 download the chkconfig_11.0-79.1-1_all.deb package
It should install the chkconfig when you double click on the downloaded package.

---

### Post by blade4 on 2011-08-20
There is a quicker way ( unless we're talking about a completely different chkconfig ) 

sudo apt-get install chkconfig

( I just found this out now when I entered chkconfig into the terminal and was told I could get it from apt-get  )


As for boot up manager , I think it does show all the services for installed programs but again I can't say for FTP services . All I can say is that the output from bum and chkconfig are the same for my system . 

Hope this solves your problem

---

### Post by spiky001 on 2011-08-20
And Software centre. I found the rest from google

---

### Post by Morbius1 on 2011-08-20
Does chkconfig understand upstart jobs?

I think that's the problem here. Update-rc.d, BUM, and the rest handle the old System-V jobs but they do not see the upstart jobs.

If you run the following command you will get a list of services:
```
sudo service --status-all
```The ones with a "?" next to it are most likely upstart jobs.

To get a list of Upstart jobs run this command:
```
sudo initctl list
```I'm not aware of a GUI for upstart jobs but that does not mean one does not exist.

---

### Post by Frogs Hair on 2011-08-20
I'm  not sure if this would be helpful.[http://www.cyberciti.biz/tips/how-to-controlling-access-to-linux-services.html](http://www.cyberciti.biz/tips/how-to-controlling-access-to-linux-services.html)

---

### Post by Morbius1 on 2011-08-20
> **Frogs Hair said:**
> I'm  not sure if this would be helpful.[http://www.cyberciti.biz/tips/how-to-controlling-access-to-linux-services.html](http://www.cyberciti.biz/tips/how-to-controlling-access-to-linux-services.html)
From that link:
> Traditionally, Debian provided various tools to manage services. There  are various  methods for managing access to system services:
a) [COLOR=Blue]/etc/init.d/service[/COLOR]
b) rcconf
c) update-rc.d etc
Upstart jobs themselves aren't in /etc/init.d/. They are in /etc/init, like smbd for example: /etc/init/smbd.conf

---

### Post by NCMS on 2011-08-22
[SIZE=3][B]spiky001
[/B][/SIZE]Thanks but when I tried the command  **sudo apt-get install libnewt0.51**
I got this error (last line)
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libnewt0.51 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libnewt0.52
[COLOR=Red][B]E: Package libnewt0.51 has no installation candidate
[/B][/COLOR]

And I couldn't download the RPM from the URL you sent because it is unavailable
[U][COLOR=Blue][B][http://rpmfind.net//linux/RPM/PLD/dists/ac/ready/i386/chkconfig-1.2.24h-7.i386.html](http://rpmfind.net//linux/RPM/PLD/dists/ac/ready/i386/chkconfig-1.2.24h-7.i386.html)
[/B][/COLOR][/U]

**THANKS...**

---

### Post by NCMS on 2011-08-22
[SIZE=3]**Blade4**[/SIZE]

You deserve the full marks ;)

[COLOR=DarkRed][B]sudo apt-get install chkconfig
[/B][/COLOR]
worked fine

Thanks...

---

### Post by NCMS on 2011-08-22
[SIZE=2][B][COLOR=Red]Morbius1  [/COLOR]&  [COLOR=Red]Frogs[/COLOR]
[/B][/SIZE]
  THANK YOU guys ..

---

