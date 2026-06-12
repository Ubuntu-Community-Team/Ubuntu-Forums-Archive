---
title: "Installed Tomcat and wonders about env. var, webapps priv. and auto added user priv."
date: 2009-01-16
forum: New to Ubuntu
---

### Post by tnek on 2009-01-16
I installed the servlet container and web server Tomcat 5.5 by installing the tomcat5.5 package, and I now have three multiple part questions:

[B]QUESTION ONE
[/B]
It does not set the environment variable [FONT=Courier New]CATALINA_HOME[/FONT], so I had to set it myself. I edited [FONT=Courier New]/etc/environment[/FONT] and added [FONT=Courier New]CATALINA_HOME=/var/lib/tomcat5.5/[/FONT] , was it the right way to add the environment variable and did I point it at the correct location?

Why didn't the installer fix this for me?

I found the location through locate [FONT=Courier New]webapps[/FONT] (it's where I put my WAR [Web Archive] files that I want to run) as [FONT=Courier New]CATALINA_HOME[/FONT] should be set to the parent directory of [FONT=Courier New]webapps[/FONT].

There are two locations for this, one is only symbolic links. Why is that?

```
tnek@rat:~/d$ ls -l /usr/share/tomcat5.5/
total 12
drwxr-xr-x 2 root root 4096 2009-01-10 21:23 bin
drwxr-xr-x 6 root root 4096 2009-01-10 21:23 common
lrwxrwxrwx 1 root root   14 2009-01-10 21:23 conf -> /etc/tomcat5.5
lrwxrwxrwx 1 root root   16 2009-01-10 21:23 doc -> ../doc/tomcat5.5
lrwxrwxrwx 1 root root   23 2009-01-10 21:23 logs -> /var/lib/tomcat5.5/logs
drwxr-xr-x 5 root root 4096 2009-01-14 19:53 server
lrwxrwxrwx 1 root root   25 2009-01-10 21:23 shared ->
/var/lib/tomcat5.5/shared
lrwxrwxrwx 1 root root   23 2009-01-10 21:23 temp -> /var/lib/tomcat5.5/temp
lrwxrwxrwx 1 root root   26 2009-01-10 21:23 webapps ->
/var/lib/tomcat5.5/webapps
lrwxrwxrwx 1 root root   23 2009-01-10 21:23 work -> /var/lib/tomcat5.5/work
``````
tnek@rat:~/d$ ls -l /var/lib/tomcat5.5/
total 12
lrwxrwxrwx 1 root     root   14 2009-01-10 21:23 conf -> /etc/tomcat5.5
lrwxrwxrwx 1 root     root   19 2009-01-10 21:23 logs -> ../../log/tomcat5.5
drwxr-xr-x 4 root     root 4096 2009-01-10 21:23 shared
drwxr-xr-x 2 tomcat55 root 4096 2008-12-07 20:17 temp
drwxr-xr-x 2 tomcat55 root 4096 2009-01-15 21:34 webapps
lrwxrwxrwx 1 root     root   21 2009-01-10 21:23 work -> ../../cache/tomcat5.5

```[B]QUESTION TWO
[/B]
The installer said it added a new user, called [FONT=Courier New]tomcat55[/FONT] , which I can confirm (see ls above) that it did. Has this user got a password? Could it be a security threat, if someone is able to log in using it? Can I and should I change the password?

[B]QUESTION THREE
[/B]
The user [FONT=Courier New]tomcat55[/FONT] and the group root owns the directory [FONT=Courier New]webapps[/FONT] (see ls above). I need to add a third user, called [FONT=Courier New]thethriduser[/FONT] , with the same permissions to the directory as [FONT=Courier New]tomcat55[/FONT]. How would I do that?

---

### Post by blueridgedog on 2009-01-16
For question two, the account probably has no login ability or password.  To confirm, in a terminal:

```
cat /etc/passwd | grep tomcat55
```

and post the output

As far as question 3, I would create a new group and then add the users you want to share ownership of the files to those groups and then change the the ownership of the files you want impacted to the new group.  For example, you could create a group called web

```
sudo groupadd web
```

Then to put user joe and user jane in the web group:

```
sudo usermod -G web,joe joe
sudo usermod -G web,jane jane
```

(syntax here may need tweaking as it is from memory and the man page)

Then change the ownership of the file you want owned by the new group:

```
sudo chown tomcat55:web /var/lib/tomcat5.5/webapps
```

This leaves the tomcat55 user the owner of the file, but replaces the group with web.

Individual files may need group write permissions:

```
chmod g+w /path/to/my/file
```

The code listed are examples and need to be adjusted to apply to your situation.

---

### Post by tnek on 2009-01-17
The output is:
```
tnek@rat:~$ cat /etc/passwd | grep tomcat55
tomcat55:x:111:65534::/usr/share/tomcat5.5:/bin/false

```

If I want to allow root access to the directory, just as (s)he had before. Do I have to add root to the web group then, or is root always implied?

---

### Post by blueridgedog on 2009-01-17
root can do anything, and no user will log in as root, so my call is no, you do not need to mess with root's groups.

---

