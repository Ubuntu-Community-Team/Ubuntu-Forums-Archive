---
title: "Help me setting up a Web Server and Seedbox"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by akib_ahmed on 2010-11-20
Hello,
I am Akib and I need some help please.

I purchased a vps, it comes with a ubuntu 10.04 command line interface. I need to configure this vps to:

* a complete web server (with web-admin and php my admin), where I would be able to host multiple web sites. (Instructions on how to setup my domain names would be a huge help)

* a seedbox (based on libtorrent-rtorrent and rutorrent interface)

* a mailserver 

* a ftp file server to help me transfer files between my pc and vps.

* Maximum security possible.

Here comes the confession, I am not any good with linux. But I want to be and I need your help. So please give the details and explain a bit if you could.

I know I need to disable root first and set up a new user and change ssh ports ... but no idea about exact procedures!!

And a lamp setup will be needed, I did installed it, but cant make it work ... something is always screwed up!!

And the seedbox thing seems kinda impossible for my level of linux expertise!!

I've followed almost 50 tutorials (not kidding!) found on web and still I am at nowhere (Its my fault I know).

So please .... any help would be really really great.
Thanks in advance.

---

### Post by ironic.demise on 2010-11-20
I have set up an apache2 website on my main PC.

My first hint would be to install a desktop interface.
```
sudo apt-get install ubuntu-desktop
```
...Now I know this isn't a problem solved but I think for your expertise it might help a little.

for apache2 websites are stored in /var/www assuming you didn't change anything, My first suggestion here is to place an index.html in /var/www and then from the PC with Apache installed got to [http://localhost](http://localhost) to see if it appears.

---

### Post by akib_ahmed on 2010-11-20
Hey, Thanks a lot for the hint ironic.demise.

I am on a vps with limited resource, so I want to avoid a desktop interface if possible.
I can see the default apache2 page when I go to my vps's ip, the "It works" page. But I need support for PHP and mysql too.

I am looking for some top to bottom detailed tutorial.

---

### Post by ironic.demise on 2010-11-20
Try looking at Apache's website.

If you have PHP and SQL install (the default lamp) then everything in the /var/www folder, including .php files should work as intended.

As for ftp, mail etc. that is something I have not dabbled in and I hope somebody answers your questions.

If somebody accesses your servers I.P. they should already be greeted with the welcome page, you may need to configure firewalls etc. to forward port 80 though.

What DNS service are you using?
Your DNS hostname should be a setting on your router, though there are Ubuntu applications that auto update your DNS service with your dynamic IP.

---

### Post by sandyd on 2010-11-20
> **akib_ahmed said:**
> Hello,
I am Akib and I need some help please.

I purchased a vps, it comes with a ubuntu 10.04 command line interface. I need to configure this vps to:

* a complete web server (with web-admin and php my admin), where I would be able to host multiple web sites. (Instructions on how to setup my domain names would be a huge help)

* a seedbox (based on libtorrent-rtorrent and rutorrent interface)

* a mailserver 

* a ftp file server to help me transfer files between my pc and vps.

* Maximum security possible.

Here comes the confession, I am not any good with linux. But I want to be and I need your help. So please give the details and explain a bit if you could.

I know I need to disable root first and set up a new user and change ssh ports ... but no idea about exact procedures!!

And a lamp setup will be needed, I did installed it, but cant make it work ... something is always screwed up!!

And the seedbox thing seems kinda impossible for my level of linux expertise!!

I've followed almost 50 tutorials (not kidding!) found on web and still I am at nowhere (Its my fault I know).

So please .... any help would be really really great.
Thanks in advance.
Webserver + php +mysql + mailserver + DNS server
```

tasksel
```
Using the spacebar, select
LAMP, [s]DNS server[/s], Mail Server

Get the interface installed
```

wget -c http://downloads.sourceforge.net/project/webadmin/webmin/1.520/webmin_1.520_all.deb?r=http%3A%2F%2Fwww.webmin.com%2F&ts=1290269589&use_mirror=softlayer

dpkg -i webmin_1.520_all.deb
apt-get -f install
mkdir /etc/init.d-disabled
mv /etc/init.d/webmin /etc/init.d-disabled/webmin
```

any time you want to enable the web control panel, 
```

/etc/init.d/webmin start

```
after your finished using it,
```

/etc/init.d/webmin stop
```

To access the control panel, go to [http://**your-website-ip](http://**your-website-ip)**:10000

Under the "servers" section (after you login) should be everything you need.

For the Domain part, go to [http://dns.he.net](http://dns.he.net)
Sign up.
Login
Choose "Add A New Domain"
Add your domain
Click on the "edit zone" button next to the domain name
Click "new A"
Leave the Name blank, type in your VPS ip address in the "IPv4 address" box and press save
Click "new A"
Type in www in the "Name" box. and type in your VPS ip address in the "IPv4 addresses" box and press save.

At your domain registar, set your nameservers to these

--------------
ns1.he.net
ns2.he.net
ns3.he.net
ns4.he.net
ns5.he.net
--------------
For maximum security, you will need to setup [selinux enterprise security]("https://wiki.ubuntu.com/SELinux"). Its used by the NSA and is one of the most secure patches ever.

EDIT:
and for ftp
[https://help.ubuntu.com/community/PureFTP](https://help.ubuntu.com/community/PureFTP)

---

### Post by akib_ahmed on 2010-11-20
What is tasksel? when i type it in cli, it says, command not found!!

---

### Post by sandyd on 2010-11-20
> **akib_ahmed said:**
> What is tasksel? when i type it in cli, it says, command not found!!

```

apt-get install tasksel
```

---

