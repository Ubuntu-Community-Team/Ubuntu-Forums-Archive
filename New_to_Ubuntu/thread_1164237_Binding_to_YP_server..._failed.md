---
title: "Binding to YP server... failed"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by davidstri on 2009-05-19
I set up NIS with this tutorial, [https://help.ubuntu.com/community/SettingUpNISHowTo](https://help.ubuntu.com/community/SettingUpNISHowTo)
I got through everything alright until I actually had to start NIS with /etc/init.d/nis start 
After loading a couple of times, It sayed it failed.
I set my NISSERVER in /etc/default to NISSERVER=master and then tried again, but that didn't do anything. 
How do I get this thing to work?

---

### Post by toupeiro on 2009-05-21
Unless NIS in ubuntu is VERY different, your clients yp.conf doesn't have enough information..

1) Try formatting your CLIENT yp.conf like follows:

domain     <yourdomainname>     server     <yourNISmasterIPaddress>

2) It blows me away that the guide basically blows over a pretty important config file, /etc/nsswitch.conf  sudo edit your /etc/nsswitch.conf

It will look like this by default:

> passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis


In my opinion, there's no point in using compat unless you are trying to restrict the host to specific logins from NIS.  You can go back and set this later if you like.  So, for the sake of troubleshooting, lets make it look like this:

passwd:         files nis
group:          files nis
shadow:         files nis

hosts:          files nis mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files nis

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

3)  now, lets just try typing 
> sudo ypbind

It should read the formatting of your yp.conf file, and determine which ypserver to connect to for the domain you want.

---

### Post by davidstri on 2009-06-01
Cool, thanks for the reply. I am a linux beginner so I didn't really know what I was doing when I downloaded NIS. I was having problems with apache2, (401, and You don't have permission to view this folder). I thought downloading NIS would help, but actually, I just had to change my home folder permissions with chmod. hehe. 
Thanks again for the reply.

---

