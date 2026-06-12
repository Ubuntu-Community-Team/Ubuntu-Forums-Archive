---
title: "change premissions"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by natman on 2009-11-28
Hi,
I am trying to change the premissions on a directory of my server. My current directory is viewable online but after a created a new user his is not. I just get the error message " forbidden.." I did ls -ld on both and see there is a difference as follows:
> drwxr-xr-x   14 pbro  pbro      4096 Sep 14 15:21 . this works fine while the next one is the problem
> drwx------    5 tempest  tempest      4096 Nov 27 11:33 

Is it some sort of "chmod" command to change the second premissions? I have root access also.

Thanks:

---

### Post by scragar on 2009-11-28
```
sudo chmod -R +rx /home/tempest
```

---

### Post by natman on 2009-11-28
nope that isnt working, at the moment the working one is
> [pbro@larmor pbro]$ ls
public_html
[pbro@larmor pbro]$ ls -ld
drwxr-xr-x   14 pbro  pbro      4096 Sep 14 15:21 .
[pbro@larmor pbro]$

 and the one not working is:
> [tempest@larmor tempest]$ ls
public_html
[tempest@larmor tempest]$ ls -ld
drwx------    5 tempest  tempest      4096 Nov 27 11:33 .
[tempest@larmor tempest]$


Im pretty sure the problem is the permissions on tempest aren't the same as pbro, so pbro homepage is viewable while tempest is not ( just see forbidden message ) So i think i need to change the permissions on tempest

---

### Post by Some Penguin on 2009-11-28
Have you actually tried the 'sudo chmod...' command he gave?  That *is* the command to change permissions.

---

### Post by natman on 2009-11-28
Yes, it still doesnt let me view the page, perhaps there is something else going on here. Firefox give the error message
> Forbidden

You don't have permission to access /~tempest/ on this server.

---

### Post by Some Penguin on 2009-11-28
Are you using Apache httpd?  (Probably yes).

Then see [http://httpd.apache.org/docs/2.0/configuring.html](http://httpd.apache.org/docs/2.0/configuring.html) -- you will want to look at the [http://httpd.apache.org/docs/2.0/mod/core.html#directory](http://httpd.apache.org/docs/2.0/mod/core.html#directory) section in particular, and then modify your httpd.conf file.

---

