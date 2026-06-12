---
title: "sharing /var/www/"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by AudioSpark on 2009-12-29
I'm running apache2 on ubuntu 9.10 and have configured virtual hosts for 2 sites.  The webpage files are to be located in /var/www/site1, /var/www/site2.

I'd like to share /var/www/ and all subdirectories under it.

Sharing Documents and Pictures was successful and are visible to Dreamweaver. I own these two directories.  root owns /var.

How do I share the /var/www directory so that it is visible to Dreamweaver running on a mac OS X 10.4 system?

:confused:

AudioSpark !

---

### Post by sandyd on 2009-12-29
> **AudioSpark said:**
> I'm running apache2 on ubuntu 9.10 and have configured virtual hosts for 2 sites.  The webpage files are to be located in /var/www/site1, /var/www/site2.

I'd like to share /var/www/ and all subdirectories under it.

Sharing Documents and Pictures was successful and are visible to Dreamweaver. I own these two directories.  root owns /var.

How do I share the /var/www directory so that it is visible to Dreamweaver running on a mac OS X 10.4 system?

:confused:

AudioSpark !
```

chown -R *username */var/www
```will cause all directories under /var/www to be owned by *username*.

```

sudo chmod -R 777 /var/www/*

```
will  make it writable for everyone. but that wouldn't be good right? so i advise you to simply use the first method.

---

### Post by phillw on 2009-12-29
> **AudioSpark said:**
> I'm running apache2 on ubuntu 9.10 and have configured virtual hosts for 2 sites.  The webpage files are to be located in /var/www/site1, /var/www/site2.

I'd like to share /var/www/ and all subdirectories under it.

Sharing Documents and Pictures was successful and are visible to Dreamweaver. I own these two directories.  root owns /var.

How do I share the /var/www directory so that it is visible to Dreamweaver running on a mac OS X 10.4 system?

:confused:

AudioSpark !

Hi,

I'd do it slightly differently.

make a directory called, say, dreamweaver, in /var/www
and then put your sites under that. you can then change the ownership of all under /var/www/dreamweaver, yet retain the default permissions in case you later want to add another site that has nothing to do with dreamweaver.

```
cd /var/www
sudo mkdir dreamweaver
sudo chmod 755 /var/www/dreamweaver 
cd dreamweaver
mkdir site1
mkdir site2

```move your existing site1 & site2 to their new homes
then  site1 and site2 would now be owned by you, but, as the permissions of the files within them may not, I'd do a```


chown -R *username */var/www/dreamweaver 
```just to make sure :-)

That's only because it would be easier to do that now, then in 6 months time when you decide to add a new site, NOT via dreamweaver.

Regards,

Phill.

---

