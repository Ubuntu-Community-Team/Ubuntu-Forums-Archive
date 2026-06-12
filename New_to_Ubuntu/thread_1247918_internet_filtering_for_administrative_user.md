---
title: "internet filtering for administrative user"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by sunshyne on 2009-08-23
I have a new laptop and I am running Jaunty.  I would like to set up some sort of internet filtering system (either blocking certain sites or logging them).  I currently have DansGuardian set up which seems to work fine.  There's just one problem: I can disable it at any time with my sudo password and I'm the one that needs the filtering.  But I'm also the one who needs to have administrative rights to do the rest of maintenance, etc.  Is there a way that sites blocked can be logged to a file I don't have permissions on or emailed to someone elses account?  Or can the times that I disable DansGuardian be logged somewhere?  Is there another program that will do this better than dansguardian?  Thanks!

---

### Post by mike555 on 2009-08-23
You could use "OpenDNS" it can be set to filter ......  [http://www.opendns.com/](http://www.opendns.com/)

---

### Post by tommynz1975 on 2009-08-24
I forget the site, but yes your surfing history can be emailed out to a sponsor. A bit like an AA snoop.  "Hey Bob, John just went into the bottle shop"

I will do a search and post back if I find the site.

the net gear router lets you email out a  history.

---

### Post by MrWES on 2009-08-24
> **sunshyne said:**
> I have a new laptop and I am running Jaunty.  I would like to set up some sort of internet filtering system (either blocking certain sites or logging them).  I currently have DansGuardian set up which seems to work fine.  There's just one problem: I can disable it at any time with my sudo password and I'm the one that needs the filtering.  But I'm also the one who needs to have administrative rights to do the rest of maintenance, etc.  Is there a way that sites blocked can be logged to a file I don't have permissions on or emailed to someone elses account?  Or can the times that I disable DansGuardian be logged somewhere?  Is there another program that will do this better than dansguardian?  Thanks!

You could route the site to 127.0.0.1 in your /etc/hosts files. It's rw root only.

```
www.facebook.com  127.0.0.1
```

Bill

---

### Post by sunshyne on 2009-08-24
> **mike555 said:**
> You could use "OpenDNS" it can be set to filter ......  [http://www.opendns.com/](http://www.opendns.com/)

yes, but can't anyone (especially one with administrator rights) just change the DNS proxy?

---

### Post by SuaSwe on 2009-08-24
[[color="blue"]Squid[/color]]("https://help.ubuntu.com/7.04/server/C/squid.html") seems to be pretty popular (although quite resource-heavy, apparently!). The hosts file idea is pretty clever otherwise, as long as you keep your root password to yourself and set strict permissions for the file. :)

---

### Post by mike555 on 2009-08-24
> **sunshyne said:**
> yes, but can't anyone (especially one with administrator rights) just change the DNS proxy?

   If you use OpenDNS and put it on your modem then have someone set a password to the modem.... only the person with the modem password could change it ..
   but of course if a person was using a laptop and got wifi from somewhere else it wouldn't work ..

---

### Post by sunshyne on 2009-08-26
It's on a laptop so it can't be based on router settings only.

---

### Post by achase79 on 2009-08-26
Using separate administrator and user accounts would be the most appropriate way to do this.

---

### Post by sunshyne on 2009-08-29
> **achase79 said:**
> Using separate administrator and user accounts would be the most appropriate way to do this.


But this would require that I am just a normal user and that someone else has to be administrator on my computer. It can't be based on a router as this is a laptop and I need to retain administrative rights for all other things.  Those are really the only requirements. Isn't there some script that can log when someone would turn off Dansguardian or otherwise bypass the system?

---

