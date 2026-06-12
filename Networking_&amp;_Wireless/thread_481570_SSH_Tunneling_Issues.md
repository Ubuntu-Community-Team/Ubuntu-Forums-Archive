---
title: "SSH Tunneling Issues"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by s21825 on 2007-06-22
Hi Everyone,

I'm trying to connected to a remote MySQL database over an SSH tunnel. This is what I'm doing:

ssh -L 12345:127.0.0.1:3306 myusername@ipofserver

I get prompted for my password (which I enter) and I connect. Then I open up MySQL Query Browser and connect to localhost port 12345. MySQL Query Browser connects but it connects to my local mysql database server not the remote one. So I tried stopping my local database server and attempted to connect again. This time I got an error:

> Could not connect to host 'localhost'.
MySQL Error Nr. 2002
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

While troubleshooting I tried disconnecting from the remote server all together. Then I tried connecting to my local database server using port 12345 and it connected ... ??? So I tried a bunch of random port numbers and they all connected ... ???

Anyway, I'm not sure what's going on but I'm not able to connect to the remote database using SSH tunneling.

Does anyone have any ideas or suggestions?

---

### Post by steve0921 on 2007-06-22
Your ssh command is definitely right, I just used it to tunnel port 12345 on localhost to port 80 on my webserver (I normally use gSTM for such things).

I guess the problem lies in mysql, with which I am not particularly familiar. When you try to connect to the database, are you certain the query browser recognizes different ports? Have you specified it in the correct manner? Is there maybe a configuration file that tells it what port to use? I assume your local database is not listening on port 12345 and confusing ssh.

As a slightly clunkier alternative, I have often done database management through web applications. Granted, I have used postgres, but mysql must have one too.

Hope this helps.

---

### Post by s21825 on 2007-06-22
Thanks, it does help to have someone verify I'm not doing something dumb with my ssh.

I've done a bit more troubleshooting and I've replicated the issue with a different MySQL client: MySQL Navigator. I have also tried using just the command line client with the same result. 

For some reason my MySQL server is accepting connections on every port I try. I've check my my.cnf file and it clearly specifies the default port of 3306 so I don't know why connections to random ports are being accepted.

I'm stumped ...

---

### Post by s21825 on 2007-06-22
So, after *a lot* of searching I found this bug report:

[http://bugs.mysql.com/bug.php?id=28532](http://bugs.mysql.com/bug.php?id=28532)

Apparently, when connecting if you specify a host as 'localhost' the client always uses a unix socket to connect -- I don't fully understand what that means other than it means the mysql client ignores what ever port you specify. So to get the client to listen to you when you specify a port you have to connect to 127.0.0.1. So that explains why I was able to 'connect using random ports' and why the tunneling was not working.

Apparently this is not a bug but I don't really understand why. So if anyone else is having a similar issue that's how I got things working.

---

### Post by kevdog on 2007-06-22
Can you post the exact commands that you found to work so others can use this as an example

Thanks

---

### Post by s21825 on 2007-06-23
Sure.

Well to set up the ssh port forwarding I did this:

ssh -L 12345:127.0.0.1:3306 my-username@ip-of-remote-server

Which means forward connections made to 127.0.0.1 port 12345 on this machine to 127.0.0.1 port 3306 on the remote machine.

Then, once you are connected to the remote server via ssh, you can use whatever MySQL client you want to but when you specify the host you want the client to connect to, specify 127.0.0.1 instead of localhost. I thought that 127.0.0.1 and localhost were always the exact same ... but in this case there is a difference.

So if you were connecting to the MySQL server using the command line client, you would do this:

mysql -u your-mysql-username -p -h 127.0.0.1 -P 12345

Which means connect as user 'your-mysql-username', prompt for a password before connecting, connect to host 127.0.0.1 using port 12345. The key thing to remember is to specify 127.0.0.1 instead of localhost. If you specify localhost, the client will connect using a unix socket instead of the TCP port that you specified.

That should do it.

---

