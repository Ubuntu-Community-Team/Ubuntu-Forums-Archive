---
title: "Create DEB for Python software system-config-vsftpd"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by lkraemer on 2009-11-19
[www.sourceforge.net](www.sourceforge.net) has a Python package for configuring vsftp named
"system-config-vsftpd", but there is no DEB file for Debian (Ubuntu)
available.  

I have downloaded the source, and tried to compile the code, but I can't
get it to function correctly.  The SERVER status is always shown as
STOPPED.  I don't get any errors from the make, or make install, so
I'm at a loss as how to find the problem. 

Can/will one of you fine Python knowledgeable folks please create a 
DEB file for the Debian (Ubuntu) folks so we have an easy way to configure
a vsftp server via the GUI?

Thanks.

lkraemer

---

### Post by ukripper on 2009-11-19
any particular reason why you want to use that package for VSFTP? VSFTP is really easy to setup as it is.

---

### Post by lkraemer on 2009-11-19
Well, it is because I am having trouble setting up vsftp.  I have a
crossover cable connecting two laptops and that works with Filezilla.
But, I have read that the username and password are transfered in plain
text.  Since I am wanting to set the system up, and connect over the
internet. I am trying to make a secure FTP server by using ssh to generate
a certificate.  That means I have to change my configuration file for
vsftp, and after two days of trying I can't get Filezilla to connect.
I booted Fedora 12 , noticed that software package was in the
repositories.  So I was trying to get it fully functional to help with
the configuration.

Do you have, or know of a good tutorial for beginners like me.  I've never
set up, or used a FTP Server, or anything like that in the past.

Any help will be appreciated.

Thanks.

lk

---

### Post by ukripper on 2009-11-20
This one is brilliant tutorial - [http://ubuntuforums.org/showthread.php?t=518293](http://ubuntuforums.org/showthread.php?t=518293)

For ducumentation REDHAT can't be beaten , they provide the best documentation.
[https://www.redhat.com/docs/manuals/enterprise/RHEL-3-Manual/ref-guide/s1-ftp-servers.html](https://www.redhat.com/docs/manuals/enterprise/RHEL-3-Manual/ref-guide/s1-ftp-servers.html)

---

### Post by lkraemer on 2009-11-20
Thanks, ukripper.  I finally got it working last night.  I had cut and
paste the TLS/SSL/FTPS configuration from another conf file I found on the
internet, and there happened to be a typo in that file.  I compared my
conf file to a document I was making for future reference, and stumbled
on the typo.  Boy, that took a while to locate.  I just couldn't figure
out why the server would stop after it was started, only when trying
TLS/SSL/FTPS.

I had not stumbled on the REDHAT Information with all my Google searches.

lk

---

### Post by ukripper on 2009-11-20
> **lkraemer said:**
> Thanks, ukripper.  I finally got it working last night.  I had cut and
paste the TLS/SSL/FTPS configuration from another conf file I found on the
internet, and there happened to be a typo in that file.  I compared my
conf file to a document I was making for future reference, and stumbled
on the typo.  Boy, that took a while to locate.  I just couldn't figure
out why the server would stop after it was started, only when trying
TLS/SSL/FTPS.

I had not stumbled on the REDHAT Information with all my Google searches.

lk

i guess best way to learn is through mistakes! That is how i learn.

Yeh redhat documentation doesn't come in google searches unless specified. Redhat documentation has helped me ever since about 10 years. They are exceptionally good at manuals and troubleshooting guides. Helping me in my RHCE exam preparation too. Even CENTOS wikis are very helpful [http://wiki.centos.org/TipsAndTricks](http://wiki.centos.org/TipsAndTricks).

for ubuntu - [http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic) this is excellent resource.

---

### Post by lkraemer on 2009-11-22
OK, Here is what is needed to correct the install of system-config-vsftpd.

These changes were made to the README file included in the source
to update the actual compile procedure.

!! Before install please edit src/main.py and change line from _LOCAL = True 
to _LOCAL = False. Then execute:

# sudo make clean
# sudo make
# sudo make install

Running
=======
You must be root to run SCV so modify the ICON properties for command: 
gksudo system-config-vsftpd
to actually execute the software.

Removing
=========
# make uninstall

This will make system-config-vsftpd functional in Ubuntu 8.04.3 LTS.

But, the problem is that the messages don't get transfered correctly,
so a few more changes are required to make it possible to start and stop
the server from the server control tab.

Next you will need to install vsftpd-2.2.2 from the tar.gz source since
Ubuntu doesn't have the latest in the repos.

Then change the builddefs.h file to:
```

#undef VSF_BUILD_TCPWRAPPERS
#define VSF_BUILD_PAM
#define VSF_BUILD_SSL

```
for the center three lines of code.

Then just do:
```

make clean
make
make install

```

Now make these changes in /etc/init.d/vsftpd
EXISTING:
```

  stop)
    log_begin_msg "Stopping FTP server: $NAME"
    start-stop-daemon --stop --pidfile /var/run/vsftpd/vsftpd.pid 
--oknodo --exec $DAEMON && log_end_msg 0 || l
og_end_msg 1
    rm -f /var/run/vsftpd/vsftpd.pid
    ;;
  restart)
    $0 stop
    $0 start
    ;;

```
TO:
```

  stop)
    log_begin_msg "Stopping FTP server: $NAME"
    start-stop-daemon --stop --pidfile /var/run/vsftpd/vsftpd.pid 
--oknodo --exec $DAEMON && log_end_msg 0 || l
og_end_msg 1
    rm -f /var/run/vsftpd/vsftpd.pid
    ;;
  status)
    log_begin_msg "Status FTP server" && [ -e /var/run/vsftpd/vsftpd.pid ] && log_end_msg 0 || log_end_msg 1
    exit 0
    ;;
  restart)
    $0 stop
    $0 start
    ;;

```
(Make sure you are in a full open window so the line ending in pid doesn't wrap.)
Now system-config-vsftpd will work properly, just as it does in Fedora 12.
(Note: I did not compile vsftp for TCP Wrappers.)
And the command:
```

vsftpd -v 

```
will display the current Version.

Thanks to my brother for figuring it out.....

UPDATE:
I also had to add:
```

sudo gedit /etc/vsftpd.conf

```
ADDED:
```

require_ssl_reuse=NO

```

lk

---

