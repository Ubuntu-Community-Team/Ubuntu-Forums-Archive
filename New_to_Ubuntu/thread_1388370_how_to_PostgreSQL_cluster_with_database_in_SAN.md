---
title: "how to: PostgreSQL cluster with database in SAN"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by jayakrishnanlll on 2010-01-23
Hello,
First of all I am not well versed in UBUNTU. I need to create a Ubuntu cluster with PostgreSQL service running. My database should lie on s SAN. I have already configured iSCSI, mounted a drive to my ubuntu machine, and moved my PostgreSQL database to it. But I dont know how to configure a cluster to host the PostgreSQL databse.

My requirement is like this:
I have 1 iSCSI target which is the database storage. Now When my master node fails, the slave node should take its place and it should the same iSCSI target as database location. That is I have only one database storage. 

I think the master and slave nodes should share ths schemas and all, but I am not clear about it. Please help me out.  

I have my iSCSI target ready and i can change my database to the iSCSI mounted drive (using open-iscsi as initiator). 

Any help is highly appreciated. 

With thanks,
JK.:confused:

---

### Post by yeats on 2010-01-23
You might be asking this in the wrong section of the forums.  "Absolute Beginner" topics don't usually include database clustering.  However, this may be what you need to move forward:

[http://www.slony.info/](http://www.slony.info/)

---

