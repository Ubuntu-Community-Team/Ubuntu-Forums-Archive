---
title: "Set upNIS client"
date: 2010-03-26
forum: New to Ubuntu
---

### Post by foppeh on 2010-03-26
I have set up a NIS server on a local machine:
```
foppe-desktop.lan has been set up as a NIS master server.

Now you can run ypinit -s foppe-desktop.lan on all slave server.
foppe-desktop:~# /etc/init.d/nis stop
foppe-desktop:~# /etc/init.d/nis start
Starting NIS services: ypserv yppasswdd ypxfrd ypbind.
```
From another machine in the local network I try to contact but I don't seem to get the /etc/yp.conf right. I tried every possible combination like
```
# ypserver foppe-desktop.lan

# domain foppe-desktop.lan server 192.168.1.65

# domain hemminga.sp server 192.168.1.65

domain foppe-desktop.lan broadcast

ypserver 192.168.1.65
```
But it still gives me
```
foppe@CC793205-B:~$ sudo /etc/init.d/nis start
 * Starting NIS services                                                         * binding to YP server...                                                       * ....                                                                          * ....                                                                          * ....                                                                          * ....                                                                          * ....                                                                          * ....                                                                          * ....                                                                          * ....                                                                          * ....                                                                          * ....                                                                  [fail]
```

Any clues? I did look at /etc/nsswitch.conf

---

### Post by HermanAB on 2010-03-27
Hmm, NIS is very old.  Is anyone still using it?  

The whole LDAP thing is going the way of the dodo, since there are other database engines that are easier to manage.  MySQL PAM seems to be more popular.

---

