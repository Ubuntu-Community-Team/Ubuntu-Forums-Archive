---
title: "setup startup scripts in  /etc/rc.local"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by cggerry on 2011-03-18
**setup startup scripts in /etc/rc.local** 
I am very new to Ubuntu Linux. I have installed Ubuntu on a Virtual Machine on my laptop. I am trying to follow this project --
 
[[COLOR=#444444]http://www.geek.com/articles/chips/f...untu-20090116/[/COLOR]]("http://www.geek.com/articles/chips/feature-buiding-a-mini-itx-web-content-filter-with-ubuntu-20090116/")
 
I am stuck on adding the firewall.sh and adding it to the startup scripts in /etc/rc.local. (before Setting Up System Services)
 
I'm afraid i don't even know where to start on this. Do i add the file to rc.local or add what is in firewall.sh into rc.local? Please note, i don't even know what editor to use.
 
I tried "update-rc.d firewall.sh defaults", but i get a file not found error.
 
Any help would be greatly appreciated.
 
Thanks,
Gerry

---

### Post by renjithforever on 2011-03-18
[SIZE=3]hi,
to call a script at startup all u have to do is to add a line to /etc/rc.local

open any editor...go for gedit..

in terminal ....
```
$ sudo gedit /etc/rc.local
```and add the complete path of the script..
eg: /home/YOUR_USERNAME/firewall.sh

pls make sure u have made the script an execuatable..
```
$ sudo chmod u+x /home/USERNAME/firewall.sh
```now that u have made the script executable and added it to rc.local..go ahead an reboot ur system..
```
$ sudo reboot 
```hope that helps :)
[/SIZE]

---

### Post by PunkLV on 2011-03-18
Quick question: does it support raw bash script inside? Or how exactly are the lines inside treated?

---

### Post by renjithforever on 2011-03-18
when u add a script in rc.local make sure the added script has the bash hash bang..
ie the first line of the script should be
```
#!/bin/bash
```else the bash script may not run as expected..because the rc.local itself is run by dash (#!/bin/sh)..which is not bash...so the script within it will also be run by dash...and may run into trouble if there is bash specific stuff in your script.

---

### Post by PunkLV on 2011-03-18
Damn. I new I was doing something wrong. 
Been using /bin/bash in most of scripts, which run totally fine from terminal/console.

Thank you indeed.

---

### Post by profdreamer on 2011-04-06
Thank you! Worked perfectly on my Lucid Lynx box.

---

### Post by kenju4u on 2012-05-31
does rc.local also run if i login to XBMC instead of Ubuntu?

---

### Post by oldos2er on 2012-05-31
Closed. Please start a new thread for your question; this one is over a year old.

---

