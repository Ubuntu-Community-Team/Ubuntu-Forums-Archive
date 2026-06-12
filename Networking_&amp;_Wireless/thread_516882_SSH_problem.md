---
title: "SSH problem"
date: 2007-08-03
forum: Networking &amp; Wireless
---

### Post by C-{pR0F on 2007-08-03
Hello every body ... i came here after getting sick of searching and searching and asking , and this is the only place that i haven' checked yet , but i hope to find an answer here :
THe Object : I have a normal PC connected to internet via dsl caple , (ubuntu fiesty) but what i want to do is this :
I want to let athoer people to access my pc (i use static ip) , and download files from it 
from google , i found ssh is the best for this , but it drove me mad , and a spent a whole week just trying to get it working and i was getting this
1- netstat -ntap | grep ssh , was return this 
tcp6       0      0 :::22                   :::*                    LISTEN     5087/sshd  
2- when i try to connect to my self using this : ssh user@ubuntu (which is the host name i choosed while installing) it works
but when i try ssh user@myip i get this 
ssh: connect to host XXX.XXX.XXX.XXX port 22: Connection refused


now , I don't care for what is the way to do this , either if it's ssh or something else , but i want a way to let someone else download files from my pc ***_via internet_*** cuz all the articles are about sharin via internal networks

and i'll b very grateful

---

### Post by dougfractal on 2007-08-03
don't use ssh unless you trust the other user.

you could use a web server i.e apache and just put files you what to share there   /var/www/.

with both ssh and http you may need to setup port forwarding on your dsl modem box

"(i use static ip)" your ISP gave you? 

```
ping -c 4 myip
```

---

### Post by kevdog on 2007-08-04
You need to open up a port on your computer to let in access from the outside and also port forward from your router.  To open up port 22 on your computer, either manually modify the IP tables, or install a firewall program such as Guarddog or Firestarter that allows you do to this through a GUI.

---

### Post by C-{pR0F on 2007-08-04
> **dougfractal said:**
> don't use ssh unless you trust the other user.

you could use a web server i.e apache and just put files you what to share there   /var/www/.

with both ssh and http you may need to setup port forwarding on your dsl modem box

"(i use static ip)" your ISP gave you? 

```
ping -c 4 myip
```

yes the ISP gave me ,,, and in addition that i trust them, at the moment I don't care for the security , I am frustrated of it , and i just want to have it working......

now if i install apahce , what will the way b to access my pc , is it IP or what ... and kevdog , the port 22 is opened , that appear from the netstat -ntap | grep ssh

---

### Post by dougfractal on 2007-08-04
*security*  user will see all files that aren't read protected.
launch application as if a user on your computer. i.e. wget -m [www.google.com](www.google.com)   
You will get oWnEd.


*apache*  [http://myisp/](http://myisp/)

I recomend apache2 if you what to share files. If you what to 

I find that I can't contact [http://myisp/](http://myisp/) from within the LAN unless its added to the /etc/hosts
If i what to see it from outside, I must use a "Free Anonymous Proxy Server" such as youhide.com

---

### Post by smileypaul on 2007-08-04
Hey man, 
  SSH is not what you're looking for. If you're just in for sharing files, definately set up an ftp server. easy as beans.

sudo apt-get update

sudo apt-get install proftpd

the configuration file is located in /etc/proftpd/proftpd.conf

all you have to do is make some minor changes to the config .. and add users so they can log in.

best of luck,

Paul

ps: sorry, i never check the forums ..

---

