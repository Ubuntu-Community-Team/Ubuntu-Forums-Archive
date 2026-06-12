---
title: "rsyslog in Ubuntu 9.10"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by huichol on 2010-02-21
I was wondering if you could help me troubleshoot an issue I came across with rsyslog:

I am able to send myself messages to a text file I created in /var/log:

$ sudo touch /var/log/all-logs

After creating the file, I restarted syslog as it was currently running:

$ sudo service rsyslog stop
$ sudo service rsyslog start

I can receive logs, but the latest message caught my attention:

"rsyslogd-2039: Could no open output file '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]"

'/dev/xconsole' is in the following directory; the last few lines are listed below as well:

/etc/rsyslog.d/50-default.conf

# sends logs to all-logs
*.*                                                            /var/log/all-logs

# The named pipe /dev/xconsole is for the `xconsole' utility.  To use it,
# you must invoke `xconsole' with the `-file' option:
# 
#    $ xconsole -file /dev/xconsole [...]
#
# NOTE: adjust the list below, or you'll go crazy if you have a reasonably
#      busy site..
#
daemon.*;mail.*;\
    news.err;\
    *.=debug;*.=info;\
    *.=notice;*.=warn    |/dev/xconsole

---------------------
I did some research and it turns out that it corresponds with:
EACCES -  An attempt was made to access an object in a way forbidden by its object access permissions.

Can you advise how to access an object in a way that it is allowed by its object access permissions?

Can you advise how to open '/dev/xconsole'? What will happen is this file can be opened?

Not sure what other info you would need. Please advise. Thank you.

[B]########
[/B]**UPDATE 4:36pm**

I did a search for '/dev/xconsole' and to my surprise found nothing:

$ ls -ld /dev/ /dev/xconsole

ls: cannot access /dev/xconsole: No such file or directory

##

I wanted to change the permissions on the '/dev/xconsole' with the chmod command:

$ sudo chmod 0777 /dev/xconsole

But, seeing as there is no such file or directory....i'm not sure if i should create one, replace it or use an existing file.

THANKS!

---

### Post by huichol on 2010-02-21
> **huichol said:**
> I was wondering if you could help me troubleshoot an issue I came across with rsyslog:

I am able to send myself messages to a text file I created in /var/log:

$ sudo touch /var/log/all-logs

After creating the file, I restarted syslog as it was currently running:

$ sudo service rsyslog stop
$ sudo service rsyslog start

I can receive logs, but the latest message caught my attention:

"rsyslogd-2039: Could no open output file '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]"

'/dev/xconsole' is in the following directory; the last few lines are listed below as well:

/etc/rsyslog.d/50-default.conf

# sends logs to all-logs
*.*                                                            /var/log/all-logs

# The named pipe /dev/xconsole is for the `xconsole' utility.  To use it,
# you must invoke `xconsole' with the `-file' option:
# 
#    $ xconsole -file /dev/xconsole [...]
#
# NOTE: adjust the list below, or you'll go crazy if you have a reasonably
#      busy site..
#
daemon.*;mail.*;\
    news.err;\
    *.=debug;*.=info;\
    *.=notice;*.=warn    |/dev/xconsole

---------------------
I did some research and it turns out that it corresponds with:
EACCES -  An attempt was made to access an object in a way forbidden by its object access permissions.

Can you advise how to access an object in a way that it is allowed by its object access permissions?

Can you advise how to open '/dev/xconsole'? What will happen is this file can be opened?

Not sure what other info you would need. Please advise. Thank you.

[B]########
[/B]**UPDATE 4:36pm**

I did a search for '/dev/xconsole' and to my surprise found nothing:

$ ls -ld /dev/ /dev/xconsole

ls: cannot access /dev/xconsole: No such file or directory

##

I wanted to change the permissions on the '/dev/xconsole' with the chmod command:

$ sudo chmod 0777 /dev/xconsole

But, seeing as there is no such file or directory....i'm not sure if i should create one, replace it or use an existing file.

THANKS!



ALSO tried to list to find out wich permisions were set to '/dev/xconsole':

$ ls -ld /dev/ /dev/xconsole
ls: cannot access /dev/xconsole: No such file or directory
drwxr-xr-x 15 root root 3820 2010-02-21 16:24 /dev/

---

### Post by huichol on 2010-02-21
> **huichol said:**
> ALSO tried to list to find out wich permisions were set to '/dev/xconsole':

$ ls -ld /dev/ /dev/xconsole
ls: cannot access /dev/xconsole: No such file or directory
drwxr-xr-x 15 root root 3820 2010-02-21 16:24 /dev/

[B]
########
UPDATE 5:17pm[/B]

I ended up changing the named pipe '/dev/xconsole' to /var/log/all-logs to keep everything in one central location.

daemon.*;mail.*;\
     news.err;\
     *.=debug;*.=info;\
     *.=notice;*.=warn    |/var/log/all-logs

---
huichol

---

### Post by masuch on 2012-02-12
I know it is old post , 
but does anybody know solution ?
I have just found xconsole located in /usr/bin/xconsole
but I am not sure if it is the corresponding thing.

---

### Post by overdrank on 2012-02-12
Hi and please start a new thread with your issue. Thread closed.

---

