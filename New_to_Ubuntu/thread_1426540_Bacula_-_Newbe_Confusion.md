---
title: "Bacula - Newbe Confusion"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by Hawkcode on 2010-03-10
Hi,

I'm very new to Ubantu. We need to set up a server to do central backups of our other servers.

I first looked at BackupPC but gave up as I want a GUI. Then I heard of Bacula, seems just what I need.

So I first downloaded it from Source Forge and coming from the Windows world discovered no Setup like file.

I started looking at the docs and got more confused as I did not want to deal with compiling the app. I then ran across something on a blog somewhere that there are binarys you can install with out havine to build it your self.

Then it dawned on me, check the Package Manager. There is was. So I checked the options I thought I needed, MYSql and applied. It downloaded all and installed.

Then I went to the Menus and can not figure out how to launch it.

Can someone here give me an idea of what to do as I'm totally lost.

I'm a programmer (php and Access - Don't ask) and our network admin among other things. I need to get this up and running.

Thanks in advance!

Richard S Albrecht

---

### Post by MelDJ on 2010-03-10
go to apps-accesories-terminal and enter: 
```
bacula
```

---

### Post by Hawkcode on 2010-03-10
Got command not found...

---

### Post by undecim on 2010-03-10
I have no experience with bacula, but looking at the packages available in aptitude, it looks like you need to install bacula-client on the client machines, and bacula-server on your backup server

---

### Post by Hawkcode on 2010-03-11
Aren't there any Bacula experts out there?

Rich

---

### Post by undecim on 2010-03-11
This might be useful: [https://help.ubuntu.com/community/Bacula](https://help.ubuntu.com/community/Bacula)

---

### Post by Hawkcode on 2010-03-24
Was not able to find the answer there.

Anybody else?

---

### Post by cripperz on 2010-03-28
oh wow, ok, i am in the same situation too. I was looking into some backup system that can act as a backup server receiving all the files / dirs from various client at various remote location. More of like backup over WAN kinda solution.

I have read around and stumbled into Bacula and Amanda. Have yet to come out with a proper configs. I was going through the manuals and stuff still though

=/ Wonder if anyone here have already done it and willing to share how to go about doing it.

---

### Post by cripperz on 2010-03-28
hey Hawkcode,

ok here is what i did. I am running on ubuntu 8.04 LTS. I have installed bacula and webmin together in my system and i am using webmin to configure and administrate my bacula.

Install bacula using apt-get command (in root / sudo su):

#apt-get install bacula-sd-mysql 

this will install bacula files and bacula base on mysql and not sqlite. take note of the bacula mysql user and password as you will need this in your webmin later.

You can install webmin at [www.webmin.com](www.webmin.com) . Just download the deb file and use the command below. Normally it resolve its on dependancy

#cd /tmp
#wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.510_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.510_all.deb)
#dpkg -i webmin_1.510_all.deb
#apt-get install -f

Now go to your webmin panel - [https://localhost:10000](https://localhost:10000)
Enter you server's admin user id and password

Left menu has a "System -> Bacula Backup"
then go to "module config"

change the portion which mention database type. Change it to mysql and enter the mysql password that you have set during your bacula setup.

You should be up and running by now. =P I have still yet to explore the bacula functionalities and so on coz i have not fully implement it yet on at work. Maybe we can further share the progress with each other in the future =)

cheers!

---

### Post by Hawkcode on 2010-03-29
I will try that latter this week. I had found a GUI front end:
[http://www.bacula.org/en/?page=screenshot](http://www.bacula.org/en/?page=screenshot)
and
[http://www.bacula.org/manuals/en/console/console/GUI_Programs.html](http://www.bacula.org/manuals/en/console/console/GUI_Programs.html)


I have installed it already, not doing it with apt-get. You thing I can just jump to that Web Interface or how do I reverse what I did and start all over?

Thanks 

Rich

---

### Post by cripperz on 2010-03-30
hey rich,

i think you can install both side by side. I have yet to look into that bweb as of yet. I have manage to install the linux bacula but i am having problem installing the client on windows 2003 R2 server. The client seems to keep crashing when i use 2.4.2. But it seems find when i use windows client 5.0.1.

The thing is, i have my bacula server setup from ubuntu rep which is a 2.4.2. I have yet to manage get the windows client hooked up to the bacula server. 

Getting frustrated.

---

