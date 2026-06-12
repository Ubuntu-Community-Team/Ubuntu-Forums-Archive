---
title: "SSH Has Died On ME"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by CameronCalver on 2007-01-13
I am running Edgy on all my 3 computers and until yesterday it was working fine this is how it was set up
Server 192.168.0.2
My comp 192.168.0.5
Family comp 192.168.0.4 
Mums Laptop 192.168.0.3 ( windows so doesn't matter)
 
And i had it so family comp connects to server
my comp connects to family comp and the sever

but now the ssh is not working i click on the Lan-Share and it just comes up as 
```
Opening Lan
``` and it says that for ages and never quits

---

### Post by scrooge_74 on 2007-01-13
reboot the ssh server you are connecting to, check if the server is running ok, any changes on firewalls?did you change any IPs?

---

### Post by CameronCalver on 2007-01-13
Umm yeh i did actually but i  changed the ip's back and it still does not work

---

### Post by CameronCalver on 2007-01-15
Hello i really needed to transfer some files so i went on the server and found that i could connect to the family comp and my comp from the server but not from my computer and the family comp to the server why would i be able to go one way but not the other

---

### Post by scrooge_74 on 2007-01-15
any particular message? Like an invalid ssh key?

try from a terminal

to go into the /home/user.ssh folder  and if there is a ssh key file, edit it and delete its content

maybe that will help, I sometiomes changed ips on y server and then I could not log from other computers, ssh was protecting me from someone spoofing the address and tricking me into login into a false computer somewhere else.

Maybe that is the reason you can't log

---

### Post by CameronCalver on 2007-01-15
It just says Opening Lan and no error message so what command do i do i termnal

---

### Post by scrooge_74 on 2007-01-15
Ok I just reread your posts (now that I am: sobber, rested and starting fresh the week)

open a terminal window and then type ssh user@ip_of_machine and see if you can connect from another PC.

You can also open a terminal in the server and connect using ssh user@localhost

if that is working you may have to remake the Lan shares, because they are probably pointing at the wrong place

---

### Post by CameronCalver on 2007-01-15
Ok when i did ssh server@192.168.0.103 it just hung it didnt do anything just this 
```
cameron@ubuntu:~$ ssh server@192.168.0.103
```
 but if i did it local host on the server it worked fine and also i can connect threw ssh from my comp to family comp it is just the server that is messing up

---

### Post by scrooge_74 on 2007-01-15
Looks like a firewall thing, the server is just dropping the connections silently, the ssh server is working fine. 

 Check your firewall config, my money is on it

---

### Post by CameronCalver on 2007-01-15
Yeh its working now but i dont  understand why it would be affecting it because firestarter wasnt open

---

### Post by scrooge_74 on 2007-01-15
Ok, every linux system uses iptables so it actually has a firewall buid into the kernel.

You can manipulate iptables from the command line, but to tell you the truth I can make heads or tails from that.

What you use is a GUI interface like firestarted to make changes, even when you dont have firestarter working the system has its security in place. not like windows which needs a firewall program to the the job.

We happy few only use Firestarter when we have to make changes and leave our trusty linux system to take care of the rest.

So have fun with your systems and laugh at others attemps to hack in :D

---

