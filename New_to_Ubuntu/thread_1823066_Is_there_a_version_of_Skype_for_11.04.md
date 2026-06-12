---
title: "Is there a version of Skype for 11.04?"
date: 2011-08-11
forum: New to Ubuntu
---

### Post by L Campbell on 2011-08-11
I have tried 'sudo apt-get install' and I get this:-

Package skype is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source.

I have also downloaded a package from 'Skype' (where it was shown as being for 10.4) and it didn't work for me.

Your help will be appreciated.

---

### Post by haqking on 2011-08-11
> **L Campbell said:**
> I have tried 'sudo apt-get install' and I get this:-

Package skype is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source.

I have also downloaded a package from 'Skype' (where it was shown as being for 10.4) and it didn't work for me.

Your help will be appreciated.

[http://ubuntuguide.net/install-skype-on-ubuntu-11-04-natty-narwhal-3264-bit](http://ubuntuguide.net/install-skype-on-ubuntu-11-04-natty-narwhal-3264-bit)

[http://blog.sudobits.com/2011/04/25/how-to-install-skype-on-ubuntu-11-04/](http://blog.sudobits.com/2011/04/25/how-to-install-skype-on-ubuntu-11-04/)

---

### Post by AgentZ86 on 2011-08-11
I just went to the Skype site and downloaded the linux version of skype for ubuntu 10 and above.

Works perfectly and brings up the ubuntu software center on it's own NO PROBLEM at all.

Happy chatting

---

### Post by cgroza on 2011-08-11
I am using their latest version which is 2.2 BETA and it works with no problems here.
Hopefully they will release another version soon.

---

### Post by L Campbell on 2011-08-14
> **haqking said:**
> [http://ubuntuguide.net/install-skype-on-ubuntu-11-04-natty-narwhal-3264-bit](http://ubuntuguide.net/install-skype-on-ubuntu-11-04-natty-narwhal-3264-bit)

[http://blog.sudobits.com/2011/04/25/how-to-install-skype-on-ubuntu-11-04/](http://blog.sudobits.com/2011/04/25/how-to-install-skype-on-ubuntu-11-04/)

Thanks for the suggestions. I tried this one:-

[http://blog.sudobits.com/2011/04/25/...-ubuntu-11-04/](http://blog.sudobits.com/2011/04/25/...-ubuntu-11-04/) as it seemed to be the most specific but was unable to get it to work.

Here is what I got from Terminal:-

qwer@qwer-P9852A-ABA-753N:~$ sudo apt-get install libqt4-dbus libqt4-network libqt4-xml libasound2 
[sudo] password for qwer: 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
libasound2 is already the newest version. 
libqt4-dbus is already the newest version. 
libqt4-dbus set to manually installed. 
libqt4-network is already the newest version. 
libqt4-network set to manually installed. 
libqt4-xml is already the newest version. 
libqt4-xml set to manually installed. 
The following packages were automatically installed and are no longer required: 
  linux-headers-2.6.38-8 linux-headers-2.6.38-8-generic 
Use 'apt-get autoremove' to remove them. 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
qwer@qwer-P9852A-ABA-753N:~$ wget [http://www.skype.com/go/getskype-linux-beta-ubuntu-32](http://www.skype.com/go/getskype-linux-beta-ubuntu-32) 
--2011-08-12 11:02:08--  [http://www.skype.com/go/getskype-linux-beta-ubuntu-32](http://www.skype.com/go/getskype-linux-beta-ubuntu-32) 
Resolving [www.skype.com](www.skype.com)... 204.9.163.162 
Connecting to [www.skype.com|204.9.163.162|:80](www.skype.com|204.9.163.162|:80)... connected. 
HTTP request sent, awaiting response... 302 Found 
Location: [http://www.skype.com/go/getskype-linux-ubuntu-32](http://www.skype.com/go/getskype-linux-ubuntu-32) [following] 
--2011-08-12 11:02:09--  [http://www.skype.com/go/getskype-linux-ubuntu-32](http://www.skype.com/go/getskype-linux-ubuntu-32) 
Reusing existing connection to [www.skype.com:80](www.skype.com:80). 
HTTP request sent, awaiting response... 302 Found 
Location: [http://download.skype.com/linux/skype-ubuntu_2.2.0.35-1_i386.deb](http://download.skype.com/linux/skype-ubuntu_2.2.0.35-1_i386.deb) [following] 
--2011-08-12 11:02:09--  [http://download.skype.com/linux/skype-ubuntu_2.2.0.35-1_i386.deb](http://download.skype.com/linux/skype-ubuntu_2.2.0.35-1_i386.deb) 
Resolving download.skype.com... 213.146.168.242 
Connecting to download.skype.com|213.146.168.242|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 23595390 (23M) [application/octet-stream] 
Saving to: `getskype-linux-beta-ubuntu-32' 

100%[======================================>] 23,595,390   106K/s   in 2m 46s  

2011-08-12 11:04:56 (138 KB/s) - `getskype-linux-beta-ubuntu-32' saved [23595390/23595390] 

qwer@qwer-P9852A-ABA-753N:~$ sudo dpkg -i skype-*.deb 
dpkg: error processing skype-*.deb (--install): 
 cannot access archive: No such file or directory 
Errors were encountered while processing: 
 skype-*.deb 
qwer@qwer-P9852A-ABA-753N:~$ sudo apt-get -f install 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
The following packages were automatically installed and are no longer required: 
  linux-headers-2.6.38-8 linux-headers-2.6.38-8-generic 
Use 'apt-get autoremove' to remove them. 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
qwer@qwer-P9852A-ABA-753N:~$

---

