---
title: "Access computer from the internet."
date: 2014-04-13
forum: Networking &amp; Wireless
---

### Post by abdulmajid on 2014-04-13
Hi all,

I have a question here. I want to access my computer from the internet. I have a public static IP which is accessible over the iternet. I have that internet cable plugged into my wifi router and I was able to login to my router from the itnernet. However I want to loginto my computer running Xubuntu which is in my home's lan connection with IP 192.168.1.2. My router's static IP starts in 183.83.x.x. What changes/configurations I have to make to be able to login to my computer while the internet cable still plugged into the router, as my other devices needs wifi. 

Thanks in advance.

---

### Post by bashiergui on 2014-04-13
You need to run a service on your computer (like [ssh]("http://help.ubuntu.com/community/SSH")). You reserve the address 192.168.1.2 for you computer on your router. You then configure your router to [forward the port ]("http://ubuntuforums.org/portforward.com/english/routers/port_forwarding/")your computer is listening on (for ssh or whatever you use). Then you can log in to your computer over the internet.

---

### Post by abdulmajid on 2014-04-13
Thanks, I was able to configure it and was successfull in connecting from outside network via SSH. How ever I could not get that done via SFTP although I have vsftpd service running on it.
> abdulmajid@abdulmajid-Ezeebee-MAX4781:~/Desktop$ sudo service vsftpd status
[sudo] password for abdulmajid: 
vsftpd start/running, process 959
abdulmajid@abdulmajid-Ezeebee-MAX4781:~/Desktop$ 


---

### Post by bashiergui on 2014-04-14
What error did you get?

---

### Post by abdulmajid on 2014-04-16
I dont know, it kept trying and nothing happened. Anyway, I was able to login from outside via SSH and I would like to make my computer more secure from hackers. Any tips...?

---

