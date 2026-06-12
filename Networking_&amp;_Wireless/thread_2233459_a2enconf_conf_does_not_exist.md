---
title: "a2enconf conf does not exist"
date: 2014-07-08
forum: Networking &amp; Wireless
---

### Post by peter120 on 2014-07-08
Ubuntu server 14.04
I am attempting to install submin2.

Following the instruction in [https://ssl.supermind.nl/collab/svn/submin/submin/trunk/INSTALL](https://ssl.supermind.nl/collab/svn/submin/submin/trunk/INSTALL) (having manually installed python-central & sendmail)
The config files are generated OK & I receive a password link email.

```
sudo a2enconf apache-2.4-webui-cgi.conf
```
returns the error
```
ERROR: Conf apache-2.4-webui-cgi does not exist!
```

How do I enable a config file?
What is the config file?

I have used other config files before. Previously I have just included .conf in the site file.
The apache-svn.conf file looks similar to basic svn.conf files I have used (& included in the site file) previously.
I tried including the config files in the site but the email password link does not work.

Any help or working submin guide would be great!

---

