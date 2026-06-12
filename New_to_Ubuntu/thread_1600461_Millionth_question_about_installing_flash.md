---
title: "Millionth question about installing flash"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by pzico on 2010-10-19
I barely remember any time when I have got flash installed properly without further tweaking. Why it just can't be made simple and always working?

For example right now when I tried to install it on 10.04 LTS x86:

sudo apt-get install flashplugin-installer
....
Downloading...
--2010-10-19 08:23:29--  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.85.3.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.85.3.orig.tar.gz)
Resolving archive.canonical.com... 91.189.88.33
Connecting to archive.canonical.com|91.189.88.33|:80... failed: Connection timed out.
Retrying.
....

So it stays on this loop forever..

---

### Post by pzico on 2010-10-19
Heh, I tried how would gnash work. It seems to make all annoying advertisements work, but the actual content I wanted to see doesn't ([www.slideshare.net](www.slideshare.net)). How convenient!

---

### Post by xXNI4NI on 2010-10-19
Not to sure if you need to purge your system of existing versions, (I had a problem back in 8.04 with that) but in 10.04 all I needed to do was to go to...
Applications -> Ubuntu Software Center -> Search for Adobe Flash Plugin -> I installed the plugin for Mozilla and was good to go.
Give it a shot and see if it works.

---

### Post by mikewhatever on 2010-10-19
It looks like something is wrong with the connection to Canonical's partner repository from your geographic location (works from mine). Trying again later usually works.
Remove Gnash before installing Adobe's plugin, otherwise it wouldn't work.

---

### Post by jmszr on 2010-10-19
pzico,

I have found FLASH-AID to work extremely well: [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/) .

Here is a thread that explains it: [http://ubuntuforums.org/showthread.php?t=1491268](http://ubuntuforums.org/showthread.php?t=1491268) .

---

### Post by dr_kabuto on 2010-10-19
Enable the 'Canonical Partner' repository then launch:
```
sudo apt-get install adobe-flashplugin
```

---

### Post by lovinglinux on 2010-10-19
> **dr_kabuto said:**
> Enable the 'Canonical Partner' repository then launch:
```
sudo apt-get install adobe-flashplugin
```

That doesn't matter. The flashplugin-installer package gets the flash tar.gz file from the partner repository, even if the repository is disabled.

This problem has been reported by several users. It seems Canonical's partner repository is failing frequently recently. Get flash directly from adobe at [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

---

### Post by ubudog on 2010-10-19
This command will install flash and a bunch of other codecs, for watching dvds, mp3's, etc.

```
sudo apt-get install ubuntu-restricted-extras
```

It is a big download and may take a while, so it is sometimes best to leave it on at night before sleep.

---

### Post by lovinglinux on 2010-10-19
> **ubudog said:**
> This command will install flash and a bunch of other codecs, for watching dvds, mp3's, etc.

```
sudo apt-get install ubuntu-restricted-extras
```

It is a big download and may take a while, so it is sometimes best to leave it on at night before sleep.

That is not the issue. The problem is that the Canonical partner repository is failing to connect on several occasions. Installing flashplugin-nonfree or ubuntu-restricted-extras will render the same results.

---

### Post by ubudog on 2010-10-19
> **lovinglinux said:**
> That is not the issue. The problem is that the Canonical partner repository is failing to connect on several occasions. Installing flashplugin-nonfree or ubuntu-restricted-extras will render the same results.

Ah, sorry.

---

### Post by TBABill on 2010-10-19
+1 on Flash Aid. Worked flawlessly on every install for me. Simple to use and lovinglinux supports you all the way if you need help.

---

### Post by lovinglinux on 2010-10-19
> **TBABill said:**
> +1 on Flash Aid. Worked flawlessly on every install for me. Simple to use and lovinglinux supports you all the way if you need help.

:popcorn:

---

