---
title: "Networking tools to show network structure?"
date: 2007-11-25
forum: Networking &amp; Wireless
---

### Post by teryowen on 2007-11-25
I currently have a small home network with 5 computers, i would like to get some programs to show me the structure of the network (im probably using the wrong terminology) But something to show me what computers are connected what IPs are assigned to them, the name of the computer, the MAC address.

If anyone knows some good networking tools that i would find useful let me know. They don't have to have a nice interface heck im fine with it working from terminal.

Thanks in advance

EDIT: im running Ubuntu gusty 7.10

---

### Post by intelligentfool on 2007-11-26
i use NMAP for this type of stuff. its very flexible, usually quick, and does what your looking for. its command line only, but i think if you search around, there might be a gui frontend. 

> sudo apt-get install nmap

---

### Post by teryowen on 2007-11-26
Hey thanks for the reply.

I already have nmap its pertty good for other things but it requires to input a target im looking for something that will scan the network, along the lines of cain (cain &abel for windows)

---

### Post by intelligentfool on 2007-11-27
you can make your target as large as you want with nmap. 

if your on a 192.168.x.x network, just use "nmap -v -sP 192.168.0.0/16". that will scan every device on the entire network. unless your trying to scan stuff on the internet, then good luck, because most routers have ICMP turned off so you'd never get any successful scans anyway, unless you already know the IP's.

edit: ok, nevermind, you dont want a network scanner, you want a password cracker. ala - [http://www.snapfiles.com/get/cainabel.html](http://www.snapfiles.com/get/cainabel.html)

what exactly is it your trying to do?

---

### Post by teryowen on 2007-11-27
No im not scanning the internet lol, just home network.

ill try that next time, Its just nmap seems to take a very long time compared to other apps that ive used in the past, some of which were from back track 2.

---

### Post by derbouka on 2007-11-27
You should look at ZABBIX([http://www.zabbix.com/](http://www.zabbix.com/)). It's a very powerful Network Administration Tool.

---

### Post by teryowen on 2007-11-27
Great ill be looking into it, just wondering it will still work even if i down load the 6.10 version, (i have 7.10 gg running)

---

### Post by derbouka on 2007-11-27
> **teryowen said:**
> Great ill be looking into it, just wondering it will still work even if i down load the 6.10 version, (i have 7.10 gg running)You can install the version from gutsy [universe](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=zabbix&searchon=names&subword=1&version=all&release=all) repositorie or if you like you can install it from the source code. If you want to install it from the source code, you may consider looking at this post [http://ubuntuforums.org/showpost.php?p=2880865&postcount=7](http://ubuntuforums.org/showpost.php?p=2880865&postcount=7)

---

