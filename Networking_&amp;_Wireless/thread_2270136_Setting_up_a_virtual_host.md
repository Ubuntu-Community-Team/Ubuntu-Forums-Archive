---
title: "Setting up a virtual host"
date: 2015-03-20
forum: Networking &amp; Wireless
---

### Post by chriso0258 on 2015-03-20
Hello,

I'm running Ubuntu 12.04.5. I've set up a website on our company's private network. Now, I want to set up a virtual host so I can have a duplicate site to test changes before implementing them on the production site. I set up a virtual host per various instructions and I keep getting a Server not found message. Here is what I've done.

The working site is itsweb.chat.tenn. I'm trying to create a test site called test-site.chat.tenn

1. I created a new root directory for the site: /var/www/test-site and have placed a temporary index.html file there. (Note: I set file permissions on this directory to 755)

2. I created a .conf file in the sites-available directory called test-site.chat.tenn.conf. Here is what's in the file:

<VirtualHost *:80>
    ServerAdmin admin@localhost
    ServerName test-site.chat.tenn
    ServerAlias [www.test-site.chat.tenn]("http://www.test-site.chat.tenn")
    DocumentRoot /var/www/test-site  
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

3. I ran a2ensite test-site.chat.tenn.conf which ran fine.
4. I ran service apache2 reload which ran fine.

When I tested the site I get the Server not found message. I also tried adding the loopback address with test-site.chat.tenn to the hosts file and rebooted the server but that didn't work. I then changed the loopback address to the IP of the server, rebooted, but that didn't work either. What am I missing?

Thanks for your help.

---

### Post by SeijiSensei on 2015-03-20
Try adding "test-site.chat.tenn" as an alias in /etc/hosts like this:
```

127.0.0.1     localhost test-site.chat.tenn

```

---

### Post by chriso0258 on 2015-03-23
Thanks for your reply. I tried your suggestion and it still didn't work; still keep getting "Server not found" page. Here is what my hosts file looks like:

```

127.0.0.1    localhost
127.0.1.1    itsweb.chat.tenn    itsweb
127.0.1.1    localhost test-site.chat.tenn

```

I also tried it this way:

```

127.0.0.1    localhost
127.0.1.1    itsweb.chat.tenn    itsweb
127.0.1.1    localhost test-site.chat.tenn    test-site

```

and this way:

```

127.0.0.1    localhost
127.0.1.1    itsweb.chat.tenn    itsweb
127.0.1.1    test-site.chat.tenn    test-site

```

After I updated the hosts file I rebooted the machine each time.

Here's what the test-site.chat.tenn.conf file looks like:

```

<VirtualHost *:80>
    ServerAdmin admin@localhost
    ServerName test-site.chat.tenn
    ServerAlias www.test-site.chat.tenn
    DocumentRoot /var/www/test-site
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

```

Can you see/think of anything I am missing? this is very puzzling. Would the problem have anything to do with the fact I'm on a private network? Should I use a static IP address instead of a host name? I'm grasping for straws at this point.

Thanks for your assistance.

---

### Post by matt_symes on 2015-03-23
Hi

You are trying to access the site using test-site.chat.tenn ?

What does this return ?

```
getent hosts test-site.chat.tenn
```

You have enabled the site correctly ? What does this return ?

```
for i in /etc/apache2/sites-enabled/*; do file "$i"; done
```

You nssswitch file is configured correctly ?

```
cat /etc/nsswitch.conf
```

You reloaded the apache configuration after editing the sites config file ?

```
sudo service apache2 reload
```

What do your log files say ?

BTW: Any reason you used 127.0.1.1 instead of 127.0.0.1 in your hosts file ?

Kind regards

---

### Post by SeijiSensei on 2015-03-23
Just have one entry per IP address in /etc/hosts together with its canonical name and aliases.  
```
127.0.0.1     localhost     test-site.chat.tenn test-site-for-chris another-alias yet-another-alias
```

---

### Post by chriso0258 on 2015-03-24
Hello, thanks for your reply.
> **matt_symes said:**
> 

You are trying to access the site using test-site.chat.tenn ?



Yes.

> **matt_symes said:**
> 
What does this return ?

```
getent hosts test-site.chat.tenn
```


Nothing.

> **matt_symes said:**
> 
You have enabled the site correctly ? What does this return ?

```
for i in /etc/apache2/sites-enabled/*; do file "$i"; done
```



```

**> for i in /etc/apache2/sites-enabled/*; do file "$i"; done**
/etc/apache2/sites-enabled/000-default: symbolic link to `../sites-available/default'
/etc/apache2/sites-enabled/default: ASCII text
```

> **matt_symes said:**
> 
You nssswitch file is configured correctly ?

```
cat /etc/nsswitch.conf
```



```

**> cat /etc/nsswitch.conf**
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```
> **matt_symes said:**
> 
You reloaded the apache configuration after editing the sites config file ?

```
sudo service apache2 reload
```


Yes.

> **matt_symes said:**
> 
What do your log files say ?


Not sure which logs to look at.

> **matt_symes said:**
> 
BTW: Any reason you used 127.0.1.1 instead of 127.0.0.1 in your hosts file ?


When I installed Ubuntu, that was the loop back Ubuntu assigned upon installation. I just copied it and replaced the itsweb for the virtual host.

---

### Post by matt_symes on 2015-03-24
Hi

> getent hosts test-site.chat.tenn

This should have returned the ip address of test-site.chat.tenn as set in the file /etc/hosts. 

Here's one of mine as an example.

```
matthew-laptop:/home/matthew:1 % grep pwc /etc/hosts
127.0.0.1       localhost pwc
matthew-laptop:/home/matthew:1 %
```

```
matthew-laptop:/home/matthew:1 % getent hosts pwc
127.0.0.1       localhost pwc
matthew-laptop:/home/matthew:1 %
```

Can you post your current hosts file.
> /etc/apache2/sites-enabled/000-default: symbolic link to `../sites-available/default' /etc/apache2/sites-enabled/default: ASCII text

You have not enabled the site correctly as it is not enabled. There should be a symbolic link in the directory /etc/apache2/sites-enabled/ that points to the configuration file in /etc/apache2/sites-available.

You enabled the site using 

```
cd /etc/apache2/sites-available/ && sudo a2ensite test-site.chat.tenn.conf && sudo service apache2 reload
```

Does the above command return any errors ?

Here's mine as an example again. Just a simple wiki i have on this laptop for my personal use protected by my firewall.

```
matthew-laptop:/home/matthew:1 % cat /etc/apache2/sites-available/pwc.conf 
<VirtualHost *:80>
        ServerName pwc
        DocumentRoot /var/www/pwc

        <Directory /var/www/pwc>
                Options -Indexes +FollowSymLinks -MultiViews
                AllowOverride None
                Order allow,deny
                Allow from 127.0.0.1
        </Directory>
</VirtualHost>
matthew-laptop:/home/matthew:1 % ls -l /etc/apache2/sites-enabled/pwc.conf 
lrwxrwxrwx 1 root root 27 Dec 10 15:21 /etc/apache2/sites-enabled/pwc.conf -> ../sites-available/pwc.conf
matthew-laptop:/home/matthew:1 %
```

So we know where you are, can you post all the config files you have edited, the steps you have taken and all the commands you have run so far.

To demonstrate to you my setup works without showing you my wiki

```
matthew-laptop:/home/matthew:1 % wget pwc
--2015-03-24 22:56:33--  http://pwc/
Resolving pwc (pwc)... 127.0.0.1
Connecting to pwc (pwc)|127.0.0.1|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: &#8216;index.html&#8217;

    [ <=>                                                                                         ] 12,920      --.-K/s   in 0s      

2015-03-24 22:56:33 (82.1 MB/s) - &#8216;index.html&#8217; saved [12920]

matthew-laptop:/home/matthew:1 %
```

Kind regards

---

### Post by chriso0258 on 2015-03-26
Thanks for your reply and support. 

I’m starting from scratch to make sure I pass on to you all the steps I’ve taken. This site is not on my local computer. It is on another computer in another room. The DNS server is located in another city.

 1. I created a directory called test-site (/var/www/test-site) and assigned 755 permissions. Within that directory I created an index.html file with 644 permissions.
2. I created a virtual host file in the /etc/apache2/sites-available directory called test-site.chat.tenn.conf containing the following: 

<VirtualHost *:80>
ServerAdmin webmaster@localhost
ServerName test-site.chat.tenn
ServerAlias [www.test-site.chat.tenn]("http://www.test-site.chat.tenn")
DocumentRoot /var/www/test-site
ErrorLog ${APACHE_LOG_DIR}/error.log
CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
 
There are two other files in this directory, default and default-ssl.
 
3. In the /etc/apache2/sites-enabled there are two entries. There is a file called default. Then, there is another entry (but not a file and there is no arrow indicating it is a symbolic link) called 000-default (there is no icon next to this entry). 
 
I enabled the virtual host using the following command: a2ensite test-site.chat.tenn.conf. The result was:

        Enabling site test-site.chat.tenn.conf.
        To activate the new configuration, you need to run:
         service apache2 reload
 
4. I ran service apache2 restart and the results were: 

* Reloading web server config apache2[Thu Mar 26 08:39:33 2015] [warn] NameVirtualHost 10.187.221.144:0 has no VirtualHosts   ...done. 

In the /etc/apache2/sites-enabled directory there was now an entry (with no icon next to it) called test-site.chat.tenn.conf.

5. While installing Ubuntu I selected to install Lamp. During the installation Ubuntu/Lamp was the one that assigned the local address 127.0.1.1. I don’t know why it did that vice 127.0.0.1. My original hosts file looked like this:

127.0.1.1   itsweb.chat.tenn   itsweb
 
# The following lines are desirable for IPv6 capable hosts
::1ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
 
I have added the following to the host file and rebooted my server
127.0.1.1 test-site.chat.tenn   test-site
 
6. I tested the set up by putting test-site.chat.tenn in my browser and I get a server not found message. I suspect that the DNS server (at another location) can’t resolve that name. 
 
I also tried changing the host file to reflect the IP address of the pc
10.187.221.144  test-site.chat.tenn  test-site but had the same problem.

Here was what was in the Apache2 error.log:

[Thu Mar 26 08:39:33 2015] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.14 with Suhosin-Patch configured -- resuming normal operations
[Thu Mar 26 09:03:35 2015] [notice] caught SIGTERM, shutting down
[Thu Mar 26 09:04:24 2015] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.14 with Suhosin-Patch configured -- resuming normal operations
[Thu Mar 26 09:09:26 2015] [notice] caught SIGTERM, shutting down
[Thu Mar 26 09:10:16 2015] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.14 with Suhosin-Patch configured -- resuming normal operations

---

### Post by matt_symes on 2015-03-29
Hi

> 6. I tested the set up by putting test-site.chat.tenn in my browser and I  get a server not found message. I suspect that the DNS server (at  another location) can&#8217;t resolve that name.

It should be using the hosts file and not DNS to resolve the hostname.

What does this return now ?

```
getent hosts test-site
```

```
getent hosts test-site.chat.tenn
```

What does this return ?

```
cd ~; wget test-site.chat.tenn; wget test-site
```

Which browser are you using ?

Kind regards

---

