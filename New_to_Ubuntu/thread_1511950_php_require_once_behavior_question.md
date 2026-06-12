---
title: "php require_once behavior question"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by Mr. Hyde on 2010-06-17
I'm brand spanking new to linux/ubuntu, so please bear with me (I'm fairly competent in php however).

I'm running an ubuntu 10.04 LAMP server (PHP Version 5.3.2-1ubuntu4.2). I created a large set of scripts that work well in a windows XAMPP environment, but when I moved them to Ubuntu nothing worked. I narrowed it down to lines of code like these:

require_once dirname(__file__) . '/../login/traffic_cop.php';

I'm trying to move up the directory tree and go into a different folder, obviously this isn't working presently.

Does require_once behave differently on a linux environment?

Thanks,

---

### Post by mörgæs on 2010-06-17
Are there enough read and execute rights on the directories?

This is a good beginning in Ubuntu:
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

---

### Post by Mr. Hyde on 2010-06-17
> **mörgæs said:**
> Are there enough read and execute rights on the directories?

This is a good beginning in Ubuntu:
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

Yes, originally this was a problem until I read about using chmod, but everything in that directory is 755. I found out I can even set rights w/ my FTP program.

Temporarily, I've just shoved everything in one folder (and it works fine like that), but I don't like it, aesthetically... and I don't enjoy not knowing why things don't work.

---

### Post by mörgæs on 2010-06-18
Which rights are on the directory itself (not the files within)?

---

### Post by Mr. Hyde on 2010-06-18
> **mörgæs said:**
> Which rights are on the directory itself (not the files within)?

The rights from var all the way up to the sub directory that contains it are 755.

---

### Post by lisati on 2010-06-18
Shouldn't this:
> require_once dirname(__file__) . '/../login/traffic_cop.php';
be more like this:????
> require_once('../login/traffic_cop.php');

---

### Post by Mr. Hyde on 2010-06-18
> **lisati said:**
> Shouldn't this:

be more like this:????

Got the same error...

Warning: require_once(../login/test.php): failed to open stream: No such  file or directory in /var/www/Spider/delete_me.php on line 21  Fatal error: require_once(): Failed opening required '../login/test.php'  (include_path='.:/usr/share/php:/usr/share/pear') in  /var/www/Spider/delete_me.php on line 21 

btw, using "dirname(__file__)" should be SOP  (even though I didn't use it to test your suggestion) for includes because:
"A key problem to hierarchical include trees is  that PHP processes include paths relative to the original file, not the  current including file."

[http://php.net/manual/en/function.dirname.php](http://php.net/manual/en/function.dirname.php)

If I had known about that when I started programming in php it would have saved me about 2 days of bashing my face into my computer screen.

---

### Post by Mr. Hyde on 2010-07-01
So, I figured it out... and I feel like an absolute idiot, but I'll post the solution up here so that others don't have to repeat my error.

So, using XAMPP on my windows developer environment capitalization of the included files doesn't matter, but on Linux it does.

If anyone knows how to enable that feature in Apache I would be interested, but it's a low priority item in my book (now that I know what's going on and how to fix it).

---

