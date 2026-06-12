---
title: "Rsync limit directories"
date: 2017-01-31
forum: Networking &amp; Wireless
---

### Post by fpttech on 2017-01-31
Hello Everybody.

I am new to this forum, and have a question regarding rsync.  I was able to set up Rsync on both client (windows using cgwin) and server (ubuntu server), and syncing appears to work well, the only hitch is I can type in any directory to backup to.  How do I lock individual users to a specified directory so various users cannot tamper with each other's directory. 

Thank You

---

### Post by Keith_Helms on 2017-02-01
I'm assuming from your description that you have multiple clients each with a unique userid who are all syncing data to individual directories on a common server.  Correct?

By tamper with, do you mean actually edit/save or do you want to block them even reading someone else's directory?

If you want to block them from even accessing each other's directories, just set the permissions on each user's directory  to 700.
```

sudo chmod 700 userdirectory

```
That will block any other user from even looking into that directory.

If you don't mind them looking but not touching each other's directories:
```

sudo chmod 755 userdirectory

```

---

### Post by SeijiSensei on 2017-02-01
> **fpttech said:**
> the only hitch is I can type in any directory to backup to.
Do you mean "backup from" or do you really mean "backup to?"  As an ordinary user I cannot insert files into another user's directory by any method, rsync included.  Are you using rsync with sudo ("sudo rsync ...")?  Then you have root privileges and can trash the system in any way you desire.  Presumably you're not giving other people sudo access, right?

---

### Post by fpttech on 2017-02-01
Yes good catch I meant backup top.  The Rsync Server is virtualized Ubuntu server.   The clients are windows standalone machines.  I should be more specific about "users", I created the users in a secrets file according to this tutorial [http://www.jveweb.net/en/archives/2011/01/running-rsync-as-a-daemon.html#jveweb_en_021_02](http://www.jveweb.net/en/archives/2011/01/running-rsync-as-a-daemon.html#jveweb_en_021_02).  In the directory I set rsync to sync from (on the server) there are various folders I created for the individual users to backup to.  The issue lies in the are able to type in any folder in that directory to sync to and from.

---

### Post by geeksmith on 2017-02-01
Could you create a separate account on the Linux box for each user? This would grant each user his own backup space, without privileges to read/write other users' data.

---

### Post by SeijiSensei on 2017-02-01
That example you linked to assumes that you have multiple users, as defined in the rsyncd secrets file, that all have full rights to a shared directory.  To have each user have a unique personal directory, you need to create users on the server and a matching secrets file.  So sue can then write /home/sue, bill to /home/bill, etc.  

It's been quite a while since I ran rsync in daemon mode, so I might not be entirely correct here.  I either run backups as root, typically from a script in /etc/cron.daily, or have matching users on both ends of the connection and run plain rsync:
```
bill@myserver:~$ cd ~; rsync -av Documents bill@remote:/home/bill
```
to synchronize bill's /home/bill/Documents directory to the remote.  This approach uses SSH without a daemonized version of rsync on the remote.

---

