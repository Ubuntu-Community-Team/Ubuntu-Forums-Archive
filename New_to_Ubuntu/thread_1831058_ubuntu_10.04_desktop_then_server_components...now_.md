---
title: "ubuntu 10.04 desktop then server components...now what?"
date: 2011-08-22
forum: New to Ubuntu
---

### Post by richyrage on 2011-08-22
Hello Ubuntu community forums!!!

I have a few questions at this current situation.

Firstly, I have installed Ubuntu 10.04 LTS desktop i386, and things went well without a hitch.
When restarting I followed these instructions to update and install the server components
for Ubuntu:

~$ sudo apt-get update

~$ sudo apt-get install apache2 mysql-client mysql-server php5 libapache2-mod-php5 php5-mysql phpmyadmin php5-gd

Now my question lies within this realm....

Can I startup/choose to start the system as a server (as currently it boots into the password screen--then the gui desktop version) with command prompt etc.

How can I change/can i change this setting.....or is it better to install the server version of Ubuntu first, then install the gui elements(as I found this way to install in a tutorial somewhere...)

I am kinda stumped, as I would like to start with this project (and have a fully functional 
Ubuntu server that can be used as a local test server, and as well as a secure web server for my websites)

Please let me know of the best path/steps to get to this solution, as addtional links to 
tutorials/information resources would be more than greatly appreciated.

Regards,
RichyRage

---

### Post by dave01945 on 2011-08-22
it usually best to keep server and desktop seperate but if you have installed the server packages they will all run at the same time as the desktop system if it's a dedicated server you want without a gui it's easier to install server version

basically it will run as a server and a desktop with gui at the same time but it will obviously use more system resources  than a dedicated server

---

### Post by alphacrucis2 on 2011-08-22
> **richyrage said:**
> Hello Ubuntu community forums!!!

I have a few questions at this current situation.

Firstly, I have installed Ubuntu 10.04 LTS desktop i386, and things went well without a hitch.
When restarting I followed these instructions to update and install the server components
for Ubuntu:

~$ sudo apt-get update

~$ sudo apt-get install apache2 mysql-client mysql-server php5 libapache2-mod-php5 php5-mysql phpmyadmin php5-gd

Now my question lies within this realm....

Can I startup/choose to start the system as a server (as currently it boots into the password screen--then the gui desktop version) with command prompt etc.

How can I change/can i change this setting.....or is it better to install the server version of Ubuntu first, then install the gui elements(as I found this way to install in a tutorial somewhere...)

I am kinda stumped, as I would like to start with this project (and have a fully functional 
Ubuntu server that can be used as a local test server, and as well as a secure web server for my websites)

Please let me know of the best path/steps to get to this solution, as addtional links to 
tutorials/information resources would be more than greatly appreciated.

Regards,
RichyRage

Apache should start regardless of whether or not you log in to the desktop. So its really up to what you prefer.

---

### Post by richyrage on 2011-08-22
Hello again,
And thanks for the replies dave and alphacrusis.

I guess my question should be, in a real world setting, where I want the server to 
be optimized and use as little resources as possible, would I be better off re-installing again
from the server disk, and later updating with the gui modules so i can choose to start at bootup as server or workstation?

I ask this because I would like to start and begin this server project as I would have it (how it should be configured properly) for realistic usage and with a real-world configuration.

Please advise,
Thanks again,
RichRage

---

