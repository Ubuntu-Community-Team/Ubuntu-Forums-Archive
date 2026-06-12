---
title: "How can I start update-manager"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by Pierrot Lafouine on 2009-08-26
I don't know why, the icon update-manager used to be there, now it disappear.

How can I start update-manager from command line ?

Or how can I restore the update-manager icon in system/administration ?

I'm using version 7.10
Thanks

---

### Post by alexlafreniere on 2009-08-26
```
sudo apt-get update

```

---

### Post by alexlafreniere on 2009-08-26
Or choose System &#8594; Administration &#8594; Update Manager and press **Check**.

---

### Post by tperwez on 2009-08-26
Typically ALT-F2 should launch the application loader and you can then type in update-manager in the window and hit Enter. I believe this should work for 7.10. Good luck.

---

### Post by slakkie on 2009-08-26
If you use 7.10, upgrade to 8.04.

See the EOL link in my sig.

---

### Post by michy99 on 2009-08-26
7.10 has not been supported since April 18, 2009, so you won't get any updates, anyway.

[http://www.ubuntu.com/news/ubuntu-7.10-eol](http://www.ubuntu.com/news/ubuntu-7.10-eol)

---

### Post by nick_nik on 2009-08-26
```
update-manager -d
```

will do a distribution upgrade to a more current version

---

### Post by Pierrot Lafouine on 2009-08-26
> **michy99 said:**
> 7.10 has not been supported since April 18, 2009, so you won't get any updates, anyway.

[http://www.ubuntu.com/news/ubuntu-7.10-eol](http://www.ubuntu.com/news/ubuntu-7.10-eol)

Ok thanks
Can I upgrade with CD ?  Or it will install fresh files only ?
Thanks

---

### Post by michy99 on 2009-08-26
You should be able to upgrade to 8.04, which is a LTS release on will be supported through April, 2011.

First you have to open sources.list for editing.```
gksudo gedit /etc/apt/sources.list
```Everwhere you see 'archive.ubuntu.com' replace it with 'old-releases.ubuntu.com. For example:```
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
```becomes```
deb http://us.old-releases.ubuntu.com/ubuntu/ gutsy universe
```After making the changes, save and close the file. Then run```
sudo apt-get update && sudo apt-get upgrade
```After that finishes, run```
update-manager -d
```

---

### Post by Todamont on 2013-01-15
none of you guys answered the question...

How to launch update manager from command line?

---

### Post by oldos2er on 2013-01-16
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

