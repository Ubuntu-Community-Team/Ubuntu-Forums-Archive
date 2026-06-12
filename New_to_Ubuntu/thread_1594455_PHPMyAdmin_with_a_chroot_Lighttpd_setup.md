---
title: "PHPMyAdmin with a chroot Lighttpd setup?"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by walnut100 on 2010-10-12
Hey everyone,

I've had a Linode with Ubuntu 10.04 LTS for a little while and one of my friends managed it for me. One day he went kinda nuts and did something weird to the image, made it so it wouldn't boot up, which left me to build a new one and transfer the data to it.

I Googled around for a while and found lots of good tutorials to get started, ended up doing a chroot lighttpd install with PHP5 FastCGI, MySQL, XCache, pretty basic setup.

I only need to install PHPMyAdmin and Ioncube now and then I think I've got everything setup and ready to go again. My problem is I've been having issues with PHPMyAdmin.

Since I'm very very very green to Linux (I just started Thursday) I still don't totally understand chroot and have been having trouble getting PHPMyAdmin to work. I installed it through the apt-get packages, setup a vhost, and copied /usr/share/phpmyadmin to /chroot/usr/share/phpmyadmin

When I boot it up it says to check my PHP install and server error logs but I don't see any errors being recorded anywhere, which leads me to believe that I just haven't moved it to the chroot correctly.

Any advice Linux gurus? I'm sure lots of people have done this before

---

Well guys, I figured it out after sitting on it for a bit. I misinterpreted what session meant. It meant session as in a PHP session and not session as in a schoolhouse session. All you have to do is install by copying to /chroot/usr/share/phpmyadmin, set your vhosts so it'll show up (May not even be necessary), make sure you have a folder for PHP to save sessions, go to your /chroot/etc/php5/cgi folder or wherever your php.ini file is, and edit it accordingly. Make sure it has proper permissions so that PHP can write to it and you're golden.

---

