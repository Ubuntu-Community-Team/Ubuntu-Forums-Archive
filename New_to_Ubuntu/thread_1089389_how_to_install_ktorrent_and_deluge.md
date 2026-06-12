---
title: "how to install ktorrent and deluge?"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by beanco on 2009-03-07
OK, I had both prgms, there were some issues so I purged. remove them per instructions on a thread I started yesterday.

I want to reinstall them but I cannot,

at the command line I get this when trying sudo apt-get install ktorrent:

```
Err http://archive.ubuntu.com feisty/main libgmp3c2 2:4.2.1+dfsg-4build1
  404 Not Found [IP: 91.189.88.45 80]
Err http://archive.ubuntu.com feisty-backports/main ktorrent 2.2.5-0ubuntu1~feisty1
  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/gmp/libgmp3c2_4.2.1+dfsg-4build1_i386.deb  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/k/ktorrent/ktorrent_2.2.5-0ubuntu1~feisty1_i386.deb  404 Not Found [IP: 91.189.88.45 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

this when I tried sudo apt-get install deluge-torrent:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package deluge-torrent is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package deluge-torrent has no installation candidate
```

I could not get them to install via synaptic or add/remove either....

robi

ps, yeah I am still on Feisty....

---

### Post by Xiong Chiamiov on 2009-03-07
Did you
```

sudo apt-get update && apt-get install ktorrent && apt-cache search deluge

```
Update will update the package lists; your first error is probably caused by the fact that you're looking for files that don't exist any more, because they've been updated, and the version number upped.

Install you know.

Apt-cache search searches packages for deluge.  Find the one you want and install it.

---

### Post by sisco311 on 2009-03-07
Feisty does not have ongoing support and has now been removed from the normal archives and mirrors. So you can not use the repositories to install applications.

You can upgrade to gutsy (supported until April 2009) and then to Hardy. But I would recommend a fresh installation of Hardy  or Intrepid. 

[uwiki]Releases[/uwiki]
[uhelp]community/GutsyUpgrades[/uhelp]
[uhelp]community/HardyUpgrades[/uhelp]

---

### Post by ugm6hr on 2009-03-07
[http://ubuntuforums.org/showthread.php?p=6319924#post6319924](http://ubuntuforums.org/showthread.php?p=6319924#post6319924)

---

### Post by iamkrazee on 2009-03-07
> **sisco311 said:**
> Feisty does not have ongoing support and has now been removed from the normal archives and mirrors. So you can not use the repositories to install applications.

You can upgrade to gutsy (supported until April 2009) and then to Hardy. But I would recommend a fresh installation of Hardy  or Intrepid. 

[uwiki]Releases[/uwiki]
[uhelp]community/GutsyUpgrades[/uhelp]
[uhelp]community/HardyUpgrades[/uhelp]

Or kubuntu-jaunty, but it doesn't come with ktorrent either. lol

---

### Post by beanco on 2009-03-07
well, for some reason I have been procrastinating getting newer versions of ubuntu.... i kind of like having one thing that works, be it a car, a computer a bike, skis, whatever and really prefer that to always getting the newest thing.... 

back on track now.... i either have to get a new flavour of ubuntu going or use the link that Ugm... provided.... well, I di dnot quite understand that info.. ie. I have no idea how to edit the source list.. but I will give it a look. if it fails, then I will get intrepid...

Xiong, what are the && for in your code?

I tried simply sudo apt-get update

and got  this... well this is just the end...:

```
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz  Could not resolve 'medibuntu.sos-sts.com'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

I assume the issue here is that feisty is old....

thanks all for the help.

robi

---

### Post by ugm6hr on 2009-03-07
> **beanco said:**
> use the link that Ugm... provided.... well, I di dnot quite understand that info.. ie. I have no idea how to edit the source list.. but I will give it a look. if it fails, then I will get intrepid...

I would still advise upgrading (for security reasons), but, if you want to stick with Feisty, just post output from:

```
cat /etc/apt/sources.list
```

Then backup the original:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
```

I will edit and repost, then you can just copy & paste into a new file.

---

### Post by iamkrazee on 2009-03-07
To edit sources list : 

```
 sudo kate /etc/apt/sources.list
```

*replace kate by whichever editor you want.

If you want latest stable, go for intrepid.

If you want latest proven stable with Long Time Support(LTS) go for Hardy.

If you want bleeding edge latest, go for jaunty alpha5.

---

### Post by beanco on 2009-03-07
well, this is becoming more intriguing.

I like the idea of sticking with feisty, editing the source and all, I would have the illusion that I am learning sg that could be useful .

REgarding upgrading... well if I go for Intrepid do I have to go through the other verisons  or can I jump right to Intrepid? Just how safe is it to update without backing up the important files first? Just curious.... and lazy... no time or way to get CD/DVd/pendrive for backing up right now.....

robi

---

### Post by iamkrazee on 2009-03-07
You can jump to whichever version you like, without trouble. But it´s always a good idea to back the data up regardless. No fool-proof guarantees anywhere. There are non-ubuntu factors in the world too you know, like power failure. Or a tornado. lol

---

### Post by ugm6hr on 2009-03-07
> **beanco said:**
> REgarding upgrading... well if I go for Intrepid do I have to go through the other verisons  or can I jump right to Intrepid? Just how safe is it to update without backing up the important files first? Just curious.... and lazy... no time or way to get CD/DVd/pendrive for backing up right now.....

If you want to upgrade, you have to upgrade sequentially.

If you do a fresh new installation, you can jump to any version.

I would not recommend upgrading without a backup, unless you have a separate /home partition, or your data is not that valuable to you.

---

### Post by beanco on 2009-03-07
Ugm,

there is some imrortant stuff on it, but I am stuck at home for a few days and decided to get the computer problems taken care of...

now I understand the difference between update and new install, so thanks.


robi

---

### Post by Xiong Chiamiov on 2009-03-07
> **beanco said:**
> Xiong, what are the && for in your code?
&& is the binary operator for "and" in bash.  If the first operation is successful, then it will continue on to the next.  It's an easy way to string multiple commands on one line.

I didn't realize that Fiesty's unsupported now, so forget what I said and pay attention to these guys.

---

