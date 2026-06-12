---
title: "Command will not work"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by ex-para on 2010-01-05
Following instructions from Calomel.org I am given this command  /usr/local/sbin/thttpd -r -d /var/www/htdocs/  but it does not work. I have tried sudo in front of it but still no good so there must be something wrong with it but what, it has me stuck. Thttpd is a Synaptic package in Ubuntu.

---

### Post by nothingspecial on 2010-01-05
Have you got a /var/www/htdocs/ directory?

```
ls /var/www/ | grep htdocs
```

---

### Post by doas777 on 2010-01-05
is this 'T' supposed to be there? 

"/usr/local/sbin/[SIZE=3]_**t**_[/SIZE]httpd -r -d /var/www/htdocs/ "

I don't have any particular expertise with this process, but that just doesn't look quite right.
hth

---

### Post by nothingspecial on 2010-01-05
And, having quickly installed and removed it, I notice it is located at /usr/sbin/thttpd not /usr/local/sbin/thttpd

so maybe, and bear in mind I have no idea what I`m talking about -
```

sudo mkdir /var/www/htdocs

/usr/sbin/thttpd -r -d /var/www/htdocs/
```

I reiterate, I have no idea what I`m talking about or what this command does, I`m merely trying to fix the syntax for you.

---

### Post by ex-para on 2010-01-05
I think the command is to open thttpd and place it where it should be but when opened it will have /var/www/htdocs/ directory and yes the T is part of it and I will try this  sudo mkdir /var/www/htdocs /usr/sbin/thttpd -r -d /var/www/htdocs/

mkdir: invalid option -- r

Try `mkdir --help' for more information.
 This is the result, I have tried nothingspecial.
There is now a docs folder in WWW with nothing in it should that be all.

---

### Post by bodhi.zazen on 2010-01-05
Those are two separate commands.

```
sudo mkdir /var/www/htdocs
```

then

```
/usr/sbin/thttpd -r -d /var/www/htdocs/
```

You will likely have permissions problems, and I do not know what user thttpd runs as (nobody ? www-data ?).

so you will likely need to use sudo again, sudo chown thttpd-user:thttpd-user /var/www/htdocs

Also, as you are following a how to, it would help others to assist you if you would post a linky, otherwise we have to fire up google and try to find your how-to =)

---

### Post by ex-para on 2010-01-06
Yes I did try the the two commands.
This is what I am following (tHttpd "how to" Tiny Web Server) and there is very little to it.Calomel.org is the website.
Thanks for your trouble.

---

### Post by bodhi.zazen on 2010-01-06
> **ex-para said:**
> Yes I did try the the two commands.
This is what I am following (tHttpd "how to" Tiny Web Server) and there is very little to it.Calomel.org is the website.
Thanks for your trouble.

And, for the lazy, the exact link to your how to you are following is ....

And the error message you are getting is ....

And of course you know thttpd is in the ubuntu repositories so you do nt need to build from source ....

[http://packages.ubuntu.com/karmic/thttpd](http://packages.ubuntu.com/karmic/thttpd)

---

### Post by ex-para on 2010-01-07
And, for the lazy, the exact link to your how to you are following is (tHttpd "how to") just type that into google amd it will be there. ....

And the error message you are getting is, this won't work (/usr/local/sbin/thttpd -r -d /var/www/htdocs/)
....

And of course you know thttpd is in the ubuntu repositories so you do nt need to build from source, yes I found it in packages.

---

### Post by nothingspecial on 2010-01-07
This is not working for a couple of reasons. Let me break the command down for you.

/usr/local/sbin/thttpd is invoking the program using it`s full path, but as I have said, when I installed it, it was in /usr/sbin/ not /usr/local/sbin

As both /usr/local/sbin and /usr/sbin are in your default $PATH then you can invoke it by simply typing thttpd.

-r -d is telling thttpd to chroot to a directory you are about to define ( /var/www/htdocs/). You can chroot to any directory you like. /var/www/bananas or /tmp/icecream for example.

The purpose of the chroot is that no user, as in someone accessing your web server can access any file or directory outside of the one you have chrooted (is that a word?) to.

So make a directory, anywhere, but lets say /var/www/hotdocs

```
sudo mkdir /var/www/hotdocs
```

Then ```
sudo thttpd -r -d /var/www/hotdocs/
```

The reason for the sudo is that only root can chroot however the programs documentation states

> the last thing it does during initialization is to give up root access by becoming another user, so this is safe. 

How true this is I do not know.

---

### Post by ex-para on 2010-01-07
It just will not have it, did it work for you, if so it must be something I am doing wrong.

acme@acme-laptop:~$ sudo mkdir /var/www/hotdocs
[sudo] password for acme: 
acme@acme-laptop:~$ sudo thttpd -r -d /var/www/hotdocs/
sudo: thttpd: command not found
acme@acme-laptop:~$

---

### Post by nothingspecial on 2010-01-07
> **ex-para said:**
> It just will not have it, did it work for you, if so it must be something I am doing wrong.

acme@acme-laptop:~$ sudo mkdir /var/www/hotdocs
[sudo] password for acme: 
acme@acme-laptop:~$ sudo thttpd -r -d /var/www/hotdocs/
sudo: thttpd: command not found
acme@acme-laptop:~$

Are you sure you have thttpd installed?```


sudo apt-get install thttpd
[sudo] password for ns: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
Suggested packages:
  thttpd-util
The following NEW packages will be installed
  thttpd
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 60.8kB of archives.
After this operation, 246kB of additional disk space will be used.
Get: 1 http://gb.archive.ubuntu.com karmic/universe thttpd 2.25b-6 [60.8kB]
Fetched 60.8kB in 2s (26.7kB/s)
Selecting previously deselected package thttpd.
(Reading database ... 163862 files and directories currently installed.)
Unpacking thttpd (from .../thttpd_2.25b-6_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up thttpd (2.25b-6) ...
Starting web server: thttpd.

ns@ns-netbook:~$ sudo mkdir /var/www/hotdocs
ns@ns-netbook:~$ sudo thttpd -r -d /var/www/hotdocs/
ns@ns-netbook:~$ sudo service thttpd stop
Stopping web server: thttpd.
ns@ns-netbook:~$ sudo thttpd -r -d /var/www/hotdocs/
ns@ns-netbook:~$ 
```

No errors there. 

```
sudo apt-get install thttpd
```

Then try again.

---

### Post by ex-para on 2010-01-08
This one did not work in the code you sent me. Will it make any difference?
acme@acme-laptop:~$ sudo service thttpd stop

[sudo] password for acme: 

sudo: service: command not found

acme@acme-laptop:~$ 


but I also have this so maybe it is OK.
thttpd is running
Looks like you got it working. Congrats. 
Here's a link to the thttpd web pages.

---

### Post by nothingspecial on 2010-01-08
No, it doesn`t matter, I was just stopping it to see if I could start it again.

Are you running an earlier version of Ubuntu? thttpd runs in the background on boot. The service command just stops those programs (daemons). In earlier versions of Ubuntu the command was sudo /etc/init.d/thttpd stop. But that doen`t matter. Just for your information.

Glad you got it working.

---

### Post by ex-para on 2010-01-08
I am running 8.04 LTS. Now I just have to find out how to get webpages onto it.

Many thanks for the help you have given me.

---

### Post by nothingspecial on 2010-01-08
Well that`s for someone who knows more about web development/design. I know nothing of that.

Maybe I`ll look into it one day.

---

