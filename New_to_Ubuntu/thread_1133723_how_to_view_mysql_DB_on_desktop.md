---
title: "how to view mysql DB on desktop?"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by kramer65 on 2009-04-23
Hello,

I often have to look into a .sql file on my ubuntu desktop. I don't want to always upload it to my server and looking at it in mousepad is often confusing.

Is there anything like phpmyadmin, but then for on the ubuntu desktop?

---

### Post by MrWES on 2009-04-23
> **kramer65 said:**
> Hello,

I often have to look into a .sql file on my ubuntu desktop. I don't want to always upload it to my server and looking at it in mousepad is often confusing.

Is there anything like phpmyadmin, but then for on the ubuntu desktop?

Doesn't Open Office Base allow connections to a SQL database?

---

### Post by kramer65 on 2009-04-23
But I don't want a connection. I just want to view the sql file instead of uploading it, importing it etc. etc.

I currently have a 500 MB sql file on my desktop and mousepad constantly freezes while viewing it in that.. very anoying. Because of that I wanted to have something [like this]("http://wareseeker.com/Web-Development/mysql-desktop-1.0.zip/389503"), but then for ubuntu..

Anything out there?

---

### Post by scheuri on 2009-04-23
Hi there

```
aptitude search mysql
```

This will show you all packages including mysql in their name. If I am not mistaken there are some admin-tools which you can install and they will run from Gnome/KDE.
Or you install phpmyadmin on the server or locally (however, if you do locally you need to configure the server correctly).

cheers
scheuri

SORRY: didnt see you reply on the reply of MrWES.
Well, there is nothing I know of to open such a file to see what it logically does. However, there are plenty of normal text editors...
Or do I get something wrong?

---

### Post by theDaveTheRave on 2009-04-25
kramer65.

you have a number of options for this.

you could log onto the mysql server from your a terminal

```

~$ mysql -h127.0.0.1 -udavem -p
Enter password:

```

I assume you are using the default port number for mysql (3306) and you will obviously need to change the ip address (here I have used the loopback), and your username (davem is mine, remember no space after the "u").

Then you will want to do a select into outfile, something like this

```

select * from databaseName.tableName
into outfile '/home/myHome/Directory/myDataBase.txt'
fields terminated by ','
lines terminated by '\n';

```

here you will need to change the name of <databaseName.tableName> to the name of your desire database and table.

also the name of where you are going to be writing the output needs to be accessable to the mysql user (so you could use the local mysql directory - assuming you have one, or your local /tmp/ directory).

yous will also need the <FILE> privilege for the user performing this function, on the table that you are selecting into outfile for...

```

GRANT FILE on databaseName.tableName
to 'username'@'%' identified by 'userPassWord'

```

again change username, and userPassWord to the user that will perform this select statement, you want to keep the single quote in the statement.

I have made the assumption you are going to perform this from a <non local host> hence the '%' after username, to signify this privilege can be utilised by the designated user from any logon location.

There is a single proviso in all of this..

I don't know if you require any mysql stuff on your local terminal to log into the remote system? I guess that you do, I've never tried this from a terminal that doesn't have an instalation of mysql though. A quick look at the repos shows that there is the <mysql navigator> and <mysql client> I guess that the client is all you will need for command line access, as it doesn't show there being any depedencies?

Alternatively if your database admin has seen fit to give you a PHP interface, PHP myAdmin or similar, then you may be able to perform this function from there... I don't personally use PhP my admin... I do most stuff from the CLI, as I find it "easier" (you should see the look on my bosses face when I say that :lolflag:).

Well I hope that helps you out

David

Edit 1

The other problem is that you probably won't be able to "view" the whole of a 500mb file in a single attempt - you'll need <lots> of memory. I have a terminal with 2GB and it can't open a plain text file of 500mb in length without a LONG delay in loading it, on the other hand another terminal with 8GB of memory handles the whole thing fine!.

So your options in this instance are..

if you are looking for certain information, grab that as part of your select statement...

```


select * from databaseName.tableName
where databaseName.tableName.columnName = "value"

```

if you then just replace this select statement with that in the select into outfile adding the required <where> clause you will change the number of lines you are collecting....

the other option is to use a <limit> clause

```


select * from databaseName.tableName
limit 0, 100

```

will just spit out the first 100 lines, then just keep going with the outfile thing untill you have files that cover the whole thing...

once you get this to work you can get a script to loop through to the end of the table changing the limit clause with each pass....

```

select count(*) from databaseName.tableName

```

will tell you how many records there are...

David

---

### Post by albinootje on 2009-04-25
> **kramer65 said:**
>  Is there anything like phpmyadmin, but then for on the ubuntu desktop?

There's the package mysql-navigator in the Ubuntu repositories which might be what you want, but you can of course also run phpmyadmin on your desktop (localhost).

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=mysql+navigator](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=mysql+navigator)

---

### Post by theDaveTheRave on 2009-04-27
albinootje is right about the mysql-navigator, it is really rather nice, you can drag field names into it to build queries, it colour codes your queries (so you know if it is wrong!) - but you can get that in gedit also (and I assume most of the other text edditors)

one thing to be aware of with it however, you aren't able to collect any error messages from it, if you are expecting some in a query and you suppress them with an <IGNORE> flag (or whatever it is :rolleyes:) you will only see a few of the errors in the message section of the navigator.

You can however open a <terminal> interface from the <tools - mysql text console> menu, so it offers the best of both worlds, if you are doing some advance query stuff use the navigator to build the query and then copy/paste it into the terminal, after running the query send the command
```
show messages
```

and it will show a table of all the messages that the query threw out... just hope that there aren't too many!


David.

---

