---
title: "Problem installing pear modules.."
date: 2009-07-17
forum: New to Ubuntu
---

### Post by niiklas on 2009-07-17
Hello,

im trying to install pear module http like this:

```
root@www:/testarea# pear install http
pear/HTTP requires PEAR Installer (version >= 1.7.1), installed version is 1.6.1
No valid packages found
install failed

```

And when i try to update pear following this site:
[http://pear.php.net/package/PEAR/download/1.7.1](http://pear.php.net/package/PEAR/download/1.7.1)
i get this:
```
root@www:/testarea# pear install PEAR-1.7.1
Ignoring installed package pear/PEAR
Nothing to install

```

Been googling like a maniac the last hour and cant find a solution that works for me.

---

### Post by Tibuda on 2009-07-17
PEAR is case-sensitive. You should use
```
pear install HTTP
```
When installing a beta package, you should also specify the version number.

---

### Post by niiklas on 2009-07-17
> **danielrmt said:**
> PEAR is case-sensitive. You should use
```
pear install HTTP
```
When installing a beta package, you should also specify the version number.

I successfully installed http package. but i still get this error from my php script that should work.
```
Warning: require_once(HTTP/Client.php) [function.require-once]: failed to open stream: No such file or directory in /home/niklas/lasias.com/classes/phptube.class.php on line 30

Fatal error: require_once() [function.require]: Failed opening required 'HTTP/Client.php' (include_path='.:/usr/share/php:/usr/share/pear') in /home/niklas/lasias.com/classes/phptube.class.php on line 30
```

Source:
[http://kamleitner.com/wp-content/uploads/2008/08/phptube-0.1.7.zip](http://kamleitner.com/wp-content/uploads/2008/08/phptube-0.1.7.zip)

Anyone see where the problem is ?

---

### Post by Tibuda on 2009-07-17
To include that "HTTP/Client.php" file, you have to install the HTTP_Client PEAR package.
```
sudo pear install HTTP_Client
```

---

