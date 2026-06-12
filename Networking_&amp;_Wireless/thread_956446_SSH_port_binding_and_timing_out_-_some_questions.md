---
title: "SSH port binding and timing out - some questions"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by eludlow on 2008-10-23
I hope someone can explain to me how this is working, and help with a solution to a question I will ask in a minute!

My company website is hosted on one server (let's call it fileserver) while the mySQL databases that drive the site are on another server (let's say dbserver).

Now as far as I can make out, the only host that is allowed to connect to dbserver is fileserver - when I want to connect to the dbserver to make changes to the database, I run the following SSH command on my PC:

```
ssh -L 3306:dbserver:3306 -N user@fileserver
```

My understanding is that this creates an SSH connection to fileserver, and binds port 3306 of dbserver to 3306 on my local machine.  When I'm connected using this, I just connect to server 127.0.0.1 (ie my machine) and "it is" the dbserver's databases.

Hope you're still with me so far . . . !

First question is why does the above command need to mention both dbserver and fileserver - surely all I'm doing is binding the port from dbserver to mine - why does the connection need to go through fileserver?

Now, I've just set up a new Ubuntu server here, one purpose being to perform a nightly back up of the mySQL database.  As the owners of dbserver won't allow my server to connect directly to theirs, I'm stuck using the above command, which isn't a problem except that it times out after ten minutes or so of inactivity.  The solution I've thought of to this is to send a command every minute (using cron) to the mySQL server running on 127.0.0.1 (which when port bound IS my remote dbserver) just to keep the SSH connection active.

Question is, and I think this is pretty basic, how do I run the above command and then close the terminal session I've opened it in?  I'm running Ubuntu server edition so only access to it is through SSH.

Hope this makes sense?  

Thanks a lot,
Ed Ludlow

PS have tried using SSH keys to connect but apparently the owners of dbserver don't want to allow this.

---

