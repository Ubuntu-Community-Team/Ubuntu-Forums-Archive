---
title: "Beginner advice"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by jazzersaxman on 2010-03-19
Hello,

I was hoping to resurrect my old computer into a server, but have absolutely no idea where to start or how to go about it.  I am a PC user, I have 3 computers (not including the old one)- 2 are using Vista and 1 is using XP (on a netbook).  My goal is to be able to share files all from the same system, remote desktop access, shared internet and possibly whatever else I can make it do.  I decided the server must be the best option because I was tired of having 2 different sets of music files to sync from 2 different computers...

Can anyone advise me as to what the best step is?  I was told Ubuntu was the way to go, but any suggestions/tutoring would be very appreciated.

Thanks.

---

### Post by ayenack on 2010-03-19
This can be quite in depth stuff take a look at these and do a google search on Ubuntu LAMP server/gateway and media server.

[http://www.howtoforge.com/ultimate_freebsd_media_server](http://www.howtoforge.com/ultimate_freebsd_media_server)

[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

[http://www.cyberciti.biz/faq/howto-debian-ubutnu-set-default-gateway-ipaddress/](http://www.cyberciti.biz/faq/howto-debian-ubutnu-set-default-gateway-ipaddress/)

There're many other options including mail server, virus scanner etc. Search on google for how-to's.

---

### Post by oldos2er on 2010-03-19
What are the old computer's specs? Ubuntu server is a CLI environment, so it might be a bit rough for a newbie. [https://help.ubuntu.com/9.10/serverguide/C/index.html](https://help.ubuntu.com/9.10/serverguide/C/index.html)

---

### Post by jazzersaxman on 2010-03-20
I have a Dell Dimension 4300 1.6 Ghz 512MB RAM...I have the full spec sheet if needed...

---

### Post by oldos2er on 2010-03-20
Those specs are more than enough for Ubuntu server; you should be good to go.

---

### Post by Trandre on 2010-03-20
I found these handy for understanding CLI:

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)


Trandre:D

---

### Post by sandyd on 2010-03-20
> **jazzersaxman said:**
> Hello,

I was hoping to resurrect my old computer into a server, but have absolutely no idea where to start or how to go about it.  I am a PC user, I have 3 computers (not including the old one)- 2 are using Vista and 1 is using XP (on a netbook).  My goal is to be able to share files all from the same system, remote desktop access, shared internet and possibly whatever else I can make it do.  I decided the server must be the best option because I was tired of having 2 different sets of music files to sync from 2 different computers...

Can anyone advise me as to what the best step is?  I was told Ubuntu was the way to go, but any suggestions/tutoring would be very appreciated.

Thanks.
ok, so lets get started....

you want all computers to access the internet connection through that computer.

A good way to do this is to run a proxy server such as squid on the server machine.

Then you can configure all the computers to connect through the proxy.


you want to use it as a file server.
This is one of the harder parts to do in ubuntu server, but there IS a shortcut. You can install a program called webmin that you can use to graphically manage your file server from other computers (its generally easier to do this than to go through all these config files.

---

### Post by Old_Grey_Wolf on 2010-03-20
For a home network, you aren't going to place the performance demand on the server that a web hosting server will experience. The single core processor with 512MB RAM should work well.

You mentioned all Microsoft systems; therefore, I assume you are not that familiar with Linux. If you want something to use, and don't really care about learning how servers work, you can make things a little easier by just installing Ubuntu Desktop. It provides a graphical user interface so you don't have to use the command line as much. After installing Ubuntu Desktop you can add Samba to share files, download a LAMP (Linux, Apache, MySQL, PHP) stack for blogs/bulletin boards/etc., and Squid to share the Internet using the proxy server. There are packages in the Ubuntu repositories for those readily available for download. You can also search the repositories for packages to allow you to stream video files, and other things. You will find that the Ubuntu Desktop Edition already has many, if not most, of the Ubuntu Server Edition applications already installed.

Look at this page..[http://www.unixmen.com/linux-tutorials/570-install-lamp-with-1-command-in-ubuntu-910](http://www.unixmen.com/linux-tutorials/570-install-lamp-with-1-command-in-ubuntu-910)

---

### Post by Tikkyca on 2010-03-20
Well i see your specs with those specs server will run great.

---

### Post by jazzersaxman on 2010-03-22
Thanks for the sites...it's study time!

---

### Post by jazzersaxman on 2010-03-22
> **carlee said:**
> ok, so lets get started....

you want all computers to access the internet connection through that computer.

A good way to do this is to run a proxy server such as squid on the server machine.

Then you can configure all the computers to connect through the proxy.


you want to use it as a file server.
This is one of the harder parts to do in ubuntu server, but there IS a shortcut. You can install a program called webmin that you can use to graphically manage your file server from other computers (its generally easier to do this than to go through all these config files.
Thanks for the help...I am looking forward to this challenge...

I used to do some minor programming, so CLI should be fun!  if not, I guess I will use a GUI...with respect to the webmin, can I use that like a remote access terminal?

---

