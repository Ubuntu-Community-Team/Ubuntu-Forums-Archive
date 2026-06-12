---
title: "MySQL backup wont restore"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by sunrex on 2009-08-29
I have a backup of MyBB 1.2 (MyBB is now 1.4+) and I'm trying to install it on mysql-server 5+.

```
#1064 - You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''mybb_adminlog' ( `uid` int(10) unsigned NOT NULL default '0', `dateline` ' at line 1
```

The first part of the database with the error:

```
CREATE TABLE `mybb_adminlog` (

`uid` int(10) unsigned NOT NULL default '0',

`dateline` bigint(30) NOT NULL default '0',

`scriptname` varchar(50) NOT NULL default '',

`action` varchar(50) NOT NULL default '',

`querystring` varchar(150) NOT NULL default '',

`ipaddress` varchar(50) NOT NULL default '',

KEY `scriptname` (`scriptname`,`action`)

) ENGINE=MyISAM DEFAULT CHARSET=latin1

INSERT INTO mybb_adminlog (uid,dateline,scriptname,action,querystring,ipaddress) VALUES ('1','1163696637','index.php','home',NULL,'72.232.56.122')

INSERT INTO mybb_adminlog (uid,dateline,scriptname,action,querystring,ipaddress) VALUES ('1','1163696641','index.php','vercheck',NULL,'72.232.56.122')
```

Does anyone know how to go about converting this?. I think at the time of backup I was using mysql4 something.

Or does anyone know how to install a older version of the mysql-server?. Everytime I try, I have to use 5.

I would rather convert the backup seeing as how many security holes a older mysql server probably has.

---

### Post by JillSwift on 2009-08-29
It looks like "dateline", "action" and "querrystring" are reserved words in MySQL5.
Also, you may want to consider changing from latin1 to utf8.

Hope this helps :D

---

### Post by Shii on 2009-08-29
> **sunrex said:**
> 
Does anyone know how to go about converting this?. I think at the time of backup I was using mysql4 something.

Or does anyone know how to install a older version of the mysql-server?. Everytime I try, I have to use 5.

I would rather convert the backup seeing as how many security holes a older mysql server probably has.

Besides what Jill pointed out, all MySQL 4 documents will work in 5, so there's no need to look for conversion software.

---

### Post by sunrex on 2009-08-30
> **JillSwift said:**
> It looks like "dateline", "action" and "querrystring" are reserved words in MySQL5.
Also, you may want to consider changing from latin1 to utf8.

Hope this helps :D

So can I still use this in mysql 5 then?.

If not, can you link me to the MySQL 4 database install instructions?. (Im asking for the instructions because I cant find it in apt-get and installing from source is not something i want to do)

This is a pretty big .sql file, and I wont be able to go through it and fix this line to line.

---

### Post by JillSwift on 2009-08-30
Yes, you can still use mysql5 :)

I played about with it for a bit, and found one more keyword, uid.

To use keywords in a query, you have to surround it with `
Also, in MySQL5 each query needs to be terminated with a ;

Here's a quick sed command line to do most of the work for you:

```
sed -e "s/dateline/\`dateline\`/g" -e "s/action/\`action\`/g" -e "s/querystring/\`querystring\`/g" -e "s/uid/\`uid\`/g" -e "s/)$/);/g" -e "s/\`\`/\`/g" mysqlerr.sql > mysqlworks.sql
``` replacing "mysqlerr.sql" for the original backup file, and "mysqlworks.sql" for the converted version.

As usual for my sed work, it mauls the 'create table query' a little bit, leaving a ; at the end of the key descriptor. But, you have to go in and edit it anyway to allow nulls in `querystring`, so what the heck, hmm? :)

The create table query should look like so:
```
CREATE TABLE `mybb_adminlog` (

`uid` int(10) unsigned NOT NULL default '0',

`dateline` bigint(30) NOT NULL default '0',

`scriptname` varchar(50) NOT NULL default '',

`action` varchar(50) NOT NULL default '',

`querystring` varchar(150) default '',

`ipaddress` varchar(50) NOT NULL default '',

KEY `scriptname` (`scriptname`,`action`)

) ENGINE=MyISAM DEFAULT CHARSET=latin1;
```Again, switching to utf8 over latin1 might be a good idea, depending on the application accessing the database.

Hope this helps :D

---

