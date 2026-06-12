---
title: "How to set permissions for MySQL?"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by ffrr on 2010-06-01
Hi all,

I am migrating a MySQL database system from Windows to Linux and am contending with permission problems which I obviously didn't have on the Windows machine. 

The other day I lost access on the Linux machine and, after scouring the MySQL forum for solutions, I handed over ownership of my data directory and data files to user 'mysql' and group 'mysql'. (chown mysql:mysql .; chown mysql:mysql *). This restored working order.

The incident leaves me confused. My understanding was that if a user runs a program that accesses data, the program has the rights of the user. That doesn't seem to be the case with MySQL. 

In practice, I'd prefer not to open my data to a group like 'mysql' over whose membership I have no control, all the more since I keep my data in my $HOME directory tree and don't consider it appropriate by any standard having to erode its permission discipline by order of applications. So, my question is: How does one structure permissions in a case like this?

Frederic

---

### Post by indytim on 2010-06-01
My recommendation is to not "over engineer" the mysql permissions folders (as in leave it the way it was set up by default).  The important thing to consider is the access provisions for the apps accessing the mysql database ( ie. /var/www).

IndyTim

---

### Post by new_tolinux on 2010-06-01
Since MySQL will be configured to start at boot by default, your home-directory isn't the right place to put mysql-databases.
Therefore the default folder will probably be the best place (there are some exceptions to it, but then you're mainly talking of space issues where you'll _need_ to have the data-folder on a bigger drive/volume).

You should not copy the /mysql/ folder from your Windows data-folder, that's the database MySQL uses to grant different users rights on certain databases and tables. Ubuntu create a user in that database to perform certain jobs (stop/start database etc.). That said, you will have to create the user which your website/program uses by hand.

Every file in the MySQL database-folder and it's subfolders should have owner:group set to mysql:mysql and at least read+write (e.g. chmod 660)
Otherwise it won't run properly.

---

### Post by ffrr on 2010-06-01
Thank you both for your ideas. 

I have no problem with MySQL putting my data wherever it wants to. I put it into my own home, because I am learning my way around a pretty extensive and complex system and so I tend to make things easier to remember. Actually, what I did is putting a link to my data into the required data area, thinking that this was functionally equivalent. And so it seems to be. I suppose I could take the link out and put the data back, but this wouldn't solve the problem of enforcing its confidentiality in any way, as I understand. I suspect, though, that I am missing a point. It seems inconceivable that, membership of group 'mysql' being a prerequisite to using MySQL, all members of that group should have access to each other's data. There has got to be some way to include and, or exclude members and groups. What could it be?

Frederic

---

### Post by new_tolinux on 2010-06-01
A link should work and will probably do no real harm. Although the rights on the files should be set to mysql:mysql, therefore a home-directory is probably not the best place to store them.

You don't need to put anyone in the mysql group to use the mysql server. You only need to create accounts within the MySQL server to grant access. One (easy) way to do that is with phpmyadmin.

For example: my website uses mysql data. I specified a mysql-loginname+password in my PHP-files to connect. My webserver runs as www-data (=default) and does not belong to the linux-group "mysql". Still, because I put my mysql-credentials in that PHP-file, the webserver can access mysql data.

MySQL credentials (usernames/passwords) are not the same as linux-credentials. Setting up a new user in the mysql server will not result in that same user having access to linux. It's only used to perform certain actions with the mysql server (where the rights you granted define what that user can or can't do on that server).

---

### Post by ffrr on 2010-06-01
I will digest your post first thing tomorrow. For now I'm off, with many thanks.

Frederic

---

### Post by ffrr on 2010-06-02
Okay, so the right way to organize permissions is to use MySQL's own system. I suppose the Unix permissions wouldn't quite meet the security requirements of a data base system that interacts with the world at large.

This means then that a user had best use his name to name his data base, not a topical name like 'private', 'business' and the like. Since MySQL puts all data bases into the same directory (../data) and uses data base names to name subdirectories, names could clash if a user picks a name another user has already picked. 

As to setting the permissions, I am not familiar with PHP. But I believe mysql has all that's required for system administration purposes (grant tables). And then there's also mysqladmin.

Thanks for the help!

Frederic

---

### Post by new_tolinux on 2010-06-02
> **ffrr said:**
> Okay, so the right way to organize permissions is to use MySQL's own system. I suppose the Unix permissions wouldn't quite meet the security requirements of a data base system that interacts with the world at large.
MySQL doesn't use any unix/linux permissions. Only the server has to be allowed to access the files needed and run, which is by default all granted to the linux-user+linux-group "mysql". No database user needs direct linux rights, as there's no need to access the server-executables or the files in which the databases are stored.
> **ffrr said:**
>  This means then that a user had best use his name to name his data base, not a topical name like 'private', 'business' and the like. Since MySQL puts all data bases into the same directory (../data) and uses data base names to name subdirectories, names could clash if a user picks a name another user has already picked. 
MySQL won't allow 2 databases having the same name. Probably just because the reason you mentioned. Therefore it should never clash.
<edit>
Although 2 databases can't have the same name, tables can if they're in different databases. For example, if you create a database "mydatabase" and a database "yourdatabase" both databases can have a table called "data". They will not clash either, as both are in different databases and therefore in different subdirectories on the filesystem.
</edit>
> **ffrr said:**
>  As to setting the permissions, I am not familiar with PHP. But I believe mysql has all that's required for system administration purposes (grant tables). And then there's also mysqladmin.
I know about phpmyadmin which is a very nice admin utility to manage MySQL. It's written in PHP-language, so you'll need to set up a basic webserver (Apache2) with PHP5 and phpmyadmin, which can all be found in the repositories.

I don't know for sure if all the requirements for phpmyadmin (like mcrypt) are installed by default (I don't use the phpmyadmin version from the repositories as my "old" version which was used on a Windows webserver before works better for me, so I always install those dependencies manually). No problem there, phpmyadmin will tell you if there's missing anything when you browse to [http://localhost/phpmyadmin](http://localhost/phpmyadmin)
If there's anything missing, just "sudo apt-get install missing_component" and restart the apache server ("sudo /etc/init.d/apache2 restart") and you're fine.

---

### Post by ffrr on 2010-06-03
I put my data back to where they were and set myself up as a new user and created a db with my name. (create user, grant ... and create database--MySQL commands all of them. Everything works fine now. I've never used encryption. Is that for an https web site?

---

### Post by new_tolinux on 2010-06-03
> **ffrr said:**
> I put my data back to where they were and set myself up as a new user and created a db with my name. (create user, grant ... and create database--MySQL commands all of them. Everything works fine now. I've never used encryption. Is that for an https web site?
I don't use https on my testserver, so it can also be for https, but it's at least not only for https.
I don't know exactly what phpmyadmin is using mcrypt for, I only know that phpmyadmin complains if it's not there.

---

### Post by ffrr on 2010-06-04
I see. I don't think I need it, then. I try to keep things as simple as possible. Before I'd add on stuff I would exhaust the primary resources. Anyway, I thank you for your excellent suggestions. 

Frederic

---

