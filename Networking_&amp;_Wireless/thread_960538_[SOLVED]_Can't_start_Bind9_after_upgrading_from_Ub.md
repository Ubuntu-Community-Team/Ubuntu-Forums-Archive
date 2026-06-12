---
title: "[SOLVED] Can't start Bind9 after upgrading from Ubuntu Server 7.10"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by Yarbo on 2008-10-27
Hi!

Hopefully someone can help me, because I have been googling for an answer to this problem all weekend long!!! As anyone can imagine, i'm getting kind of frustrated.

I installed Ubuntu Server 7.10, and then installed all of my applications.

I upgraded the server by running the following commands:

```

sudo apt-get update
sudo apt-get upgrade

```

I am running Bind9, a LAMP server, and a Samba server, and I administer all of this using Webmin, or the command-line when Webmin can't do what I want.

After I upgraded everything was working fine, except I noticed that my domain's primary name server was offline (I only host the primary, with the secondary being hosted by my registrar.)

I went into Webmin and tried to start Bind, but I got an error saying: 

```
rndc: connect failed: 127.0.0.1#953: connection refused
```I checked to make sure the key in my rndc.conf matches the one in my Bind configuration, and it does. So that doesn't seem to be the problem.

So I did some mucking around, and I changed the first line of /etc/default/bind to:

```
OPTIONS="-u bind -t /var/lib/named"
```This changed the behavior of the problem I am having, when I tried to start bind, It just said "fail" instead of displaying the error above.

So I checked /var/log/syslog and it lists the following:

```

Oct 27 11:30:22 sluggo named[4719]: starting BIND 9.4.1-P1.1 -u bind -t /var/lib/named
Oct 27 11:30:22 sluggo named[4719]: found 1 CPU, using 1 worker thread
Oct 27 11:30:22 sluggo named[4719]: loading configuration from '/etc/bind/named.conf'
Oct 27 11:30:22 sluggo named[4719]: none:0: open: /etc/bind/named.conf: permission denied
Oct 27 11:30:22 sluggo named[4719]: loading configuration: permission denied
Oct 27 11:30:22 sluggo named[4719]: exiting (due to fatal error)

```I am unable to figure out why bind is unable to access /etc/bind/named.conf, if anyone has any insight, or perhaps a possible solution, then PLEASE tell me where to find it.

Also, if there is a way to roll-back the upgrade I did, and go back to the way things were before I would do that as well.  I am starting to wonder if upgrading was such a good idea.

I'd rip the hair right out of my head in frustration, but I am bald and lack this source of relief :(.

Thanks in advance!

---

### Post by Yarbo on 2008-10-28
Please, I am desperate at this point. I am going to have to reformat and re-install the OS if I can't fix this soon.  Thanks again.

---

### Post by Yarbo on 2008-10-28
I hate to bump this again, I know some people tend to frown upon that.  I read the rules, and didn't find anything dis-allowing the practice.

If I am wrong, please accept my apologies.

If someone who has seen this before can point me in the right direction I would be very appreciative.  Unfortunately all of my emails are down until I can get my bind server back online, so its a bit of a urgent issue.

I think I may need to resort to re-installing the OS from scratch, but I would like to avoid that if I can.

Thanks again.

---

### Post by Yarbo on 2008-10-28
.

Duplicate post, sorry.

---

### Post by puppywhacker on 2008-10-28
hi,

In the options you put "-u bind" ... which means the system user "bind" is used to start the named service. This also means the config file should be readable by that user.

I compared my syslog, basically yours goes wrong at the line:

```
none:0: open: /etc/bind/named.conf: permission denied
```

I guess "none:0" is the owner:group of the config file. I think the file is not readable, so I guess you can check and fix it with the following commands

ls -la /etc/bind/named.conf

chmod +r /etc/bind/named.conf
chown bind:bind /etc/bind/named.conf


goodluck

---

### Post by Yarbo on 2008-10-28
Thanks for responding!

This at least points me in the right direction, so maybe I can figure it out.  I tried to run the commands you posted, but unfortunately it didn't seem to fix it. 

Is there a different user that Bind should be running as, would it make more sense to run it as root, because then it would have access to everything.

The log as it stands after making the changes suggested above is: 

```
Oct 28 11:53:30 sluggo named[27052]: starting BIND 9.4.1-P1.1 -u bind -t /var/lib/named
Oct 28 11:53:30 sluggo named[27052]: found 1 CPU, using 1 worker thread
Oct 28 11:53:30 sluggo named[27052]: loading configuration from '/etc/bind/named.conf'
Oct 28 11:53:30 sluggo named[27052]: none:0: open: /etc/bind/named.conf: permission denied
Oct 28 11:53:30 sluggo named[27052]: loading configuration: permission denied
Oct 28 11:53:30 sluggo named[27052]: exiting (due to fatal error)
```


If anyone else has any other suggestions, I would appreciate it.

Cheers!

---

### Post by puppywhacker on 2008-10-28
hi,

One more tip. In the options field, -t sets a chroot for the named service to run in. I don't think that was your intention. Otherwise you should have a directory /var/lib/named with all the named configurations in it.

```
      -t directory
          chroot() to directory after processing the command line arguments,
          but before reading the configuration file.
```

remove the "-t /var/lib/named" statement. and post the output of your syslog and the "ls -l" again.

goodluck

---

### Post by Yarbo on 2008-10-28
Alright, so it looks like we are making some progress.  I still cannot start Bind, but since removing the stuff you mentioned above from /etc/default/bind9, I am getting a new message in the log.

Below is the latest from my syslog after making the change stated above.

```
Oct 28 12:59:11 sluggo named[5020]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Oct 28 12:59:11 sluggo named[5020]: automatic empty zone: D.F.IP6.ARPA
Oct 28 12:59:11 sluggo named[5020]: automatic empty zone: 8.E.F.IP6.ARPA
Oct 28 12:59:11 sluggo named[5020]: automatic empty zone: 9.E.F.IP6.ARPA
Oct 28 12:59:11 sluggo named[5020]: automatic empty zone: A.E.F.IP6.ARPA
Oct 28 12:59:11 sluggo named[5020]: automatic empty zone: B.E.F.IP6.ARPA
Oct 28 12:59:11 sluggo named[5020]: command channel listening on 127.0.0.1#953
Oct 28 12:59:11 sluggo named[5020]: command channel listening on ::1#953
Oct 28 12:59:11 sluggo named[5020]: couldn't open pid file '/var/run/bind/run/named.pid': Permission denied
Oct 28 12:59:11 sluggo named[5020]: exiting (due to early fatal error)
```

Also, if I do ls -la /etc/bind/named.conf I get:

```
yarbo@sluggo:~$ ls -la /etc/bind/named.conf
-rwxrwxrwx 1 bind bind 1611 2008-07-07 13:59 /etc/bind/named.conf
```

Again, any more help you can provide I would be in your debt!

Cheers!

---

### Post by puppywhacker on 2008-10-29
Hi,

You could remove the pid file, it generally gets created every time you start the service, but you're running into ownership problems again.

couldn't open pid file '/var/run/bind/run/named.pid': Permission denied

1. make sure the whole directory path exist.
mkdir -p /var/run/bind/run/

2. make sure the directory is owned by bind, so that user can create files in that directory
chown bind:bind /var/run/bind/run/

3. make sure the pid-file is owned by bind. otherwise you can't overwrite it
chown bind:bind /var/run/bind/run/named.pid

4. make sure the file is writable.
chmod +rw /var/run/bind/run/named.pid

goodluck

---

### Post by Yarbo on 2008-10-29
So I created the directory, and made sure to give full access to it to the bind user, however there is no named.pid file in that location, so I am confused as to why it doesn't simply create the file.

After making the changes specified above, the log still shows exactly the same thing:

```
Oct 29 09:07:57 sluggo named[26242]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Oct 29 09:07:57 sluggo named[26242]: automatic empty zone: D.F.IP6.ARPA
Oct 29 09:07:57 sluggo named[26242]: automatic empty zone: 8.E.F.IP6.ARPA
Oct 29 09:07:57 sluggo named[26242]: automatic empty zone: 9.E.F.IP6.ARPA
Oct 29 09:07:57 sluggo named[26242]: automatic empty zone: A.E.F.IP6.ARPA
Oct 29 09:07:57 sluggo named[26242]: automatic empty zone: B.E.F.IP6.ARPA
Oct 29 09:07:57 sluggo named[26242]: command channel listening on 127.0.0.1#953
Oct 29 09:07:57 sluggo named[26242]: command channel listening on ::1#953
Oct 29 09:07:57 sluggo named[26242]: couldn't open pid file '/var/run/bind/run/named.pid': File exists
Oct 29 09:07:57 sluggo named[26242]: exiting (due to early fatal error)
```

Unless anyone has any other idea's or suggestions, I think I will just format, and re-install the operating system when I get home.

I would much prefer trying to fix this, because the machine I use as a server is in my closet with no screen or keyboard.  Its a bit of a pain having to turn it off, detach all the cables and lug it over to my main workstation, so I was hoping to avoid that. 

Again, thanks for all your help, and if you have any other idea's please let me know, as I won't be able to get home for some time.

Cheers!

---

### Post by puppywhacker on 2008-10-29
The error message is slightly different

couldn't open pid file '/var/run/bind/run/named.pid': Permission denied
couldn't open pid file '/var/run/bind/run/named.pid': File exists

this time it says that it already exists. That ofcourse can be fixed :)

rm /var/run/bind/run/named.pid

I see your point in reinstalling, but personnally I'm a big fan of hardcore troubleshooting :) ... either way goodluck

---

### Post by Yarbo on 2008-10-29
Under normal circumstances, I would be more then happy to perform this kind of troubleshooting. I find it's the best way to learn how the underlying systems work.  

Unfortunately with BIND down, all of my emails and websites are down.  Granted they are not production servers, so its not costing me any money, but I am not receiving any personal emails either, which is frustrating.

I've tried to remove the named.pid file, and it goes back the what it said before.  Here is my syslog after running sudo rm /var/run/bind/run/named.pid.

```
Oct 29 12:50:53 sluggo named[31929]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Oct 29 12:50:53 sluggo named[31929]: automatic empty zone: D.F.IP6.ARPA
Oct 29 12:50:53 sluggo named[31929]: automatic empty zone: 8.E.F.IP6.ARPA
Oct 29 12:50:53 sluggo named[31929]: automatic empty zone: 9.E.F.IP6.ARPA
Oct 29 12:50:53 sluggo named[31929]: automatic empty zone: A.E.F.IP6.ARPA
Oct 29 12:50:53 sluggo named[31929]: automatic empty zone: B.E.F.IP6.ARPA
Oct 29 12:50:53 sluggo named[31929]: command channel listening on 127.0.0.1#953
Oct 29 12:50:53 sluggo named[31929]: command channel listening on ::1#953
Oct 29 12:50:53 sluggo named[31929]: couldn't open pid file '/var/run/bind/run/named.pid': Permission denied
Oct 29 12:50:53 sluggo named[31929]: exiting (due to early fatal error)
```

I am still at work, and will be here for a while longer, so if you have any other idea's or suggestions I would be open to try them.

Thanks again for all your help, you're the only person that has responded to my questions here on the Ubuntu forums, or anywhere else for that matter.  I appreciate it!

Cheers!

---

### Post by Yarbo on 2008-10-30
I've changed my DNS hosting over to my Registrar for now, and it's working fine. 

So because of this, I've decided to try and troubleshoot BIND until I can fix it.

So if anyone else has any idea's I would be open to suggestions.  I figured trying to troubleshoot the problem will probably teach me more about Linux and BIND then if I just reformated.

Everything else works on my server anyway, so, why not. :)

---

### Post by puppywhacker on 2008-10-30
hooray for troubleshooting :)

The thing is that you keep running against "permission denied" messages, which have to do with ownership and rights. Specifically I think the directory where the process-id file is written is not allowing the bind user to write in it's directory. So chown and chmod are your tools.

I have the opinion that PID files are prehistoric and I feel strongly that it shouldn't stop the service from running.

I'll give you some printouts from my system (ubuntu 8.04.1) so that you have something to compare against.

```

chown bind:bind /var/run/bind/run/
chmod a+rwx /var/run/bind/run/

```

```
root@sneezy:/# tail -f /var/log/syslog
Oct 30 18:50:39 sneezy named[9626]: command channel listening on ::1#953
Oct 30 18:50:39 sneezy named[9626]: zone 0.in-addr.arpa/IN: loaded serial 1
Oct 30 18:50:39 sneezy named[9626]: zone 127.in-addr.arpa/IN: loaded serial 1
Oct 30 18:50:39 sneezy named[9626]: zone 255.in-addr.arpa/IN: loaded serial 1
Oct 30 18:50:39 sneezy named[9626]: zone localhost/IN: loaded serial 2
Oct 30 18:50:39 sneezy named[9626]: running

```

```

root@sneezy:/# ls -la /var/run/bind/run/
total 4
drwxrwxr-x 2 root bind 60 2008-10-30 18:50 .
drwxr-xr-x 3 root root 60 2008-10-30 18:48 ..
-rw-r--r-- 1 bind bind  5 2008-10-30 18:50 named.pid

```

---

### Post by Yarbo on 2008-10-30
I fiiiiiiiiiixed it!~

Woooohooooo!

Now for anyone who is curious, the problem was due to the bind user, apparently something with it got mucked around when I upgraded.

I simply uninstalled BIND, deleted all the old configuration files and directories left behind, I then deleted the bind user, then reinstalled BIND, and it started working again right off the bat.

I noticed that there might be something wrong, when I noticed that the 'bind' user was in the 'dovecot' group, which I thought was strange. Troubleshooting FTW!

It always feels rather nice when you fix something like this, it's almost as if I defeated the computer somehow ;-).

Thanks for ALL the help puppywhacker, I really do appreciate it!

Cheers!

---

