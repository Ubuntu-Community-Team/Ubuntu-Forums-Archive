---
title: "Help!  Accidentally changed permissions on all files in /var folder!"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by quickk on 2009-05-25
Hi everyone, I accidentally changed all the file permissions in the var folder and now everything is messed up.  

I did

```
sudo chown . 777 -R 
```

when I was in the /var folder (I thought that I was in the /var/www folder instead).  

How can I return all the permissions to the way they were before?

How can I change all the directories to +x (but not the files)?  

Thanks!

---

### Post by Mornedhel on 2009-05-25
I *think* there's no way to return to the previous rights, unless you have another install of Linux around, and can do an ls -Rl on its /var, and then probably a few lines of bash could restore it.

Changing all directories to +x is easy, however :

Ensure only directories are returned :
```
find /var -type d
```

Chmod it all (WARNING) :
```
sudo find /var -type d -exec chmod a+x '{}' \;
```

Warning: this may be a really bad idea. It sets all users rights to cd into all directories in /var, which may or may not be what you are attempting to do. Execute the above command at your own risk.

---

### Post by asmoore82 on 2009-05-25
Did you really do *exactly* what you said?

`ch**_own_** 777` as opposed to `ch**_mod_** 777` ??

If this really is the case, you screwed up file ownership and not permissions.

looking at another system may help, mine is:
```
**~$** ls -l /var/
total 44
drwxr-xr-x  2 root root  4096 2009-05-23 08:05 [COLOR="Blue"]backups[/COLOR]
drwxr-xr-x 16 root root  4096 2009-05-11 09:46 [COLOR="Blue"]cache[/COLOR]
drwxrwxrwt  2 root root  4096 2009-03-18 05:48 [COLOR="Lime"]crash[/COLOR]
drwxr-xr-x  2 root root  4096 2009-03-23 20:13 [COLOR="Blue"]games[/COLOR]
drwxr-xr-x 57 root root  4096 2009-05-14 16:28 [COLOR="Blue"]lib[/COLOR]
drwxrwsr-x  2 root staff 4096 2009-03-05 12:44 [COLOR="Blue"]local[/COLOR]
drwxrwxrwt  2 root root    60 2009-05-25 07:36 [COLOR="Lime"]lock[/COLOR]
drwxr-xr-x 13 root root  4096 2009-05-25 07:36 [COLOR="Blue"]log[/COLOR]
drwxrwsr-x  2 root mail  4096 2009-03-23 19:55 [COLOR="Blue"]mail[/COLOR]
drwxr-xr-x  2 root root  4096 2009-03-23 19:55 [COLOR="Blue"]opt[/COLOR]
drwxr-xr-x 20 root root   800 2009-05-25 20:30 [COLOR="Blue"]run[/COLOR]
drwxr-xr-x  7 root root  4096 2009-05-14 16:28 [COLOR="Blue"]spool[/COLOR]
drwxrwxrwt  3 root root  4096 2009-05-25 20:26 [COLOR="Lime"]tmp[/COLOR]
```

if `chmod` is what you actually did and you have screwed up permissions,
you will probably want a cmdline to take away execute on just files:
```
sudo find /var -type f -print0 | sudo xargs -0 chmod -x
```

---

### Post by quickk on 2009-05-25
Whoops, I meant chmod, not chown!  Today really isn't my day...  

As for changing the permissions, Thanks for the tip... I always wondered how to do that.  

I'm afraid that I really messed things up though since I rebooted my computer and now I can't get to the desktop.  I get a message saying that it "failed to initialize HAL."  I'm using a live cd to type this.  I'll play around with the permissions, and hopefully I can fix this...

---

