---
title: "How to download updates offline"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by dileepdinesh on 2008-12-10
Hi,
   I have to install 8.04(kubuntu) on my destkop. I have access to only dialup internet. I know that the updates are more than 250MB, its almost impossible to download that via dialup. Anyway my friend do have broad band internet connection,,but unfortunately it is windows....
           Is there anyway via which i can download all updates via windows and install it in my desktop

---

### Post by rakris on 2008-12-10
Ask your friend to install Ubuntu.

Clear the /var/apt/cache.

do a sudo apt-get upgrade.

then copy the files to your computer.

see if it works..

:P

---

### Post by HavocXphere on 2008-12-10
You could try running a liveCD on his box...but I'm not 100% sure how adept behaves in a liveCD environment.

Or you could install kubuntu on an extra drive/memory stick and boot from the external drive on his PC.

If its a specific big file, then use a download manager on flaky connections (kget etc). Then put the file into the apt cache.

---

### Post by robert shearer on 2008-12-10
You may want to try this app.

It is beta so would be an experiment but sounds promising.

I have not used it myself.
Post back if it works for you.

[http://keryx.betaserver.org/](http://keryx.betaserver.org/)

---

### Post by hyper_ch on 2008-12-10
(1) in the cli run
```

sudo apt-get update && sudo apt-get upgrade

```
That will give you a list of all packages that are needed to upgrade.

(2) Use that list to download them somewhere else. On ubuntu you can run
```

sudo apt-get --download-only package1 package2 package2 ...

```
Not sure where the files will be downloaded to... but I think it's also /var/apt/cache
If that's the case, then first clean that folder:
```

sudo apt-get clean

```
Then copy all the files in /var/apt/cache

(3) or if you don't have someone iwth ubuntu you can download all packages manually from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by theozzlives on 2008-12-10
> **dileepdinesh said:**
> Hi,
   I have to install 8.04(kubuntu) on my destkop. I have access to only dialup internet. I know that the updates are more than 250MB, its almost impossible to download that via dialup. Anyway my friend do have broad band internet connection,,but unfortunately it is windows....
           Is there anyway via which i can download all updates via windows and install it in my desktop

In this day and age, you really need broadband. Heck, I don't even have a land-line phone.

---

