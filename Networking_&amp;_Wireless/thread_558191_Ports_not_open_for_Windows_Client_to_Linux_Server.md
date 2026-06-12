---
title: "Ports not open for Windows Client to Linux Server"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by shoutchens on 2007-09-23
Hi

I have two computers on the home network.  One is Ubuntu 7.04 and the second is a Windows Vista 
system.  I have a Linksys Broadband Router connecting the systems.

On the Ubuntu system, I have configured LAMP, FTPd and Perforce.  From the Windows system, I can 
http and ftp to the Linux box as expected.  However, I am not able to connect to the mySQL or 
Perforce instances on the Linux box.

Perforce (p4) works fine on the Linux box using "localhost:1666" as host and port.  However, trying 
to make the connection to the Perforce instance from the Windows box yields the following message:
[FONT="Courier New"]TCP connect to 192.168.1.105:1666 failed.
connect: 192.168.1.105:1666: WSAECONNREFUSED[/FONT]

From the Linux machine, I use Nmap and receive the info below for localhost.

[FONT="Courier New"]Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-09-23 11:27 PDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1686 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
25/tcp   open  smtp
53/tcp   open  domain
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
631/tcp  open  ipp
953/tcp  open  rndc
1666/tcp open  netview-aix-6
3306/tcp open  mysql
5900/tcp open  vnc[/FONT]

From the Windows machine, using Nmap I get:

[FONT="Courier New"]Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-09-23 09:25 Pacific Daylight Time
Interesting ports on 192.168.1.105:
Not shown: 1690 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
25/tcp   open  smtp
53/tcp   open  domain
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
5900/tcp open  vnc[/FONT]

Can anyone point me in the right direction to set up the configuration of the two machines, so that 
a Windows client will be able to connect to the Perforce Linux instance on port 1666?  I believe it 
may be the same problem and solution for the Windows client connecting to the Linux instance of 
mySQL on port 3306.

Thanks for your help.

Steve

---

### Post by helgman on 2007-09-25
You've got to make sure that the MySQL-server and the Perforce machine are listening on the NIC that you try to connect to.  If I remember correctly the default MySQL-installation in Ubuntu listens only on localhost (security reasons). You also have to make sure that the user account you use have the right to access the server from the network.

The first problem is solved in the MySQL configuration file **/etc/mysql/my.cnf** and the second problem in the MySQL database.

As for Perforce I've never used it but if it's not a localhost problem you might have to figure out how to open the port manually.

Regards,
Helgman

---

### Post by dvystrcil on 2007-09-25
Having the same problem here. 

Any help is appreciated.

---

### Post by helgman on 2007-09-25
> **dvystrcil said:**
> Having the same problem here.

Is the problem MySQL or Perforce or both?

---

### Post by dvystrcil on 2007-09-25
> **helgman said:**
> Is the problem MySQL or Perforce or both?

I'm at work ATM so I won't be able to look at this till tonight. :( 

Whats interesting is that the P4 admin will connect on the local machine (the server) without any issue, and it uses localhost:1666. I would think that if MySQL was causing a problem with communication it would interfere with that as well.

For the curious of heart, I followed these steps for installation.
[http://www.jroller.com/codebits/entry/setting_up_a_ubuntu_perforce](http://www.jroller.com/codebits/entry/setting_up_a_ubuntu_perforce)

I've sent a email to this guy a few days ago, but no response yet.

---

### Post by helgman on 2007-09-25
When connecting to localhost you use a different network interface from when you are trying to connect (the lo interface in Ubuntu with IP-address 127.0.0.1 or something like this). When you communicate over the network you use a different interface (as eth0) with an other IP-address. If the server is set up to so that it only listens on the localhost interface then you can't reach it from the network.

When it comes to MySQL, head over to **/etc/mysql/my.cnf** and edit the line saying:

```
bind-address = 0.0.0.0
```

If you read the comment above it you'll see that MySQL is configured to only listen to localhost per default. You can change it to some other IP-address or * (the * makes it listen on all interfaces). There is security involved in this so think about it before you make the change ... as for other ways to configure the bind-address I'm sure there is documentation out there.

If you still can't connect it might be because the user account doesn't have privileges to access the MySQL server from the network. In the database *mysql* table *user* there is a row named Host. Put the IP-address of the host the user should connect from in there or a % if the user should be able to connect from any computer (again security ...).

Now, for P4 or Perforce I've never used it, never seen it in action, nothing like that. There seems to be a few variables that can be set but I don't have time to go through the [documentation](http://www.perforce.com/perforce/doc.042/manuals/p4guide/index.html), but what is the variable P4PORT set to on the server (if at all)?

Regards,
Helgman

---

### Post by dvystrcil on 2007-09-25
$P4PORT is 1666. One thing I have not tried yet is to change that to something else. I would rather not open any holes with MySQL if I can help it. If P4 isn't going to to work the way I want then I will move to subversion *sigh*.

---

### Post by helgman on 2007-09-25
> **dvystrcil said:**
> $P4PORT is 1666. One thing I have not tried yet is to change that to something else.

The documentation was showing it something like P4PORT = hostname.com:1666 but maybe that is on the clients only. Looking at [this script](http://www.piap.com/faq/p4d.html) (for OSX) you'll see the option **-p [IP-address]**, maybe that could be something. If your server is started with -p 127.0.0.1 then you can't access it from the network (I guess).

But again, I know nothing about P4 and I'm only guessing this to give you avenues to investigate.

Regards,
Helgman

---

### Post by dvystrcil on 2007-09-25
> **helgman said:**
> The documentation was showing it something like P4PORT = hostname.com:1666 but maybe that is on the clients only. Looking at [this script](http://www.piap.com/faq/p4d.html) (for OSX) you'll see the option **-p [IP-address]**, maybe that could be something. If your server is started with -p 127.0.0.1 then you can't access it from the network (I guess).

But again, I know nothing about P4 and I'm only guessing this to give you avenues to investigate.

Regards,
Helgman

No, you are correct about P4PORT being hostname : port. I was mistaken. I'll look into the -p command later tonight. Thanks.

---

### Post by dvystrcil on 2007-09-26
OK, that worked. :)

On to the next problem... I can't get the script that starts and stops p4d to work. It errors out with "command not found"

```

#!/bin/sh -e

export P4JOURNAL=/var/log/perforce/journal
export P4LOG=/var/log/perforce/p4err
export P4ROOT=/usr/share/perforce_depot
export P4PORT=1888

PATH="/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin"

. /lib/lsb/init-functions
p4start="p4d -d -p 192.168.1.100:1888"
p4stop="p4 admin stop"
p4user=perforce

case "$1" in
start)
    log_action_begin_msg "Starting Perforce Server"
    daemon -u $p4user $p4start;
    ;;

stop)
    log_action_begin_msg "Stopping Perforce Server"
    daemon -u $p4user $p4stop;
    ;;

restart)
    stop
    start
    ;;

*)
    echo "Usage: /etc/init.d/perforce (start|stop|restart)
    exit 1
    ;;

esac

exit 0

```

As you can tell I am new to the linux world. Thanks for all your help.

---

### Post by helgman on 2007-09-27
Glad it worked, as for the new problem, I'm no pro but ...

You must "end" the echo line:
```
echo "Usage: /etc/init.d/perforce (start|stop|restart)
```
I think it should be:
```
echo "Usage: /etc/init.d/perforce (start|stop|restart)"
```
You've missed a **"** (quotation mark, is that the English name for it?). I see other "example" start script ([this one](http://affy.blogspot.com/2007_09_01_affy_archive.html)) that don't but if I try the script I get an error saying that's the problem so ...

If it still doesn't work you should make sure that ```
sudo /etc/init.d/perforce
``` give you the output ```
Usage: /etc/init.d/perforce (start|stop|restart)
``` and if it don't then maybe the script is not properly installed. The **Setup Perforce As Bootup Service** section in the link above *should* work, just use your script.

What did you do (how did you start it) when it worked?

What is the output of the above command?

And what is the output of: ```
sudo /etc/init.d/perforce start
```

Also, did you install the script using ```
sudo update-rc.d perforce defaults
``` or something similar?

Regards,
Helgman

---

### Post by dvystrcil on 2007-09-27
Adding the ending quote did not help.

I started p4 using the command line. 

```
sudo p4d -d -p 192.168.1.100:1888
```

Could it be something to do with permission? If I login as root and try '/etc/init.d/perforce' I get: permission denied. This also happens with any other account that I have on the machine. Using sudo throws the 'command not found' error.

---

### Post by helgman on 2007-09-27
Must admit I don't get this. What are the permissions on the file? ```
ls -l /etc/init.d/perforce
```

Also, I'm not really sure about the documentation but have you tried setting P4PORT=192.168.1.100:1888? I've seen some examples where P4PORT=localhost:xxxx so maybe that is an accepted way of setting it?

If the documentation is not against the above setting try changing the line ```
p4start="p4d -d -p 192.168.1.100:1888"
``` to the default ```
p4start="p4d -d"
``` and see if it works, if not change the P4PORT back to 1888 and see if it works (keeping the p4start="p4d -d"). Just to make sure that it's not "-p 192.168..." that is causing these problems.

And, did it work like it should BEFORE you got involved in this tread (apart from the fact that you only could access it from localhost)?

Regards,
Helgman

---

### Post by dvystrcil on 2007-09-27
for permissions I have:
```
-rw-r--r-- 1 root root 669 2007-09-26 22:40 /etc/init.d/perforce
```

originally I had:
```
p4start="p4d -d"
```
just like the web site had it, but since using the -p switch worked from the command line I thought I would give it a try.

---

### Post by helgman on 2007-09-27
I guess root should have the right to execute the file ... all files in my init.d folder has the permissions set to rws-r-xr-x so ```
sudo chmod 755 /etc/init.d/perforce
``` should not be a problem (I guess). That should solve the permission part ...

As for the other suggestions I had, any luck?

Regards,
Helgman

---

### Post by dvystrcil on 2007-09-27
Now we are getting somewhere!

I changed the permissions and I was able to run using the script; however, I now get this message:
```
/etc/init.d/perforce: 36: log_action_begin_msg: not found
```

---

### Post by helgman on 2007-09-27
Alright, a new problem ...

All I can find about it [is this](http://www.nabble.com/-Bug-27475--laptop-mode-tools,-NEW:--etc-init.d-laptop-mode-uses--lib-lsb-init-functions-but-package-does-not-require-lsb-core-t2907945.html) that says something about Debian packages (Ubuntu is based on Debian). (It's not much but it's something.) If I understand that reply (OBS! that post has nothing to do with Perforce) you should have installed Perforce from a Debian package and not source to get it working that way.

I'd try to comment out that line and see if it works. If it does, then you have to find a way to change it so that it works. I'd really like to know how to do it but I'm not sure I'd be able to help you "at a glance" since I really don't know where to start the research. Maybe you could use *logger* but I'm just guessing here, you really should try to start a new thread about that specific problem, maybe in some other part of the forum, to get help from someone who know programing a bit better then I do. Just let me know where ... ;)

Regards,
Helgman

---

### Post by dvystrcil on 2007-09-27
ok I accidentally commented out the 
```
. /lib/lsb/init-functions
```
while I was trying to figure this out.

The script works but now I am getting problems with the daemon app that the web site directed me to use. I will fiddle around with it some more before I come running for help again.

Thanks for you time on this. :)

---

### Post by shoutchens on 2007-09-28
Thanks helgman.  

You were spot on with regard to perforce and mysql configuration settings.  

I edited /etc/mysql/my.cnf and changed bind-address to the local network ip address of the linux box, and that did the trick for the mysql installation.  I can now manage the mysql instance from the Windows machine.

For the Perforce installation, I was changing several parameters at once and don't remember exactly which modifications provided the solution.  But I do remember noticing that I had not set the Domain name under "System >> Administration >> Network - Tab:General".  After setting the host name to an appropriate value, and setting the Domain name to "mshome", then things started to come alive.

Thanks again for the detailed and helpful suggestions.

Steve

---

### Post by helgman on 2007-09-28
Glad I could help!

Helgman

---

