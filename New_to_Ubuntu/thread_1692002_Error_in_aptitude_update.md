---
title: "Error in aptitude update"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by jonnybarnes on 2011-02-20
When I run sudo aptitude update -v and it returns this for one of the sources:

```
Err http://ppa.launchpad.net maverick/main amd64 Packages                       
  404  Not Found
```

I'm not sure how to tell which of my PPA sources I've added is the culprit. Anyone know if theres a log file I could look at that has the full URL thats returning 404?

Cheers

---

### Post by strongdrink on 2011-02-20
Try this..

sudo apt-get update

if it returns an error.. open /etc/apt/sources.list as root and delete that line.
It should be something like...

deb      [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages

---

### Post by Old_Grey_Wolf on 2011-02-20
> **jonnybarnes said:**
> When I run sudo aptitude update -v and it returns this for one of the sources:

```
Err http://ppa.launchpad.net maverick/main amd64 Packages                       
  404  Not Found
```

I'm not sure how to tell which of my PPA sources I've added is the culprit. Anyone know if theres a log file I could look at that has the full URL thats returning 404?

Cheers

It looks like the server you are using is not responding; therefore, the 404 error.

Get into Synaptic Package Manager and go to the menu "Settings > Repositories"; then, select "Other..." from the "Download from:" menu. Then click on the "Select Best Server" button. It will take some time for Synaptic to test the servers and give you a suggested server. When it does, click the "Choose Server button". Then follow the instructions to Reload.

Then try updating again.

Many times the problem will resolve itself after a few hours or days when the server has been updated or the network/server problem resolved.

---

### Post by jonnybarnes on 2011-02-21
Running sudo apt-get update worked as it threw this line at the end:

```
W: Failed to fetch http://ppa.launchpad.net/tsbarnes/inidicator-keylock/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found
```

So I knew which files to remove from my sources.list.d folder.

Cheers

---

