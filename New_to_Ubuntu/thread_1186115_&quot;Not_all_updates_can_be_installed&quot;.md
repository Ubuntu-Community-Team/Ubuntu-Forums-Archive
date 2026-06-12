---
title: "&quot;Not all updates can be installed&quot;"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by watermole on 2009-06-13
Hello,
I'm a very new user, trying to get Ubuntu to work on an old Dell Dimension T600.  A while ago I installed 8.01 and then did not get back to it until last week.  I've been trying to update to the latest version, but I keep getting a "Not all updates can be installed", message. Even more weird, when I look for the version installed I get blanks.

One of the causes noted is "a previous update did not complete" which is what I think happened, but I don't know how to fix it.  Here are three screen shots.

[http://picasaweb.google.com/lh/photo/AkrmTA_q-8R07KV8rzB4GA?feat=directlink](http://picasaweb.google.com/lh/photo/AkrmTA_q-8R07KV8rzB4GA?feat=directlink)
[http://picasaweb.google.com/lh/photo/tbr7qie5s08MdBdnGqFJaw?feat=directlink](http://picasaweb.google.com/lh/photo/tbr7qie5s08MdBdnGqFJaw?feat=directlink)
[http://picasaweb.google.com/lh/photo/e2GCjemD8S9uova_1Qirsg?feat=directlink](http://picasaweb.google.com/lh/photo/e2GCjemD8S9uova_1Qirsg?feat=directlink)
[IMG]http://picasaweb.google.com/lh/photo/e2GCjemD8S9uova_1Qirsg?feat=directlink[/IMG]

[IMG]http://picasaweb.google.com/lh/photo/AkrmTA_q-8R07KV8rzB4GA?feat=directlink[/IMG]

---

### Post by nandemonai on 2009-06-13
I'm assuming you tried the 'mark all upgrades' option in synaptic?

How's about in terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

If that doesn't do it for you then please post the output of:

```
cat /etc/apt/sources.list
```

And finally:

```
ls -l /etc/apt/sources.list.d/
```

Also, please attach any errors you come across using these commands. ;)

---

### Post by Paddy Landau on 2009-06-25
I have exactly the same problem. I've attached the [precise message below]("http://ubuntuforums.org/attachment.php?attachmentid=118911&stc=1&d=1245931506"), and it refers to python-libtorrent.

I've put in the code as nandemonai suggested, and here are the results.

```
$ sudo apt-get update
<lots of output, and then...>
Fetched 2B in 1s (1B/s)
Reading package lists... Done
``````
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  python-libtorrent
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```File: /etc/apt/sources.list <see [attachment sources.list.txt]("http://ubuntuforums.org/attachment.php?attachmentid=118913&stc=1&d=1245931506")>

```
$ ls -l /etc/apt/sources.list.d/
total 24
-rw-r--r-- 1 root root 166 2009-05-29 16:13 medibuntu.list
-rw-r--r-- 1 root root 166 2009-05-29 16:13 medibuntu.list.save
-rw-r--r-- 1 root root 138 2009-05-29 16:13 playonlinux.list
-rw-r--r-- 1 root root 138 2009-05-29 16:13 playonlinux.list.save
-rw-r--r-- 1 root root  73 2009-05-05 23:01 spideroak.com.sources.list
-rw-r--r-- 1 root root  75 2009-05-13 14:45 spideroak.com.sources.list.save
```Thanks in advance...

---

### Post by madverb on 2009-06-25
sudo apt-get dist-upgrade

---

### Post by nandemonai on 2009-06-25
> **Paddy Landau said:**
> I have exactly the same problem. I've attached the [precise message below]("http://ubuntuforums.org/attachment.php?attachmentid=118911&stc=1&d=1245931506"), and it refers to python-libtorrent.

I've put in the code as nandemonai suggested, and here are the results.

```
$ sudo apt-get update
<lots of output, and then...>
Fetched 2B in 1s (1B/s)
Reading package lists... Done
``````
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  python-libtorrent
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```File: /etc/apt/sources.list <see [attachment sources.list.txt]("http://ubuntuforums.org/attachment.php?attachmentid=118913&stc=1&d=1245931506")>

```
$ ls -l /etc/apt/sources.list.d/
total 24
-rw-r--r-- 1 root root 166 2009-05-29 16:13 medibuntu.list
-rw-r--r-- 1 root root 166 2009-05-29 16:13 medibuntu.list.save
-rw-r--r-- 1 root root 138 2009-05-29 16:13 playonlinux.list
-rw-r--r-- 1 root root 138 2009-05-29 16:13 playonlinux.list.save
-rw-r--r-- 1 root root  73 2009-05-05 23:01 spideroak.com.sources.list
-rw-r--r-- 1 root root  75 2009-05-13 14:45 spideroak.com.sources.list.save
```Thanks in advance...

I usually get around this by 'marking all upgrades' in synaptic (package being held back). I'm not sure why this happens (dependency issues?) or how to get around it with apt-get. Possibly apt-get -f?

If anyone can shed more light on the matter for me that would be awesome. I'm pretty sure packages are held back for a reason. Be it dependency or possible known bugs / breakage? I don't quite know.

---

### Post by Paddy Landau on 2009-06-25
> **madverb said:**
> sudo apt-get dist-upgrade
That didn't work.

But I had a thought.

Using Synaptic Package Manger, I uninstalled python-libtorrent (it had no dependencies).

Then I reinstalled python-libtorrent (the latest version). It gave this message:

*To be removed: libtorrent-raster1. To be installed: libtorrent-raster4.*

That fixed the problem!

Clearly, there was some dependency that was not visible earlier.

As python-libtorrent has no dependencies, is it OK for me to uninstall python-libtorrent anyway? Or is there something important about it?

---

### Post by Paddy Landau on 2009-06-25
> **nandemonai said:**
> ... 'marking all upgrades' in synaptic 
Pity I didn't see your post until after I'd posted mine! I'll bear it in mind.

---

### Post by nandemonai on 2009-06-25
I found this on the topic of held back updates, makes sense now. :)

[https://answers.launchpad.net/ubuntu/+question/18330](https://answers.launchpad.net/ubuntu/+question/18330)

---

