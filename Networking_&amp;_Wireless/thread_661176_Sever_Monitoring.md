---
title: "Sever Monitoring"
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by bobthebob1234 on 2008-01-07
Hi, kinda new to this whole ubunutu forum thingy, so bear with me.

I have 3 ubuntu servers all running different services(apache, MySQL, FTP, etc). All of these computers do not have very reliable hardware, so I was wondering if there is any open source software out there that can monitor multiple servers. The output would be prefreably in a webpage, so I could access it from my PDA via the wireless. 

Will I need to hand code it or is there anything out there? I googled it but not much sucess.#-o


Thanks in advance

Bob


](*,)

---

### Post by rickyjones on 2008-01-07
I can recommend Nagios as a monitoring platform. I've used it in the past and it worked great for my use.

-Richard

---

### Post by bobthebob1234 on 2008-01-07
I just looked and it looks ideal. However does it require many lines of configuration in a terminal somewhere? I've just looked at Mon and Monit which both require lots of configuring!

---

### Post by rickyjones on 2008-01-07
It does require installation and configuration.

Installation will require some terminal commands (unless the latest version is in apt), then you can actually use other web interfaces to configure it.

-Richard

---

### Post by bobthebob1234 on 2008-01-08
Thanks, i'll try it

---

### Post by Mithrilhall on 2008-01-08
[http://www.cacti.net/](http://www.cacti.net/) is another option.

---

### Post by bobthebob1234 on 2008-01-11
thanks again everyone. I have now got monit, which on the outside looks complicated, but after you find all the pid files it works a treat!

---

### Post by Railsbuntu on 2008-03-05
Hi which tutorial did you use to setup Monit?

---

### Post by bobthebob1234 on 2008-03-06
[http://www.tildeslash.com/monit/doc/examples.php](http://www.tildeslash.com/monit/doc/examples.php)

you have to edit the pid file locations though. Just do some searching.

(/var/run/ is a good place to  start) 

eg apache's pid is 
/var/run/apache2.pid

Good luck!:guitar:

---

### Post by Railsbuntu on 2008-03-10
Hi,

Monit finally got me pissed off. I am having issues in monitoring mysql, for some reason, it won't create a mysqld.pid, and although is has been started, it won't detect it. And I had my cpu usage go 100% when trying to monitor my citadel mail server.

---

### Post by bobthebob1234 on 2008-03-10
i asume that ur using ubuntu here.

try

```

check process mysql with pidfile /var/run/mysqld/mysqld.pid
   group database
   start program = "/etc/init.d/mysql start"
   stop program = "/etc/init.d/mysql stop"
   if failed host 192.168.1.1 port 3306 protocol mysql then restart
   if 5 restarts within 5 cycles then timeout
   depends on mysql_rc

 check file mysql_rc with path /etc/init.d/mysql
   group database
   if failed checksum then unmonitor
   if failed permission 755 then unmonitor
   if failed uid root then unmonitor
   if failed gid root then unmonitor

```

I was a bit naughty when setting up my monitoring, as i just used
```

check process mysql with pidfile /var/run/mysqld/mysqld.pid

```
That seemed to work and tell me if mysql was running or not, but didn't restart it or anything.

The file you need to edit is /etc/monit/monitrc

Did you use apt-get or did you download it? You can use 
```

sudo apt-get install monit 

```

---

### Post by bobthebob1234 on 2008-03-10
as for citadel i have not used it, but start simple. eg 
```

 check process citadel with pidfile /var/run/citadel/citadel.pid

```
Note that i am just guessing where the pid file is.

If that works, (and doesn't eat up ur CPU!) then try adding other bits

---

### Post by Railsbuntu on 2008-03-10
Crap! I actually had another script run monit in the background which I completely forgot about, when I removed it, everything went back in order.

I just found it by chance by plugging my computer screen on the server and finding out about plenty error message about monit being started although I had uninstalled it.

Anyway thanks for showing me how to "group" in monitrc, I didn't understand how it worked until now.

---

### Post by bobthebob1234 on 2008-03-11
Any time!

Once you get to now it, it is quite easy.

Have you got the web interface running as well?

---

### Post by Railsbuntu on 2008-03-11
Yes it is!

I am just having some troubles with monitoring lighttpd's spawn-fcgi for handling php. For some reason it doesn't detect that it is started. :confused:

---

### Post by bobthebob1234 on 2008-03-12
If you start it manually, it takes some time for monit to detect it. I found this out by stopping apache and waiting about 5 minis for it to detect the change! I don't know how long a 'cycle' is, but you can set it up to check every one or many 'cycle's.

---

### Post by jmunkham on 2008-06-30
I can't get monit to run...

```
root@k1:~# /etc/init.d/monit start
/etc/default/monit: 18: check: not found
```

if I strace it looks for a "check" program...
```
stat64("/sbin/check", 0xffd79360)       = -1 ENOENT (No such file or directory)
stat64("/bin/check", 0xffd79360)        = -1 ENOENT (No such file or directory)
stat64("/usr/sbin/check", 0xffd79360)   = -1 ENOENT (No such file or directory)
stat64("/usr/bin/check", {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
```

Where can I find the check program? Do you guys have it? I have googled a lot but check is a too common word.

cheers, J

---

### Post by bobthebob1234 on 2008-06-30
What is in your config file?

---

