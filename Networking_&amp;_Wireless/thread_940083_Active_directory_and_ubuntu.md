---
title: "Active directory and ubuntu"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by whitenight639 on 2008-10-06
Hi people,

I'm looking to install ubuntu or edubuntu on about 20 laptops at work (secondry school). 

I'm not very savy with networking and active directory, I could do with some advice on how to get ubuntu authenticating with AD, I dont have a linux pc at work so find it hard to download the software i need (eg samba , Kerberos etc) as the laptop ive got ubuntu on wont connect to the network. 

I've seen the guides here [https://help.ubuntu.com/community/ActiveDirectoryHowto](https://help.ubuntu.com/community/ActiveDirectoryHowto)

but I dont have alot of time i can dedicate to this as im a technician and busy getting called out and about. 

I think its a shame we use lots of proprietry software in education environments and would like to get these older spec laptops up and running.

Soo does anybody know of a package or install script that is availible that I can use to insstall samba and all the other bits and that i need pieces in one?

or is there anything else that will help?

many thanks

---

### Post by PardusLynx on 2008-10-07
There's an integrated solution in Ubuntu, look for likewise-open in Synaptic. Or follow these steps:

   1. sudo apt-get update
   2. sudo apt-get install likewise-open
   3. sudo domainjoin-cli join fqdn.of.your.domain Administrator
   4. sudo update-rc.d likewise-open defaults
   5. sudo /etc/init.d/likewise-open start


You can also take a look at [http://sadms.sourceforge.net/](http://sadms.sourceforge.net/)

These are the alternatives I know, but none of them fully worked for me including the tutorial you linked in your message. Still looking to solve some problems!

---

### Post by likeWiseGuy on 2008-10-09
> **whitenight639 said:**
> Hi people,

I'm looking to install ubuntu or edubuntu on about 20 laptops at work (secondary school). 

I'm not very savy with networking and active directory, I could do with some advice on how to get ubuntu authenticating with AD, I dont have a linux pc at work so find it hard to download the software i need (eg samba , Kerberos etc) as the laptop ive got ubuntu on wont connect to the network. 

I've seen the guides here [https://help.ubuntu.com/community/ActiveDirectoryHowto](https://help.ubuntu.com/community/ActiveDirectoryHowto)

but I dont have alot of time i can dedicate to this as im a technician and busy getting called out and about. 

I think its a shame we use lots of proprietry software in education environments and would like to get these older spec laptops up and running.

Soo does anybody know of a package or install script that is availible that I can use to insstall samba and all the other bits and that i need pieces in one?

or is there anything else that will help?

many thanks

Hi whitenight639,

Likewise Open is a very ideal solution for your school's Ubuntu/Linux Active Directory integration. Likewise Open is free for you to download from Ubuntu's repository and can configure it any way you want.

```

sudo apt-get update
sudo apt-get install likewise-open

```
There is also a [Likewise Open 10-Minute Setup Guide for Linux]("http://likewisesoftware.com/resources/user_documentation/Likewise-Open-Quick-Start-Linux.pdf") that can help you get started. You can also reply to this thread if you need help getting started with Likewise Open in your school's network.

Thanks.

---

