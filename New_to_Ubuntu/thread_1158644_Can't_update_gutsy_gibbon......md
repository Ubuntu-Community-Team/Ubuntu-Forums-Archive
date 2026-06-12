---
title: "Can't update gutsy gibbon....."
date: 2009-05-13
forum: New to Ubuntu
---

### Post by Cobblestone57 on 2009-05-13
I am having trouble updating.  I have gutsy-gibbon.  I get the following error message.  It does not seem to be the same one as others listed here.  I am very new to Ubuntu.  Can you please help.....?

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg)  

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2)  

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2)  

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2)  

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2)  

Some index files failed to download, they have been ignored, or old ones used instead.

Joe

---

### Post by namd3r on 2009-05-13
The reason for this is your version of Ubuntu is no longer supported.

You will have to install or upgrade to a newer version, either Hardy Heron (8.04) or later.

---

### Post by Ericyzfr1 on 2009-05-13
You might as well install Jaunty directly.

---

### Post by OMRebel on 2009-05-13
Actually, it looks like some of the repos are down right now.

---

### Post by Cobblestone57 on 2009-05-14
Thank you, I will upgrade.  I was concerned about upgrading while I had an existing problem, but I will go with the latest and greatest today.

---

### Post by Cobblestone57 on 2009-05-14
I'm at standstill.  I looked on at the upgrades and they all require you to update your current edition, then they tell you that there is a new edition available.  However, I never get that far, it just keeps giving me the same errors over and over.  How do I break out of the loop?

---

### Post by namd3r on 2009-05-14
If you haven't already, you can try running the following in Terminal.

```
update-manager -d
```

That is how I usually upgrade my version.

If that doesn't work, I believe you can upgrade by modifying a sources.list file, which is a little more work.

---

