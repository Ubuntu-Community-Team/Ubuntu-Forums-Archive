---
title: "About Online Synchronization"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by onlinesynch on 2008-11-01
[Synchronization]("http://www.onlinesynchronization.com/synchronization.html") is a process which update the one object according to requirement by source object. Like syncing  database table from other database table. There are a variety of great tools on the market that will run these comparisons, as well as perform many other functions. You don't need to go out and buy one because SQL Server comes with a tool called XML-RPC that will do this for you.

XML-RPC is a high-performance, multithreaded, multi platform application to automate and schedule Synchronization of Data between two MySQL hosts. XML-RPC allows you to easily compare the data in tables, and it creates scripts for you to synchronize your environments. In addition to being a great tool for synchronizing lookup data between your testing and production environments, XML-RPC is also very useful for synchronizing data between production servers and replication servers to accommodate for when replication problems occur.

XML-RPC does not require any installation at hosts running the MySQL server. You can use any host to run the XML-RPC. For example you can use XML-RPC to keep your production databases ( probably hosted with an ISP ) in complete sync with your test database located in your PC or LAN.

XML-RPC uses an efficient algorithm to generate checksums to find out the changes. Therefore, only those rows that have been inserted, updated or deleted since the last sync are transferred between the hosts.

Additionally, you can configure XML-RPC to detect changes only for specific rows and columns. For example ? you can exclude blob columns or include only those rows that fulfill a WHERE clause. This makes is an ideal tool to sync data even if there is limited bandwidth.

XML-RPC is a command line tool that accepts a Job Definition file encoded in XML as one of the parameters. You can either create the Job Definition file manually or use one of the wizards included with SQLyog. If you use SQLyog to create your job files, you don't need to have any knowledge about XML or the Job Definition schema.

On Windows platforms, SQLyog uses the Task Scheduler services to schedule your jobs. On other platforms you can use the respective OS scheduling services, e.g - on Linux, you can use cron to schedule jobs.

Apart from regular administration tools, SQLyog also contains the following features:
- Migrate File, MS SQL, DB2, etc to MySQL with a powerful wizard based interface!
- Schema Synchronization Tool
- Automatically generate scripts to bring the table structures of two databases in sync.
- Relationship Manager
- Intuitive interface to create and manage relationships.

---

