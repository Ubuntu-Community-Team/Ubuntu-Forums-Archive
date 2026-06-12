---
title: "Haveing trouble with wget"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by slyfrost810 on 2010-10-25
I'm doing the post-install exercise for Ubuntu. This exercise is used in my class as well. 
I'm haveing a hard time with wget trying to get something to install.

im trying to use this command:

wget [http://noc/workshop/scripts/rc-config](http://noc/workshop/scripts/rc-config)

But i keep getting this error:
resolving noc... failed: Name or service not known.
wget: unable to resolve host address 'noc'

Any ideas on how to fix this?

---

### Post by anewguy on 2010-10-25
First off, it's telling you it can find any known internet domain of "noc".  Are you sure it's not something like "noc.com" or some other name instead of just "noc"?

Dave ;)

---

### Post by slyfrost810 on 2010-10-25
wget [http://noc.com/workshop/scripts/rc-config/](http://noc.com/workshop/scripts/rc-config/)
--2010-10-25 15:29:02--  [http://noc.com/workshop/scripts/rc-config/](http://noc.com/workshop/scripts/rc-config/)
Resolving noc.com... 174.121.95.151
Connecting to noc.com|174.121.95.151|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.noc.com/workshop/scripts/rc-config/](http://www.noc.com/workshop/scripts/rc-config/) [following]
--2010-10-25 15:29:02--  [http://www.noc.com/workshop/scripts/rc-config/](http://www.noc.com/workshop/scripts/rc-config/)
Resolving [www.noc.com](www.noc.com)... 174.121.95.151
Reusing existing connection to noc.com:80.
HTTP request sent, awaiting response... 404 Component not found
2010-10-25 15:29:03 ERROR 404: Component not found.

Hmm do I need new software sources?

---

### Post by cgroza on 2010-10-25
Go there with your browser. The thing does not exist.

---

### Post by slyfrost810 on 2010-10-25
> **cgroza said:**
> Go there with your browser. The thing does not exist.

Its part of this exercise

Finally, there is a nice Bash script that has been written which emulates the Red Hat chkconfig
script. This is called rc-config. We have placed this script on our “noc” box. Let's download the script an install it for use on your machine:

$cd
$wget [http://noc/workshop/scripts/rc-config](http://noc/workshop/scripts/rc-config)
$chmod 755 rc-config
$sudo mv rc-config /usr/local/bin

---

### Post by cgroza on 2010-10-25
I get the same error.

---

### Post by slyfrost810 on 2010-10-25
This seems to happen alot in this class lol. So the conclusion is that it just doesnt exist?

---

### Post by endotherm on 2010-10-25
> **slyfrost810 said:**
> This seems to happen alot in this class lol. So the conclusion is that it just doesnt exist?
at least not at that url.

---

