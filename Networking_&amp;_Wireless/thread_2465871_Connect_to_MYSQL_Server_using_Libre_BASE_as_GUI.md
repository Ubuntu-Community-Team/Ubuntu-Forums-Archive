---
title: "Connect to MYSQL Server using Libre BASE as GUI"
date: 2021-08-13
forum: Networking &amp; Wireless
---

### Post by bigislanddigger on 2021-08-13
I am using Ubuntu 20.04 and have installed MYSQL server successfully on this computer.  I also installed Libre BASE.   
I want to use SSH to create tunnel for the link between MYSQL server and Libre Base.  
Normally this link is done with ODBC or JDBC (which I have working).   
I am testing connection using localhost.  Later I will move to MYSQL on another computer/host over my network, then over the internet. 
How can I use SSH in this configuration, connecting to MYSQL via localhost, to test the connection?  

I assume I make a SSH connection to localhost first (which is logically possible as the computer is its own 'host' with an IP)
Then when this SSH connection is working, I would next establish the normal JDBC connection to localhost. 

My problem is I'm not aware how I would create the SSH 'tunnel' to begin this process. 

HELP

bigislanddigger

---

