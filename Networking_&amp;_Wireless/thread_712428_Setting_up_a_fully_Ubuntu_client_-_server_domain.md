---
title: "Setting up a fully Ubuntu client - server domain"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by mattdavis90 on 2008-03-01
Hi All,

I have read around on both google and the Ubuntu Forums and haven't found what I'm looking for. I am sure it must be possible so here goes;

I have a domain set up using Windows 200 Server as PDC and several Windows XP client machines. A user can log on at any workstation and gets the same profile and my docs directory, I have my user arranged into groups which have different policies applied, I'm sure most of you are familiar with the set up. Now my question is, Is this all possible using ONLY Ubuntu (or another linux os)? I have read about connecting linux clients to a windows server and connecting windows clients to a linux server but both methods have linux emulating the microsoft way of doing things. Is this the only way? or does linux, in particular Ubuntu, have any native way of setting up a client/server domain?

I hope my question is clear.
Thanks,

Mattdavis90

---

### Post by vinnn on 2008-03-01
From what I understand from your post, I think you have setup some basic active directory policies on a Windows domain and you want to know how do implement a similar directory model on a purely Linux server/client model.
I can tell you that MS Active Directory is just Microsoft's own proprietory implementation (i.e. copy) of the standard directory services protocol LDAP, which is the usual method of setting up directory services in a Unix, Netware or Linux style infrastructure.

Wikipedia would be a good place to start to read about LDAP... [http://en.wikipedia.org/wiki/Lightweight_Directory_Access_Protocol]("http://en.wikipedia.org/wiki/Lightweight_Directory_Access_Protocol")

---

### Post by mattdavis90 on 2008-03-02
Thanks for the response, I will definitely read up on LDAP. I have briefly read about OpenLDAP, and kerberos (i think), is this easy to set up and implement or is it easier for me to just stay with my windows 2000 server and just change clients to linux?

Thanks again,

Mattdavis90

---

### Post by mattdavis90 on 2008-03-02
I have just been searching around for LDAP and Ubuntu server client on google and have found a link to ubuntuforums - [http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760) So, thanks for pointing me in the direction of LDAP and thanks to everyone on the other thread.

Cheers again,

Mattdavis90

---

