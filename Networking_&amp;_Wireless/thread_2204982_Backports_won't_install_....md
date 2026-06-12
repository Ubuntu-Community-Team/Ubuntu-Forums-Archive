---
title: "Backports won't install ..."
date: 2014-02-11
forum: Networking &amp; Wireless
---

### Post by Rob Sayer on 2014-02-11
This may be an issue with lubuntu rather than wireless per se, but I can't think of a better place.

Just installed Lubuntu 13.10 on my netbook, updated until there wasn't any more.  It's blazing fast but there seems to be a bit more work involved, which isn't unexpected.

Did the same stuff I did before for my Broadcom 4313 (14e4:4727 rev 01) wireless adapter.  Installed linux-firmware-nonfree.  It's using the brcsmac driver, which mostly works OK anyway in 13.10.

Then I tried to do the same steps I did previously in this thread, post #14, to install backports-3.12.2-1 ...

[http://ubuntuforums.org/showthread.php?t=2191126&page=2](http://ubuntuforums.org/showthread.php?t=2191126&page=2)

... and it didn't work.  First, to my surprise, I had to install make.  Then i got a lot of error msgs when I ran make.

Unfortunately, the lubuntu terminal doesn't have copy and paste commands that I could find, or I'd post the output.  I'm looking for a terminal to install that does.

Fortunately it didn't bork brcmsmac as far as I can see ... wireless is still working.

Does anyone know what steps in lubuntu I'd need to take to get this to work?  It works in kubuntu 13.10 and also in mint 16 Mate, which is 13.10 based.

---

### Post by chili555 on 2014-02-11
See post #2 in the thread you linked. I believe you skipped:> Please get a temporary wired ethernet connection and do:

```
sudo apt-get install linux-headers-generic build-essential
```

Please try again. Since you have a flawed 'make,' clean up first:```
cd ~/Desktop/backports-3.12.2-1/
[COLOR="#FF0000"]make clean[/COLOR]
make defconfig-brcmsmac
make
sudo make install
sudo modprobe -r brcmsmac && sudo modprobe brcmsmac
```

---

### Post by Rob Sayer on 2014-02-11
Thanks, will do.  I didn't do the 1st step before ...

---

### Post by Rob Sayer on 2014-02-11
All right, it's working.  Thanks.

---

