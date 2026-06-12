---
title: "Unable to download repository indexes"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by benjamin.s.vaccaro on 2009-05-12
Hello,

I am currently using Ubuntu 9.01 and initially there appeared to be no issues. However I suddenly cannot download repositories. I have a notification icon saying that i need to manually check for updates so I did so. And during the process of finding repositories another notification window appears saying 
"The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct."

within the suggestions box underneath that text is:
"Failed to fetch [http://wine.budgetdedicated.com/apt/dists/edgy/Release](http://wine.budgetdedicated.com/apt/dists/edgy/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)"

"Some index files failed to download, they have been ignored, or old ones used instead."

Is anyone suffering from this?

Note: I am using a wireless router and I have very little signal strength, but that will change by next week. I also doubt it is the wireless as it as never been an issue before.

Thanks.

---

### Post by Elfy on 2009-05-12
You have an edgy repo in there - edit the file and remove it - if there are more remove them too then try the update again.

Backup the file first

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
gksudo gedit /etc/apt/sources.list
sudo apt-get update
```

---

### Post by benjamin.s.vaccaro on 2009-05-13
That worked, thanks.

---

### Post by benjamin.s.vaccaro on 2009-05-13
Okay, so that worked as a temporary solution. But I'm back at my question again.

---

### Post by Elfy on 2009-05-13
Which question?

---

### Post by benjamin.s.vaccaro on 2009-05-13
Is there a permanent resolution?
I use to just use:
sudo aptitude update
sudo aptitude full-upgrade

but since the repositories aren't loading then i'm upgrading nothing.

---

### Post by alaukik.kot on 2009-08-07
hello guys;
  even i encountered same problem. whet i tried above remedy, i got this message cp: cannot stat `/etc/apt/source.list': No such file or directory

---

### Post by drs305 on 2009-08-07
> **alaukik.kot said:**
> hello guys;
  even i encountered same problem. whet i tried above remedy, i got this message cp: cannot stat `/etc/apt/source.list': No such file or directory

Bit of a typo there: source[COLOR="Red"]s[/COLOR].list

---

### Post by alaukik.kot on 2009-08-07
thanks, i did that change and again applied for updates and recived this message 
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by drs305 on 2009-08-07
> **alaukik.kot said:**
> thanks, i did that change and again applied for updates and recived this message 
E: Some index files failed to download, they have been ignored, or old ones used instead.

You can try a different server (Synaptic, Settings, Repositories, download from: Other). If you think there are errors in your sources.list you can post it here and we'll take a look at it.

---

### Post by alaukik.kot on 2009-08-08
deb [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

deb [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

deb [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

deb [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-netbook-remix main universe multiverse restricted
deb-src [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-netbook-remix main universe multiverse restricted

---

### Post by alaukik.kot on 2009-08-08
This is my source.list


and
 my comp config - 
alaukik@alaukik-desktop:~$ uname -a
Linux alaukik-desktop 2.6.27-14-generic #1 SMP Tue Jun 30 19:54:46 UTC 2009 x86_64 GNU/Linux

---

### Post by drs305 on 2009-08-08
alaukik.kot,

I've looked at your sources.list - in fact I used it myself to test it. I don't know how the netbook-remix repositories are set up, but the one you have is missing most of the normal folders. For example, compare what is in both the netbook-remix "main" and my karmic "main" folders:

[_http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/_]("http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/")

[_http://netbook-remix.archive.canonical.com/ubuntu/dists/hardy/main/_]("http://netbook-remix.archive.canonical.com/ubuntu/dists/hardy/main/")

You are getting the message because most of the places your sources.list is trying to look don't exist.

Try changing to another server in Software Sources or Synaptic, Settings, Repositories, "Download from", select Other.

You can check a repository's integrity by taking the address from sources.list and putting it in a browser and clicking through the folders. From the original address, the progression is usually something like:
... dists >> hardy >> (_main_, multiverse, restricted, universe) >> and then about 5-8 subfolders in each of those containing 32-bit, 64-bit, installers, binaries, etc.

---

