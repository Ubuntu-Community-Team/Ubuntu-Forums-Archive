---
title: "Apache2 and apache-ssl quagmire"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by ernestmogg on 2007-05-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/debian/+source/apache2/+bug/77675](https://bugs.launchpad.net/debian/+source/apache2/+bug/77675) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm going round in circles with the apache-ssl installation. I've had apache2 running under feisty for some time now dishing up php pages. What I can't seem to get right is apache-ssl.

When I installed apache-ssl it went through the process of creating a ssl cerificate but bombed out during the install muttering about an error (not specified). I completed the install   using dpkg reconfigure apache-ssl and the install completed. 

I have tried to follow the various howtos but they aren't clear and also refer to apache2-ssl-certificate which isn't available in the feisty packages. There are pointers to how to obtain and use this, but that makes things even more confusing.

What I need is some clear instructions as how to convert a normal http apache2 website to an apache-ssl https website. I don't want both.

I'm thinking of purging both apache2 and apache-ssl and starting again, but has any kind person got a simple method for doing this under feisty as instructions for other ubuntus just make things too complicated!

It is no use to point me at apache tutorials  It just adds to the complexity by introducing even more concepts. I just want a secure web server! Help anybody?

---

### Post by ernestmogg on 2007-05-23
Well, I haven't had anyone suggesting a cure for my aspache ssl ills, but I have come up with something. Basically it occurred to me to look to see in which order apache2 and apache-ssl were started. This showed that apache-ssl was being started first as they were listed like this in /etc/rc.2

S91apache-ssl
S91apache2

It was the same in rc.3, rc.4 and rc.5

I then stopped both apache-ssl and apache2 and then restarted them by starting apache2 first. Bingo my problems went away and I could connect to my website via [http://my-website](http://my-website), or [https://my-website](https://my-website).

I then decided to delete the S91apache-ssl links in rc.2 to rc.5 and name them S92apache-ssl  instead to force apache2 to start first. A reboot after these changes showed that all was still well.

The last thing was to delete the 000-default link in /etc/apache2/sites-enabled. This left me with only ssl in there and now I can only connect to my website via https, just what I wanted.

I don't know why this state of affairs came about, or whether I caused it somehow, or even whether apache2 must be started first. I leave that to an expert. I'm not one!

I hope this helps someone else in this torment.

---

### Post by twowheeler on 2007-05-24
Just a quick reply to let  you know that you are not alone.  See my thread on a related but not identical topic here: [click]("http://ubuntuforums.org/showthread.php?t=442811")

You have an interesting idea, I will try it out.

Thanks.

Edit:  ah, it looks like you have two versions of apache running.  Apache2 has ssl support built in, but it was an add-on for apache1.  The apache-ssl package is version 1.3.  You don't need that and apache2 both. 

Cheers.

---

### Post by ruy_lopez on 2007-05-24
This command enables the ssl mod for Apache2

```
$ sudo a2enmod ssl
```

Also, see this howto: [https://help.ubuntu.com/7.04/server/C/httpd.html](https://help.ubuntu.com/7.04/server/C/httpd.html)

---

### Post by gentoo-user on 2007-05-29
Hi guys,
I'm in the same boat for the last few days. I hopped on irc #apache channel and got awesome help.  Please note that apache-ssl is for apache 1.x and is NOT needed for apache2.  Use mod-ssl which is already has.

I'm using Ubunut Fiesty server edition, installed from iso I burnt and using lamp server option.

I was told to do the following.

1. install latest apache 
2. change NameVirtualHost * and <VirtualHost *> to NameVirtualHost *:80 and <VirtualHost *:80> 
3) add listen 443 to ports.conf 
4) add in ssl vhost config... 
5) restart apache... if this doesn't work make sure ssl is in /etc/apache2/mods-enabled. if not use a2enmod ssl and restart apache

If you are using the Linux firewall, here is a handy links also.  [http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)
Another useful link [http://wiki.apache.org/httpd/ScratchPad/DebianPHP](http://wiki.apache.org/httpd/ScratchPad/DebianPHP)

Hope this help someone.  I had to remove apache-ssl from my ubuntu box as it wasn't needed.  sudo aptitude purge apache-ssl

---

### Post by gentoo-user on 2007-05-29
Forgot this one.  I didnt' use the rewrite portion as I don't have users accessing webmail.

[http://www.linode.com/wiki/index.php/Apache2_SSL_in_Ubuntu](http://www.linode.com/wiki/index.php/Apache2_SSL_in_Ubuntu)

Enjoy.

---

