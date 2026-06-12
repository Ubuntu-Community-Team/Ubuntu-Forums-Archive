---
title: "cannot download repository indexes"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by clovis66 on 2011-07-15
I'm a new user running 8.04.1 (kernel 2.6.24-19-lpia) when I try to update an error message  comes up with "cannot to download registry indexes" and a text box containing the following.  This has to be an easy fix but I'm not yet familiar enough with ubuntu to find it unaided.  Apreciate if someone can tell me the steps needed to fix this. 

Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/hardy/Release](http://netbook-remix.archive.canonical.com/ubuntu/dists/hardy/Release)  Unable to find expected entry  public/binary-lpia/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/hardy-updates/Release](http://netbook-remix.archive.canonical.com/ubuntu/dists/hardy-updates/Release)  Unable to find expected entry  public/binary-lpia/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/hardy-security/Release](http://netbook-remix.archive.canonical.com/ubuntu/dists/hardy-security/Release)  Unable to find expected entry  public/binary-lpia/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/hardy-netbook-remix/Release](http://netbook-remix.archive.canonical.com/ubuntu/dists/hardy-netbook-remix/Release)  Unable to find expected entry  public/binary-lpia/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Vahe Nersesian on 2011-07-15
Have you tried
sudo apt-get update

---

### Post by ajgreeny on 2011-07-15
8.04 desktop version, is not supported any more, hence your problem.

Only the server edition will continue getting updates, so you need to get a newer version of ubuntu.  I suggest 10.04, the next LTS after 8.04, unless you are prepared to go with the very different unity desktop.

---

### Post by stlsaint on 2011-07-15
> **clovis66 said:**
> I'm a new user running 8.04.1 (kernel 2.6.24-19-lpia) when I try to update an error message  comes up with "cannot to download registry indexes" and a text box containing the following.  This has to be an easy fix but I'm not yet familiar enough with ubuntu to find it unaided.  Apreciate if someone can tell me the steps needed to fix this. 

Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/hardy/Release](http://netbook-remix.archive.canonical.com/ubuntu/dists/hardy/Release)  Unable to find expected entry  public/binary-lpia/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/hardy-updates/Release](http://netbook-remix.archive.canonical.com/ubuntu/dists/hardy-updates/Release)  Unable to find expected entry  public/binary-lpia/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/hardy-security/Release](http://netbook-remix.archive.canonical.com/ubuntu/dists/hardy-security/Release)  Unable to find expected entry  public/binary-lpia/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/hardy-netbook-remix/Release](http://netbook-remix.archive.canonical.com/ubuntu/dists/hardy-netbook-remix/Release)  Unable to find expected entry  public/binary-lpia/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

Why are you wanting to run 8.04?? I agree ajgreeny that you should run either 10.04 if you want a Long Term Support OS or the newer releases.

---

### Post by Swagman on 2011-07-15
Indeed.. That's akin to wanting to install Win 98 (first edition)

---

### Post by clovis66 on 2011-07-18
Folks the question was _not _that I want to run 8.04
I _want to update from_ 8.04 and thats where the problem arises,
Anyone got a solution they are willing to share?

---

### Post by Bleak888 on 2011-07-18
The best option to avoid hosing your system would be to do a fresh install. backup your data and install from Live CD. 

I believe you can perform an upgrade but to avoid damaging the running system, you would have to upgrade in increments. I believe you can go from 8.04 to 10.04 thru the update manager. 

press Alt+F2 to launch the command box,and type in update-manager -d. Update Manager should open up and tell you: New distribution release ’10.04&#8242; is available. Click Upgrade and follow the on-screen instructions.

I would definitely perform a backup first thou.

---

### Post by oldos2er on 2011-07-18
> **clovis66 said:**
> Folks the question was _not _that I want to run 8.04
I _want to update from_ 8.04 and thats where the problem arises,
Anyone got a solution they are willing to share?

You could try ```
update-manager -d
```

---

### Post by snowpine on 2011-07-20
Support for lpia architecture was dropped. Fresh reinstall is your only choice. I suggest 10.04 or 11.04 (try a live CD/USB of both and see which you prefer).

---

