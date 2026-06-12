---
title: "Turn webcam into security monitor"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by nasachusetts on 2011-06-09
So I found an old webcam lying around and thought about using it for a security monitor when I am away from home.  I am currently using Natty and tried installing zoneminder using these instructions:

open a terminal window (Applications > Accessories > Terminal)
sudo apt-get install zoneminder (install the package)
sudo ln -s /etc/zm/apache.conf /etc/apache2/conf.d/zoneminder.conf (add a config to apache)
sudo /etc/init.d/apache2 force-reload (restarts Apache)
service zoneminder start
Open a web browser to [http://localhost/zm/](http://localhost/zm/)

Everything seemed to be going fine up until the service zonemaster start part when I got this message:
Starting ZoneMinder: Can't open log file '/tmp/zmpkg.log': Permission denied at /usr/share/perl5/ZoneMinder/Debug.pm line 279.

Any ideas of what I should do?

---

### Post by whatthefunk on 2011-06-09
> **nasachusetts said:**
> So I found an old webcam lying around and thought about using it for a security monitor when I am away from home.  I am currently using Natty and tried installing zoneminder using these instructions:

open a terminal window (Applications > Accessories > Terminal)
sudo apt-get install zoneminder (install the package)
sudo ln -s /etc/zm/apache.conf /etc/apache2/conf.d/zoneminder.conf (add a config to apache)
sudo /etc/init.d/apache2 force-reload (restarts Apache)
service zoneminder start
Open a web browser to [http://localhost/zm/](http://localhost/zm/)

Everything seemed to be going fine up until the service zonemaster start part when I got this message:
Starting ZoneMinder: Can't open log file '/tmp/zmpkg.log': Permission denied at /usr/share/perl5/ZoneMinder/Debug.pm line 279.

Any ideas of what I should do?

Maybe try
sudo service zoneminder start

---

### Post by hakermania on 2011-06-09
or turn /tmp's permissions to user? I don't know if it's right but i don't think so it will be a problem either. If nothing else work you could try
```
sudo chown -R $USERNAME:$USERNAME /tmp
```

---

### Post by baz.g on 2011-11-16
any solutions to this?

i tried
```

sudo chown -R $USERNAME:$USERNAME /tmp

```

then
```

service zoneminder start

```

and got this:
```


service zoneminder start
Starting ZoneMinder: Can't open log file '/var/log/zm/zmpkg.log': Permission denied at /usr/share/perl5/ZoneMinder/Debug.pm line 279.
Can't connect: Permission denied at /usr/share/perl5/ZoneMinder/Debug.pm line 349
	ZoneMinder::Debug::Fatal('Can\'t connect: Permission denied') called at /usr/bin/zmdc.pl line 168
failure

```

even if i tried:
```


sudo service zoneminder start
Starting ZoneMinder: Can't connect: Permission denied at /usr/share/perl5/ZoneMinder/Debug.pm line 349
	ZoneMinder::Debug::Fatal('Can\'t connect: Permission denied') called at /usr/bin/zmdc.pl line 168
failure

```

---

### Post by wyliecoyoteuk on 2011-11-23
[http://ubuntuforums.org/archive/index.php/t-1535947.html](http://ubuntuforums.org/archive/index.php/t-1535947.html)

---

### Post by trosettie on 2011-11-27
I too got this message. Looks like ZoneMinder is up and running - it just chokes on that part of the start.

---

### Post by seltyk on 2012-04-13
[FONT=monospace]ZoneMinder uses temporary folder /tmp/zm. After a machine reboot the folder is modified and /tmp/zm probably deleted. Make sure that the folder has access for apache user 'www-data'

sudo chown www-data:www-data /tmp[/FONT]/zm

Worked for me.

---

### Post by kojenhome on 2012-09-15
While this may be too late to help nasachusetts, I'd like to offer what I just found.

In place of
service zoneminder start

I used
zmpkg.pl start

Then I opened a web browser to [http://localhost/zm/](http://localhost/zm/). It worked.

zmpkg.pl can be found in /usr/bin.

---

