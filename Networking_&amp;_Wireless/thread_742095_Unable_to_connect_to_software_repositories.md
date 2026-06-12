---
title: "Unable to connect to software repositories"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by MrPaez on 2008-04-01
Hi I have installed 8.04 x86 on a HP DC5000SFF for some testing at work. We have a proxy server and I think that it may be the cause of me not being able to get software updates of download software to join the Desktop to our MS AD.

Any ideas what I can do to change the 111 connection refused message I am getting?

Also, does anyone have a good guide for joing a Ubuntu desktop to a Microsoft AD network enviroment?

---

### Post by bapoumba on 2008-04-01
You have to place your proxy settings in /etc/apt/apt.conf:
[http://linux.die.net/man/5/apt.conf]("http://linux.die.net/man/5/apt.conf")

---

### Post by MrPaez on 2008-04-01
Thanks I will check out that link you provided.

I am looking under /etc/apt$ dir
and this is whats listed.
apt.conf.d  secring.gpg  sources.list  sources.list.d  sources.list.save  trustdb.gpg  trusted.gpg  trusted.gpg~

I will let you know how I make out.

---

### Post by bapoumba on 2008-04-01
If you do not have one, you can create it.

In the above link, look at the acquire group. The line should look like:
```
Acquire::http::Proxy "http://[[user][:pass]@]host[:port]";
```

---

### Post by MrPaez on 2008-04-01
I am sorry bapoumba but i am not following you in terms of creating the proxy file and the acquire group in the above link.


All I have is the following:
$ /etc/apt/apt.conf.d$ ls

00trustcdrom  01ubuntu    10periodic  50unattended-upgrades  99update-notifier
01autoremove  05aptitude  20archive   70debconf


I think what you are saying is to create a file called: "http" and then enter in the code you provided?

Sorry if I am missing something in the site.

---

### Post by MrPaez on 2008-04-28
bapoumba, do I keep the brackets in there?

---

### Post by bapoumba on 2008-04-28
Sorry, I've been away and missed your previous post.
No you do not keep the brackets.

Please create the file:
```
sudo nano /etc/apt/apt.conf
```
and add the info matching your network settings.
CTRL-O to save the file
CTRL-X to exit nano.

As an example, here is the file on my corporate proxy:
```
ACQUIRE { 
http::proxy "http://proxy.unicaen.fr:3128"
};
```
The trailing semi-colon is mandatory.

```
sudo apt-get update
```
Please post the exact error message if necessary.

---

### Post by MrPaez on 2008-04-28
Well I tried configuring the apt.conf as you suggested. I still recieve the same error message:

```
mpaez@WAYNE-1516UBMP:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy Release.gpg                                   
Ign http://archive.canonical.com gutsy Release.gpg                                   
Ign http://archive.canonical.com gutsy/partner Translation-en_US                     
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US                        
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://archive.canonical.com gutsy Release
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates Release.gpg
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Ign http://archive.canonical.com gutsy/partner Packages            
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-security Release.gpg
Ign http://us.archive.ubuntu.com gutsy-security/main Translation-en_US
Ign http://archive.canonical.com gutsy/partner Sources
Ign http://us.archive.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-security/multiverse Translation-en_US
Err http://archive.canonical.com gutsy/partner Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Ign http://us.archive.ubuntu.com gutsy Release
Ign http://us.archive.ubuntu.com gutsy-updates Release
Ign http://us.archive.ubuntu.com gutsy-security Release
Err http://archive.canonical.com gutsy/partner Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

```

Thats basically what happens but much more lines. The error message **407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )** is repeated.

the contents of the apt.conf look like:
```
ACQUIRE { 
http::proxy "http://hostname.domain.com:port"
};
```

I dont get it. I dont understand why Firefox works but issues arrive with the synaptic manager.

---

### Post by bapoumba on 2008-04-28
Ah, it's an ISA proxy..
I think you'll need to use ntlmaps, let me browse for some infos, I remember people successfully connect to the repos with it.

Package managers have their own ways, different from browsers ;)

---

### Post by bapoumba on 2008-04-28
Please check this thread:
[http://ubuntuforums.org/showthread.php?t=589854]("http://ubuntuforums.org/showthread.php?t=589854")
There are also links to other UF threads that may help you in it.

---

