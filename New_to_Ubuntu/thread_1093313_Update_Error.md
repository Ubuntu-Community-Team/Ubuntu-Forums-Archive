---
title: "Update Error"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by raymondh on 2009-03-11
Doing an update today, I have this message:

E: etcinsvk:subprocess post-installation script returned error exit status 10
E: debian-edu-config: dependency problems -leaving unconfigured
E: debian-edu-install: dependency problems -leaving inconfigured

I was installing educational programs for the kids yesterday (gnome educational) thru synaptic manager when I was hit with a power outage.  Back online, I thought to run dpkg --configure -a in terminal (I had a similar incident previously) to no avail.

Any tips appreciated

Also tried synaptic>custom filters>broken  ... none listed

Should I go ahead and install all items on "missing recommend"?

---

### Post by stanz on 2009-03-11
Hey raymondhenson...power to ya - for trying!! 
Until someone more seasoned comes by...

Synaptic Package Manager is a front-end (GUI) to apt-get, I'll stop there--
cause you can read this yourself by typing in the terminal "man apt-get" (no quotes).
The terminal may be your friend here--and fix this error, which seams to me is
something being interrupted--while installing(?)

What order to do this...hopefully someone will help here.

I'd try an:
apt-get update
apt-get clean
apt-get dselect (not sure to include -upgrade}
apt-get -f

You'll see the explanation of those--while reading thru the man pages in your terminal.
Dependency problems need to be checked out differently...--maybe a version conflict?

I googled the:
[ E: etcinsvk:subprocess post-installation script returned error exit status 10]("http://www.google.ca/search?q=E%3A+etcinsvk%3Asubprocess+post-installation+script+returned+error+exit+status+10&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a")
and have 3 ubuntu specific results...check which one suits you.

I would wait -- before going ahead with installing items on "missing recommend"?

hope it helps~  :)

---

### Post by raymondh on 2009-03-11
Thanks ..... I think apt-get clean did the trick .... I tried to update again and did not get the error message

---

