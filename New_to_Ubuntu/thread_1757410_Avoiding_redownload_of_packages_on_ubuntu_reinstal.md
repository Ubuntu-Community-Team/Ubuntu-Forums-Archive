---
title: "Avoiding redownload of packages on ubuntu reinstall"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by NikS on 2011-05-13
Hi all,
I came across this post on a blog about setting up a local repository: [http://blog.sayanriju.co.cc/2009/07/31/using-a-local-ubuntu-repository-to-avoid-redownloading-packages-on-a-reinstall/](http://blog.sayanriju.co.cc/2009/07/31/using-a-local-ubuntu-repository-to-avoid-redownloading-packages-on-a-reinstall/)

I have not tried it myself, But I was wondering:
Ubuntu seems to keep backup of all the downloaded packages at the location: /var/cache/apt/archives/, if installing an application that has a dependency it should be searching in those packages if it is already downloaded..!

So instead of going through all that effort of creating a repository, if I just copy back all the debs to the location and carry out the installation process normally, i.e. installing from software center, it should pick up the packages! Right?

So that will save me all those steps mentioned.. Just keep a backup, copy back in the new installation and done!

Now the questions is: Does it work this way!! :P

disclaimer: I have absolutely no idea how the downloads/installations are handled.. This is just a guess..! Please correct me if wrong! :)

---

### Post by QLee on 2011-05-13
[QUOTE=NikS]... But I was wondering:
Ubuntu seems to keep backup of all the downloaded packages at the location: /var/cache/apt/archives/, if installing an application that has a dependency it should be searching in those packages if it is already downloaded..! [/QUOTE]

Those are not "backups", that is the location where the package manager puts the package files it downloads, those are the actual downloads, the "package cache".

[QUOTE=NikS]So instead of going through all that effort of creating a repository, if I just copy back all the debs to the location and carry out the installation process normally, i.e. installing from software center, it should pick up the packages! Right?

So that will save me all those steps mentioned.. Just keep a backup, copy back in the new installation and done!

Now the questions is: Does it work this way!! :P

disclaimer: I have absolutely no idea how the downloads/installations are handled.. This is just a guess..! Please correct me if wrong! :)[/QUOTE]

It would work very similiar to the way you describe, for a while, then after some time some of the package versions that would be in the cache would be old versions and a new version would have to be downloaded anyway, and you would likely end up with several versions of many of the packages (only one would be the latest, installable), it could be more work than you realise trying to keep your "store" (your saved copies) up to date and with only the latest version if you were intending on doing it manually. Ubuntu changes fairly rapidly (Edit: by this I'm referring to security upgrades which are produced as exploits are discovered over time), thus over the course of a release lifetime there will be several or many versions of a lot of the packages. You could still do what you described but it might not be easier than some of the other solutions for local repositorys.

---

### Post by NikS on 2011-05-13
Thanks QLee..
I understand it now..!

The problem is that I have a fairly limited connection, 5GB per month and it becomes difficult to search and download all the applications I need every time I install Ubuntu.. While still trying to understand how things work, I bloat the system quite frequently! :)

Well.. may be I will list all the required applications into a script and run it after install, still, the download limit is a problem! Anyway.. that is how I think it is.. Will cut on video calls in the month I install Ubuntu! :)

---

### Post by QLee on 2011-05-14
[QUOTE=NikS]...
The problem is that I have a fairly limited connection, 5GB per month and it becomes difficult to search and download all the applications I need every time I install Ubuntu.. While still trying to understand how things work, I bloat the system quite frequently! :) [/QUOTE]

I do understand limited connection as well as metered, perhaps this is a time for an amended method, a different strategy. Develop a backup solution that works for your situation, one that you can easily restore. 

The truth is that, most of the time, it is not necessary to re-install a system, it just can be easier in some instances and many inexperienced users come with that practice their standard practice. 

When I was in the situation of crashing more than I fixed I kept a separate install on another partition so I could boot up to it and have a working system to fix the other one with.

[QUOTE=NikS]Well.. may be I will list all the required applications into a script and run it after install, still, the download limit is a problem! Anyway.. that is how I think it is.. Will cut on video calls in the month I install Ubuntu! :)[/QUOTE]

If we are talking about only the one machine, it probably isn't worth doing a local mirror. Apt-move might be one to investigate if you want to try.

---

### Post by fabricator4 on 2011-05-14
> **NikS said:**
> Thanks QLee..
I understand it now..!

The problem is that I have a fairly limited connection, 5GB per month and it becomes difficult to search and download all the applications I need every time I install Ubuntu.. While still trying to understand how things work, I bloat the system quite frequently! :)

Well.. may be I will list all the required applications into a script and run it after install, still, the download limit is a problem! Anyway.. that is how I think it is.. Will cut on video calls in the month I install Ubuntu! :)

Indeed, you can cut your downloads by copying all the deb files in /var/cache/apt/archives.  I maintain three 10.04 machines and have been doing this for some time now as it saves literally 700 MB of downloads, including programs and my monthly bandwidth is less than yours.  As stated you will finish up with extra versions, but they don't cause any problems and are easy to get rid of - just look for duplicate filenames with slightly different release numbers in them.

It also makes changing friends from Win to Ubuntu easy.  I install 10.04 LTS for them and copy all the debs to /var/cache/apt/archives either during the install (you have to find the right mount point) or immediately after.  I tell them the update will not download very much but may take some time as there's quite a lot of it, and the system will take a performance hit during the updates.  Generally they do the update immediately while playing with their new OS.

Chris.

---

